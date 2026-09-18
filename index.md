---
layout: default
title: Sehaj Vohra
---

<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 32'%3E%3Crect width='32' height='32' rx='7' fill='%230d1117'/%3E%3Ctext x='5' y='22' font-family='monospace' font-weight='700' font-size='15' fill='%233fb950'%3E%3E_%3C/text%3E%3C/svg%3E">

<script>
  // Set the theme before first paint so there's no light/dark flash.
  (function () {
    try {
      var saved = localStorage.getItem('sv-theme');
      var prefersDark = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
      if (saved === 'dark' || (!saved && prefersDark)) {
        document.documentElement.setAttribute('data-theme', 'dark');
      }
    } catch (e) {}
  })();
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=IBM+Plex+Sans:wght@400;500;600;700&family=IBM+Plex+Mono:wght@400;500;600;700&display=swap');

  /* ---------- Design tokens ---------- */
  :root {
    --bg: #ffffff;
    --bg-soft: #f6f8fa;
    --surface: #ffffff;
    --border: #d0d7de;
    --ink: #1f2328;
    --ink-soft: #59636e;
    --ink-faint: #8c959f;
    --accent: #1a7f37;
    --accent-strong: #116329;
    --accent-soft: #dafbe1;
    --accent-2: #8250df;
    --shadow-sm: 0 1px 2px rgba(31, 35, 40, 0.08);
    --shadow-md: 0 10px 28px rgba(31, 35, 40, 0.10);
    --shadow-lg: 0 22px 55px rgba(31, 35, 40, 0.16);
    --radius-sm: 6px;
    --radius-md: 10px;
    --radius-lg: 14px;
    --font-sans: 'IBM Plex Sans', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    --font-mono: 'IBM Plex Mono', ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
    color-scheme: light;
  }

  [data-theme="dark"] {
    --bg: #0d1117;
    --bg-soft: #161b22;
    --surface: #10151c;
    --border: #30363d;
    --ink: #e6edf3;
    --ink-soft: #9198a1;
    --ink-faint: #6e7681;
    --accent: #3fb950;
    --accent-strong: #56d364;
    --accent-soft: rgba(63, 185, 80, 0.15);
    --accent-2: #a371f7;
    --shadow-sm: 0 1px 2px rgba(1, 4, 9, 0.4);
    --shadow-md: 0 10px 28px rgba(1, 4, 9, 0.45);
    --shadow-lg: 0 22px 55px rgba(1, 4, 9, 0.6);
    color-scheme: dark;
  }

  * { box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--ink);
    font-family: var(--font-sans);
    transition: background 0.35s ease, color 0.35s ease;
  }

  ::selection { background: var(--accent); color: #ffffff; }

  ::-webkit-scrollbar { width: 11px; }
  ::-webkit-scrollbar-track { background: var(--bg-soft); }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 10px; border: 3px solid var(--bg-soft); }
  ::-webkit-scrollbar-thumb:hover { background: var(--accent); }

  a { color: inherit; }

  :focus-visible {
    outline: 2px solid var(--accent);
    outline-offset: 3px;
    border-radius: 4px;
  }

  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
      transition-duration: 0.01ms !important;
    }
    html { scroll-behavior: auto; }
  }

  /* ---------- Scroll progress ---------- */
  .progress-bar {
    position: fixed;
    top: 0;
    left: 0;
    height: 3px;
    width: 0%;
    background: var(--accent);
    z-index: 1000;
  }

  /* ---------- Terminal-caret custom cursor ---------- */
  .caret-cursor {
    position: fixed;
    top: 0;
    left: 0;
    width: 2px;
    height: 22px;
    background: #ffffff;
    mix-blend-mode: difference;
    pointer-events: none;
    z-index: 999;
    border-radius: 1px;
    transform: translate(-50%, -50%);
    transition: width 0.18s ease, height 0.18s ease, opacity 0.18s ease;
    animation: caretBlink 1s steps(1) infinite;
  }
  .caret-cursor.is-hovering {
    width: 20px;
    height: 20px;
    border-radius: 5px;
    animation: none;
  }
  @keyframes caretBlink { 0%, 100% { opacity: 1; } 50% { opacity: 0.25; } }
  @media (hover: none), (pointer: coarse) { .caret-cursor { display: none; } }

  /* ---------- Layout shell ---------- */
  .portfolio {
    max-width: 880px;
    margin: 0 auto;
    padding: 0 24px;
  }

  /* ---------- Nav ---------- */
  .site-nav {
    position: sticky;
    top: 0;
    z-index: 900;
    width: 100%;
    border-bottom: 1px solid transparent;
    transition: background 0.3s ease, border-color 0.3s ease, backdrop-filter 0.3s ease;
  }
  .site-nav.is-scrolled {
    background: color-mix(in srgb, var(--bg) 82%, transparent);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    border-bottom-color: var(--border);
  }
  .nav-inner {
    max-width: 880px;
    margin: 0 auto;
    padding: 16px 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
  }
  .nav-logo {
    font-family: var(--font-mono);
    font-weight: 600;
    font-size: 15px;
    text-decoration: none;
    color: var(--ink);
    display: inline-flex;
    align-items: center;
    gap: 2px;
  }
  .nav-logo span { color: var(--accent); }
  .nav-links {
    display: flex;
    gap: 26px;
    font-size: 14px;
    font-weight: 500;
  }
  .nav-link {
    position: relative;
    text-decoration: none;
    color: var(--ink-soft);
    padding: 4px 0;
    transition: color 0.2s ease;
  }
  .nav-link::after {
    content: "";
    position: absolute;
    left: 0;
    bottom: -3px;
    width: 0;
    height: 2px;
    background: var(--accent);
    transition: width 0.25s ease;
  }
  .nav-link:hover, .nav-link.is-active { color: var(--ink); }
  .nav-link:hover::after, .nav-link.is-active::after { width: 100%; }
  .nav-right { display: flex; align-items: center; gap: 10px; }
  .theme-toggle {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--ink-soft);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: border-color 0.2s ease, color 0.2s ease, transform 0.3s ease;
  }
  .theme-toggle:hover { border-color: var(--accent); color: var(--accent); transform: rotate(14deg); }
  .theme-toggle .icon-moon { display: none; }
  [data-theme="dark"] .theme-toggle .icon-sun { display: none; }
  [data-theme="dark"] .theme-toggle .icon-moon { display: block; }

  @media (max-width: 620px) {
    .nav-links { display: none; }
  }

  /* ---------- Hero ---------- */
  .hero {
    position: relative;
    padding: 64px 24px 88px;
    overflow: hidden;
  }
  .hero-field {
    position: absolute;
    inset: 0;
    z-index: 0;
    pointer-events: none;
    background-image: radial-gradient(var(--border) 1px, transparent 1px);
    background-size: 26px 26px;
    -webkit-mask-image: radial-gradient(ellipse 65% 55% at 50% 30%, black 30%, transparent 75%);
    mask-image: radial-gradient(ellipse 65% 55% at 50% 30%, black 30%, transparent 75%);
    opacity: 0.55;
  }
  .hero-glow {
    position: absolute;
    z-index: 0;
    border-radius: 50%;
    filter: blur(90px);
    pointer-events: none;
    opacity: 0.28;
  }
  .hero-glow-a { width: 320px; height: 320px; top: -80px; left: 8%; background: var(--accent); }
  .hero-glow-b { width: 260px; height: 260px; bottom: -60px; right: 10%; background: var(--accent-2); }

  .terminal-window {
    position: relative;
    z-index: 1;
    max-width: 700px;
    margin: 0 auto;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-lg);
    overflow: hidden;
    animation: riseIn 0.7s ease both;
  }
  @keyframes riseIn { from { opacity: 0; transform: translateY(18px); } to { opacity: 1; transform: translateY(0); } }

  .terminal-bar {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 12px 16px;
    background: var(--bg-soft);
    border-bottom: 1px solid var(--border);
  }
  .terminal-dot { width: 11px; height: 11px; border-radius: 50%; }
  .terminal-dot.red { background: #ff5f57; }
  .terminal-dot.yellow { background: #febc2e; }
  .terminal-dot.green { background: #28c840; }
  .terminal-title {
    margin: 0 auto;
    font-family: var(--font-mono);
    font-size: 12.5px;
    color: var(--ink-faint);
  }

  .terminal-body {
    padding: 32px clamp(20px, 4vw, 44px) 36px;
    font-family: var(--font-mono);
  }
  .term-line {
    margin: 0 0 6px;
    font-size: 14px;
    color: var(--ink-faint);
  }
  .term-comment-line {
    margin: 0 0 18px;
    font-size: 13px;
    color: var(--ink-faint);
  }
  .prompt { color: var(--accent); margin-right: 8px; }
  .term-name {
    margin: 2px 0 22px;
    font-family: var(--font-sans);
    font-weight: 700;
    font-size: clamp(2.1rem, 5vw + 1rem, 3.1rem);
    letter-spacing: -0.02em;
    color: var(--ink);
  }
  .term-output {
    margin: 0 0 22px;
    font-size: 16px;
    color: var(--ink-soft);
    min-height: 24px;
  }
  .term-cursor {
    display: inline-block;
    width: 9px;
    height: 17px;
    margin-left: 3px;
    background: var(--accent);
    vertical-align: -3px;
    animation: caretBlink 1s steps(1) infinite;
  }
  .term-welcome {
    margin: 0 0 30px;
    font-family: var(--font-sans);
    font-size: 15.5px;
    line-height: 1.75;
    color: var(--ink-soft);
    max-width: 54ch;
  }
  .term-welcome::before { content: "// "; color: var(--ink-faint); }

  .term-actions {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
  }

  /* ---------- Buttons ---------- */
  .button {
    position: relative;
    display: inline-flex;
    align-items: center;
    gap: 9px;
    padding: 11px 18px;
    border-radius: var(--radius-sm);
    font-family: var(--font-sans);
    font-weight: 600;
    font-size: 14px;
    text-decoration: none;
    border: 1px solid transparent;
    transition: transform 0.2s ease, box-shadow 0.2s ease, border-color 0.2s ease, color 0.2s ease, background 0.2s ease;
  }
  .button svg { width: 16px; height: 16px; flex-shrink: 0; }
  .button-primary {
    background: var(--accent);
    color: #ffffff !important;
  }
  .button-primary:hover { background: var(--accent-strong); box-shadow: var(--shadow-md); transform: translateY(-2px); }
  .button-secondary {
    background: var(--surface);
    color: var(--ink) !important;
    border-color: var(--border);
  }
  .button-secondary:hover { border-color: var(--accent); color: var(--accent) !important; transform: translateY(-2px); box-shadow: var(--shadow-sm); }
  .button-linkedin:hover { border-color: #0a66c2; color: #0a66c2 !important; }

  /* ---------- Reveal on scroll ---------- */
  [data-reveal] {
    opacity: 0;
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  [data-reveal="up"] { transform: translateY(26px); }
  [data-reveal="left"] { transform: translateX(-26px); }
  [data-reveal="scale"] { transform: scale(0.96); }
  [data-reveal].is-visible { opacity: 1; transform: none; }

  /* ---------- Sections ---------- */
  .section { margin-bottom: 76px; }
  .section-heading { margin-bottom: 26px; }
  .section-heading h2 {
    margin: 0 0 6px;
    font-size: 26px;
    font-weight: 700;
    letter-spacing: -0.01em;
  }
  .section-heading p { margin: 0; color: var(--ink-soft); font-size: 15.5px; }
  .section-path {
    display: inline-block;
    margin-bottom: 10px;
    font-family: var(--font-mono);
    font-size: 12.5px;
    color: var(--ink-faint);
  }

  /* ---------- About ---------- */
  .about-block {
    border-left: 3px solid var(--accent);
    padding: 4px 0 4px 22px;
  }
  .about-block p {
    margin: 0;
    color: var(--ink-soft);
    font-size: 16px;
    line-height: 1.85;
    max-width: 68ch;
  }

  /* ---------- Skills ---------- */
  .skill-group { margin-bottom: 22px; }
  .skill-group:last-child { margin-bottom: 0; }
  .skill-group-label {
    font-family: var(--font-mono);
    font-size: 13px;
    color: var(--ink-faint);
    margin-bottom: 12px;
  }
  .skill-group-label::before { content: "# "; }
  .skill-chip-list { display: flex; flex-wrap: wrap; gap: 9px; }
  .skill-chip {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    padding: 7px 13px;
    border-radius: 999px;
    border: 1px solid var(--border);
    background: var(--surface);
    font-family: var(--font-mono);
    font-size: 13px;
    color: var(--ink-soft);
    transition: border-color 0.2s ease, transform 0.2s ease, color 0.2s ease, box-shadow 0.2s ease;
  }
  .skill-chip:hover {
    border-color: var(--lang-color, var(--accent));
    color: var(--ink);
    transform: translateY(-2px);
    box-shadow: var(--shadow-sm);
  }
  .lang-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--lang-color, var(--accent));
    flex-shrink: 0;
  }

  /* ---------- Work / project ---------- */
  .project-card {
    position: relative;
    padding: 30px clamp(20px, 4vw, 36px);
    border: 1px solid var(--border);
    border-left: 3px solid transparent;
    border-radius: var(--radius-md);
    background: var(--surface);
    transition: border-color 0.25s ease, background 0.25s ease, transform 0.25s ease, box-shadow 0.25s ease;
  }
  .project-card:hover {
    border-left-color: var(--accent);
    background: color-mix(in srgb, var(--accent-soft) 55%, var(--surface));
    transform: translateY(-3px);
    box-shadow: var(--shadow-md);
  }
  .project-head {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 14px;
  }
  .project-head svg { width: 19px; height: 19px; color: var(--ink-faint); flex-shrink: 0; }
  .project-card h3 {
    margin: 0;
    font-family: var(--font-mono);
    font-weight: 600;
    font-size: 20px;
    color: var(--ink);
  }
  .project-card p {
    max-width: 64ch;
    margin: 0 0 20px;
    color: var(--ink-soft);
    font-size: 15.5px;
    line-height: 1.75;
  }
  .project-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 24px; }
  .project-tag {
    padding: 5px 11px;
    border-radius: var(--radius-sm);
    background: var(--bg-soft);
    border: 1px solid var(--border);
    color: var(--ink-soft);
    font-family: var(--font-mono);
    font-size: 12.5px;
  }

  /* ---------- Connect ---------- */
  .connect-block {
    text-align: center;
    padding-top: 44px;
    border-top: 1px solid var(--border);
  }
  .connect-block h2 { margin: 0 0 10px; font-size: 26px; font-weight: 700; }
  .connect-block p {
    margin: 0 auto 24px;
    max-width: 52ch;
    color: var(--ink-soft);
    font-size: 15.5px;
    line-height: 1.75;
  }
  .connect-actions {
    display: flex;
    justify-content: center;
    gap: 12px;
    flex-wrap: wrap;
  }

  /* ---------- Footer ---------- */
  .footer {
    padding: 34px 20px 46px;
    text-align: center;
  }
  .footer-socials {
    display: flex;
    justify-content: center;
    gap: 14px;
    margin-bottom: 14px;
  }
  .footer-socials a {
    width: 36px;
    height: 36px;
    border-radius: 50%;
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--ink-soft);
    text-decoration: none;
    transition: border-color 0.2s ease, color 0.2s ease, transform 0.2s ease;
  }
  .footer-socials a svg { width: 16px; height: 16px; }
  .footer-socials a:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }
  .footer p {
    margin: 0;
    font-family: var(--font-mono);
    color: var(--ink-faint);
    font-size: 12.5px;
  }

  /* ---------- Back to top ---------- */
  .back-to-top {
    position: fixed;
    right: 22px;
    bottom: 22px;
    width: 44px;
    height: 44px;
    border-radius: 50%;
    border: 1px solid var(--border);
    background: var(--surface);
    color: var(--ink-soft);
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    box-shadow: var(--shadow-md);
    opacity: 0;
    visibility: hidden;
    transform: translateY(10px);
    transition: opacity 0.3s ease, transform 0.3s ease, visibility 0.3s ease, border-color 0.2s ease, color 0.2s ease;
    z-index: 800;
  }
  .back-to-top.is-visible { opacity: 1; visibility: visible; transform: translateY(0); }
  .back-to-top:hover { border-color: var(--accent); color: var(--accent); }
  .back-to-top svg { width: 18px; height: 18px; }

  section[id] { scroll-margin-top: 84px; }

  @media (max-width: 620px) {
    .hero { padding: 40px 16px 60px; }
    .terminal-body { padding: 26px 18px 30px; }
    .section { margin-bottom: 56px; }
    .project-card { padding: 24px 20px; }
  }
