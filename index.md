<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Effie’s Enchiridion</title>

  <style>
    :root {
      --bg: #f7f1df;
      --panel: #fff9ea;
      --panel-dark: #eadfbe;
      --text: #3a2f1f;
      --accent: #b45f6c;
      --accent-dark: #7c3e47;
      --green: #708b75;
      --blue: #7b9cb3;
      --shadow: #c9b78e;
      --border-dark: #5b4b32;
      --border-light: #fffdf5;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      image-rendering: pixelated;
    }

    body {
      background:
        linear-gradient(to bottom, #efe6cf 0%, #efe6cf 60%, #e4d6b6 60%, #e4d6b6 100%);
      color: var(--text);
      font-family: "Courier New", monospace;
      line-height: 1.7;
      padding: 24px 16px 60px;
      min-height: 100vh;
    }

    .container {
      max-width: 920px;
      margin: 0 auto;
    }

    .title-box {
      background: var(--panel);
      border: 4px solid var(--border-dark);
      box-shadow:
        0 0 0 4px var(--border-light),
        8px 8px 0 0 var(--shadow);
      padding: 20px;
      margin-bottom: 24px;
      position: relative;
    }

    .title-box::after {
      content: "SAVE FILE";
      position: absolute;
      top: -14px;
      left: 16px;
      background: var(--accent);
      color: #fff8ef;
      padding: 4px 10px;
      border: 3px solid var(--border-dark);
      font-size: 12px;
      letter-spacing: 1px;
    }

    h1 {
      font-size: clamp(28px, 5vw, 42px);
      line-height: 1.2;
      margin-bottom: 10px;
      color: var(--accent-dark);
      text-shadow: 2px 2px 0 #f4e9cf;
    }

    .subtitle {
      font-size: 15px;
      color: #5f5038;
    }

    .grid {
      display: grid;
      grid-template-columns: 1.1fr 0.9fr;
      gap: 22px;
      margin-bottom: 22px;
    }

    @media (max-width: 760px) {
      .grid {
        grid-template-columns: 1fr;
      }
    }

    .panel {
      background: var(--panel);
      border: 4px solid var(--border-dark);
      box-shadow:
        0 0 0 4px var(--border-light),
        6px 6px 0 0 var(--shadow);
      padding: 18px;
      position: relative;
    }

    .panel h2 {
      display: inline-block;
      font-size: 18px;
      margin-bottom: 14px;
      padding: 4px 10px;
      background: var(--green);
      color: #fffaf0;
      border: 3px solid var(--border-dark);
      letter-spacing: 0.5px;
    }

    .name {
      font-size: 22px;
      font-weight: bold;
      color: var(--accent-dark);
      margin-bottom: 6px;
    }

    .nickname {
      font-size: 15px;
      color: #7b5e46;
      margin-left: 6px;
    }

    .role {
      font-size: 15px;
      margin-bottom: 16px;
    }

    .avatar-frame {
      margin-top: 12px;
      padding: 10px;
      width: fit-content;
      background: #f0e5c8;
      border: 4px solid var(--border-dark);
      box-shadow: 4px 4px 0 0 #d6c39b;
    }

    .avatar-frame img {
      display: block;
      width: 220px;
      max-width: 100%;
      height: auto;
      border: 4px solid #fff7e8;
      background: #fff;
    }

    .interests {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-top: 6px;
    }

    .tag {
      padding: 8px 12px;
      background: #f3e6c5;
      border: 3px solid var(--border-dark);
      box-shadow: 3px 3px 0 0 #d8c49c;
      font-size: 14px;
      white-space: nowrap;
    }

    .menu-list {
      list-style: none;
      display: grid;
      gap: 12px;
      margin-top: 6px;
    }

    .menu-list a,
    .profile-list a {
      display: block;
      text-decoration: none;
      color: var(--text);
      background: #f6ebcf;
      border: 3px solid var(--border-dark);
      padding: 12px 14px;
      box-shadow: 4px 4px 0 0 #d8c49c;
      transition: transform 0.08s ease, box-shadow 0.08s ease;
      font-weight: bold;
    }

    .menu-list a:hover,
    .profile-list a:hover {
      transform: translate(2px, 2px);
      box-shadow: 2px 2px 0 0 #d8c49c;
      background: #fff2d7;
    }

    .menu-list a::before {
      content: "▶ ";
      color: var(--accent-dark);
    }

    .profile-list {
      list-style: none;
      display: grid;
      gap: 12px;
      margin-top: 6px;
    }

    .profile-list a::before {
      content: "★ ";
      color: var(--blue);
    }

    .footer-box {
      margin-top: 22px;
      text-align: center;
      font-size: 13px;
      color: #6a5a43;
      padding: 14px;
      background: var(--panel-dark);
      border: 4px solid var(--border-dark);
      box-shadow:
        0 0 0 4px var(--border-light),
        6px 6px 0 0 var(--shadow);
    }

    .blink {
      display: inline-block;
      animation: blink 1s steps(1) infinite;
      color: var(--accent-dark);
    }

    @keyframes blink {
      50% {
        opacity: 0;
      }
    }

    .small-note {
      font-size: 13px;
      margin-top: 12px;
      color: #6d5d45;
    }

    .divider {
      height: 4px;
      background: repeating-linear-gradient(
        to right,
        var(--accent) 0 16px,
        #f4d7b4 16px 32px,
        var(--green) 32px 48px,
        #f4d7b4 48px 64px
      );
      border: 2px solid var(--border-dark);
      margin: 22px 0;
    }
  </style>
</head>

<body>
  <div class="container">

    <header class="title-box">
      <h1>Effie’s Enchiridion</h1>
      <p class="subtitle">
        A personal archive of bibliographic records and reading notes, with a focus on modern Chinese history, especially the Mao era.
        <span class="blink">▋</span>
      </p>
    </header>

    <div class="grid">
      <section class="panel">
        <h2>ABOUT</h2>
        <p class="name">
          Yifei Xu <span class="nickname">ʚΐɞ Effie</span>
        </p>
        <p class="role">
          PhD Student, Graduate School of Human and Environmental Studies, Kyoto University
        </p>

        <div class="avatar-frame">
          <img src="images/doraemon.png" alt="Doraemon" />
        </div>

        <p class="small-note">
          Welcome to my archive of reading, bibliography, and research notes.
        </p>
      </section>

      <section class="panel">
        <h2>RESEARCH INTERESTS</h2>
        <div class="interests">
          <span class="tag">Gender History</span>
          <span class="tag">History of Education</span>
          <span class="tag">Modern Chinese History</span>
          <span class="tag">All-China Women’s Federation</span>
        </div>

        <div class="divider"></div>

        <h2>ENTRY</h2>
        <ul class="menu-list">
          <li><a href="./notes/">Bibliography</a></li>
        </ul>
      </section>
    </div>

    <section class="panel">
      <h2>PROFILES</h2>
      <ul class="profile-list">
        <li><a href="https://researchmap.jp/xuyifei" target="_blank" rel="noopener noreferrer">Researchmap</a></li>
        <li><a href="https://jglobal.jst.go.jp/en/detail?JGLOBAL_ID=202601015025298516" target="_blank" rel="noopener noreferrer">J-GLOBAL</a></li>
      </ul>
    </section>

    <footer class="footer-box">
      © Effie’s Enchiridion · Built with GitHub Pages
    </footer>

  </div>
</body>
</html>
