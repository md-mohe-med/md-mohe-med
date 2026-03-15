<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mohammed – README</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap');

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #0a0e17;
    --surface: #111827;
    --border: rgba(99,255,180,0.12);
    --accent: #3dffa0;
    --accent2: #38bdf8;
    --accent3: #f472b6;
    --text: #e2e8f0;
    --muted: #64748b;
    --glow: 0 0 20px rgba(61,255,160,0.3);
  }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Syne', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Animated grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(99,255,180,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(99,255,180,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    z-index: 0;
    pointer-events: none;
  }

  .container {
    position: relative;
    z-index: 1;
    max-width: 860px;
    margin: 0 auto;
    padding: 60px 32px 80px;
  }

  /* Hero */
  .hero {
    margin-bottom: 64px;
    opacity: 0;
    transform: translateY(24px);
    animation: fadeUp 0.7s ease forwards;
  }

  .tag {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    border: 1px solid var(--border);
    background: rgba(61,255,160,0.06);
    padding: 4px 12px;
    border-radius: 100px;
    margin-bottom: 24px;
    letter-spacing: 0.05em;
  }

  .tag::before {
    content: '';
    width: 6px; height: 6px;
    background: var(--accent);
    border-radius: 50%;
    box-shadow: var(--glow);
    animation: pulse 2s ease-in-out infinite;
  }

  h1 {
    font-size: clamp(38px, 8vw, 68px);
    font-weight: 800;
    line-height: 1;
    letter-spacing: -0.03em;
    background: linear-gradient(135deg, #fff 30%, var(--accent) 70%, var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    margin-bottom: 20px;
  }

  .subtitle {
    font-size: 16px;
    color: var(--muted);
    line-height: 1.7;
    max-width: 520px;
    font-weight: 400;
  }

  .subtitle strong {
    color: var(--text);
    font-weight: 600;
  }

  /* Section */
  .section {
    margin-bottom: 52px;
    opacity: 0;
    transform: translateY(20px);
  }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--accent);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* Tech grid */
  .tech-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 12px;
  }

  .tech-category {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 20px;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
    cursor: default;
  }

  .tech-category::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(circle at 80% 20%, rgba(61,255,160,0.06), transparent 60%);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .tech-category:hover {
    border-color: rgba(61,255,160,0.35);
    transform: translateY(-3px);
  }

  .tech-category:hover::before { opacity: 1; }

  .cat-header {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 14px;
  }

  .cat-icon {
    width: 28px; height: 28px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 14px;
  }

  .cat-icon.frontend { background: rgba(61,255,160,0.12); }
  .cat-icon.backend  { background: rgba(56,189,248,0.12); }
  .cat-icon.db       { background: rgba(244,114,182,0.12); }
  .cat-icon.tools    { background: rgba(251,191,36,0.12); }

  .cat-name {
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    color: var(--muted);
  }

  .pill-row {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }

  .pill {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    padding: 4px 10px;
    border-radius: 100px;
    border: 1px solid;
    transition: all 0.2s;
    letter-spacing: 0.02em;
    cursor: default;
  }

  .pill:hover { transform: scale(1.05); }

  .pill-green { border-color: rgba(61,255,160,0.3); color: var(--accent); background: rgba(61,255,160,0.05); }
  .pill-blue  { border-color: rgba(56,189,248,0.3); color: var(--accent2); background: rgba(56,189,248,0.05); }
  .pill-pink  { border-color: rgba(244,114,182,0.3); color: var(--accent3); background: rgba(244,114,182,0.05); }
  .pill-amber { border-color: rgba(251,191,36,0.3); color: #fbbf24; background: rgba(251,191,36,0.05); }

  .pill-dot {
    width: 5px; height: 5px;
    border-radius: 50%;
    flex-shrink: 0;
  }
  .pill-green .pill-dot { background: var(--accent); }
  .pill-blue  .pill-dot { background: var(--accent2); }
  .pill-pink  .pill-dot { background: var(--accent3); }
  .pill-amber .pill-dot { background: #fbbf24; }

  /* Stats row */
  .stats-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    margin-bottom: 52px;
  }

  .stat-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 20px;
    text-align: center;
    transition: border-color 0.3s, transform 0.3s;
  }

  .stat-card:hover {
    border-color: rgba(61,255,160,0.35);
    transform: translateY(-3px);
  }

  .stat-num {
    font-size: 32px;
    font-weight: 800;
    background: linear-gradient(135deg, #fff, var(--accent));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    line-height: 1;
    margin-bottom: 6px;
  }

  .stat-label {
    font-size: 11px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    letter-spacing: 0.05em;
  }

  /* Focus areas */
  .focus-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .focus-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 14px;
    padding: 22px;
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s, transform 0.3s;
  }

  .focus-card:hover {
    border-color: rgba(56,189,248,0.35);
    transform: translateY(-3px);
  }

  .focus-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
    background: var(--accent2);
    border-radius: 2px 0 0 2px;
    opacity: 0.6;
  }

  .focus-card:nth-child(2)::after { background: var(--accent); }
  .focus-card:nth-child(3)::after { background: var(--accent3); }
  .focus-card:nth-child(4)::after { background: #fbbf24; }

  .focus-title {
    font-size: 14px;
    font-weight: 700;
    margin-bottom: 6px;
    color: var(--text);
  }

  .focus-desc {
    font-size: 12px;
    color: var(--muted);
    line-height: 1.6;
    font-family: 'Space Mono', monospace;
  }

  /* Terminal block */
  .terminal {
    background: #0d1117;
    border: 1px solid var(--border);
    border-radius: 14px;
    overflow: hidden;
    font-family: 'Space Mono', monospace;
  }

  .terminal-bar {
    background: rgba(255,255,255,0.04);
    border-bottom: 1px solid var(--border);
    padding: 10px 16px;
    display: flex;
    align-items: center;
    gap: 7px;
  }

  .dot { width: 10px; height: 10px; border-radius: 50%; }
  .dot-r { background: #ff5f57; }
  .dot-y { background: #febc2e; }
  .dot-g { background: #28c840; }

  .terminal-body { padding: 20px 24px; font-size: 13px; line-height: 2; }
  .t-dim   { color: #444d58; }
  .t-green { color: var(--accent); }
  .t-blue  { color: var(--accent2); }
  .t-pink  { color: var(--accent3); }
  .t-amber { color: #fbbf24; }
  .t-white { color: #e2e8f0; }

  .cursor {
    display: inline-block;
    width: 8px; height: 14px;
    background: var(--accent);
    vertical-align: middle;
    margin-left: 2px;
    animation: blink 1s step-end infinite;
  }

  /* Animations */
  @keyframes fadeUp {
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.5; transform: scale(0.8); }
  }

  @keyframes blink {
    0%, 100% { opacity: 1; }
    50% { opacity: 0; }
  }

  @keyframes scanline {
    0%   { transform: translateY(-100%); }
    100% { transform: translateY(100vh); }
  }

  /* Scan line effect */
  .scanline {
    position: fixed;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(transparent, rgba(61,255,160,0.08), transparent);
    animation: scanline 8s linear infinite;
    pointer-events: none;
    z-index: 999;
  }

  @media (max-width: 600px) {
    .focus-grid { grid-template-columns: 1fr; }
    .stats-row  { grid-template-columns: 1fr; }
    .tech-grid  { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="scanline"></div>
<div class="container">

  <!-- Hero -->
  <div class="hero">
    <div class="tag">Available for opportunities</div>
    <h1>Hi, I'm Mohammed</h1>
    <p class="subtitle">
      <strong>Junior UG Bounty Hunter</strong> &amp; <strong>Web Developer</strong> specializing in
      cybersecurity, bug hunting, and web application development. I identify vulnerabilities,
      build secure efficient code, and contribute to open-source projects.
    </p>
  </div>

  <!-- Stats -->
  <div class="stats-row section">
    <div class="stat-card">
      <div class="stat-num">7+</div>
      <div class="stat-label">Tech Stacks</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">OSS</div>
      <div class="stat-label">Contributor</div>
    </div>
    <div class="stat-card">
      <div class="stat-num">BUG</div>
      <div class="stat-label">Hunter</div>
    </div>
  </div>

  <!-- Skills -->
  <div class="section">
    <div class="section-label">Tech Stack</div>
    <div class="tech-grid">

      <div class="tech-category">
        <div class="cat-header">
          <div class="cat-icon frontend">⬡</div>
          <span class="cat-name">Frontend</span>
        </div>
        <div class="pill-row">
          <span class="pill pill-green"><span class="pill-dot"></span>HTML5</span>
          <span class="pill pill-green"><span class="pill-dot"></span>CSS3</span>
          <span class="pill pill-green"><span class="pill-dot"></span>JavaScript</span>
          <span class="pill pill-green"><span class="pill-dot"></span>React</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="cat-header">
          <div class="cat-icon backend">⬡</div>
          <span class="cat-name">Backend</span>
        </div>
        <div class="pill-row">
          <span class="pill pill-blue"><span class="pill-dot"></span>PHP</span>
          <span class="pill pill-blue"><span class="pill-dot"></span>Laravel</span>
          <span class="pill pill-blue"><span class="pill-dot"></span>Node.js</span>
          <span class="pill pill-blue"><span class="pill-dot"></span>Express</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="cat-header">
          <div class="cat-icon db">⬡</div>
          <span class="cat-name">Database</span>
        </div>
        <div class="pill-row">
          <span class="pill pill-pink"><span class="pill-dot"></span>MySQL</span>
          <span class="pill pill-pink"><span class="pill-dot"></span>MongoDB</span>
        </div>
      </div>

      <div class="tech-category">
        <div class="cat-header">
          <div class="cat-icon tools">⬡</div>
          <span class="cat-name">Tools &amp; Others</span>
        </div>
        <div class="pill-row">
          <span class="pill pill-amber"><span class="pill-dot"></span>Git</span>
          <span class="pill pill-amber"><span class="pill-dot"></span>Docker</span>
          <span class="pill pill-amber"><span class="pill-dot"></span>Linux</span>
          <span class="pill pill-amber"><span class="pill-dot"></span>Bash</span>
          <span class="pill pill-amber"><span class="pill-dot"></span>Java</span>
          <span class="pill pill-amber"><span class="pill-dot"></span>C</span>
          <span class="pill pill-amber"><span class="pill-dot"></span>Python</span>
          <span class="pill pill-amber"><span class="pill-dot"></span>Figma</span>
        </div>
      </div>

    </div>
  </div>

  <!-- Focus Areas -->
  <div class="section">
    <div class="section-label">Focus Areas</div>
    <div class="focus-grid">
      <div class="focus-card">
        <div class="focus-title">Bug Hunting</div>
        <div class="focus-desc">Identifying vulnerabilities in web applications through manual and automated testing.</div>
      </div>
      <div class="focus-card">
        <div class="focus-title">Secure Development</div>
        <div class="focus-desc">Building web apps with security-first principles and clean architecture.</div>
      </div>
      <div class="focus-card">
        <div class="focus-title">Open Source</div>
        <div class="focus-desc">Contributing to community projects and building tools for developers.</div>
      </div>
      <div class="focus-card">
        <div class="focus-title">Full Stack</div>
        <div class="focus-desc">End-to-end development across frontend, backend, and database layers.</div>
      </div>
    </div>
  </div>

  <!-- Terminal -->
  <div class="section">
    <div class="section-label">Quick Info</div>
    <div class="terminal">
      <div class="terminal-bar">
        <div class="dot dot-r"></div>
        <div class="dot dot-y"></div>
        <div class="dot dot-g"></div>
      </div>
      <div class="terminal-body">
        <div><span class="t-dim">~$</span> <span class="t-green">cat</span> <span class="t-white">about.json</span></div>
        <div>&nbsp;</div>
        <div><span class="t-dim">{</span></div>
        <div>&nbsp;&nbsp;<span class="t-blue">"name"</span><span class="t-dim">:</span> <span class="t-pink">"Mohammed"</span><span class="t-dim">,</span></div>
        <div>&nbsp;&nbsp;<span class="t-blue">"role"</span><span class="t-dim">:</span> <span class="t-pink">"Junior UG Bounty Hunter &amp; Web Developer"</span><span class="t-dim">,</span></div>
        <div>&nbsp;&nbsp;<span class="t-blue">"location"</span><span class="t-dim">:</span> <span class="t-pink">"Algeria"</span><span class="t-dim">,</span></div>
        <div>&nbsp;&nbsp;<span class="t-blue">"focus"</span><span class="t-dim">: [</span><span class="t-amber">"security"</span><span class="t-dim">,</span> <span class="t-amber">"web dev"</span><span class="t-dim">,</span> <span class="t-amber">"open source"</span><span class="t-dim">],</span></div>
        <div>&nbsp;&nbsp;<span class="t-blue">"available"</span><span class="t-dim">:</span> <span class="t-green">true</span></div>
        <div><span class="t-dim">}</span></div>
        <div>&nbsp;</div>
        <div><span class="t-dim">~$</span> <span class="cursor"></span></div>
      </div>
    </div>
  </div>

</div>

<script>
  // Staggered section reveal on scroll
  const sections = document.querySelectorAll('.section');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.style.animation = 'fadeUp 0.6s ease forwards';
        }, 0);
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.1 });

  sections.forEach((s, i) => {
    s.style.animationDelay = (i * 0.1) + 's';
    observer.observe(s);
  });
</script>
</body>
</html>