</style>

<noscript>
  <style>[data-reveal] { opacity: 1 !important; transform: none !important; }</style>
</noscript>

<!-- Reusable icon sprite -->
<svg width="0" height="0" style="position:absolute" aria-hidden="true">
  <symbol id="i-github" viewBox="0 0 24 24"><path fill="currentColor" d="M12 .5C5.73.5.5 5.74.5 12.02c0 5.02 3.25 9.28 7.77 10.79.57.1.78-.25.78-.55 0-.27-.01-1.16-.02-2.1-3.16.69-3.83-1.34-3.83-1.34-.52-1.32-1.26-1.67-1.26-1.67-1.03-.7.08-.69.08-.69 1.14.08 1.74 1.17 1.74 1.17 1.01 1.74 2.65 1.24 3.3.95.1-.74.4-1.24.72-1.53-2.52-.29-5.17-1.26-5.17-5.6 0-1.24.44-2.25 1.17-3.04-.12-.29-.51-1.45.11-3.02 0 0 .96-.31 3.14 1.16a10.9 10.9 0 0 1 5.72 0c2.18-1.47 3.14-1.16 3.14-1.16.62 1.57.23 2.73.11 3.02.73.79 1.17 1.8 1.17 3.04 0 4.35-2.65 5.31-5.18 5.59.41.35.77 1.04.77 2.1 0 1.52-.01 2.74-.01 3.11 0 .3.2.66.79.55C20.26 21.29 23.5 17.04 23.5 12.02 23.5 5.74 18.27.5 12 .5z"/></symbol>
  <symbol id="i-linkedin" viewBox="0 0 24 24"><path fill="currentColor" d="M20.45 20.45h-3.56v-5.57c0-1.33-.02-3.04-1.85-3.04-1.86 0-2.15 1.45-2.15 2.94v5.67H9.34V9h3.41v1.56h.05c.48-.9 1.63-1.85 3.36-1.85 3.6 0 4.27 2.37 4.27 5.45v6.29zM5.34 7.43a2.07 2.07 0 1 1 0-4.13 2.07 2.07 0 0 1 0 4.13zM7.11 20.45H3.56V9h3.55v11.45z"/></symbol>
  <symbol id="i-sun" viewBox="0 0 24 24"><path fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" d="M12 4.5V2m0 20v-2.5M4.5 12H2m20 0h-2.5M6.3 6.3 4.6 4.6m14.8 14.8-1.7-1.7M6.3 17.7l-1.7 1.7M19.4 4.6l-1.7 1.7"/><circle cx="12" cy="12" r="4.3" fill="none" stroke="currentColor" stroke-width="1.7"/></symbol>
  <symbol id="i-moon" viewBox="0 0 24 24"><path fill="currentColor" d="M20 14.5A8.5 8.5 0 1 1 9.5 4a7 7 0 1 0 10.5 10.5z"/></symbol>
  <symbol id="i-arrow-up" viewBox="0 0 24 24"><path fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" d="M12 19V5M5 12l7-7 7 7"/></symbol>
  <symbol id="i-folder" viewBox="0 0 24 24"><path fill="none" stroke="currentColor" stroke-width="1.7" stroke-linecap="round" stroke-linejoin="round" d="M3 7a2 2 0 0 1 2-2h4l2 2h8a2 2 0 0 1 2 2v8a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V7z"/></symbol>
