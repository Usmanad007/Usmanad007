<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Muhammad Usman — DevOps & Cloud Engineer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #020510;
    --surface: #0a0f1e;
    --card: #0e1628;
    --border: rgba(99,179,237,0.12);
    --accent1: #38bdf8;
    --accent2: #818cf8;
    --accent3: #34d399;
    --gold: #f59e0b;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow1: rgba(56,189,248,0.35);
    --glow2: rgba(129,140,248,0.3);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    overflow-x: hidden;
    cursor: none;
  }

  /* Custom cursor */
  .cursor {
    width: 12px; height: 12px;
    background: var(--accent1);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9999;
    transition: transform 0.15s ease;
    mix-blend-mode: screen;
  }
  .cursor-trail {
    width: 36px; height: 36px;
    border: 1px solid rgba(56,189,248,0.4);
    border-radius: 50%;
    position: fixed; top: 0; left: 0;
    pointer-events: none;
    z-index: 9998;
    transition: all 0.3s ease;
  }

  /* ─── HERO ─── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  /* 3D perspective canvas background */
  #canvas3d {
    position: absolute;
    inset: 0;
    z-index: 0;
  }

  /* Mesh gradient blobs */
  .blob {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    opacity: 0.45;
    animation: blobFloat 8s ease-in-out infinite alternate;
  }
  .blob1 { width: 500px; height: 500px; background: radial-gradient(circle, #1e40af, transparent); top: -100px; left: -100px; animation-delay: 0s; }
  .blob2 { width: 400px; height: 400px; background: radial-gradient(circle, #0f766e, transparent); bottom: -80px; right: -80px; animation-delay: -3s; }
  .blob3 { width: 300px; height: 300px; background: radial-gradient(circle, #581c87, transparent); top: 50%; left: 50%; transform: translate(-50%,-50%); animation-delay: -5s; }

  @keyframes blobFloat {
    from { transform: scale(1) translate(0,0); }
    to   { transform: scale(1.15) translate(30px, 20px); }
  }

  /* Grid overlay */
  .grid-overlay {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(56,189,248,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(56,189,248,0.04) 1px, transparent 1px);
    background-size: 60px 60px;
    z-index: 1;
  }

  /* Scanline */
  .scanline {
    position: absolute;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.03) 2px,
      rgba(0,0,0,0.03) 4px
    );
    z-index: 2;
    pointer-events: none;
  }

  .hero-content {
    position: relative;
    z-index: 10;
    text-align: center;
    padding: 2rem;
    max-width: 900px;
  }

  /* Badge */
  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(56,189,248,0.08);
    border: 1px solid rgba(56,189,248,0.25);
    border-radius: 100px;
    padding: 6px 18px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--accent1);
    text-transform: uppercase;
    margin-bottom: 2rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.2s forwards;
  }
  .badge-dot {
    width: 6px; height: 6px;
    background: var(--accent3);
    border-radius: 50%;
    animation: pulse 2s infinite;
  }
  @keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:0.3;} }

  /* Name */
  .hero-name {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(3rem, 9vw, 7rem);
    line-height: 0.95;
    letter-spacing: -0.03em;
    margin-bottom: 0.4em;
    opacity: 0;
    animation: fadeUp 0.9s 0.4s forwards;
    position: relative;
  }
  .hero-name .first { display: block; color: #fff; }
  .hero-name .last {
    display: block;
    background: linear-gradient(135deg, var(--accent1) 0%, var(--accent2) 50%, var(--accent3) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    position: relative;
  }
  .hero-name .last::after {
    content: 'USMAN';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    filter: blur(20px);
    opacity: 0.5;
    z-index: -1;
  }

  /* Role ticker */
  .hero-role {
    font-family: 'Space Mono', monospace;
    font-size: clamp(0.9rem, 2vw, 1.1rem);
    color: var(--muted);
    margin-bottom: 2.5rem;
    opacity: 0;
    animation: fadeUp 0.9s 0.6s forwards;
  }
  .role-prefix { color: var(--accent1); margin-right: 8px; }

  /* Skills slider */
  .skills-ticker-wrap {
    margin-bottom: 3rem;
    overflow: hidden;
    opacity: 0;
    animation: fadeUp 0.9s 0.8s forwards;
  }
  .skills-ticker {
    display: flex;
    gap: 12px;
    animation: tickerScroll 18s linear infinite;
    width: max-content;
  }
  .skills-ticker:hover { animation-play-state: paused; }
  @keyframes tickerScroll {
    from { transform: translateX(0); }
    to   { transform: translateX(-50%); }
  }
  .skill-chip {
    display: flex;
    align-items: center;
    gap: 8px;
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 100px;
    padding: 8px 20px;
    font-size: 13px;
    font-weight: 500;
    white-space: nowrap;
    color: var(--text);
    backdrop-filter: blur(8px);
    transition: all 0.3s;
  }
  .skill-chip:hover {
    border-color: var(--accent1);
    color: var(--accent1);
    background: rgba(56,189,248,0.08);
    transform: translateY(-2px);
  }
  .skill-chip .icon { font-size: 16px; }

  /* CTA buttons */
  .hero-ctas {
    display: flex;
    gap: 16px;
    justify-content: center;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.9s 1s forwards;
  }
  .btn-primary {
    padding: 14px 32px;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    border: none;
    border-radius: 8px;
    color: #020510;
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 14px;
    letter-spacing: 0.05em;
    cursor: pointer;
    transition: all 0.3s;
    text-decoration: none;
    display: inline-block;
    position: relative;
    overflow: hidden;
  }
  .btn-primary::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(255,255,255,0.2), transparent);
    opacity: 0;
    transition: opacity 0.3s;
  }
  .btn-primary:hover { transform: translateY(-3px); box-shadow: 0 20px 40px rgba(56,189,248,0.3); }
  .btn-primary:hover::after { opacity: 1; }
  .btn-ghost {
    padding: 14px 32px;
    background: transparent;
    border: 1px solid rgba(255,255,255,0.15);
    border-radius: 8px;
    color: var(--text);
    font-family: 'Syne', sans-serif;
    font-weight: 600;
    font-size: 14px;
    letter-spacing: 0.05em;
    cursor: pointer;
    transition: all 0.3s;
    text-decoration: none;
    display: inline-block;
  }
  .btn-ghost:hover { border-color: var(--accent1); color: var(--accent1); transform: translateY(-3px); }

  /* Scroll indicator */
  .scroll-ind {
    position: absolute;
    bottom: 2rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.1em;
    z-index: 10;
    opacity: 0;
    animation: fadeUp 1s 1.4s forwards;
  }
  .scroll-line {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--accent1), transparent);
    animation: scrollPulse 2s ease-in-out infinite;
  }
  @keyframes scrollPulse { 0%,100%{opacity:0.3;} 50%{opacity:1;} }

  @keyframes fadeUp {
    from { opacity:0; transform: translateY(30px); }
    to   { opacity:1; transform: translateY(0); }
  }

  /* ─── SECTIONS ─── */
  .section {
    max-width: 1100px;
    margin: 0 auto;
    padding: 6rem 2rem;
  }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    color: var(--accent1);
    text-transform: uppercase;
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 12px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    max-width: 80px;
    height: 1px;
    background: linear-gradient(to right, var(--accent1), transparent);
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2rem, 4vw, 3rem);
    font-weight: 800;
    letter-spacing: -0.02em;
    margin-bottom: 1rem;
    color: #fff;
  }

  .section-sub {
    color: var(--muted);
    max-width: 540px;
    line-height: 1.7;
    margin-bottom: 3rem;
  }

  /* About cards */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
  }
  @media(max-width:640px){.about-grid{grid-template-columns:1fr;}}

  .about-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem;
    transition: all 0.4s;
    position: relative;
    overflow: hidden;
  }
  .about-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 2px;
    background: linear-gradient(90deg, var(--accent1), var(--accent2));
    opacity: 0;
    transition: opacity 0.3s;
  }
  .about-card:hover { border-color: rgba(56,189,248,0.3); transform: translateY(-4px); box-shadow: 0 20px 40px rgba(0,0,0,0.4); }
  .about-card:hover::before { opacity: 1; }
  .card-icon { font-size: 2rem; margin-bottom: 1rem; }
  .card-title { font-family: 'Syne', sans-serif; font-size: 1.1rem; font-weight: 700; margin-bottom: 0.5rem; }
  .card-text { color: var(--muted); font-size: 0.9rem; line-height: 1.6; }

  /* Tech stack */
  .stack-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
    gap: 1rem;
  }
  .stack-item {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 1.25rem;
    text-align: center;
    transition: all 0.3s;
    cursor: default;
  }
  .stack-item:hover { border-color: var(--accent1); transform: translateY(-4px) scale(1.02); background: rgba(56,189,248,0.05); }
  .stack-item .s-icon { font-size: 2rem; margin-bottom: 0.5rem; display: block; }
  .stack-item .s-name { font-family: 'Space Mono', monospace; font-size: 11px; color: var(--muted); }

  /* Stats */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1.5rem;
    margin-bottom: 3rem;
  }
  @media(max-width:600px){.stats-row{grid-template-columns:1fr;}}
  .stat-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .stat-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 50%;
    transform: translateX(-50%);
    width: 60%;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent1), transparent);
  }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 3rem;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent1), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .stat-label { color: var(--muted); font-size: 0.85rem; margin-top: 0.25rem; }

  /* GitHub stats section */
  .gh-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.5rem;
    margin-bottom: 1.5rem;
  }
  @media(max-width:700px){.gh-grid{grid-template-columns:1fr;}}
  .gh-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    overflow: hidden;
    transition: all 0.3s;
  }
  .gh-card:hover { transform: translateY(-4px); border-color: rgba(56,189,248,0.25); }
  .gh-card img { width: 100%; display: block; }

  /* Connect */
  .connect-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
  }
  @media(max-width:600px){.connect-grid{grid-template-columns:1fr;}}
  .connect-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 12px;
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 2rem;
    text-decoration: none;
    color: var(--text);
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .connect-card::before {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 0.3s;
  }
  .connect-card.linkedin::before { background: radial-gradient(circle at center, rgba(10,102,194,0.15), transparent 70%); }
  .connect-card.github::before  { background: radial-gradient(circle at center, rgba(255,255,255,0.05), transparent 70%); }
  .connect-card.email::before   { background: radial-gradient(circle at center, rgba(234,67,53,0.12), transparent 70%); }
  .connect-card:hover { transform: translateY(-5px); }
  .connect-card:hover::before { opacity: 1; }
  .connect-card.linkedin:hover { border-color: #0a66c2; }
  .connect-card.github:hover   { border-color: rgba(255,255,255,0.3); }
  .connect-card.email:hover    { border-color: #ea4335; }
  .connect-icon { font-size: 2.5rem; }
  .connect-label { font-family: 'Syne', sans-serif; font-weight: 700; font-size: 1rem; }
  .connect-sub   { font-size: 0.8rem; color: var(--muted); }

  /* Footer */
  footer {
    text-align: center;
    padding: 3rem 2rem;
    border-top: 1px solid var(--border);
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    font-size: 12px;
  }
  footer span { color: var(--accent1); }

  /* Divider */
  .divider {
    height: 1px;
    background: linear-gradient(to right, transparent, var(--border), transparent);
    margin: 0 2rem;
  }

  /* Floating particles */
  .particles { position: absolute; inset: 0; z-index: 3; pointer-events: none; }
  .particle {
    position: absolute;
    width: 2px; height: 2px;
    background: var(--accent1);
    border-radius: 50%;
    opacity: 0;
    animation: particleFly var(--dur) ease-in-out infinite var(--delay);
  }
  @keyframes particleFly {
    0%   { opacity: 0; transform: translateY(0) translateX(0); }
    20%  { opacity: 0.8; }
    80%  { opacity: 0.4; }
    100% { opacity: 0; transform: translateY(-120px) translateX(var(--dx)); }
  }
</style>
</head>
<body>

<div class="cursor" id="cursor"></div>
<div class="cursor-trail" id="cursorTrail"></div>

<!-- ═══════════════════════════ HERO ═══════════════════════════ -->
<section class="hero">
  <canvas id="canvas3d"></canvas>
  <div class="blob blob1"></div>
  <div class="blob blob2"></div>
  <div class="blob blob3"></div>
  <div class="grid-overlay"></div>
  <div class="scanline"></div>
  <div class="particles" id="particles"></div>

  <div class="hero-content">
    <div class="hero-badge">
      <span class="badge-dot"></span>
      Available for opportunities
    </div>

    <h1 class="hero-name">
      <span class="first">Muhammad</span>
      <span class="last">Usman</span>
    </h1>

    <p class="hero-role">
      <span class="role-prefix">~/</span>DevOps &amp; Cloud Engineer
    </p>

    <!-- Skills ticker -->
    <div class="skills-ticker-wrap">
      <div class="skills-ticker">
        <!-- repeated twice for infinite loop -->
        <span class="skill-chip"><span class="icon">☁️</span> AWS Cloud</span>
        <span class="skill-chip"><span class="icon">🐳</span> Docker</span>
        <span class="skill-chip"><span class="icon">⚙️</span> GitHub Actions</span>
        <span class="skill-chip"><span class="icon">🐧</span> Linux</span>
        <span class="skill-chip"><span class="icon">📜</span> Bash Scripting</span>
        <span class="skill-chip"><span class="icon">🔁</span> CI/CD Pipelines</span>
        <span class="skill-chip"><span class="icon">📦</span> Containerization</span>
        <span class="skill-chip"><span class="icon">🏗️</span> Infrastructure as Code</span>
        <span class="skill-chip"><span class="icon">🔀</span> GitOps</span>
        <span class="skill-chip"><span class="icon">📊</span> Cloud Monitoring</span>
        <!-- duplicate -->
        <span class="skill-chip"><span class="icon">☁️</span> AWS Cloud</span>
        <span class="skill-chip"><span class="icon">🐳</span> Docker</span>
        <span class="skill-chip"><span class="icon">⚙️</span> GitHub Actions</span>
        <span class="skill-chip"><span class="icon">🐧</span> Linux</span>
        <span class="skill-chip"><span class="icon">📜</span> Bash Scripting</span>
        <span class="skill-chip"><span class="icon">🔁</span> CI/CD Pipelines</span>
        <span class="skill-chip"><span class="icon">📦</span> Containerization</span>
        <span class="skill-chip"><span class="icon">🏗️</span> Infrastructure as Code</span>
        <span class="skill-chip"><span class="icon">🔀</span> GitOps</span>
        <span class="skill-chip"><span class="icon">📊</span> Cloud Monitoring</span>
      </div>
    </div>

    <div class="hero-ctas">
      <a href="https://linkedin.com/in/YOUR_LINKEDIN" class="btn-primary">Connect on LinkedIn →</a>
      <a href="https://github.com/YOUR_GITHUB_USERNAME" class="btn-ghost">View GitHub</a>
    </div>
  </div>

  <div class="scroll-ind">
    <div class="scroll-line"></div>
    SCROLL
  </div>
</section>

<div class="divider"></div>

<!-- ═══════════════════════════ ABOUT ═══════════════════════════ -->
<section class="section">
  <div class="section-label">About</div>
  <h2 class="section-title">Engineering reliability,<br/>one pipeline at a time.</h2>
  <p class="section-sub">Passionate about building infrastructure that scales silently, deploys automatically, and fails gracefully. I bridge development and operations with precision.</p>

  <div class="about-grid">
    <div class="about-card">
      <div class="card-icon">☁️</div>
      <div class="card-title">Cloud Infrastructure</div>
      <div class="card-text">Architecting and managing scalable, secure AWS environments — from VPCs to serverless workloads — with cost efficiency in mind.</div>
    </div>
    <div class="about-card">
      <div class="card-icon">🔁</div>
      <div class="card-title">CI/CD Automation</div>
      <div class="card-text">Designing zero-downtime deployment pipelines using GitHub Actions, enabling rapid, confident software delivery at scale.</div>
    </div>
    <div class="about-card">
      <div class="card-icon">🐳</div>
      <div class="card-title">Containerization</div>
      <div class="card-text">Packaging applications with Docker for consistent, reproducible environments across dev, staging, and production.</div>
    </div>
    <div class="about-card">
      <div class="card-icon">🎓</div>
      <div class="card-title">Education</div>
      <div class="card-text">Bachelor of Computer Sciences — University of Okara, Pakistan. Class of 2024. Built strong foundations in systems, networking, and software engineering.</div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══════════════════════════ STACK ═══════════════════════════ -->
<section class="section">
  <div class="section-label">Tech Stack</div>
  <h2 class="section-title">Tools of the trade.</h2>
  <p class="section-sub">Technologies I work with daily to build, automate, and maintain production systems.</p>

  <div class="stack-grid">
    <div class="stack-item">
      <span class="s-icon">☁️</span>
      <span class="s-name">AWS</span>
    </div>
    <div class="stack-item">
      <span class="s-icon">🐳</span>
      <span class="s-name">Docker</span>
    </div>
    <div class="stack-item">
      <span class="s-icon">⚙️</span>
      <span class="s-name">GitHub Actions</span>
    </div>
    <div class="stack-item">
      <span class="s-icon">🐧</span>
      <span class="s-name">Linux</span>
    </div>
    <div class="stack-item">
      <span class="s-icon">📜</span>
      <span class="s-name">Bash</span>
    </div>
    <div class="stack-item">
      <span class="s-icon">🐙</span>
      <span class="s-name">Git / GitHub</span>
    </div>
    <div class="stack-item">
      <span class="s-icon">🏗️</span>
      <span class="s-name">IaC</span>
    </div>
    <div class="stack-item">
      <span class="s-icon">🔀</span>
      <span class="s-name">GitOps</span>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ═══════════════════════════ GITHUB STATS ═══════════════════════════ -->
<section class="section">
  <div class="section-label">GitHub</div>
  <h2 class="section-title">Code speaks louder.</h2>
  <p class="section-sub">A snapshot of my open-source contributions, streaks, and most-used technologies.</p>

  <div class="gh-grid">
    <div class="gh-card">
      <img src="https://github-readme-stats.vercel.app/api?username=YOUR_GITHUB_USERNAME&show_icons=true&theme=github_dark&border_color=0e1628&bg_color=0e1628&title_color=38bdf8&icon_color=818cf8&text_color=c9d1d9&hide_border=true&rank_icon=github&include_all_commits=true" alt="GitHub Stats"/>
    </div>
    <div class="gh-card">
      <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_GITHUB_USERNAME&layout=compact&theme=github_dark&border_color=0e1628&bg_color=0e1628&title_color=38bdf8&text_color=c9d1d9&hide_border=true" alt="Top Languages"/>
    </div>
  </div>
  <div class="gh-card" style="max-width:600px;margin:0 auto;">
    <img src="https://streak-stats.demolab.com/?user=YOUR_GITHUB_USERNAME&theme=github-dark-blue&border=0e1628&background=0e1628&stroke=38bdf8&ring=38bdf8&fire=f59e0b&currStreakLabel=38bdf8&sideLabels=64748b&dates=64748b&hide_border=true" style="width:100%;display:block;" alt="Streak"/>
  </div>
</section>

<div class="divider"></div>

<!-- ═══════════════════════════ CONNECT ═══════════════════════════ -->
<section class="section">
  <div class="section-label">Connect</div>
  <h2 class="section-title">Let's build something.</h2>
  <p class="section-sub">Open to DevOps roles, freelance infrastructure work, and collaboration. Let's talk.</p>

  <div class="connect-grid">
    <a href="https://linkedin.com/in/YOUR_LINKEDIN" class="connect-card linkedin" target="_blank">
      <span class="connect-icon">💼</span>
      <span class="connect-label">LinkedIn</span>
      <span class="connect-sub">Muhammad Usman</span>
    </a>
    <a href="https://github.com/YOUR_GITHUB_USERNAME" class="connect-card github" target="_blank">
      <span class="connect-icon">🐙</span>
      <span class="connect-label">GitHub</span>
      <span class="connect-sub">@YOUR_GITHUB_USERNAME</span>
    </a>
    <a href="mailto:YOUR_EMAIL" class="connect-card email">
      <span class="connect-icon">✉️</span>
      <span class="connect-label">Email</span>
      <span class="connect-sub">YOUR_EMAIL</span>
    </a>
  </div>
</section>

<footer>
  Crafted with precision by <span>Muhammad Usman</span> · DevOps &amp; Cloud Engineer · 2024
</footer>

<script>
// ── Cursor ──
const cursor = document.getElementById('cursor');
const trail  = document.getElementById('cursorTrail');
let mx=0, my=0, tx=0, ty=0;
document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; });
function animCursor(){
  tx += (mx - tx) * 0.12;
  ty += (my - ty) * 0.12;
  cursor.style.left = mx - 6 + 'px';
  cursor.style.top  = my - 6 + 'px';
  trail.style.left  = tx - 18 + 'px';
  trail.style.top   = ty - 18 + 'px';
  requestAnimationFrame(animCursor);
}
animCursor();

