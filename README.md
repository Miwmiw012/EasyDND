# EasyDND
By MZNR

<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#171923">
  <title>D&D Tabletop</title>
  <style>
    * { box-sizing: border-box; }
    body {
      margin: 0;
      min-height: 100vh;
      background: #171923;
      color: #f5f5f5;
      font-family: system-ui, sans-serif;
      padding: 24px 16px;
    }
    main {
      max-width: 480px;
      margin: 40px auto;
      padding: 24px;
      background: #242735;
      border: 1px solid #45495b;
      border-radius: 18px;
    }
    h1 { margin-top: 0; color: #e8c77a; }
    p { line-height: 1.7; color: #d0d3df; }
    .status {
      padding: 12px;
      background: #183d32;
      border-radius: 10px;
      color: #9cf0c9;
    }
    button {
      width: 100%;
      padding: 13px;
      margin-top: 12px;
      border: 0;
      border-radius: 10px;
      background: #e8c77a;
      color: #171923;
      font-size: 16px;
      font-weight: 700;
    }
  </style>
</head>
<body>
  <main>
    <h1>⚔️ D&D Tabletop</h1>
    <p>Virtual Tabletop สำหรับแคมเปญของเรา</p>
    <div class="status">✓ หน้าเว็บเริ่มต้นพร้อมใช้งาน</div>
    <p>ระบบที่จะเพิ่ม:</p>
    <ul>
      <li>ห้องเกมและระบบสมาชิก</li>
      <li>แผนที่และโทเคน</li>
      <li>ชีทตัวละครพร้อมรูปโปรไฟล์</li>
      <li>ลูกเต๋า 9 แบบ</li>
      <li>กระเป๋าและไอเทม</li>
    </ul>
    <button onclick="alert('เตรียมระบบเกมในขั้นต่อไป!')">
      ทดสอบหน้าเว็บ
    </button>
  </main>
</body>
<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/12.5.0/firebase-app.js";
  import {
    getAuth,
    signInAnonymously,
    onAuthStateChanged
  } from "https://www.gstatic.com/firebasejs/12.5.0/firebase-auth.js";
  import {
    getDatabase,
    ref,
    get
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

  const app = initializeApp(firebaseConfig);
  const auth = getAuth(app);
  const db = getDatabase(app);

  const status = document.querySelector(".status");

  async function startFirebase() {
    if (status) status.textContent = "กำลังเชื่อมต่อ Firebase...";

    try {
      await signInAnonymously(auth);

      if status.textContent =
  "✓ เชื่อมต่อ Firebase แล้ว\nรหัสผู้เล่น: " + auth.currentUser.uid;

      console.log("Firebase connected. UID:", auth.currentUser.uid);
    } catch (error) {
      console.error("Firebase error:", error);

      if (status) {
        status.textContent = "เชื่อมต่อไม่สำเร็จ: " + error.code;
      }
    }
  }

  startFirebase();
</script>
</body>

</html>

    