</svg>

<div class="progress-bar" id="progressBar"></div>
<div class="caret-cursor" id="caretCursor"></div>

<nav class="site-nav" id="siteNav">
  <div class="nav-inner">
    <a class="nav-logo" href="#hero">~/<span>sehaj</span></a>
    <div class="nav-links">
      <a href="#about" class="nav-link">About</a>
      <a href="#skills" class="nav-link">Skills</a>
      <a href="#work" class="nav-link">Work</a>
      <a href="#connect" class="nav-link">Connect</a>
    </div>
    <div class="nav-right">
      <button class="theme-toggle" id="themeToggle" type="button" aria-label="Toggle dark mode">
        <svg class="icon-sun" width="17" height="17"><use href="#i-sun"></use></svg>
        <svg class="icon-moon" width="17" height="17"><use href="#i-moon"></use></svg>
      </button>
    </div>
  </div>
</nav>

<section class="hero" id="hero">
  <div class="hero-field" aria-hidden="true"></div>
  <div class="hero-glow hero-glow-a" aria-hidden="true"></div>
  <div class="hero-glow hero-glow-b" aria-hidden="true"></div>

  <div class="terminal-window">
    <div class="terminal-bar">
      <span class="terminal-dot red"></span>
      <span class="terminal-dot yellow"></span>
      <span class="terminal-dot green"></span>
      <span class="terminal-title">sehaj@portfolio — zsh</span>
    </div>
    <div class="terminal-body">
      <p class="term-comment-line"># B.Tech Computer Science &amp; Engineering</p>
      <p class="term-line"><span class="prompt">$</span>whoami</p>
      <h1 class="term-name">Sehaj Vohra</h1>
      <p class="term-line"><span class="prompt">$</span>cat role.txt</p>
      <p class="term-output"><span id="typed">Computer Science &amp; Engineering</span><span class="term-cursor"></span></p>
      <p class="term-welcome">Welcome to my personal space on GitHub, where I showcase my academic work, practical learning, projects, and technical experiments.</p>
      <div class="term-actions">
        <a class="button button-primary magnetic" href="https://github.com/sehajvohra">
          <svg><use href="#i-github"></use></svg>
          GitHub Profile
        </a>
        <a class="button button-secondary magnetic" href="#work">View Work</a>
      </div>
    </div>
  </div>
