
<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#111019">
  <title>EasyDND — Enter the Realm</title>

  <style>
    * { box-sizing: border-box; }

    :root {
      --gold: #e9c77e;
      --gold-light: #ffe7ac;
      --bg: #111019;
      --panel: #1b1926;
      --muted: #aaa6ba;
      --line: #403749;
    }

    body {
      margin: 0;
      min-height: 100vh;
      background:
        radial-gradient(ellipse at 50% 0%, #40304c 0%, transparent 52%),
        radial-gradient(ellipse at 100% 100%, #24243b 0%, transparent 40%),
        var(--bg);
      color: #f7f1e8;
      font-family: system-ui, sans-serif;
    }

    button, input { font: inherit; }

    .page {
      width: min(100% - 32px, 760px);
      margin: auto;
      padding: 30px 0 36px;
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 12px;
      margin-bottom: 48px;
    }

    .brand {
      color: var(--gold);
      font-weight: 900;
      font-size: 20px;
      letter-spacing: 1px;
    }

    .brand small {
      display: block;
      color: var(--muted);
      font-size: 10px;
      letter-spacing: 3px;
      font-weight: 500;
      margin-top: 3px;
    }

    .online {
      border: 1px solid #47634f;
      background: #1c3028;
      color: #a7e7b8;
      border-radius: 30px;
      padding: 7px 10px;
      font-size: 11px;
      white-space: nowrap;
    }

    .hero {
      text-align: center;
      margin-bottom: 34px;
    }

    .crest {
      width: 92px;
      height: 92px;
      margin: 0 auto 20px;
      display: grid;
      place-items: center;
      font-size: 48px;
      color: var(--gold);
      border: 1px solid #8c7047;
      border-radius: 28px 28px 40px 40px;
      background: linear-gradient(145deg, #3b2e40, #191622);
      box-shadow: 0 0 42px #d7ae4820, inset 0 0 20px #e8c77a12;
    }

    .eyebrow {
      color: var(--gold);
      font-size: 11px;
      letter-spacing: 4px;
      font-weight: 800;
    }

    h1 {
      font-family: Georgia, serif;
      font-size: clamp(36px, 9vw, 56px);
      line-height: 1.12;
      margin: 12px 0;
      letter-spacing: 1px;
    }

    h1 span { color: var(--gold); }

    .intro {
      max-width: 430px;
      margin: auto;
      color: var(--muted);
      font-size: 14px;
      line-height: 1.9;
    }

    .divider {
      display: flex;
      align-items: center;
      gap: 14px;
      color: #8f7b61;
      font-size: 11px;
      letter-spacing: 3px;
      margin: 32px 0 18px;
    }

    .divider::before, .divider::after {
      content: "";
      height: 1px;
      flex: 1;
      background: linear-gradient(90deg, transparent, var(--line));
    }

    .divider::after {
      background: linear-gradient(90deg, var(--line), transparent);
    }

    .actions {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 14px;
    }

    .action {
      text-align: left;
      padding: 20px 16px;
      min-height: 185px;
      border: 1px solid var(--line);
      border-radius: 16px;
      background: linear-gradient(145deg, #252130, #191722);
      color: #f7f1e8;
      cursor: pointer;
      transition: transform .18s, border-color .18s;
    }

    .action:hover {
      transform: translateY(-3px);
      border-color: var(--gold);
    }

    .action.primary {
      border-color: #8d7045;
      background: linear-gradient(145deg, #44342e, #211c25 80%);
    }

    .action-icon {
      font-size: 30px;
      margin-bottom: 15px;
    }

    .action h2 {
      font-size: 17px;
      margin: 0 0 8px;
    }

    .action p {
      color: var(--muted);
      font-size: 12px;
      line-height: 1.8;
      margin: 0;
    }

    .arrow {
      display: block;
      color: var(--gold);
      font-size: 20px;
      margin-top: 12px;
    }

    .features {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 10px;
      margin-top: 28px;
    }

    .feature {
      text-align: center;
      padding: 15px 6px;
      border: 1px solid #302c3c;
      border-radius: 12px;
      background: #1a1823a8;
    }

    .feature div { font-size: 23px; }

    .feature span {
      display: block;
      color: #c3bdcf;
      font-size: 11px;
      margin-top: 8px;
    }

    .status {
      text-align: center;
      padding: 12px;
      margin-top: 24px;
      border: 1px solid #344a3d;
      background: #1a2b24;
      color: #a9e6be;
      border-radius: 10px;
      font-size: 12px;
      overflow-wrap: anywhere;
      line-height: 1.8;
    }

    .status.error {
      color: #ffb9b9;
      background: #351f27;
      border-color: #693d49;
    }

    .uid {
      color: #c2bdcd;
      font-size: 10px;
      margin-top: 5px;
      overflow-wrap: anywhere;
    }

    footer {
      text-align: center;
      color: #777184;
      font-size: 11px;
      margin-top: 30px;
      line-height: 1.9;
    }

    .modal {
      position: fixed;
      inset: 0;
      z-index: 10;
      display: none;
      place-items: center;
      padding: 20px;
      background: #08070dcc;
    }

    .modal.open { display: grid; }

    .modal-card {
      width: min(100%, 420px);
      padding: 24px;
      border: 1px solid #786044;
      border-radius: 18px;
      background: #211d2a;
      box-shadow: 0 20px 80px #0009;
    }

    .modal-card h2 {
      color: var(--gold);
      margin: 0 0 10px;
    }

    .modal-card p {
      color: var(--muted);
      font-size: 13px;
      line-height: 1.8;
    }

    .modal-card input {
      width: 100%;
      padding: 13px;
      margin: 8px 0;
      border: 1px solid #51475d;
      border-radius: 9px;
      background: #14121b;
      color: white;
      outline-color: var(--gold);
    }

    .modal-card button {
      width: 100%;
      padding: 12px;
      margin-top: 10px;
      border: 0;
      border-radius: 9px;
      cursor: pointer;
      font-weight: 700;
    }

    .confirm {
      color: #20180d;
      background: var(--gold);
    }

    .cancel {
      color: #ddd5e6;
      background: #373140;
    }

    @media (max-width: 430px) {
      .page { padding-top: 22px; }
      header { margin-bottom: 38px; }
      .actions { gap: 10px; }
      .action { padding: 15px 12px; min-height: 180px; }
      .action h2 { font-size: 15px; }
      .features { gap: 7px; }
    }
  </style>
</head>

<body>
  <div class="page">
    <header>
      <div class="brand">
        ⚔ EasyDND
        <small>BY MZNR</small>
      </div>
      <div class="online" id="connection">● กำลังเชื่อมต่อ</div>
    </header>

    <section class="hero">
      <div class="crest">⚔</div>
      <div class="eyebrow">YOUR ADVENTURE BEGINS</div>
      <h1>Enter the <span>Realm</span></h1>
      <p class="intro">
        ทุกตำนานเริ่มต้นจากการทอยลูกเต๋าเพียงครั้งเดียว<br>
        สร้างโลกของคุณ แล้วออกผจญภัยไปพร้อมกับพวกพ้อง
      </p>
    </section>

    <div class="divider">CHOOSE YOUR PATH</div>

    <section class="actions">
      <button class="action primary" onclick="openModal('create')">
        <div class="action-icon">👑</div>
        <h2>สร้างห้องเกม</h2>
        <p>สร้างแคมเปญของคุณเอง<br>รับบท Dungeon Master</p>
        <span class="arrow">↗</span>
      </button>

      <button class="action" onclick="openModal('join')">
        <div class="action-icon">🗝️</div>
        <h2>เข้าร่วมห้องเกม</h2>
        <p>มีรหัสห้องอยู่แล้วใช่ไหม<br>เข้าร่วมการผจญภัยได้เลย</p>
        <span class="arrow">↗</span>
      </button>
    </section>

    <section class="features">
      <div class="feature">
        <div>🗺️</div>
        <span>แผนที่และโทเคน</span>
      </div>
      <div class="feature">
        <div>🎲</div>
        <span>ลูกเต๋า 9 แบบ</span>
      </div>
      <div class="feature">
        <div>📜</div>
        <span>ชีทตัวละคร</span>
      </div>
    </section>

    <div class="status" id="status">
      กำลังเตรียมระบบ...
      <div class="uid" id="uid"></div>
    </div>

    <footer>
      EASYDND · VIRTUAL TABLETOP<br>
      Forged for adventures, bound by imagination.
    </footer>
  </div>

  <div class="modal" id="modal" role="dialog" aria-modal="true">
    <div class="modal-card">
      <h2 id="modalTitle">สร้างห้องเกม</h2>
      <p id="modalDescription">
        ตั้งชื่อแคมเปญของคุณ
      </p>
      <input id="roomInput" maxlength="40"
        placeholder="ชื่อแคมเปญ">
      <button class="confirm" onclick="submitRoom()">
        ดำเนินการต่อ
      </button>
      <button class="cancel" onclick="closeModal()">
        กลับหน้าหลัก
      </button>
      <p id="modalNote">
        ระบบห้องเกมกำลังอยู่ระหว่างการพัฒนา
      </p>
    </div>
  </div>

  <script>
    let modalMode = "create";

    function openModal(mode) {
      modalMode = mode;
      document.getElementById("modalTitle").textContent =
        mode === "create" ? "⚔ สร้างห้องเกม" : "🗝 เข้าร่วมห้องเกม";

      document.getElementById("modalDescription").textContent =
        mode === "create"
          ? "ตั้งชื่อแคมเปญที่คุณจะเป็น DM"
          : "กรอกรหัสห้องที่ DM ส่งให้คุณ";

      const input = document.getElementById("roomInput");
      input.value = "";
      input.placeholder =
        mode === "create" ? "ชื่อแคมเปญ" : "รหัสห้องเกม";

      document.getElementById("modalNote").textContent =
        "หน้าจอนี้เป็นส่วนติดต่อเบื้องต้น ยังไม่ได้สร้างหรือเข้าร่วมห้องจริง";

      document.getElementById("modal").classList.add("open");
    }

    function closeModal() {
      document.getElementById("modal").classList.remove("open");
    }

    function submitRoom() {
      const value = document.getElementById("roomInput").value.trim();

      if (!value) {
        document.getElementById("modalNote").textContent =
          modalMode === "create"
            ? "กรุณาตั้งชื่อแคมเปญก่อน"
            : "กรุณากรอกรหัสห้องก่อน";
        return;
      }

      document.getElementById("modalNote").textContent =
        "รับข้อมูลแล้ว แต่ระบบห้องเกมยังไม่ได้เชื่อมกับฐานข้อมูล กรุณารอขั้นตอนพัฒนาถัดไป";
    }
  </script>

  <script type="module">
    import { initializeApp }
      from "https://www.gstatic.com/firebasejs/12.5.0/firebase-app.js";

    import {
      getAuth,
      signInAnonymously
    } from "https://www.gstatic.com/firebasejs/12.5.0/firebase-auth.js";

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

    const status = document.getElementById("status");
    const uid = document.getElementById("uid");
    const connection = document.getElementById("connection");

    try {
      const app = initializeApp(firebaseConfig);
      const auth = getAuth(app);
      await signInAnonymously(auth);

      status.firstChild.textContent = "✓ เชื่อมต่อ Firebase สำเร็จ";
      uid.textContent = "รหัสผู้เล่น: " + auth.currentUser.uid;
      connection.textContent = "● เชื่อมต่อแล้ว";
    } catch (error) {
      status.classList.add("error");
      status.firstChild.textContent =
        "เชื่อมต่อ Firebase ไม่สำเร็จ: " + error.code;
      connection.textContent = "● ยังไม่เชื่อมต่อ";
      console.error("Firebase error:", error);
    }
  </script>
</body>
</html>
