<!doctype html>
<html lang="th">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>EasyDND - Virtual Tabletop</title>
<style>
:root{color-scheme:dark;--bg:#10131b;--panel:#1b2130;--panel2:#252d40;--line:#3b465e;--accent:#b49aff;--text:#f5f5fb;--muted:#b7bfd1;--green:#86e5b2}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font:16px/1.5 system-ui,sans-serif}
main{max-width:1000px;margin:auto;padding:16px}
h1{margin:4px 0;font-size:29px}h2{font-size:21px;margin:0 0 12px}
.panel{background:var(--panel);border:1px solid var(--line);border-radius:14px;padding:16px;margin:14px 0}
input,button{font:inherit;border-radius:9px;padding:11px;border:1px solid var(--line)}
input{background:#111622;color:var(--text);width:100%;min-width:0}
button{background:var(--accent);color:#171322;font-weight:700;border:0;cursor:pointer}
button.secondary{background:var(--panel2);color:var(--text);border:1px solid var(--line)}
button.danger{background:#6c3540;color:white}
button:disabled{opacity:.5}
.row{display:flex;gap:9px;align-items:center;flex-wrap:wrap}
.row>*{flex:1;min-width:110px}
.muted{color:var(--muted);font-size:14px}
.status{padding:11px;background:#141a26;border:1px solid var(--line);border-radius:9px;white-space:pre-wrap;overflow-wrap:anywhere}
.hidden{display:none!important}
.pill{font-size:13px;background:var(--panel2);padding:3px 9px;border-radius:20px}
.two{display:grid;grid-template-columns:1fr;gap:12px}
.requests,.messages{display:flex;flex-direction:column;gap:8px}
.request,.message{background:#141a26;border:1px solid var(--line);border-radius:9px;padding:10px}
.request{display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap}
.request button{padding:7px 10px}
.messages{max-height:260px;overflow-y:auto}
.meta{font-size:12px;color:var(--muted);margin-bottom:3px}
.body{white-space:pre-wrap;overflow-wrap:anywhere}
.board{display:grid;grid-template-columns:repeat(8,minmax(0,1fr));gap:4px;max-width:560px;margin:14px auto}
.cell{position:relative;aspect-ratio:1;min-width:0;padding:0;display:flex;align-items:center;justify-content:center;background:#2a354a;border:1px solid #4a5872;border-radius:5px}
.cell:nth-child(even){background:#202a3c}
.token{font-size:clamp(16px,4vw,27px)}
.cell small{position:absolute;right:3px;bottom:1px;font-size:9px;color:#b9c3d8}
.result{font-size:23px;font-weight:800;color:var(--green)}
.dice{display:flex;gap:7px;flex-wrap:wrap}
.dice button{flex:1;min-width:55px}
footer{text-align:center;color:var(--muted);font-size:12px;padding:20px}
@media(min-width:720px){.two{grid-template-columns:1fr 1fr}}
</style>
</head>
<body>
<main>
<header>
<h1>🎲 EasyDND</h1>
<div class="muted">โต๊ะเล่น Dungeons & Dragons ออนไลน์</div>
</header>

<section id="loginPanel" class="panel">
<h2>ชื่อผู้เล่น</h2>
<div class="row">
<input id="displayName" maxlength="30" placeholder="ใส่ชื่อที่ใช้ในเกม">
<button id="saveNameBtn">ยืนยันชื่อ</button>
</div>
<p class="muted">ใช้บัญชี Firebase แบบไม่ต้องตั้งรหัสผ่าน</p>
</section>

<section id="homePanel" class="hidden">
<div class="panel">
<h2>สร้างห้อง (DM)</h2>
<div class="row">
<input id="roomName" maxlength="40" placeholder="ชื่อห้องผจญภัย">
<button id="createRoomBtn">สร้างห้อง</button>
</div>
</div>
<div class="panel">
<h2>เข้าร่วมห้อง (ผู้เล่น)</h2>
<div class="row">
<input id="roomCode" maxlength="6" placeholder="รหัสห้อง 6 ตัว">
<button id="joinRoomBtn">ขอเข้าห้อง</button>
</div>
</div>
</section>

<section id="roomPanel" class="hidden">
<div class="panel">
<div class="row">
<div>
<h2 id="roomTitle">ห้อง</h2>
รหัส: <strong id="roomCodeDisplay"></strong>
<span class="pill" id="roleDisplay"></span>
</div>
<button class="secondary" id="copyCodeBtn">คัดลอกรหัส</button>
<button class="secondary" id="leaveRoomBtn">ออกจากห้อง</button>
</div>
<div id="roomStatus" class="status" style="margin-top:12px">กำลังโหลด…</div>
</div>
<div id="dmPanel" class="panel hidden">
<h2>คำขอเข้าห้อง</h2>
<div id="requests" class="requests"><p class="muted">ยังไม่มีคำขอ</p></div>
</div>
<div id="pendingPanel" class="panel hidden">
<h2>กำลังรอ DM อนุมัติ</h2>
<p>เมื่อ DM อนุมัติแล้ว ปุ่มเข้าสู่โต๊ะเล่นจะปรากฏที่นี่</p>
</div>
<div id="approvedPanel" class="panel hidden">
<h2>พร้อมเล่นแล้ว</h2>
<button id="enterGameBtn">เข้าสู่โต๊ะเล่น 🎲</button>
</div>
</section>

<section id="gamePanel" class="hidden">
<div class="panel">
<div class="row">
<div>
<h2 id="gameTitle">โต๊ะเล่น</h2>
<div class="muted">ห้องเดียวกันจะเห็นผลทอยเต๋า แชต และตัวหมากร่วมกัน</div>
</div>
<button class="secondary" id="backRoomBtn">กลับหน้าห้อง</button>
</div>
</div>

<div class="two">
<div class="panel">
<h2>🎲 ทอยเต๋า</h2>
<div class="dice" id="diceButtons">
<button data-die="4">d4</button><button data-die="6">d6</button>
<button data-die="8">d8</button><button data-die="10">d10</button>
<button data-die="12">d12</button><button data-die="20">d20</button>
<button data-die="100">d100</button>
</div>
<p id="diceResult" class="result">ยังไม่มีผลทอย</p>
<div class="muted">ผลทอยจะถูกส่งเข้าแชตของห้องโดยอัตโนมัติ</div>
</div>

<div class="panel">
<h2>💬 แชต</h2>
<div id="messages" class="messages"><p class="muted">กำลังโหลด…</p></div>
<form id="chatForm" class="row" style="margin-top:10px">
<input id="chatInput" maxlength="500" placeholder="พิมพ์ข้อความ…" autocomplete="off">
<button type="submit">ส่ง</button>
</form>
</div>
</div>

<div class="panel">
<h2>🗺️ กระดาน 8 × 8</h2>
<p class="muted">แตะช่องเพื่อย้ายตัวหมากของตัวเอง สมาชิกแต่ละคนมีตัวหมากแยกกัน</p>
<div id="board" class="board"></div>
<div id="boardStatus" class="muted"></div>
</div>
</section>

<div id="globalStatus" class="status" aria-live="polite">กำลังเชื่อมต่อ Firebase…</div>
<footer>EasyDND • เวอร์ชันทดลอง</footer>
</main>

<script type="module">
import {initializeApp} from "https://www.gstatic.com/firebasejs/12.5.0/firebase-app.js";
import {getAuth,signInAnonymously,onAuthStateChanged} from "https://www.gstatic.com/firebasejs/12.5.0/firebase-auth.js";
import {getDatabase,ref,get,set,push,remove,onValue} from "https://www.gstatic.com/firebasejs/12.5.0/firebase-database.js";

const firebaseConfig={
 apiKey:"AIzaSyApLGFjitTleBjPCbaHgL2QZ1Bxdw2uYlY",
 authDomain:"easydnd-1ab42.firebaseapp.com",
 databaseURL:"https://easydnd-1ab42-default-rtdb.asia-southeast1.firebasedatabase.app",
 projectId:"easydnd-1ab42",
 storageBucket:"easydnd-1ab42.firebasestorage.app",
 messagingSenderId:"755955885657",
 appId:"1:755955885657:web:5aceef5392db3b98673348",
 measurementId:"G-JVV8WY0BXT"
};

const app=initializeApp(firebaseConfig);
const auth=getAuth(app);
const db=getDatabase(app);
const $=id=>document.getElementById(id);

let me=null,myName="",roomId="",roomInfo=null,myRole="";
let listeners=[],tokensCache={};

function status(s){$("globalStatus").textContent=s}
function roomStatus(s){$("roomStatus").textContent=s}
function dbref(p){return ref(db,p)}
function show(id,yes=true){$(id).classList.toggle("hidden",!yes)}
function listen(p,callback){
 const unsub=onValue(dbref(p),callback,error=>{
  console.error(error);status("Firebase: "+error.message);
 });
 listeners.push(unsub);
}
function stopListeners(){listeners.forEach(fn=>fn());listeners=[]}
function hideSections(){["loginPanel","homePanel","roomPanel","gamePanel"].forEach(id=>show(id,false))}
function errorText(e){
 const s=e?.message||String(e);
 return /permission_denied|PERMISSION_DENIED/i.test(s)
  ?"Firebase Rules ยังไม่อนุญาต กรุณาตรวจขั้นที่ 2"
  :s;
}
function makeCode(){
 const chars="ABCDEFGHJKLMNPQRSTUVWXYZ23456789";
 return Array.from({length:6},()=>chars[Math.floor(Math.random()*chars.length)]).join("");
}
function safeText(s){return String(s??"").slice(0,500)}
function emojiFor(uid){
 const choices=["🧙","🧝","🛡️","🧛","🧚","🧟","🐉","🧞","🧌","⚔️"];
 let n=0;for(let i=0;i<uid.length;i++)n=(n+uid.charCodeAt(i))%choices.length;
 return choices[n];
}
async function systemMessage(text){
 if(!roomId||!me)return;
 await push(dbref(`rooms/${roomId}/game/chat`),{
  uid:me.uid,displayName:"ระบบ",text,kind:"system",createdAt:Date.now()
 });
}
function resetHome(){
 stopListeners();roomId="";roomInfo=null;myRole="";
 hideSections();show("homePanel");status("พร้อมใช้งาน");
}
async function openRoom(id,info,role,pending=false){
 stopListeners();roomId=id;roomInfo=info;myRole=role;
 hideSections();show("roomPanel");
 $("roomTitle").textContent=info.name||"EasyDND";
 $("roomCodeDisplay").textContent=id;
 $("roleDisplay").textContent=role==="dm"?"DM":"ผู้เล่น";
 show("dmPanel",role==="dm");
 show("pendingPanel",pending);
 show("approvedPanel",!pending);
 roomStatus(pending?"ส่งคำขอแล้ว กำลังรอ DM อนุมัติ":"เชื่อมต่อห้องสำเร็จ");
 status(`อยู่ในห้อง ${id}`);

 if(role==="dm"){
  listen(`rooms/${id}/joinRequests`,snap=>renderRequests(snap.val()||{}));
 }else if(pending){
  listen(`rooms/${id}/members/${me.uid}`,snap=>{
   if(snap.exists()){
    myRole=snap.val().role||"player";
    show("pendingPanel",false);show("approvedPanel",true);
    roomStatus("DM อนุมัติแล้ว! กดเข้าสู่โต๊ะเล่นได้เลย");
    status("ได้รับอนุมัติแล้ว");
   }
  });
 }
}
function renderRequests(data){
 const host=$("requests");host.replaceChildren();
 const entries=Object.entries(data);
 if(!entries.length){
  const p=document.createElement("p");p.className="muted";p.textContent="ยังไม่มีคำขอ";
  host.append(p);return;
 }
 for(const [uid,req] of entries){
  const wrap=document.createElement("div");wrap.className="request";
  const label=document.createElement("div");
  label.textContent=(req.displayName||"ผู้เล่น")+" ขอเข้าร่วมห้อง";
  const actions=document.createElement("div");actions.className="row";actions.style.flex="0 0 auto";
  const yes=document.createElement("button");yes.textContent="อนุมัติ";
  yes.onclick=async()=>{
   yes.disabled=true;
   try{
    await set(dbref(`rooms/${roomId}/members/${uid}`),{
     uid,role:"player",joinedAt:Date.now(),displayName:req.displayName||"ผู้เล่น"
    });
    await remove(dbref(`rooms/${roomId}/joinRequests/${uid}`));
    await systemMessage(`${req.displayName||"ผู้เล่น"} เข้าร่วมห้องแล้ว`);
    roomStatus("อนุมัติผู้เล่นแล้ว");
   }catch(e){alert(errorText(e));yes.disabled=false}
  };
  const no=document.createElement("button");no.textContent="ปฏิเสธ";no.className="danger";
  no.onclick=async()=>{
   no.disabled=true;
   try{await remove(dbref(`rooms/${roomId}/joinRequests/${uid}`))}
   catch(e){alert(errorText(e));no.disabled=false}
  };
  actions.append(yes,no);wrap.append(label,actions);host.append(wrap);
 }
}
async function createRoom(){
 if(!me){alert("กำลังเชื่อมต่อบัญชี กรุณารอสักครู่");return}
 const name=$("roomName").value.trim().slice(0,40);
 if(!name){alert("กรุณาใส่ชื่อห้อง");return}
 $("createRoomBtn").disabled=true;
 try{
  let id="",found=false;
  for(let i=0;i<8;i++){
   id=makeCode();
   const s=await get(dbref(`rooms/${id}/info`));
   if(!s.exists()){found=true;break}
  }
  if(!found)throw Error("สร้างรหัสห้องไม่ได้ ลองอีกครั้ง");
  const info={name,ownerUid:me.uid,createdAt:Date.now()};
  await set(dbref(`rooms/${id}/info`),info);
  await set(dbref(`rooms/${id}/members/${me.uid}`),{
   uid:me.uid,role:"dm",joinedAt:Date.now(),displayName:myName
  });
  await set(dbref(`rooms/${id}/game/tokens/${me.uid}`),{
   uid:me.uid,name:myName,emoji:emojiFor(me.uid),x:0,y:0
  });
  await openRoom(id,info,"dm");
  await systemMessage(`${myName} สร้างห้องแล้ว`);
 }catch(e){alert("สร้างห้องไม่สำเร็จ: "+errorText(e))}
 finally{$("createRoomBtn").disabled=false}
}
async function joinRoom(){
 if(!me){alert("กำลังเชื่อมต่อบัญชี กรุณารอสักครู่");return}
 const id=$("roomCode").value.trim().toUpperCase().replace(/[^A-Z0-9]/g,"").slice(0,6);
 if(id.length!==6){alert("กรอกรหัสห้อง 6 ตัว");return}
 $("joinRoomBtn").disabled=true;
 try{
  const infoSnap=await get(dbref(`rooms/${id}/info`));
  if(!infoSnap.exists()){alert("ไม่พบห้อง ตรวจสอบรหัสอีกครั้ง");return}
  const info=infoSnap.val();
  const memberSnap=await get(dbref(`rooms/${id}/members/${me.uid}`));
  if(memberSnap.exists()){
   await openRoom(id,info,memberSnap.val().role||"player");
   return;
  }
  const requestSnap=await get(dbref(`rooms/${id}/joinRequests/${me.uid}`));
  if(!requestSnap.exists()){
   await set(dbref(`rooms/${id}/joinRequests/${me.uid}`),{
    uid:me.uid,displayName:myName,requestedAt:Date.now()
   });
  }
  await openRoom(id,info,"player",true);
 }catch(e){alert("เข้าห้องไม่สำเร็จ: "+errorText(e))}
 finally{$("joinRoomBtn").disabled=false}
}
async function enterGame(){
 if(!roomId||!me)return;
 try{
  const member=await get(dbref(`rooms/${roomId}/members/${me.uid}`));
  if(!member.exists()){alert("บัญชีนี้ยังไม่ได้รับอนุมัติ");return}
  myRole=member.val().role||myRole;
  stopListeners();show("roomPanel",false);show("gamePanel",true);
  $("gameTitle").textContent=`${roomInfo?.name||"โต๊ะเล่น"} • ${roomId}`;
  listen(`rooms/${roomId}/game/tokens`,snap=>{
   tokensCache=snap.val()||{};renderBoard();
  });
  listen(`rooms/${roomId}/game/chat`,snap=>renderMessages(snap.val()||{}));
  renderBoard();status("เข้าสู่โต๊ะเล่นแล้ว");
 }catch(e){alert("เข้าโต๊ะเล่นไม่สำเร็จ: "+errorText(e))}
}
function renderBoard(){
 const board=$("board");board.replaceChildren();
 const tokens=Object.values(tokensCache).filter(Boolean);
 for(let y=0;y<8;y++)for(let x=0;x<8;x++){
  const cell=document.createElement("button");cell.type="button";cell.className="cell";
  const token=tokens.find(t=>Number(t.x)===x&&Number(t.y)===y);
  if(token){
   const icon=document.createElement("span");icon.className="token";
   icon.textContent=token.emoji||"🧙";cell.append(icon);
   cell.title=token.name||"ตัวละคร";
  }
  const small=document.createElement("small");
  small.textContent=String.fromCharCode(65+x)+(y+1);cell.append(small);
  cell.onclick=()=>moveToken(x,y);
  board.append(cell);
 }
 $("boardStatus").textContent=`จำนวนตัวหมาก: ${tokens.length}`;
}
async function moveToken(x,y){
 if(!roomId||!me)return;
 try{
  const r=dbref(`rooms/${roomId}/game/tokens/${me.uid}`);
  const snap=await get(r);
  const old=snap.val()||{uid:me.uid,name:myName,emoji:emojiFor(me.uid),x:0,y:0};
  await set(r,{...old,uid:me.uid,name:myName,emoji:old.emoji||emojiFor(me.uid),x,y});
 }catch(e){status("ย้ายตัวหมากไม่ได้: "+errorText(e))}
}
function renderMessages(data){
 const host=$("messages");host.replaceChildren();
 const entries=Object.entries(data)
  .sort((a,b)=>(a[1]?.createdAt||0)-(b[1]?.createdAt||0)).slice(-80);
 if(!entries.length){
  const p=document.createElement("p");p.className="muted";p.textContent="ยังไม่มีข้อความ";
  host.append(p);return;
 }
 for(const [,msg] of entries){
  const box=document.createElement("div");box.className="message";
  const meta=document.createElement("div");meta.className="meta";
  const time=msg.createdAt?new Date(msg.createdAt).toLocaleTimeString("th-TH",{hour:"2-digit",minute:"2-digit"}):"";
  meta.textContent=`${msg.displayName||"ผู้เล่น"} • ${time}`;
  const body=document.createElement("div");body.className="body";body.textContent=safeText(msg.text);
  box.append(meta,body);host.append(box);
 }
 host.scrollTop=host.scrollHeight;
}
async function sendChat(value){
 const text=value.trim().slice(0,500);if(!text||!roomId)return;
 await push(dbref(`rooms/${roomId}/game/chat`),{
  uid:me.uid,displayName:myName,text,kind:"chat",createdAt:Date.now()
 });
}
async function rollDice(sides){
 const result=Math.floor(Math.random()*sides)+1;
 $("diceResult").textContent=`d${sides} → ${result}`;
 try{
  await push(dbref(`rooms/${roomId}/game/chat`),{
   uid:me.uid,displayName:myName,
   text:`ทอย d${sides} ได้ ${result}`,kind:"dice",createdAt:Date.now()
  });
 }catch(e){status("บันทึกผลทอยไม่ได้: "+errorText(e))}
}

$("saveNameBtn").onclick=()=>{
 const name=$("displayName").value.trim().slice(0,30);
 if(!name){alert("กรุณาใส่ชื่อ");return}
 myName=name;localStorage.setItem("easydnd_name",name);
 show("loginPanel",false);show("homePanel",true);status(`สวัสดี ${myName}`);
};
$("createRoomBtn").onclick=createRoom;
$("joinRoomBtn").onclick=joinRoom;
$("enterGameBtn").onclick=enterGame;
$("leaveRoomBtn").onclick=resetHome;
$("backRoomBtn").onclick=()=>openRoom(roomId,roomInfo,myRole,false);
$("copyCodeBtn").onclick=async()=>{
 try{await navigator.clipboard.writeText(roomId);status("คัดลอกรหัสห้องแล้ว")}
 catch{alert("รหัสห้อง: "+roomId)}
};
$("diceButtons").addEventListener("click",e=>{
 const b=e.target.closest("button[data-die]");
 if(b&&roomId)rollDice(Number(b.dataset.die));
});
$("chatForm").addEventListener("submit",async e=>{
 e.preventDefault();
 const input=$("chatInput");
 try{await sendChat(input.value);input.value=""}
 catch(err){alert("ส่งข้อความไม่ได้: "+errorText(err))}
});

const saved=localStorage.getItem("easydnd_name");
if(saved){myName=saved;$("displayName").value=saved;show("loginPanel",false);show("homePanel",true)}
status("กำลังเข้าสู่ระบบ Firebase…");
signInAnonymously(auth).catch(e=>status("เข้าสู่ระบบไม่สำเร็จ: "+errorText(e)));
onAuthStateChanged(auth,user=>{
 me=user;
 if(user)status("เชื่อมต่อ Firebase แล้ว");
});
</script>
</body>
</html>