</section>

<div class="portfolio">

  <section class="section" id="about">
    <div class="section-heading" data-reveal="up">
      <span class="section-path">~/about</span>
      <h2>About Me</h2>
      <p>A little about my journey and what I am working on.</p>
    </div>
    <div class="about-block" data-reveal="left">
      <p>
        I am a Computer Science &amp; Engineering student interested in building
        practical software and understanding how systems work. I enjoy
        exploring programming, web development, backend technologies, and
        creating projects that turn concepts learned in class into working
        implementations. This website serves as a simple collection of my
        academic work, projects, and continued learning.
      </p>
    </div>
  </section>

  <section class="section" id="skills">
    <div class="section-heading" data-reveal="up">
      <span class="section-path">~/skills</span>
      <h2>Skills &amp; Technologies</h2>
      <p>Technologies I am currently learning and working with.</p>
    </div>

    <div class="skill-group" data-reveal="up">
      <div class="skill-group-label">Languages</div>
      <div class="skill-chip-list">
        <span class="skill-chip" style="--lang-color:#b07219"><span class="lang-dot"></span>Java</span>
        <span class="skill-chip" style="--lang-color:#f1e05a"><span class="lang-dot"></span>JavaScript</span>
        <span class="skill-chip" style="--lang-color:#e34c26"><span class="lang-dot"></span>HTML</span>
        <span class="skill-chip" style="--lang-color:#563d7c"><span class="lang-dot"></span>CSS</span>
      </div>
    </div>

    <div class="skill-group" data-reveal="up">
      <div class="skill-group-label">Backend &amp; Database</div>
      <div class="skill-chip-list">
        <span class="skill-chip" style="--lang-color:#3c873a"><span class="lang-dot"></span>Node.js</span>
        <span class="skill-chip" style="--lang-color:#3c873a"><span class="lang-dot"></span>Express.js</span>
        <span class="skill-chip" style="--lang-color:#4db33d"><span class="lang-dot"></span>MongoDB</span>
      </div>
    </div>

    <div class="skill-group" data-reveal="up">
      <div class="skill-group-label">Tools &amp; Workflow</div>
      <div class="skill-chip-list">
        <span class="skill-chip" style="--lang-color:#f34f29"><span class="lang-dot"></span>Git</span>
        <span class="skill-chip" style="--lang-color:#181717"><span class="lang-dot"></span>GitHub</span>
      </div>
    </div>
  </section>

  <section class="section" id="work">
    <div class="section-heading" data-reveal="up">
      <span class="section-path">~/work</span>
      <h2>Featured Work</h2>
      <p>Academic and practical work currently featured on this website.</p>
    </div>

    <div class="project-card" data-reveal="scale">
      <div class="project-head">
        <svg><use href="#i-folder"></use></svg>
        <h3>Backend Development</h3>
      </div>
      <p>
        A collection of practical experiments and implementations completed
        as part of my Backend Development course, covering backend concepts,
        server side programming, APIs, and modern web technologies.
      </p>
      <div class="project-tags">
        <span class="project-tag">Node.js</span>
        <span class="project-tag">Express.js</span>
        <span class="project-tag">JavaScript</span>
        <span class="project-tag">REST APIs</span>
        <span class="project-tag">GitHub</span>
      </div>
      <a class="button button-primary magnetic" href="/BackendDevelopment/">Open Backend Development →</a>
    </div>
  </section>

  <section class="section" id="connect">
    <div class="connect-block" data-reveal="up">
      <h2>Let's Connect</h2>
      <p>
        You can explore my GitHub profile to see my repositories, projects,
        and ongoing technical work, or connect with me on LinkedIn.
      </p>
      <div class="connect-actions">
        <a class="button button-primary magnetic" href="https://github.com/sehajvohra">
          <svg><use href="#i-github"></use></svg>
          Visit GitHub
        </a>
        <a class="button button-secondary button-linkedin magnetic" href="https://www.linkedin.com/in/sehajvohra/">
          <svg><use href="#i-linkedin"></use></svg>
          Connect on LinkedIn
        </a>
      </div>
    </div>
  </section>

