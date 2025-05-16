# Starlit-Slumber
紫藤微光織成的夢境，專屬浮水印與心靈守護之地。
<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>琋の祕密浮水印基地</title>
  <meta name="description" content="紫藤微光織成的夢境，專屬浮水印與心靈守護之地。" />
  <style>
    body {
      margin: 0; padding: 0;
      font-family: 'Noto Sans TC', sans-serif;
      background: linear-gradient(to bottom, #f6f0ff, #e8d8f8);
      color: #5b4a71;
    }
    .lock-screen {
      position: fixed;
      top: 0; left: 0;
      width: 100vw; height: 100vh;
      background: rgba(255,255,255,0.9);
      display: flex; flex-direction: column; align-items: center; justify-content: center;
      z-index: 9999;
    }
    .lock-screen input {
      padding: 0.6rem;
      font-size: 1rem;
      margin-top: 1rem;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    .lock-screen button {
      margin-top: 1rem;
      background: #bca1de;
      border: none;
      padding: 0.6rem 1.2rem;
      font-size: 1rem;
      border-radius: 10px;
      color: #fff;
      cursor: pointer;
    }
    header {
      background: #cdb4e5;
      padding: 1.5rem;
      text-align: center;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    }
    header h1 {
      margin: 0;
      font-size: 2rem;
      letter-spacing: 1px;
    }
    nav {
      margin-top: 1rem;
      text-align: center;
    }
    nav a {
      color: #fff;
      background: #a48fce;
      padding: 0.5rem 1rem;
      margin: 0 0.5rem;
      border-radius: 10px;
      text-decoration: none;
      transition: background 0.3s;
    }
    nav a:hover {
      background: #9176bb;
    }
    .container {
      max-width: 800px;
      margin: 2rem auto;
      padding: 1rem;
      background: rgba(255,255,255,0.8);
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.05);
    }
    .watermark-section {
      text-align: center;
    }
    input[type="text"] {
      width: 80%;
      padding: 0.6rem;
      font-size: 1rem;
      margin-bottom: 1rem;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    button {
      background: #bca1de;
      border: none;
      padding: 0.6rem 1.2rem;
      font-size: 1rem;
      border-radius: 10px;
      color: #fff;
      cursor: pointer;
    }
    canvas {
      margin-top: 1rem;
      border: 1px dashed #aaa;
    }
  </style>
</head>
<body>
  <div class="lock-screen" id="lockScreen">
    <h2>🔐 這是琋的祕密基地</h2>
    <p>請輸入妳的密語進入</p>
    <p style="font-size: 0.9rem; color: #777;">提示：專屬妳的守護密碼，是妳熟悉的秘密組合。</p>
    <input type="password" id="passwordInput" placeholder="輸入密語..." />
    <button onclick="checkPassword()">進入</button>
    <p id="errorText" style="color: crimson; display: none;">密語錯了，再試一次喔…</p>
  </div>
  <header>
    <h1>琋の祕密浮水印基地</h1>
    <nav>
      <a href="#">首頁</a>
      <a href="#watermark">浮水印製作</a>
      <a href="#about">關於我</a>
    </nav>
  </header>
  <div class="container">
    <section id="watermark" class="watermark-section">
      <h2>🫧 製作妳的專屬浮水印</h2>
      <input
        type="text"
        id="watermarkText"
        placeholder="例如：SRNSDL · 0529 · 琋 · ♓︎☾♊︎↑♋︎"
      />
      <br />
      <button onclick="generateWatermark()">點我生成浮水印</button>
      <br />
      <canvas id="watermarkCanvas" width="500" height="100"></canvas>
    </section>
    <section id="about" style="margin-top: 3rem;">
      <h2>🌸 關於我</h2>
      <p>
        這是我靈魂祕密的守護所。<br />
        透過浮水印保護我的夢、我的創作、還有我那柔軟又有力量的心。
      </p>
    </section>
  </div>
  <script>
    const correctPassword = "ala22937QWE";

    function checkPassword() {
      const input = document.getElementById("passwordInput").value;
      const errorText = document.getElementById("errorText");
      if (input === correctPassword) {
        document.getElementById("lockScreen").style.display = "none";
      } else {
        errorText.style.display = "block";
      }
    }

    function generateWatermark() {
      const text =
        document.getElementById("watermarkText").value ||
        "SRNSDL · 0529 · 琋 · ♓︎☾♊︎↑♋︎";
      const canvas = document.getElementById("watermarkCanvas");
      const ctx = canvas.getContext("2d");
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      ctx.fillStyle = "rgba(91, 74, 113, 0.4)";
      ctx.font = "28px Noto Sans TC";
      ctx.textAlign = "center";
      ctx.textBaseline = "middle";
      ctx.fillText(text, canvas.width / 2, canvas.height / 2);

      const link = document.createElement("a");
      link.download = "watermark.png";
      link.href = canvas.toDataURL();
      link.click();
    }
  </script>
</body>
</html>
