
<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#15121e">
<title>EasyDND</title>
<style>
*{box-sizing:border-box}
body{margin:0;background:#15121e;color:#f5eddf;font:16px system-ui,sans-serif}
main{max-width:650px;margin:auto;padding:24px 16px}
h1,h2{color:#e9c77e}
.card{background:#25202f;border:1px solid #504158;border-radius:14px;padding:18px;margin:14px 0}
button,input{font:inherit;padding:12px;border-radius:8px}
button{border:0;background:#e9c77e;color:#211927;font-weight:bold;cursor:pointer}
button:disabled{opacity:.5;cursor:wait}
input{width:100%;margin:8px 0;background:#17131f;color:white;border:1px solid #67546f}
.muted{color:#c2b8cc;font-size:13px;line-height:1.7;overflow-wrap:anywhere}
.status{padding:12px;background:#1c3028;border:1px solid #47634f;border-radius:10px;overflow-wrap:anywhere}
.error{background:#351f27;border-color:#8b4856;color:#ffc4c4}
.hidden{display:none!important}
.code{font-size:28px;letter-spacing:3px;color:#e9c77e;font-weight:bold;overflow-wrap:anywhere}
.actions{display:flex;gap:8px;flex-wrap:wrap}
.actions button{margin-top:8px}
</style>
</head>
<body>
<main>
<h1>⚔ EasyDND</h1>
<p class="muted">Your adventure begins.</p>

<div id="status" class="status">กำลังเชื่อมต่อ Firebase...</div>
<p id="uid" class="muted"></p>

<section id="home">
<div class="card">
<h2>👑 สร้างห้องเกม</h2>
<p class="muted">สร้างแคมเปญใหม่ คุณจะเป็น Dungeon Master</p>
<input id="newName" maxlength="40" placeholder="ชื่อแคมเปญ">
<button id="createBtn" disabled>สร้างห้องเกม</button>
</div>

<div class="card">
<h2>🗝️ เข้าร่วมห้องเกม</h2>
<p class="muted">กรอกรหัส 8 ตัวที่ DM ส่งให้</p>
<input id="joinCode" maxlength="8" placeholder="รหัสห้อง">
<button id="joinBtn" disabled>ขอเข้าร่วมห้อง</button>
</div>
</section>

<section id="room" class="card hidden">
<p id="role" class="muted"></p>
<h2 id="roomName"></h2>
<p class="muted">รหัสห้อง</p>
<div id="roomCode" class="code"></div>
<div class="actions">
<button id="copyBtn">คัดลอกรหัส</button>
<button id="homeBtn">กลับหน้าหลัก</button>
</div>
<p id="roomStatus" class="muted"></p>
<section id="requests" class="hidden">
<h2>คำขอเข้าร่วม</h2>
<div id="requestList"></div>
</section>
</section>

<p class="muted">EasyDND · Virtual Tabletop</p>
</main>

<script type="module">
import { initializeApp }
from "https://www.gstatic.com/firebasejs/12.5.0/firebase-app.js";
import { getAuth, signInAnonymously }
from "https://www.gstatic.com/firebasejs/12.5.0/firebase-auth.js";
import {
 getDatabase, ref, get, set, remove, onValue
} from "https://www.gstatic.com/firebasejs/12.5.0/firebase-database.js";

const firebaseConfig = {
 apiKey: "AIzaSyApLGFjitTleBjPCbaHgL2QZ1Bxdw2uYlY",
 authDomain: "easydnd-1ab42.firebaseapp.com",
 databaseURL: "https://easydnd-1ab42-default-rtdb.asia-southeast1.firebasedatabase.app",
 projectId: "easydnd-1ab42",
 storageBucket: "easydnd-1ab42.firebasestorage.app",
 messagingSenderId: "755955885657",
 appId: "1:755955885657:web:5aceef5392db3b98673348",
 measurementId: "G-JVV8WY0BXT"
};

const $ = id => document.getElementById(id);
const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getDatabase(app);

let currentRoom = null;
let listeners = [];
let busy = false;

function setStatus(text, error = false) {
 $("status").textContent = text;
 $("status").classList.toggle("error", error);
}

function stopListeners() {
 listeners.forEach(unsubscribe => unsubscribe());
 listeners = [];
}

function makeCode() {
 const chars = "ABCDEFGHJKLMNPQRSTUVWXYZ23456789";
 let result = "";
 for (let i = 0; i < 8; i++) {
  result += chars[Math.floor(Math.random() * chars.length)];
 }
 return result;
}

function showRoom(id, info, role) {
 stopListeners();
 currentRoom = id;
 $("home").classList.add("hidden");
 $("room").classList.remove("hidden");
 $("roomName").textContent = info.name;
 $("roomCode").textContent = id;
 $("role").textContent =
  role === "dm" ? "👑 คุณเป็น DM ของห้องนี้" : "🧙 ผู้เล่น";
 $("requests").classList.toggle("hidden", role !== "dm");
 $("roomStatus").textContent =
  role === "dm"
   ? "ส่งรหัสห้องให้เพื่อนเพื่อให้ส่งคำขอเข้าร่วม"
   : "กำลังตรวจสอบสถานะสมาชิก";

 const memberRef = ref(
  db, `rooms/${id}/members/${auth.currentUser.uid}`
 );

 listeners.push(onValue(memberRef, snap => {
  if (role === "player" && snap.exists()) {
   $("roomStatus").textContent = "DM อนุมัติให้เข้าห้องแล้ว";
  }
 }, error => {
  $("roomStatus").textContent =
   "อ่านสถานะสมาชิกไม่ได้: " + error.message;
 }));

 if (role !== "dm") return;

 const requestRef = ref(db, `rooms/${id}/joinRequests`);

 listeners.push(onValue(requestRef, snap => {
  const list = $("requestList");
  list.replaceChildren();

  const requests = snap.val() || {};
  const entries = Object.entries(requests);

  if (entries.length === 0) {
   list.textContent = "ยังไม่มีคำขอเข้าร่วม";
   return;
  }

  for (const [uid] of entries) {
   const card = document.createElement("div");
   card.className = "card";

   const label = document.createElement("p");
   label.textContent = "ผู้เล่น " + uid.slice(0, 10);

   const approve = document.createElement("button");
   approve.textContent = "อนุมัติ";
   approve.onclick = async () => {
    try {
     await set(
      ref(db, `rooms/${id}/members/${uid}`),
      { uid, role: "player", joinedAt: Date.now() }
     );
     await remove(
      ref(db, `rooms/${id}/joinRequests/${uid}`)
     );
     setStatus("อนุมัติผู้เล่นเรียบร้อย");
    } catch (e) {
     setStatus("อนุมัติไม่สำเร็จ: " + e.message, true);
    }
   };

   const deny = document.createElement("button");
   deny.textContent = "ปฏิเสธ";
   deny.style.marginLeft = "8px";
   deny.onclick = async () => {
    try {
     await remove(
      ref(db, `rooms/${id}/joinRequests/${uid}`)
     );
    } catch (e) {
     setStatus("ปฏิเสธไม่สำเร็จ: " + e.message, true);
    }
   };

   card.append(label, approve, deny);
   list.append(card);
  }
 }, error => {
  setStatus("อ่านคำขอไม่ได้: " + error.message, true);
 }));
}

$("createBtn").addEventListener("click", async () => {
 if (busy) return;
 const name = $("newName").value.trim();

 if (!name) {
  setStatus("กรุณาพิมพ์ชื่อแคมเปญก่อน", true);
  $("newName").focus();
  return;
 }

 busy = true;
 $("createBtn").disabled = true;
 setStatus("กำลังสร้างห้องเกม...");

 try {
  let id = null;

  for (let i = 0; i < 5; i++) {
   const candidate = makeCode();
   const check = await get(ref(db, `rooms/${candidate}/info`));
   if (!check.exists()) {
    id = candidate;
    break;
   }
  }

  if (!id) throw new Error("สร้างรหัสห้องไม่สำเร็จ");

  const info = {
   name: name.slice(0, 40),
   ownerUid: auth.currentUser.uid,
   createdAt: Date.now()
  };

  await set(ref(db, `rooms/${id}/info`), info);

  await set(
   ref(db, `rooms/${id}/members/${auth.currentUser.uid}`),
   {
    uid: auth.currentUser.uid,
    role: "dm",
    joinedAt: Date.now()
   }
  );

  showRoom(id, info, "dm");
  setStatus("✓ สร้างห้องสำเร็จ");
 } catch (e) {
  setStatus(
   "สร้างห้องไม่สำเร็จ: " + (e.code || e.message),
   true
  );
 } finally {
  busy = false;
  $("createBtn").disabled = false;
 }
});

$("joinBtn").addEventListener("click", async () => {
 if (busy) return;

 const id = $("joinCode").value.trim().toUpperCase();

 if (!/^[A-HJ-NP-Z2-9]{8}$/.test(id)) {
  setStatus("รหัสห้องต้องมี 8 ตัว กรุณาตรวจสอบอีกครั้ง", true);
  return;
 }

 busy = true;
 $("joinBtn").disabled = true;
 setStatus("กำลังค้นหาห้อง...");

 try {
  const infoSnap = await get(ref(db, `rooms/${id}/info`));

  if (!infoSnap.exists()) {
   throw new Error("ไม่พบห้องนี้ กรุณาตรวจสอบรหัสห้อง");
  }

  const info = infoSnap.val();
  const uid = auth.currentUser.uid;
  const memberRef = ref(db, `rooms/${id}/members/${uid}`);
  const memberSnap = await get(memberRef);

  if (memberSnap.exists()) {
   showRoom(id, info, memberSnap.val().role);
   setStatus("✓ คุณเป็นสมาชิกห้องนี้อยู่แล้ว");
   return;
  }

  await set(
   ref(db, `rooms/${id}/joinRequests/${uid}`),
   {
    uid,
    displayName: "ผู้เล่น",
    requestedAt: Date.now()
   }
  );

  showRoom(id, info, "player");
  $("roomStatus").textContent = "ส่งคำขอแล้ว รอ DM อนุมัติ";
  setStatus("✓ ส่งคำขอเข้าร่วมแล้ว");
 } catch (e) {
  setStatus(
   "เข้าร่วมห้องไม่สำเร็จ: " + (e.code || e.message),
   true
  );
 } finally {
  busy = false;
  $("joinBtn").disabled = false;
 }
});

$("copyBtn").addEventListener("click", async () => {
 if (!currentRoom) return;

 try {
  await navigator.clipboard.writeText(currentRoom);
  $("roomStatus").textContent = "คัดลอกรหัสห้องแล้ว";
 } catch {
  $("roomStatus").textContent = "รหัสห้องของคุณคือ: " + currentRoom;
 }
});

$("homeBtn").addEventListener("click", () => {
 stopListeners();
 currentRoom = null;
 $("room").classList.add("hidden");
 $("home").classList.remove("hidden");
});

async function start() {
 try {
  await signInAnonymously(auth);
  $("uid").textContent =
   "รหัสผู้เล่น: " + auth.currentUser.uid;
  $("createBtn").disabled = false;
  $("joinBtn").disabled = false;
  setStatus("✓ เชื่อมต่อ Firebase สำเร็จ พร้อมใช้งาน");
 } catch (e) {
  setStatus(
   "เชื่อมต่อ Firebase ไม่สำเร็จ: " + (e.code || e.message),
   true
  );
 }
}

start();
</script>
</body>
</html>
