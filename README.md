<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shoyeb Chaudhari — Developer Profile</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #060912;
    --bg2: #0b1120;
    --bg3: #111827;
    --cyan: #00f5ff;
    --violet: #a855f7;
    --pink: #ff3cac;
    --green: #00ff94;
    --orange: #ff6b35;
    --yellow: #ffd60a;
    --text: #e2e8f0;
    --muted: #64748b;
    --border: rgba(0,245,255,0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    overflow-x: hidden;
    position: relative;
  }

  /* === ANIMATED BACKGROUND GRID === */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,245,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,245,255,0.03) 1px, transparent 1px);
    background-size: 60px 60px;
    animation: gridMove 20s linear infinite;
    pointer-events: none;
    z-index: 0;
  }

  @keyframes gridMove {
    0% { transform: translateY(0); }
    100% { transform: translateY(60px); }
  }

  /* === FLOATING ORBS === */
  .orb {
    position: fixed;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
    opacity: 0.35;
    animation: orbFloat 12s ease-in-out infinite;
  }
  .orb1 { width: 500px; height: 500px; background: var(--violet); top: -150px; right: -150px; animation-delay: 0s; }
  .orb2 { width: 400px; height: 400px; background: var(--cyan); bottom: 20%; left: -100px; animation-delay: -4s; }
  .orb3 { width: 300px; height: 300px; background: var(--pink); bottom: -100px; right: 20%; animation-delay: -8s; }

  @keyframes orbFloat {
    0%, 100% { transform: translateY(0) scale(1); }
    50% { transform: translateY(-40px) scale(1.05); }
  }

  /* === CONTENT WRAPPER === */
  .content { position: relative; z-index: 1; max-width: 900px; margin: 0 auto; padding: 0 24px 80px; }

  /* === HERO === */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 80px 0 60px;
    position: relative;
  }

  .hero-tag {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--cyan);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 24px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.2s;
  }

  .hero-tag::before {
    content: '';
    display: inline-block;
    width: 24px;
    height: 1px;
    background: var(--cyan);
  }

  .hero-name {
    font-family: 'Syne', sans-serif;
    font-size: clamp(52px, 8vw, 96px);
    font-weight: 800;
    line-height: 0.95;
    letter-spacing: -3px;
    margin-bottom: 16px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.4s;
  }

  .hero-name .line1 { display: block; color: var(--text); }
  .hero-name .line2 {
    display: block;
    background: linear-gradient(135deg, var(--cyan) 0%, var(--violet) 50%, var(--pink) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    background-size: 200% 200%;
    animation: gradShift 4s ease infinite 1s, fadeUp 0.6s ease forwards 0.4s;
  }

  @keyframes gradShift {
    0%, 100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
  }

  .hero-role {
    font-family: 'Space Mono', monospace;
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 40px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.6s;
    line-height: 1.8;
  }

  .hero-role span {
    color: var(--cyan);
    font-weight: 700;
  }

  .hero-stats {
    display: flex;
    gap: 32px;
    flex-wrap: wrap;
    margin-bottom: 48px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.8s;
  }

  .stat {
    display: flex;
    flex-direction: column;
  }

  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 32px;
    font-weight: 800;
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .stat-label {
    font-size: 12px;
    color: var(--muted);
    letter-spacing: 1px;
    font-family: 'Space Mono', monospace;
  }

  .hero-links {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 1s;
  }

  .btn {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 12px 24px;
    border-radius: 6px;
    font-size: 13px;
    font-weight: 600;
    text-decoration: none;
    transition: all 0.3s ease;
    font-family: 'Space Mono', monospace;
    letter-spacing: 0.5px;
    position: relative;
    overflow: hidden;
  }

  .btn::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    opacity: 0;
    transition: opacity 0.3s;
  }

  .btn:hover::before { opacity: 0.15; }

  .btn-primary {
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    color: #000;
    font-weight: 700;
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 30px rgba(0,245,255,0.4);
  }

  .btn-outline {
    border: 1px solid var(--border);
    color: var(--text);
    background: rgba(255,255,255,0.03);
  }

  .btn-outline:hover {
    border-color: var(--cyan);
    color: var(--cyan);
    transform: translateY(-2px);
  }

  /* === SCROLL INDICATOR === */
  .scroll-hint {
    position: absolute;
    bottom: 30px;
    left: 0;
    display: flex;
    align-items: center;
    gap: 12px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 2px;
    animation: fadeUp 0.6s ease forwards 1.4s, bobble 2s ease-in-out infinite 2s;
    opacity: 0;
  }

  .scroll-line {
    width: 40px;
    height: 1px;
    background: linear-gradient(90deg, var(--muted), transparent);
  }

  @keyframes bobble {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(6px); }
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* === SECTION STYLES === */
  .section { margin-bottom: 100px; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 40px;
  }

  .section-num {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--cyan);
    letter-spacing: 2px;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 36px;
    font-weight: 800;
    letter-spacing: -1px;
  }

  .section-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* === CODE BLOCK ABOUT === */
  .code-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    line-height: 1.8;
  }

  .code-header {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 14px 20px;
    background: rgba(255,255,255,0.03);
    border-bottom: 1px solid var(--border);
  }

  .code-dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
  }

  .code-filename {
    margin-left: auto;
    font-size: 11px;
    color: var(--muted);
  }

  .code-body { padding: 24px; }

  .c-purple { color: var(--violet); }
  .c-cyan { color: var(--cyan); }
  .c-green { color: var(--green); }
  .c-orange { color: var(--orange); }
  .c-yellow { color: var(--yellow); }
  .c-pink { color: var(--pink); }
  .c-muted { color: var(--muted); }

  /* === ABOUT GRID === */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
    margin-top: 24px;
  }

  .about-pill {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 16px 20px;
    background: rgba(0,245,255,0.04);
    border: 1px solid var(--border);
    border-radius: 10px;
    font-size: 14px;
    transition: all 0.3s;
  }

  .about-pill:hover {
    border-color: var(--cyan);
    background: rgba(0,245,255,0.08);
    transform: translateX(4px);
  }

  .about-pill-icon {
    font-size: 20px;
    min-width: 28px;
  }

  /* === SKILLS === */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
    gap: 12px;
  }

  .skill-chip {
    padding: 12px 16px;
    border-radius: 8px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    text-align: center;
    border: 1px solid transparent;
    transition: all 0.3s ease;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .skill-chip::before {
    content: '';
    position: absolute;
    inset: 0;
    opacity: 0;
    transition: opacity 0.3s;
  }

  .skill-chip:hover { transform: translateY(-4px); }
  .skill-chip:hover::before { opacity: 1; }

  .sk-python { background: rgba(55,118,171,0.15); border-color: rgba(55,118,171,0.4); color: #79aadc; }
  .sk-python:hover { box-shadow: 0 8px 24px rgba(55,118,171,0.3); border-color: #3776AB; }

  .sk-java { background: rgba(237,139,0,0.12); border-color: rgba(237,139,0,0.3); color: #f0a830; }
  .sk-java:hover { box-shadow: 0 8px 24px rgba(237,139,0,0.25); border-color: #ED8B00; }

  .sk-react { background: rgba(97,218,251,0.1); border-color: rgba(97,218,251,0.25); color: #61dafb; }
  .sk-react:hover { box-shadow: 0 8px 24px rgba(97,218,251,0.2); border-color: #61DAFB; }

  .sk-tf { background: rgba(255,111,0,0.1); border-color: rgba(255,111,0,0.25); color: #ff8c3a; }
  .sk-tf:hover { box-shadow: 0 8px 24px rgba(255,111,0,0.2); border-color: #FF6F00; }

  .sk-android { background: rgba(61,220,132,0.1); border-color: rgba(61,220,132,0.25); color: #3ddc84; }
  .sk-android:hover { box-shadow: 0 8px 24px rgba(61,220,132,0.2); border-color: #3DDC84; }

  .sk-mongo { background: rgba(78,169,75,0.1); border-color: rgba(78,169,75,0.25); color: #4ea94b; }
  .sk-mongo:hover { box-shadow: 0 8px 24px rgba(78,169,75,0.2); border-color: #4EA94B; }

  .sk-firebase { background: rgba(255,202,40,0.1); border-color: rgba(255,202,40,0.25); color: #ffca28; }
  .sk-firebase:hover { box-shadow: 0 8px 24px rgba(255,202,40,0.2); border-color: #FFCA28; }

  .sk-flask { background: rgba(255,255,255,0.06); border-color: rgba(255,255,255,0.12); color: #cbd5e1; }
  .sk-flask:hover { box-shadow: 0 8px 24px rgba(255,255,255,0.08); border-color: rgba(255,255,255,0.3); }

  .sk-git { background: rgba(240,80,50,0.1); border-color: rgba(240,80,50,0.25); color: #f08060; }
  .sk-git:hover { box-shadow: 0 8px 24px rgba(240,80,50,0.2); border-color: #F05032; }

  .sk-linux { background: rgba(252,198,36,0.1); border-color: rgba(252,198,36,0.25); color: #fcc624; }
  .sk-linux:hover { box-shadow: 0 8px 24px rgba(252,198,36,0.2); border-color: #FCC624; }

  .sk-cpp { background: rgba(0,89,179,0.15); border-color: rgba(0,89,179,0.35); color: #6ea8fe; }
  .sk-cpp:hover { box-shadow: 0 8px 24px rgba(0,89,179,0.3); border-color: #0059B3; }

  .sk-sklearn { background: rgba(247,147,30,0.1); border-color: rgba(247,147,30,0.25); color: #f7931e; }
  .sk-sklearn:hover { box-shadow: 0 8px 24px rgba(247,147,30,0.2); border-color: #F7931E; }

  /* === EXPERIENCE === */
  .timeline { position: relative; padding-left: 28px; }

  .timeline::before {
    content: '';
    position: absolute;
    left: 0;
    top: 8px;
    bottom: 0;
    width: 1px;
    background: linear-gradient(180deg, var(--cyan), var(--violet), transparent);
  }

  .timeline-item {
    position: relative;
    margin-bottom: 48px;
    opacity: 0;
    animation: fadeUp 0.5s ease forwards;
  }

  .timeline-item::before {
    content: '';
    position: absolute;
    left: -33px;
    top: 8px;
    width: 10px;
    height: 10px;
    border-radius: 50%;
    border: 2px solid var(--cyan);
    background: var(--bg);
    box-shadow: 0 0 12px var(--cyan);
  }

  .timeline-meta {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 8px;
    flex-wrap: wrap;
  }

  .timeline-company {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--text);
  }

  .timeline-badge {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    padding: 3px 10px;
    border-radius: 20px;
    letter-spacing: 1px;
  }

  .badge-founder { background: rgba(168,85,247,0.2); color: var(--violet); border: 1px solid rgba(168,85,247,0.4); }
  .badge-dev { background: rgba(0,245,255,0.1); color: var(--cyan); border: 1px solid rgba(0,245,255,0.3); }
  .badge-intern { background: rgba(0,255,148,0.1); color: var(--green); border: 1px solid rgba(0,255,148,0.3); }

  .timeline-role {
    font-size: 13px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    margin-bottom: 12px;
  }

  .timeline-desc {
    font-size: 14px;
    line-height: 1.8;
    color: #94a3b8;
  }

  .timeline-desc li {
    list-style: none;
    padding: 4px 0;
    padding-left: 16px;
    position: relative;
  }

  .timeline-desc li::before {
    content: '▸';
    position: absolute;
    left: 0;
    color: var(--cyan);
  }

  /* === ACHIEVEMENTS === */
  .achievements-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
  }

  .achievement-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    transition: all 0.3s ease;
    position: relative;
    overflow: hidden;
  }

  .achievement-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, var(--cyan), var(--violet));
    transform: scaleX(0);
    transition: transform 0.3s;
    transform-origin: left;
  }

  .achievement-card:hover::before { transform: scaleX(1); }

  .achievement-card:hover {
    border-color: rgba(0,245,255,0.3);
    transform: translateY(-4px);
    box-shadow: 0 16px 40px rgba(0,0,0,0.4);
  }

  .achievement-icon {
    font-size: 28px;
    margin-bottom: 12px;
    display: block;
  }

  .achievement-title {
    font-family: 'Syne', sans-serif;
    font-size: 15px;
    font-weight: 700;
    margin-bottom: 6px;
    color: var(--text);
  }

  .achievement-sub {
    font-size: 12px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
  }

  /* === GITHUB STATS === */
  .stats-grid {
    display: grid;
    gap: 20px;
  }

  .stats-img {
    width: 100%;
    border-radius: 12px;
    border: 1px solid var(--border);
    transition: all 0.3s;
  }

  .stats-img:hover {
    border-color: rgba(0,245,255,0.3);
    box-shadow: 0 8px 40px rgba(0,245,255,0.1);
    transform: translateY(-2px);
  }

  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }

  /* === WORKFLOW === */
  .workflow-steps {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    position: relative;
  }

  .workflow-steps::before {
    content: '';
    position: absolute;
    top: 32px;
    left: 15%;
    right: 15%;
    height: 1px;
    background: linear-gradient(90deg, var(--cyan), var(--violet), var(--pink));
    z-index: 0;
  }

  .workflow-step {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 0 8px;
    position: relative;
    z-index: 1;
  }

  .workflow-icon {
    width: 64px;
    height: 64px;
    border-radius: 50%;
    background: var(--bg2);
    border: 2px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    margin-bottom: 12px;
    transition: all 0.3s;
    position: relative;
  }

  .workflow-step:hover .workflow-icon {
    border-color: var(--cyan);
    box-shadow: 0 0 24px rgba(0,245,255,0.3);
    transform: scale(1.1);
  }

  .workflow-label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
  }

  .workflow-row2 {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    margin-top: 40px;
  }

  .stack-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    text-align: center;
    transition: all 0.3s;
  }

  .stack-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 16px 40px rgba(0,0,0,0.3);
  }

  .stack-card.mobile:hover { border-color: #3DDC84; box-shadow: 0 16px 40px rgba(61,220,132,0.15); }
  .stack-card.web:hover { border-color: #61DAFB; box-shadow: 0 16px 40px rgba(97,218,251,0.15); }
  .stack-card.ai:hover { border-color: #FF6F00; box-shadow: 0 16px 40px rgba(255,111,0,0.15); }

  .stack-emoji { font-size: 32px; margin-bottom: 12px; }
  .stack-name {
    font-family: 'Syne', sans-serif;
    font-weight: 700;
    font-size: 16px;
    margin-bottom: 8px;
  }

  .stack-tags {
    display: flex;
    gap: 6px;
    flex-wrap: wrap;
    justify-content: center;
  }

  .stack-tag {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    padding: 3px 8px;
    border-radius: 4px;
    background: rgba(255,255,255,0.06);
    color: var(--muted);
  }

  /* === CURRENTLY === */
  .current-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 16px;
  }

  .current-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    display: flex;
    align-items: flex-start;
    gap: 16px;
    transition: all 0.3s;
  }

  .current-card:hover {
    border-color: rgba(0,245,255,0.3);
    transform: translateX(4px);
  }

  .current-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    background: var(--green);
    box-shadow: 0 0 8px var(--green);
    margin-top: 4px;
    flex-shrink: 0;
    animation: pulse 2s ease infinite;
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50% { opacity: 0.6; transform: scale(0.8); }
  }

  .current-text {
    font-size: 14px;
    line-height: 1.6;
    color: #94a3b8;
  }

  .current-text strong { color: var(--text); }

  /* === CONNECT === */
  .connect-card {
    background: var(--bg2);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 48px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .connect-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse at 50% 0%, rgba(0,245,255,0.08), transparent 70%);
  }

  .connect-title {
    font-family: 'Syne', sans-serif;
    font-size: 42px;
    font-weight: 800;
    letter-spacing: -2px;
    margin-bottom: 16px;
    background: linear-gradient(135deg, var(--cyan), var(--violet));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .connect-sub {
    color: var(--muted);
    font-size: 15px;
    margin-bottom: 36px;
    line-height: 1.6;
  }

  .connect-links {
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
  }

  .connect-link {
    display: inline-flex;
    align-items: center;
    gap: 10px;
    padding: 14px 28px;
    border-radius: 8px;
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    text-decoration: none;
    letter-spacing: 1px;
    transition: all 0.3s;
    border: 1px solid;
  }

  .cl-portfolio {
    background: linear-gradient(135deg, var(--cyan), #0096a0);
    color: #000;
    border-color: transparent;
    font-weight: 700;
  }
  .cl-portfolio:hover { transform: translateY(-3px); box-shadow: 0 10px 30px rgba(0,245,255,0.4); }

  .cl-linkedin { border-color: rgba(0,119,181,0.5); color: #0a66c2; }
  .cl-linkedin:hover { border-color: #0a66c2; background: rgba(0,119,181,0.1); transform: translateY(-3px); }

  .cl-email { border-color: var(--border); color: var(--text); }
  .cl-email:hover { border-color: var(--cyan); color: var(--cyan); transform: translateY(-3px); }

  /* === FOOTER === */
  .footer {
    text-align: center;
    padding: 40px 0;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 2px;
    border-top: 1px solid var(--border);
  }

  .footer span { color: var(--pink); }

  /* === QUOTE === */
  .quote-block {
    border-left: 3px solid;
    border-image: linear-gradient(180deg, var(--cyan), var(--violet)) 1;
    padding: 20px 28px;
    margin: 40px 0;
    background: rgba(0,245,255,0.03);
    border-radius: 0 8px 8px 0;
  }

  .quote-text {
    font-size: 15px;
    font-style: italic;
    color: #94a3b8;
    line-height: 1.8;
  }

  /* === SCROLL REVEAL === */
  .reveal {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }
  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Stagger children */
  .reveal-stagger > * {
    opacity: 0;
    transform: translateY(20px);
    transition: opacity 0.4s ease, transform 0.4s ease;
  }
  .reveal-stagger.visible > *:nth-child(1) { opacity: 1; transform: translateY(0); transition-delay: 0s; }
  .reveal-stagger.visible > *:nth-child(2) { opacity: 1; transform: translateY(0); transition-delay: 0.08s; }
  .reveal-stagger.visible > *:nth-child(3) { opacity: 1; transform: translateY(0); transition-delay: 0.16s; }
  .reveal-stagger.visible > *:nth-child(4) { opacity: 1; transform: translateY(0); transition-delay: 0.24s; }
  .reveal-stagger.visible > *:nth-child(5) { opacity: 1; transform: translateY(0); transition-delay: 0.32s; }
  .reveal-stagger.visible > *:nth-child(6) { opacity: 1; transform: translateY(0); transition-delay: 0.40s; }
  .reveal-stagger.visible > *:nth-child(7) { opacity: 1; transform: translateY(0); transition-delay: 0.48s; }
  .reveal-stagger.visible > *:nth-child(8) { opacity: 1; transform: translateY(0); transition-delay: 0.56s; }
  .reveal-stagger.visible > *:nth-child(9) { opacity: 1; transform: translateY(0); transition-delay: 0.64s; }
  .reveal-stagger.visible > *:nth-child(10) { opacity: 1; transform: translateY(0); transition-delay: 0.72s; }
  .reveal-stagger.visible > *:nth-child(11) { opacity: 1; transform: translateY(0); transition-delay: 0.80s; }
  .reveal-stagger.visible > *:nth-child(12) { opacity: 1; transform: translateY(0); transition-delay: 0.88s; }

  /* === ACTIVITY GRAPH === */
  .activity-img {
    width: 100%;
    border-radius: 12px;
    border: 1px solid var(--border);
    transition: all 0.3s;
  }

  .activity-img:hover {
    border-color: rgba(0,245,255,0.3);
    box-shadow: 0 8px 40px rgba(0,245,255,0.1);
  }

  @media (max-width: 640px) {
    .about-grid { grid-template-columns: 1fr; }
    .stats-row { grid-template-columns: 1fr; }
    .workflow-steps { grid-template-columns: repeat(2, 1fr); gap: 20px; }
    .workflow-steps::before { display: none; }
    .workflow-row2 { grid-template-columns: 1fr; }
    .current-grid { grid-template-columns: 1fr; }
    .achievements-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="orb orb1"></div>
<div class="orb orb2"></div>
<div class="orb orb3"></div>

<div class="content">

  <!-- ═══════════════════ HERO ═══════════════════ -->
  <section class="hero">
    <div class="hero-tag">👋 Available for opportunities</div>

    <h1 class="hero-name">
      <span class="line1">Shoyeb</span>
      <span class="line2">Chaudhari</span>
    </h1>

    <p class="hero-role">
      <span>Python Dev</span> · AI/ML Explorer · Android + Web Builder<br>
      Founder @ KodeNeurons · Final Year B.Tech CSE · Aurangabad, India
    </p>

    <div class="hero-stats">
      <div class="stat">
        <span class="stat-num">3+</span>
        <span class="stat-label">YEARS CODING</span>
      </div>
      <div class="stat">
        <span class="stat-num">5+</span>
        <span class="stat-label">TECH STACKS</span>
      </div>
      <div class="stat">
        <span class="stat-num">3+</span>
        <span class="stat-label">HACKATHONS</span>
      </div>
      <div class="stat">
        <span class="stat-num">∞</span>
        <span class="stat-label">CURIOSITY</span>
      </div>
    </div>

    <div class="hero-links">
      <a href="https://shoyeb.kodeneurons.tech/" class="btn btn-primary">🌐 Portfolio</a>
      <a href="https://www.linkedin.com/in/shoyeb-chaudhari-033b44234" class="btn btn-outline">💼 LinkedIn</a>
      <a href="mailto:chaudharishoyeb@gmail.com" class="btn btn-outline">📬 Email Me</a>
      <a href="https://github.com/ShoyebChaudhari45" class="btn btn-outline">🐙 GitHub</a>
    </div>

    <div class="scroll-hint">
      <span class="scroll-line"></span>
      SCROLL TO EXPLORE
    </div>
  </section>


  <!-- ═══════════════════ ABOUT ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">01</span>
      <h2 class="section-title">About Me</h2>
      <div class="section-line"></div>
    </div>

    <div class="code-card">
      <div class="code-header">
        <div class="code-dot" style="background:#ff5f57"></div>
        <div class="code-dot" style="background:#febc2e"></div>
        <div class="code-dot" style="background:#28c840"></div>
        <span class="code-filename">shoyeb.py</span>
      </div>
      <div class="code-body">
        <div><span class="c-purple">class</span> <span class="c-cyan">ShoyebChaudhari</span>:</div>
        <div style="margin-left:20px;margin-top:8px">
          <div><span class="c-purple">def</span> <span class="c-green">__init__</span>(self):</div>
          <div style="margin-left:20px">
            <div>self.<span class="c-cyan">name</span>         = <span class="c-yellow">"Shoyeb Chaudhari"</span></div>
            <div>self.<span class="c-cyan">role</span>         = <span class="c-yellow">"Python Dev | AI/ML | Founder @ KodeNeurons"</span></div>
            <div>self.<span class="c-cyan">location</span>     = <span class="c-yellow">"Aurangabad, Maharashtra, India 🇮🇳"</span></div>
            <div>self.<span class="c-cyan">education</span>    = <span class="c-yellow">"B.Tech Computer Science Engineering"</span></div>
            <div>self.<span class="c-cyan">learning</span>     = [<span class="c-yellow">"AI/ML"</span>, <span class="c-yellow">"Cloud"</span>, <span class="c-yellow">"Advanced Android"</span>]</div>
            <div>self.<span class="c-cyan">fun_fact</span>     = <span class="c-yellow">"Curiosity + Coffee = Problem Solved ☕"</span></div>
          </div>
          <br>
          <div><span class="c-purple">def</span> <span class="c-green">say_hi</span>(self):</div>
          <div style="margin-left:20px"><span class="c-muted"># Let's build something incredible together 🚀</span></div>
          <div style="margin-left:20px"><span class="c-orange">print</span>(<span class="c-yellow">"Thanks for stopping by!"</span>)</div>
        </div>
        <br>
        <div>me = <span class="c-cyan">ShoyebChaudhari</span>()</div>
        <div>me.<span class="c-green">say_hi</span>()</div>
      </div>
    </div>

    <div class="about-grid reveal-stagger" style="margin-top:24px">
      <div class="about-pill"><span class="about-pill-icon">🚀</span> Founder of KodeNeurons — student-driven tech venture</div>
      <div class="about-pill"><span class="about-pill-icon">🤖</span> AI/ML explorer building intelligent applications</div>
      <div class="about-pill"><span class="about-pill-icon">📱</span> Android developer crafting seamless experiences</div>
      <div class="about-pill"><span class="about-pill-icon">🏆</span> Best Event In-Charge · INNOHACK 2025</div>
    </div>

    <div class="quote-block">
      <p class="quote-text">"The thrill of turning code into something useful, beautiful, and scalable — whether it's an app, a system, or an AI model — that's what drives me every single day."</p>
    </div>
  </section>


  <!-- ═══════════════════ TECH STACK ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">02</span>
      <h2 class="section-title">Tech Stack</h2>
      <div class="section-line"></div>
    </div>

    <div class="skills-grid reveal-stagger">
      <div class="skill-chip sk-python">🐍 Python</div>
      <div class="skill-chip sk-java">☕ Java</div>
      <div class="skill-chip sk-react">⚛️ React</div>
      <div class="skill-chip sk-tf">🧠 TensorFlow</div>
      <div class="skill-chip sk-android">🤖 Android</div>
      <div class="skill-chip sk-mongo">🍃 MongoDB</div>
      <div class="skill-chip sk-firebase">🔥 Firebase</div>
      <div class="skill-chip sk-flask">🌶️ Flask</div>
      <div class="skill-chip sk-git">🔀 Git</div>
      <div class="skill-chip sk-linux">🐧 Linux</div>
      <div class="skill-chip sk-cpp">⚡ C++</div>
      <div class="skill-chip sk-sklearn">📊 scikit-learn</div>
    </div>

    <div class="workflow-row2 reveal" style="margin-top:40px">
      <div class="stack-card mobile">
        <div class="stack-emoji">📱</div>
        <div class="stack-name" style="color:#3DDC84">Mobile</div>
        <div class="stack-tags">
          <span class="stack-tag">Android Studio</span>
          <span class="stack-tag">Java</span>
          <span class="stack-tag">Kotlin</span>
          <span class="stack-tag">Firebase</span>
          <span class="stack-tag">XML</span>
        </div>
      </div>
      <div class="stack-card web">
        <div class="stack-emoji">🌐</div>
        <div class="stack-name" style="color:#61DAFB">Web</div>
        <div class="stack-tags">
          <span class="stack-tag">React.js</span>
          <span class="stack-tag">Flask</span>
          <span class="stack-tag">HTML5</span>
          <span class="stack-tag">CSS3</span>
          <span class="stack-tag">REST API</span>
        </div>
      </div>
      <div class="stack-card ai">
        <div class="stack-emoji">🤖</div>
        <div class="stack-name" style="color:#FF6F00">AI / ML</div>
        <div class="stack-tags">
          <span class="stack-tag">TensorFlow</span>
          <span class="stack-tag">scikit-learn</span>
          <span class="stack-tag">Pandas</span>
          <span class="stack-tag">NumPy</span>
        </div>
      </div>
    </div>
  </section>


  <!-- ═══════════════════ WORKFLOW ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">03</span>
      <h2 class="section-title">Workflow</h2>
      <div class="section-line"></div>
    </div>

    <div class="workflow-steps reveal-stagger">
      <div class="workflow-step">
        <div class="workflow-icon">💡</div>
        <div class="workflow-label">IDEATE</div>
      </div>
      <div class="workflow-step">
        <div class="workflow-icon">📐</div>
        <div class="workflow-label">DESIGN</div>
      </div>
      <div class="workflow-step">
        <div class="workflow-icon">⚡</div>
        <div class="workflow-label">BUILD</div>
      </div>
      <div class="workflow-step">
        <div class="workflow-icon">🧪</div>
        <div class="workflow-label">TEST</div>
      </div>
      <div class="workflow-step">
        <div class="workflow-icon">🚀</div>
        <div class="workflow-label">DEPLOY</div>
      </div>
      <div class="workflow-step">
        <div class="workflow-icon">📊</div>
        <div class="workflow-label">MONITOR</div>
      </div>
      <div class="workflow-step">
        <div class="workflow-icon">🔄</div>
        <div class="workflow-label">ITERATE</div>
      </div>
    </div>
  </section>


  <!-- ═══════════════════ EXPERIENCE ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">04</span>
      <h2 class="section-title">Experience</h2>
      <div class="section-line"></div>
    </div>

    <div class="timeline">
      <div class="timeline-item" style="animation-delay:0.1s">
        <div class="timeline-meta">
          <span class="timeline-company">KodeNeurons</span>
          <span class="timeline-badge badge-founder">FOUNDER</span>
        </div>
        <div class="timeline-role">Software Developer · Jan 2025 – Present</div>
        <ul class="timeline-desc">
          <li>Founded a student-driven tech venture focused on Android & web innovation</li>
          <li>Built and deployed custom Android apps using Java, XML, Firebase & third-party APIs</li>
          <li>Led a team managing timelines, task distribution, and quality assurance</li>
          <li>Integrated AI/ML features using Python and TensorFlow Lite</li>
        </ul>
      </div>

      <div class="timeline-item" style="animation-delay:0.2s">
        <div class="timeline-meta">
          <span class="timeline-company">Mountreach Solution Pvt. Ltd.</span>
          <span class="timeline-badge badge-dev">DEVELOPER</span>
        </div>
        <div class="timeline-role">Software Developer · June 2025 – Present</div>
        <ul class="timeline-desc">
          <li>Developing scalable software solutions and managing full-stack projects</li>
          <li>Collaborating with cross-functional teams on production-grade applications</li>
        </ul>
      </div>

      <div class="timeline-item" style="animation-delay:0.3s">
        <div class="timeline-meta">
          <span class="timeline-company">Idyllic Services</span>
          <span class="timeline-badge badge-intern">INTERN</span>
        </div>
        <div class="timeline-role">Associate Developer Intern · Jan 2026 – Present</div>
        <ul class="timeline-desc">
          <li>Working on cutting-edge development projects</li>
          <li>Learning industry best practices in a professional environment</li>
        </ul>
      </div>
    </div>
  </section>


  <!-- ═══════════════════ ACHIEVEMENTS ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">05</span>
      <h2 class="section-title">Achievements</h2>
      <div class="section-line"></div>
    </div>

    <div class="achievements-grid reveal-stagger">
      <div class="achievement-card">
        <span class="achievement-icon">🥇</span>
        <div class="achievement-title">Best Event In-Charge</div>
        <div class="achievement-sub">INNOHACK 2025</div>
      </div>
      <div class="achievement-card">
        <span class="achievement-icon">🚀</span>
        <div class="achievement-title">Hackathon Submission</div>
        <div class="achievement-sub">Bhartiya Antariksh Hackathon 2025</div>
      </div>
      <div class="achievement-card">
        <span class="achievement-icon">🏆</span>
        <div class="achievement-title">Hackathon Winner</div>
        <div class="achievement-sub">AI & Security Day Hackathon</div>
      </div>
      <div class="achievement-card">
        <span class="achievement-icon">📜</span>
        <div class="achievement-title">Software Engineering Sim</div>
        <div class="achievement-sub">J.P. Morgan — Job Simulation</div>
      </div>
      <div class="achievement-card">
        <span class="achievement-icon">📊</span>
        <div class="achievement-title">Data Analytics & Visualization</div>
        <div class="achievement-sub">Accenture — Job Simulation</div>
      </div>
      <div class="achievement-card">
        <span class="achievement-icon">✅</span>
        <div class="achievement-title">Certificate of Participation</div>
        <div class="achievement-sub">AI and Security Day</div>
      </div>
    </div>
  </section>


  <!-- ═══════════════════ GITHUB STATS ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">06</span>
      <h2 class="section-title">GitHub Stats</h2>
      <div class="section-line"></div>
    </div>

    <div class="stats-grid">
      <div class="stats-row">
        <img class="stats-img"
          src="https://github-readme-stats-sigma-five.vercel.app/api?username=ShoyebChaudhari45&show_icons=true&theme=algolia&include_all_commits=true&count_private=true&hide_border=true&bg_color=0b1120&title_color=00f5ff&icon_color=a855f7&text_color=e2e8f0"
          alt="GitHub Stats" />
        <img class="stats-img"
          src="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=ShoyebChaudhari45&layout=compact&theme=algolia&hide_border=true&bg_color=0b1120&title_color=00f5ff&text_color=e2e8f0&langs_count=8"
          alt="Top Languages" />
      </div>
      <img class="stats-img"
        src="https://nirzak-streak-stats.vercel.app/?user=ShoyebChaudhari45&theme=algolia&hide_border=true&background=0b1120&ring=00f5ff&fire=a855f7&currStreakLabel=00f5ff&sideLabels=e2e8f0&dates=64748b"
        alt="GitHub Streak" />
      <img class="activity-img"
        src="https://github-readme-activity-graph.vercel.app/graph?username=ShoyebChaudhari45&bg_color=0b1120&color=00f5ff&line=a855f7&point=ffffff&area=true&hide_border=true"
        alt="Activity Graph" />
    </div>
  </section>


  <!-- ═══════════════════ CURRENTLY WORKING ON ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">07</span>
      <h2 class="section-title">Currently Building</h2>
      <div class="section-line"></div>
    </div>

    <div class="current-grid reveal-stagger">
      <div class="current-card">
        <div class="current-dot"></div>
        <div class="current-text"><strong>AI-powered mobile apps</strong> — blending TensorFlow Lite with Android for on-device intelligence</div>
      </div>
      <div class="current-card">
        <div class="current-dot"></div>
        <div class="current-text"><strong>Full-stack web solutions</strong> — modern React frontends with Flask backends</div>
      </div>
      <div class="current-card">
        <div class="current-dot"></div>
        <div class="current-text"><strong>Advanced ML algorithms</strong> — gradient boosting, neural networks, and ensemble methods</div>
      </div>
      <div class="current-card">
        <div class="current-dot"></div>
        <div class="current-text"><strong>Open-source contributions</strong> — giving back to the community that taught me everything</div>
      </div>
    </div>
  </section>


  <!-- ═══════════════════ CONNECT ═══════════════════ -->
  <section class="section reveal">
    <div class="section-header">
      <span class="section-num">08</span>
      <h2 class="section-title">Let's Connect</h2>
      <div class="section-line"></div>
    </div>

    <div class="connect-card">
      <h3 class="connect-title">Open to Opportunities</h3>
      <p class="connect-sub">
        Looking for internships or freelance work in Android, Web, or ML.<br>
        Open to collaborations on student & startup projects.<br>
        Seeking mentors who can help me level up.
      </p>
      <div class="connect-links">
        <a href="https://shoyeb.kodeneurons.tech/" class="connect-link cl-portfolio">🌐 Visit Portfolio</a>
        <a href="https://www.linkedin.com/in/shoyeb-chaudhari-033b44234" class="connect-link cl-linkedin">💼 LinkedIn</a>
        <a href="mailto:chaudharishoyeb@gmail.com" class="connect-link cl-email">📬 Email Me</a>
      </div>
    </div>
  </section>

  <footer class="footer">
    Built with <span>♥</span> by Shoyeb Chaudhari · &copy; 2025 KodeNeurons · Aurangabad, India
  </footer>

</div>

<script>
  // Intersection Observer for scroll reveals
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('visible');
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.reveal, .reveal-stagger').forEach(el => {
    observer.observe(el);
  });

  // Typewriter cursor blink on hero
  const heroRole = document.querySelector('.hero-role');
  if (heroRole) {
    heroRole.insertAdjacentHTML('beforeend', '<span style="color:var(--cyan);animation:blink 1s step-end infinite">|</span>');
  }

  const style = document.createElement('style');
  style.textContent = `@keyframes blink { 0%,100%{opacity:1}50%{opacity:0} }`;
  document.head.appendChild(style);

  // Parallax on orbs
  document.addEventListener('mousemove', (e) => {
    const x = (e.clientX / window.innerWidth - 0.5) * 30;
    const y = (e.clientY / window.innerHeight - 0.5) * 30;
    document.querySelector('.orb1').style.transform = `translate(${x * 0.5}px, ${y * 0.5}px)`;
    document.querySelector('.orb2').style.transform = `translate(${-x * 0.3}px, ${-y * 0.3}px)`;
    document.querySelector('.orb3').style.transform = `translate(${x * 0.4}px, ${y * 0.4}px)`;
  });
</script>
</body>
</html>