</div>

<footer class="footer">
  <div class="footer-socials">
    <a href="https://github.com/sehajvohra" aria-label="GitHub"><svg><use href="#i-github"></use></svg></a>
    <a href="https://www.linkedin.com/in/sehajvohra/" aria-label="LinkedIn"><svg><use href="#i-linkedin"></use></svg></a>
  </div>
  <p>Sehaj Vohra · Computer Science &amp; Engineering</p>
</footer>

<button class="back-to-top" id="backToTop" type="button" aria-label="Back to top">
  <svg><use href="#i-arrow-up"></use></svg>
</button>

<script>
document.addEventListener('DOMContentLoaded', function () {

  /* ---- Theme toggle ---- */
  var root = document.documentElement;
  var themeToggle = document.getElementById('themeToggle');
  if (themeToggle) {
    themeToggle.addEventListener('click', function () {
      var isDark = root.getAttribute('data-theme') === 'dark';
      if (isDark) {
        root.removeAttribute('data-theme');
        try { localStorage.setItem('sv-theme', 'light'); } catch (e) {}
      } else {
        root.setAttribute('data-theme', 'dark');
        try { localStorage.setItem('sv-theme', 'dark'); } catch (e) {}
      }
    });
  }

  /* ---- Scroll: progress bar, nav state, back-to-top, scrollspy ---- */
  var progressBar = document.getElementById('progressBar');
  var nav = document.getElementById('siteNav');
  var backToTop = document.getElementById('backToTop');
  var sections = document.querySelectorAll('section[id]');
  var navLinks = document.querySelectorAll('.nav-link');

  function onScroll() {
    var scrollTop = window.scrollY;
    var docHeight = document.documentElement.scrollHeight - window.innerHeight;
    var progress = docHeight > 0 ? (scrollTop / docHeight) * 100 : 0;
    if (progressBar) progressBar.style.width = progress + '%';
    if (nav) nav.classList.toggle('is-scrolled', scrollTop > 24);
    if (backToTop) backToTop.classList.toggle('is-visible', scrollTop > window.innerHeight * 0.6);

    var currentId = '';
    sections.forEach(function (sec) {
      var rect = sec.getBoundingClientRect();
      if (rect.top <= 130 && rect.bottom >= 130) currentId = sec.id;
    });
    navLinks.forEach(function (link) {
      link.classList.toggle('is-active', link.getAttribute('href') === '#' + currentId);
    });
  }
  window.addEventListener('scroll', onScroll, { passive: true });
  onScroll();

  if (backToTop) {
    backToTop.addEventListener('click', function () {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    });
  }

  /* ---- Reveal on scroll ---- */
  var revealEls = document.querySelectorAll('[data-reveal]');
  if ('IntersectionObserver' in window) {
    var io = new IntersectionObserver(function (entries) {
      entries.forEach(function (entry) {
        if (entry.isIntersecting) {
          entry.target.classList.add('is-visible');
          io.unobserve(entry.target);
        }
      });
    }, { threshold: 0.15 });
    revealEls.forEach(function (el) { io.observe(el); });
  } else {
    revealEls.forEach(function (el) { el.classList.add('is-visible'); });
  }

  /* ---- Typed terminal output ---- */
  var typedEl = document.getElementById('typed');
  if (typedEl) {
    var phrases = [
      'Computer Science & Engineering',
      'Backend development enthusiast',
      'Building with Node.js & Express'
    ];
    var phraseIndex = 0, charIndex = 0, deleting = false;
    typedEl.textContent = '';

    function typeLoop() {
      var current = phrases[phraseIndex];
      if (!deleting) {
        charIndex++;
        typedEl.textContent = current.slice(0, charIndex);
        if (charIndex === current.length) {
          deleting = true;
          setTimeout(typeLoop, 1700);
          return;
        }
      } else {
        charIndex--;
        typedEl.textContent = current.slice(0, charIndex);
        if (charIndex === 0) {
          deleting = false;
          phraseIndex = (phraseIndex + 1) % phrases.length;
        }
      }
      setTimeout(typeLoop, deleting ? 30 : 55);
    }
    setTimeout(typeLoop, 600);
  }

  /* ---- Magnetic buttons ---- */
  document.querySelectorAll('.magnetic').forEach(function (el) {
    el.addEventListener('mousemove', function (e) {
      var rect = el.getBoundingClientRect();
      var x = e.clientX - rect.left - rect.width / 2;
      var y = e.clientY - rect.top - rect.height / 2;
      el.style.transform = 'translate(' + x * 0.2 + 'px,' + y * 0.3 + 'px)';
    });
    el.addEventListener('mouseleave', function () { el.style.transform = ''; });
  });

  /* ---- Custom terminal-caret cursor ---- */
  var caret = document.getElementById('caretCursor');
  var fineHover = window.matchMedia('(hover: hover) and (pointer: fine)').matches;
  var reducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  if (caret && fineHover && !reducedMotion) {
    window.addEventListener('mousemove', function (e) {
      caret.style.left = e.clientX + 'px';
      caret.style.top = e.clientY + 'px';
    });
    document.querySelectorAll('a, button, .skill-chip').forEach(function (el) {
      el.addEventListener('mouseenter', function () { caret.classList.add('is-hovering'); });
      el.addEventListener('mouseleave', function () { caret.classList.remove('is-hovering'); });
    });
  } else if (caret) {
    caret.style.display = 'none';
  }

});
</script>