// ── Particles ──
const container = document.getElementById('particles');
for(let i=0;i<30;i++){
  const p = document.createElement('div');
  p.className = 'particle';
  p.style.cssText = `
    left:${Math.random()*100}%;
    top:${Math.random()*100}%;
    --dur:${4+Math.random()*6}s;
    --delay:-${Math.random()*8}s;
    --dx:${(Math.random()-0.5)*60}px;
    width:${Math.random()>0.7?3:2}px;
    height:${Math.random()>0.7?3:2}px;
    background: ${Math.random()>0.5?'#38bdf8':'#818cf8'};
  `;
  container.appendChild(p);
}

// ── 3D Canvas (floating torus-like geometry) ──
const canvas = document.getElementById('canvas3d');
const ctx = canvas.getContext('2d');
let W, H, t = 0;

function resize(){
  W = canvas.width  = window.innerWidth;
  H = canvas.height = window.innerHeight;
}
resize();
window.addEventListener('resize', resize);

function drawScene(){
  ctx.clearRect(0,0,W,H);
  t += 0.008;

  const cx = W/2, cy = H/2;
  const rings = 5;
  const pointsPerRing = 60;

  for(let r=0;r<rings;r++){
    const R = 180 + r*60;
    const phase = t + r*0.4;
    const opacity = 0.06 - r*0.008;

    ctx.beginPath();
    for(let i=0;i<=pointsPerRing;i++){
      const angle = (i/pointsPerRing)*Math.PI*2;
      const wobble = Math.sin(angle*3 + phase)*12;
      const x = cx + Math.cos(angle)*(R + wobble);
      const y = cy + Math.sin(angle)*(R + wobble)*0.35;
      i===0 ? ctx.moveTo(x,y) : ctx.lineTo(x,y);
    }
    ctx.strokeStyle = `rgba(56,189,248,${opacity})`;
    ctx.lineWidth = 1;
    ctx.stroke();
  }

  // Floating dots on the ring
  for(let d=0;d<20;d++){
    const angle = (d/20)*Math.PI*2 + t*0.5;
    const R = 250 + Math.sin(t + d)*40;
    const x = cx + Math.cos(angle)*R;
    const y = cy + Math.sin(angle)*R*0.35;
    const size = 1.5 + Math.sin(t*2+d)*0.5;
    const alpha = 0.3 + Math.sin(t+d)*0.2;

    const grad = ctx.createRadialGradient(x,y,0,x,y,size*4);
    grad.addColorStop(0, `rgba(56,189,248,${alpha})`);
    grad.addColorStop(1, 'transparent');
    ctx.fillStyle = grad;
    ctx.beginPath();
    ctx.arc(x,y,size*4,0,Math.PI*2);
    ctx.fill();
  }

  requestAnimationFrame(drawScene);
}
drawScene();

// ── Scroll-reveal for cards ──
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if(e.isIntersecting){
      e.target.style.opacity = '1';
      e.target.style.transform = 'translateY(0)';
    }
  });
},{threshold:0.15});

document.querySelectorAll('.about-card, .stack-item, .connect-card, .gh-card, .stat-card').forEach(el=>{
  el.style.opacity = '0';
  el.style.transform = 'translateY(24px)';
  el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
  observer.observe(el);
});
</script>
</body>
</html>
