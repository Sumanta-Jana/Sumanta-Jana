<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Sumanta Jana — Dev Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0a0c10;
    --surface: #111419;
    --surface2: #161b22;
    --border: #21262d;
    --accent: #39d353;
    --accent2: #58a6ff;
    --accent3: #f78166;
    --text: #e6edf3;
    --muted: #7d8590;
    --card-bg: #13181f;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(57,211,83,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(57,211,83,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(120px);
    opacity: 0.12;
    pointer-events: none;
    z-index: 0;
  }
  .orb1 { width: 500px; height: 500px; background: #39d353; top: -150px; left: -150px; }
  .orb2 { width: 400px; height: 400px; background: #58a6ff; bottom: -100px; right: -100px; }
  .orb3 { width: 300px; height: 300px; background: #f78166; top: 50%; right: 10%; }

  main { position: relative; z-index: 1; max-width: 1000px; margin: 0 auto; padding: 40px 20px 80px; }

  .header-bar {
    display: flex; align-items: center; gap: 12px;
    margin-bottom: 48px; font-size: 12px;
    color: var(--muted); letter-spacing: 2px; text-transform: uppercase;
  }
  .header-bar::after {
    content: ''; flex: 1; height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }
  .header-dot {
    width: 8px; height: 8px; background: var(--accent);
    border-radius: 50%; box-shadow: 0 0 10px var(--accent);
    animation: pulse 2s infinite;
  }
  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  .profile-grid {
    display: grid; grid-template-columns: 220px 1fr;
    gap: 32px; margin-bottom: 40px; align-items: start;
  }
  .avatar-wrap {
    position: relative; display: flex;
    flex-direction: column; align-items: center; gap: 16px;
  }
  .avatar-ring { position: relative; width: 160px; height: 160px; }
  .avatar-ring::before {
    content: ''; position: absolute; inset: -3px; border-radius: 50%;
    background: conic-gradient(var(--accent), var(--accent2), var(--accent3), var(--accent));
    animation: spin 4s linear infinite;
  }
  @keyframes spin { to { transform: rotate(360deg); } }
  .avatar-inner {
    position: absolute; inset: 3px; border-radius: 50%;
    background: var(--bg); display: flex; align-items: center;
    justify-content: center; font-size: 64px; z-index: 1;
  }
  .status-badge {
    background: var(--surface2); border: 1px solid var(--border);
    border-radius: 20px; padding: 6px 14px; font-size: 11px;
    color: var(--accent); display: flex; align-items: center; gap: 6px; letter-spacing: 1px;
  }
  .status-badge::before {
    content: ''; width: 6px; height: 6px; background: var(--accent);
    border-radius: 50%; animation: pulse 1.5s infinite;
  }
  .follow-btn {
    width: 100%; padding: 8px; background: var(--accent); color: #000;
    border: none; border-radius: 6px; font-family: 'Space Mono', monospace;
    font-weight: 700; font-size: 12px; cursor: pointer; letter-spacing: 1px; transition: all 0.2s;
  }
  .follow-btn:hover { background: #56e374; transform: translateY(-1px); box-shadow: 0 4px 15px rgba(57,211,83,0.3); }

  .name-line {
    font-family: 'Syne', sans-serif; font-size: 36px; font-weight: 800;
    line-height: 1.1; letter-spacing: -1px; margin-bottom: 4px;
  }
  .name-line span { color: var(--accent); }
  .username { color: var(--muted); font-size: 16px; margin-bottom: 14px; }
  .bio-text {
    font-size: 13px; line-height: 1.8; color: #c9d1d9; margin-bottom: 18px;
    max-width: 500px; border-left: 2px solid var(--accent); padding-left: 14px;
  }
  .meta-tags { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 20px; }
  .meta-tag { display: flex; align-items: center; gap: 6px; font-size: 12px; color: var(--muted); }
  .meta-tag svg { width: 14px; height: 14px; stroke: var(--accent2); fill: none; }

  .stats-row { display: flex; gap: 20px; margin-bottom: 32px; flex-wrap: wrap; }
  .stat-pill {
    background: var(--surface2); border: 1px solid var(--border);
    border-radius: 8px; padding: 12px 20px; text-align: center;
    transition: border-color 0.2s, transform 0.2s;
  }
  .stat-pill:hover { border-color: var(--accent); transform: translateY(-2px); }
  .stat-num { font-family: 'Syne', sans-serif; font-size: 22px; font-weight: 800; color: var(--accent); }
  .stat-lbl { font-size: 10px; color: var(--muted); letter-spacing: 1px; text-transform: uppercase; }

  .section-title {
    font-family: 'Syne', sans-serif; font-size: 14px; font-weight: 700;
    letter-spacing: 3px; text-transform: uppercase; color: var(--muted);
    margin-bottom: 16px; display: flex; align-items: center; gap: 10px;
  }
  .section-title::after { content: ''; flex: 1; height: 1px; background: var(--border); }

  .lang-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 12px; margin-bottom: 40px;
  }
  .lang-card {
    background: var(--card-bg); border: 1px solid var(--border);
    border-radius: 10px; padding: 14px; display: flex; align-items: center;
    gap: 10px; transition: all 0.25s; cursor: default;
  }
  .lang-card:hover { border-color: var(--accent2); transform: translateY(-3px); box-shadow: 0 8px 20px rgba(0,0,0,0.4); }
  .lang-icon {
    width: 32px; height: 32px; border-radius: 6px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px; flex-shrink: 0;
  }
  .lang-name { font-size: 12px; font-weight: 700; }
  .lang-level { font-size: 10px; color: var(--muted); }
  .py  { background: rgba(255,215,0,0.15); }
  .html{ background: rgba(228,77,38,0.15); }
  .css { background: rgba(38,77,228,0.15); }
  .c   { background: rgba(88,166,255,0.15); }
  .cpp { background: rgba(243,119,54,0.15); }

  .contrib-section { margin-bottom: 40px; }
  .contrib-graph {
    background: var(--surface2); border: 1px solid var(--border);
    border-radius: 12px; padding: 20px; overflow-x: auto;
  }
  .contrib-label { font-size: 11px; color: var(--muted); margin-bottom: 12px; letter-spacing: 1px; }
  .grid-wrap { display: flex; gap: 3px; }
  .week-col { display: flex; flex-direction: column; gap: 3px; }
  .day-cell { width: 11px; height: 11px; border-radius: 2px; background: var(--border); transition: transform 0.2s; }
  .day-cell:hover { transform: scale(1.4); }
  .lvl1 { background: #0e4429; }
  .lvl2 { background: #006d32; }
  .lvl3 { background: #26a641; }
  .lvl4 { background: #39d353; }

  .links-grid {
    display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px; margin-bottom: 40px;
  }
  .link-card {
    background: var(--card-bg); border: 1px solid var(--border);
    border-radius: 10px; padding: 14px 16px; display: flex; align-items: center;
    gap: 12px; text-decoration: none; color: var(--text); transition: all 0.25s; font-size: 12px;
  }
  .link-card:hover { border-color: var(--accent); transform: translateX(4px); }
  .link-icon {
    width: 36px; height: 36px; border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 18px; flex-shrink: 0;
  }
  .link-name { font-weight: 700; letter-spacing: 0.5px; }
  .link-handle { color: var(--muted); font-size: 10px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }

  .repos-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin-bottom: 40px; }
  .repo-card {
    background: var(--card-bg); border: 1px solid var(--border);
    border-radius: 10px; padding: 16px; transition: all 0.25s; cursor: pointer;
  }
  .repo-card:hover { border-color: var(--accent2); transform: translateY(-3px); box-shadow: 0 10px 30px rgba(0,0,0,0.5); }
  .repo-name { color: var(--accent2); font-size: 13px; font-weight: 700; margin-bottom: 6px; }
  .repo-name::before { content: '📁 '; }
  .repo-desc { font-size: 11px; color: var(--muted); line-height: 1.6; margin-bottom: 12px; }
  .repo-meta { display: flex; gap: 14px; font-size: 10px; color: var(--muted); align-items: center; }
  .repo-lang { display: flex; align-items: center; gap: 5px; }
  .lang-dot { width: 8px; height: 8px; border-radius: 50%; }

  .terminal {
    background: #000; border: 1px solid var(--border);
    border-radius: 10px; padding: 20px; font-size: 12px; line-height: 2;
  }
  .terminal-bar { display: flex; gap: 6px; margin-bottom: 16px; }
  .t-dot { width: 12px; height: 12px; border-radius: 50%; }
  .t-red { background: #ff5f57; }
  .t-yellow { background: #ffbd2e; }
  .t-green { background: #28c940; }
  .t-cmd::before { content: '$ '; color: var(--accent); }
  .t-out { color: var(--muted); padding-left: 16px; }
  .t-cur { display: inline-block; width: 8px; background: var(--accent); animation: blink 1s steps(1) infinite; }
  @keyframes blink { 50% { opacity: 0; } }

  @media (max-width: 650px) {
    .profile-grid { grid-template-columns: 1fr; }
    .repos-grid { grid-template-columns: 1fr; }
    .avatar-wrap { flex-direction: row; }
    .avatar-ring { width: 100px; height: 100px; }
    .avatar-inner { font-size: 40px; }
    .name-line { font-size: 26px; }
  }

  .fade-in { animation: fadeUp 0.6s ease both; }
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .d1 { animation-delay: 0.1s; }
  .d2 { animation-delay: 0.2s; }
  .d3 { animation-delay: 0.3s; }
  .d4 { animation-delay: 0.4s; }
  .d5 { animation-delay: 0.5s; }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<main>

  <div class="header-bar fade-in">
    <div class="header-dot"></div>
    github profile &nbsp;·&nbsp; sumanta-jana
  </div>

  <div class="profile-grid fade-in d1">
    <div class="avatar-wrap">
      <div class="avatar-ring">
        <div class="avatar-inner">👨‍💻</div>
      </div>
      <div class="status-badge">Available to collaborate</div>
      <button class="follow-btn" onclick="this.textContent=this.textContent==='✓ Following'?'Follow':'✓ Following'">Follow</button>
    </div>
    <div class="bio-section">
      <div class="name-line">Sumanta <span>Jana</span></div>
      <div class="username">@Sumanta-Jana</div>
      <div class="bio-text">
        B.Tech CSE AI&ML student at Parul University. Building things from scratch with code.<br/>
        Passionate about learning, creating, and sharing open-source projects.
      </div>
      <div class="meta-tags">
        <div class="meta-tag">
          <svg viewBox="0 0 24 24" stroke-width="2"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg>
          India
        </div>
        <div class="meta-tag">
          <svg viewBox="0 0 24 24" stroke-width="2"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07A19.5 19.5 0 0 1 4.15 12 19.79 19.79 0 0 1 1.07 3.38 2 2 0 0 1 3.06 1.18h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L7.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 21 16.92z"/></svg>
          7001481214
        </div>
        <div class="meta-tag">
          <svg viewBox="0 0 24 24" stroke-width="2"><path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>
          Paschim Medinipur
        </div>
      </div>
    </div>
  </div>

  <div class="stats-row fade-in d2">
    <div class="stat-pill"><div class="stat-num">5+</div><div class="stat-lbl">Languages</div></div>
    <div class="stat-pill"><div class="stat-num">∞</div><div class="stat-lbl">Curiosity</div></div>
    <div class="stat-pill"><div class="stat-num">4</div><div class="stat-lbl">Platforms</div></div>
    <div class="stat-pill"><div class="stat-num">🎓</div><div class="stat-lbl">Student</div></div>
  </div>

  <div class="section-title fade-in d2">⚙ Languages & Skills</div>
  <div class="lang-grid fade-in d3">
    <div class="lang-card"><div class="lang-icon py">🐍</div><div><div class="lang-name">Python</div><div class="lang-level">Basic</div></div></div>
    <div class="lang-card"><div class="lang-icon html">🌐</div><div><div class="lang-name">HTML</div><div class="lang-level">Basic</div></div></div>
    <div class="lang-card"><div class="lang-icon css">🎨</div><div><div class="lang-name">CSS</div><div class="lang-level">Basic</div></div></div>
    <div class="lang-card"><div class="lang-icon c">⚡</div><div><div class="lang-name">C</div><div class="lang-level">Basic</div></div></div>
    <div class="lang-card"><div class="lang-icon cpp">🔧</div><div><div class="lang-name">C++</div><div class="lang-level">Basic</div></div></div>
  </div>

  <div class="contrib-section fade-in d3">
    <div class="section-title">📊 Contribution Graph</div>
    <div class="contrib-graph">
      <div class="contrib-label">contributions in the last year</div>
      <div class="grid-wrap" id="contrib-grid"></div>
    </div>
  </div>

  <div class="section-title fade-in d3">📌 Pinned Repositories</div>
  <div class="repos-grid fade-in d4">
    <div class="repo-card">
      <div class="repo-name">portfolio-website</div>
      <div class="repo-desc">My personal portfolio built with HTML & CSS. Clean, minimal, responsive.</div>
      <div class="repo-meta"><div class="repo-lang"><div class="lang-dot" style="background:#e34c26"></div> HTML</div><span>⭐ 2</span><span>🍴 1</span></div>
    </div>
    <div class="repo-card">
      <div class="repo-name">python-basics</div>
      <div class="repo-desc">Collection of beginner Python programs and problem solutions.</div>
      <div class="repo-meta"><div class="repo-lang"><div class="lang-dot" style="background:#3572a5"></div> Python</div><span>⭐ 1</span></div>
    </div>
    <div class="repo-card">
      <div class="repo-name">c-cpp-programs</div>
      <div class="repo-desc">Data structures, algorithms and practice problems in C/C++.</div>
      <div class="repo-meta"><div class="repo-lang"><div class="lang-dot" style="background:#f34b7d"></div> C++</div><span>⭐ 1</span></div>
    </div>
    <div class="repo-card">
      <div class="repo-name">mini-projects</div>
      <div class="repo-desc">Small creative mini-projects combining HTML, CSS & Python scripts.</div>
      <div class="repo-meta"><div class="repo-lang"><div class="lang-dot" style="background:#563d7c"></div> CSS</div><span>⭐ 3</span></div>
    </div>
  </div>

  <div class="section-title fade-in d4">🔗 Connect With Me</div>
  <div class="links-grid fade-in d5">
    <a class="link-card" href="https://github.com/Sumanta-Jana" target="_blank">
      <div class="link-icon" style="background:rgba(255,255,255,0.08)">⌨️</div>
      <div><div class="link-name">GitHub</div><div class="link-handle">@Sumanta-Jana</div></div>
    </a>
    <a class="link-card" href="https://www.linkedin.com/in/sumanta-jana-1a90a5392" target="_blank">
      <div class="link-icon" style="background:rgba(10,102,194,0.2)">💼</div>
      <div><div class="link-name">LinkedIn</div><div class="link-handle">sumanta-jana-1a90a5392</div></div>
    </a>
    <a class="link-card" href="https://www.instagram.com/sumantajana60" target="_blank">
      <div class="link-icon" style="background:rgba(228,64,95,0.2)">📸</div>
      <div><div class="link-name">Instagram</div><div class="link-handle">@sumantajana60</div></div>
    </a>
    <a class="link-card" href="https://www.facebook.com/share/19o4ZRZhVu/" target="_blank">
      <div class="link-icon" style="background:rgba(24,119,242,0.2)">📘</div>
      <div><div class="link-name">Facebook</div><div class="link-handle">Sumanta Jana</div></div>
    </a>
    <a class="link-card" href="mailto:sumantajana350@gmail.com">
      <div class="link-icon" style="background:rgba(234,67,53,0.2)">✉️</div>
      <div><div class="link-name">Gmail</div><div class="link-handle">sumantajana350@gmail.com</div></div>
    </a>
  </div>

  <div class="terminal fade-in d5">
    <div class="terminal-bar">
      <div class="t-dot t-red"></div>
      <div class="t-dot t-yellow"></div>
      <div class="t-dot t-green"></div>
    </div>
    <div class="t-cmd">who am i</div>
    <div class="t-out">sumanta.jana — B.Tech CSE AI&ML Student @ Parul University, vadodara,Gujarat,India</div>
    <div class="t-cmd">cat skills.txt</div>
    <div class="t-out">["Python", "HTML", "CSS", "C", "C++"]</div>
    <div class="t-cmd">echo $STATUS</div>
    <div class="t-out">Learning every day 🚀 Open to collaborations.</div>
    <div class="t-cmd">git log --oneline</div>
    <div class="t-out">a4f2c1e  Initial commit — Hello World 🌍</div>
  </div>

</main>

<script>
  const grid = document.getElementById('contrib-grid');
  const levels = [null, 'lvl1', 'lvl2', 'lvl3', 'lvl4'];
  const weights = [0.45, 0.25, 0.15, 0.1, 0.05];

  function pickLevel() {
    const r = Math.random();
    let acc = 0;
    for (let i = 0; i < weights.length; i++) {
      acc += weights[i];
      if (r < acc) return levels[i];
    }
    return null;
  }

  for (let w = 0; w < 52; w++) {
    const col = document.createElement('div');
    col.className = 'week-col';
    for (let d = 0; d < 7; d++) {
      const cell = document.createElement('div');
      cell.className = 'day-cell';
      const lvl = pickLevel();
      if (lvl) cell.classList.add(lvl);
      col.appendChild(cell);
    }
    grid.appendChild(col);
  }
</script>
</body>
</html>
