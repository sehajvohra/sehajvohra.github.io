---
layout: default
title: Backend Development
---

<style>
  .hero {
    text-align: center;
    padding: 60px 20px 45px;
  }

  .hero h1 {
    font-size: 46px;
    margin-bottom: 12px;
    letter-spacing: -1px;
  }

  .hero p {
    max-width: 650px;
    margin: 0 auto;
    font-size: 18px;
    line-height: 1.7;
    opacity: 0.75;
  }

  .badge {
    display: inline-block;
    margin-bottom: 20px;
    padding: 7px 14px;
    border-radius: 999px;
    background: #f1f5f9;
    color: #475569;
    font-size: 13px;
    font-weight: 600;
    letter-spacing: 0.5px;
  }

  .section {
    max-width: 900px;
    margin: 0 auto 55px;
    padding: 0 20px;
  }

  .section-title {
    text-align: center;
    margin-bottom: 28px;
  }

  .section-title h2 {
    font-size: 28px;
    margin-bottom: 8px;
  }

  .section-title p {
    opacity: 0.65;
  }

  .experiments {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
  }

  .card {
    padding: 28px;
    border: 1px solid #e5e7eb;
    border-radius: 18px;
    background: #ffffff;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
  }

  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 30px rgba(0, 0, 0, 0.08);
  }

  .card-number {
    font-size: 13px;
    font-weight: 700;
    color: #64748b;
    text-transform: uppercase;
    letter-spacing: 1px;
  }

  .card h3 {
    margin: 10px 0;
    font-size: 22px;
  }

  .card p {
    line-height: 1.6;
    opacity: 0.7;
  }

  .button {
    display: inline-block;
    margin-top: 12px;
    padding: 10px 17px;
    border-radius: 10px;
    background: #111827;
    color: white !important;
    text-decoration: none;
    font-size: 14px;
    font-weight: 600;
    transition: opacity 0.2s ease;
  }

  .button:hover {
    opacity: 0.8;
  }

  .technologies {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
  }

  .tech {
    padding: 9px 15px;
    border: 1px solid #e5e7eb;
    border-radius: 999px;
    background: #f8fafc;
    font-size: 14px;
    font-weight: 500;
  }

  .footer {
    text-align: center;
    padding: 35px 20px;
    border-top: 1px solid #e5e7eb;
    opacity: 0.65;
    font-size: 14px;
  }
</style>

<div class="hero">

  <div class="badge">B.Tech CSE • Practical Work</div>

  <h1>Backend Development</h1>

  <p>
    A collection of practical experiments, implementations, and
    learning outcomes completed as part of the Backend Development course.
  </p>

</div>

<div class="section">

  <div class="section-title">
    <h2>Experiments</h2>
    <p>Explore the practical work completed throughout the course.</p>
  </div>

  <div class="experiments">

    <div class="card">

      <div class="card-number">Experiment 01</div>

      <h3>Backend Development Fundamentals</h3>

      <p>
        Practical work covering backend development concepts,
        server side programming, and web technologies.
      </p>

      <a
        class="button"
        href="/BackendDevelopment/Lab/Exp%201/index.html"
      >
        View Experiment 1 →
      </a>

    </div>

    <div class="card">

      <div class="card-number">Experiment 12</div>

      <h3>Node.js & Express Lab</h3>

      <p>
        Practical implementation using Node.js and Express.js,
        including backend server and API development.
      </p>

      <a
        class="button"
        href="/BackendDevelopment/Lab/Exp%2012/nodejs-express-lab/"
      >
        View Experiment 12 →
      </a>

    </div>

  </div>

</div>

<div class="section">

  <div class="section-title">
    <h2>Technologies</h2>
    <p>Tools and technologies used during the practical work.</p>
  </div>

  <div class="technologies">

    <span class="tech">Node.js</span>
    <span class="tech">Express.js</span>
    <span class="tech">JavaScript</span>
    <span class="tech">HTML</span>
    <span class="tech">CSS</span>
    <span class="tech">Git</span>
    <span class="tech">GitHub</span>
    <span class="tech">MongoDB</span>

  </div>

</div>

<div class="footer">

  Backend Development Practical Work

</div>