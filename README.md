<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Scoreva Tuition Classes</title>
  <link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&family=Baloo+2:wght@700;800&display=swap" rel="stylesheet"/>
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --yellow:   #FFD93D;
      --orange:   #FF6B35;
      --blue:     #1A73E8;
      --teal:     #00C6AE;
      --purple:   #7B5EA7;
      --dark:     #1A1A2E;
      --light:    #FFFDF4;
      --white:    #FFFFFF;
      --shadow:   0 8px 32px rgba(26,26,46,.12);
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: 'Nunito', sans-serif;
      background: var(--light);
      color: var(--dark);
      overflow-x: hidden;
    }

    /* ─── NAVBAR ─── */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 999;
      display: flex; align-items: center; justify-content: space-between;
      padding: 0 5vw;
      height: 70px;
      background: var(--white);
      box-shadow: 0 2px 20px rgba(0,0,0,.08);
    }

    .nav-logo {
      font-family: 'Baloo 2', cursive;
      font-size: 1.7rem;
      font-weight: 800;
      color: var(--dark);
      text-decoration: none;
    }
    .nav-logo span { color: var(--orange); }

    .nav-links { display: flex; gap: 2rem; list-style: none; }
    .nav-links a {
      text-decoration: none;
      font-weight: 700;
      font-size: .95rem;
      color: var(--dark);
      position: relative;
      transition: color .2s;
    }
    .nav-links a::after {
      content: '';
      position: absolute; bottom: -4px; left: 0; right: 0;
      height: 3px; border-radius: 2px;
      background: var(--orange);
      transform: scaleX(0);
      transition: transform .25s;
    }
    .nav-links a:hover { color: var(--orange); }
    .nav-links a:hover::after { transform: scaleX(1); }

    .nav-cta {
      background: var(--orange);
      color: var(--white) !important;
      padding: .45rem 1.2rem;
      border-radius: 50px;
      transition: background .2s, transform .2s !important;
    }
    .nav-cta:hover { background: #e8551e !important; transform: scale(1.05); }
    .nav-cta::after { display: none !important; }

    /* hamburger */
    .hamburger { display: none; flex-direction: column; gap: 5px; cursor: pointer; }
    .hamburger span { width: 26px; height: 3px; background: var(--dark); border-radius: 2px; transition: .3s; }

    /* ─── HERO ─── */
    #home {
      min-height: 100vh;
      padding: 100px 5vw 60px;
      display: flex; align-items: center;
      background: linear-gradient(135deg, #fff9e6 0%, #fff0f5 50%, #e8f4ff 100%);
      position: relative; overflow: hidden;
    }

    .hero-blobs {
      position: absolute; inset: 0; pointer-events: none; z-index: 0;
    }
    .blob {
      position: absolute; border-radius: 50%;
      filter: blur(60px); opacity: .25;
      animation: float 6s ease-in-out infinite;
    }
    .blob-1 { width: 400px; height: 400px; background: var(--yellow); top: -80px; right: 5%; animation-delay: 0s; }
    .blob-2 { width: 300px; height: 300px; background: var(--teal);  bottom: 5%; left: -60px; animation-delay: 2s; }
    .blob-3 { width: 250px; height: 250px; background: var(--orange); top: 40%; right: 15%; animation-delay: 4s; }

    @keyframes float {
      0%, 100% { transform: translateY(0) scale(1); }
      50%       { transform: translateY(-20px) scale(1.05); }
    }

    .hero-content { max-width: 620px; position: relative; z-index: 1; }
    .hero-badge {
      display: inline-block;
      background: var(--yellow);
      color: var(--dark);
      font-weight: 800;
      font-size: .82rem;
      letter-spacing: .08em;
      text-transform: uppercase;
      padding: .4rem 1rem;
      border-radius: 50px;
      margin-bottom: 1.2rem;
    }
    .hero-title {
      font-family: 'Baloo 2', cursive;
      font-size: clamp(2.4rem, 5vw, 3.8rem);
      font-weight: 800;
      line-height: 1.15;
      margin-bottom: 1.2rem;
    }
    .hero-title .highlight {
      color: var(--orange);
      position: relative; display: inline-block;
    }
    .hero-title .highlight::after {
      content: '';
      position: absolute; left: 0; bottom: 2px; right: 0;
      height: 8px;
      background: var(--yellow);
      z-index: -1;
      border-radius: 4px;
    }

    .hero-sub {
      font-size: 1.1rem; font-weight: 600;
      color: #555; margin-bottom: 2rem; line-height: 1.7;
    }
    .hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; }

    .btn {
      display: inline-block;
      padding: .75rem 1.8rem;
      border-radius: 50px;
      font-weight: 800;
      font-size: 1rem;
      text-decoration: none;
      transition: transform .2s, box-shadow .2s;
      cursor: pointer;
    }
    .btn:hover { transform: translateY(-3px); box-shadow: 0 8px 24px rgba(0,0,0,.15); }
    .btn-primary { background: var(--orange); color: var(--white); }
    .btn-secondary { background: var(--white); color: var(--dark); border: 2px solid var(--dark); }

    .hero-image {
      flex: 1; display: flex; justify-content: center; align-items: center;
      position: relative; z-index: 1;
    }
    .hero-card-stack { position: relative; width: 340px; height: 340px; }
    .stat-card {
      position: absolute;
      background: var(--white);
      border-radius: 20px;
      padding: 1.2rem 1.5rem;
      box-shadow: var(--shadow);
      font-weight: 700;
      animation: pop-in .6s ease both;
    }
    .stat-card .num {
      font-family: 'Baloo 2', cursive;
      font-size: 2rem; font-weight: 800;
    }
    .stat-card .lbl { font-size: .8rem; color: #888; font-weight: 700; }

    .card-students { top: 0;   left: 0;   background: var(--yellow); }
    .card-students .num { color: var(--dark); }
    .card-pass    { top: 0;   right: 0;  animation-delay: .15s; }
    .card-pass    .num { color: var(--teal); }
    .card-subjects{ bottom: 20px; left: 50%; transform: translateX(-50%); animation-delay: .3s; }
    .card-subjects .num { color: var(--orange); }

    .big-circle {
      position: absolute; top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      width: 220px; height: 220px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--blue), var(--teal));
      display: flex; align-items: center; justify-content: center;
      font-family: 'Baloo 2', cursive;
      font-size: 1.4rem; font-weight: 800;
      color: var(--white);
      text-align: center;
      line-height: 1.3;
      box-shadow: 0 12px 40px rgba(26,115,232,.3);
      z-index: -1;
    }

    @keyframes pop-in {
      from { opacity: 0; transform: scale(.8) translateY(10px); }
      to   { opacity: 1; transform: scale(1) translateY(0); }
    }

    /* ─── SECTION COMMON ─── */
    section { padding: 90px 5vw; }
    .section-tag {
      font-size: .8rem; font-weight: 800;
      letter-spacing: .12em; text-transform: uppercase;
      color: var(--orange); margin-bottom: .5rem;
    }
    .section-title {
      font-family: 'Baloo 2', cursive;
      font-size: clamp(1.8rem, 3.5vw, 2.6rem);
      font-weight: 800; margin-bottom: 1rem;
    }
    .section-sub { font-size: 1rem; color: #666; font-weight: 600; max-width: 560px; line-height: 1.7; }

    /* ─── ABOUT ─── */
    #about { background: var(--white); }
    .about-grid {
      display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center; margin-top: 3rem;
    }
    .about-pills { display: flex; flex-wrap: wrap; gap: .7rem; margin-top: 1.5rem; }
    .pill {
      background: var(--light);
      border: 2px solid;
      border-radius: 50px;
      padding: .4rem 1rem;
      font-weight: 700; font-size: .88rem;
    }
    .pill-orange { border-color: var(--orange); color: var(--orange); }
    .pill-blue   { border-color: var(--blue);   color: var(--blue);   }
    .pill-teal   { border-color: var(--teal);   color: var(--teal);   }
    .pill-purple { border-color: var(--purple); color: var(--purple); }

    .why-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1.2rem; }
    .why-item {
      background: var(--light);
      border-radius: 16px;
      padding: 1.2rem;
      display: flex; gap: .8rem; align-items: flex-start;
      border-left: 4px solid var(--yellow);
      transition: transform .2s, box-shadow .2s;
    }
    .why-item:hover { transform: translateY(-4px); box-shadow: var(--shadow); }
    .why-icon { font-size: 1.6rem; flex-shrink: 0; }
    .why-item h4 { font-size: .95rem; font-weight: 800; margin-bottom: .2rem; }
    .why-item p  { font-size: .82rem; color: #666; font-weight: 600; }

    /* ─── COURSES ─── */
    #courses { background: linear-gradient(180deg, #fff9e6 0%, #fff 100%); }
    .courses-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.8rem; margin-top: 3rem;
    }
    .course-card {
      background: var(--white);
      border-radius: 24px;
      overflow: hidden;
      box-shadow: var(--shadow);
      transition: transform .25s, box-shadow .25s;
      position: relative;
    }
    .course-card:hover { transform: translateY(-8px); box-shadow: 0 20px 48px rgba(0,0,0,.14); }

    .course-banner {
      height: 130px;
      display: flex; align-items: center; justify-content: center;
      font-size: 3.5rem;
      position: relative; overflow: hidden;
    }
    .course-banner::before {
      content: '';
      position: absolute; inset: 0;
      background: inherit;
      opacity: .15;
    }
    .math-banner   { background: linear-gradient(135deg, var(--blue), #5b9af8); }
    .sci-banner    { background: linear-gradient(135deg, var(--teal), #a0ead8); }
    .eng-banner    { background: linear-gradient(135deg, var(--orange), #ffa97e); }
    .found-banner  { background: linear-gradient(135deg, var(--purple), #c3aee4); }

    .course-body { padding: 1.5rem; }
    .course-level {
      font-size: .75rem; font-weight: 800;
      letter-spacing: .1em; text-transform: uppercase;
      color: #aaa; margin-bottom: .4rem;
    }
    .course-body h3 {
      font-family: 'Baloo 2', cursive;
      font-size: 1.35rem; font-weight: 800; margin-bottom: .6rem;
    }
    .course-body p { font-size: .88rem; color: #666; font-weight: 600; line-height: 1.6; margin-bottom: 1rem; }
    .course-tags { display: flex; flex-wrap: wrap; gap: .5rem; margin-bottom: 1.2rem; }
    .ctag {
      background: var(--light);
      border-radius: 50px;
      padding: .25rem .75rem;
      font-size: .75rem; font-weight: 700; color: #555;
    }
    .course-enroll {
      display: block; text-align: center;
      background: var(--dark); color: var(--white);
      border-radius: 50px; padding: .6rem 1rem;
      font-weight: 800; font-size: .9rem;
      text-decoration: none;
      transition: background .2s, transform .2s;
    }
    .course-enroll:hover { background: var(--orange); transform: scale(1.03); }

    /* ─── TESTIMONIALS ─── */
    #testimonials { background: var(--white); }
    .testimonials-grid {
      display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.5rem; margin-top: 3rem;
    }
    .tcard {
      background: var(--light);
      border-radius: 20px;
      padding: 1.6rem;
      position: relative;
      transition: transform .2s;
    }
    .tcard:hover { transform: translateY(-5px); }
    .tcard::before {
      content: '"'; font-size: 5rem; line-height: .6;
      color: var(--yellow);
      font-family: 'Baloo 2', cursive;
      position: absolute; top: 1rem; right: 1.2rem;
    }
    .tcard-text { font-size: .92rem; font-weight: 600; color: #444; line-height: 1.7; margin-bottom: 1.2rem; }
    .tcard-author { display: flex; align-items: center; gap: .8rem; }
    .tcard-avatar {
      width: 42px; height: 42px; border-radius: 50%;
      display: flex; align-items: center; justify-content: center;
      font-weight: 800; font-size: 1rem; color: var(--white);
      flex-shrink: 0;
    }
    .av-orange { background: var(--orange); }
    .av-blue   { background: var(--blue);   }
    .av-teal   { background: var(--teal);   }
    .av-purple { background: var(--purple); }
    .tcard-name { font-weight: 800; font-size: .92rem; }
    .tcard-grade { font-size: .78rem; color: #888; font-weight: 600; }
    .stars { color: var(--yellow); font-size: .9rem; margin-bottom: .6rem; }

    /* ─── CONTACT ─── */
    #contact {
      background: linear-gradient(135deg, var(--dark) 0%, #16213e 100%);
      color: var(--white);
    }
    #contact .section-tag { color: var(--yellow); }
    #contact .section-title { color: var(--white); }
    #contact .section-sub { color: #aaa; }

    .contact-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: start; margin-top: 3rem; }

    .contact-info { display: flex; flex-direction: column; gap: 1.4rem; }
    .cinfo-item { display: flex; align-items: flex-start; gap: 1rem; }
    .cinfo-icon {
      width: 48px; height: 48px; border-radius: 14px;
      background: rgba(255,255,255,.08);
      display: flex; align-items: center; justify-content: center;
      font-size: 1.3rem; flex-shrink: 0;
    }
    .cinfo-label { font-size: .78rem; color: #aaa; font-weight: 700; text-transform: uppercase; letter-spacing: .08em; }
    .cinfo-val   { font-size: 1rem; font-weight: 700; color: var(--white); }

    .contact-form { display: flex; flex-direction: column; gap: 1rem; }
    .form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
    .contact-form input,
    .contact-form select,
    .contact-form textarea {
      background: rgba(255,255,255,.07);
      border: 1.5px solid rgba(255,255,255,.12);
      border-radius: 12px;
      padding: .85rem 1.1rem;
      color: var(--white);
      font-family: 'Nunito', sans-serif;
      font-size: .95rem; font-weight: 600;
      outline: none;
      transition: border-color .2s, background .2s;
      width: 100%;
    }
    .contact-form input::placeholder,
    .contact-form textarea::placeholder { color: #888; }
    .contact-form select option { background: var(--dark); }
    .contact-form input:focus,
    .contact-form select:focus,
    .contact-form textarea:focus {
      border-color: var(--yellow);
      background: rgba(255,255,255,.1);
    }
    .contact-form textarea { resize: vertical; min-height: 110px; }
    .form-submit {
      background: var(--yellow); color: var(--dark);
      border: none; border-radius: 50px;
      padding: .9rem 2rem;
      font-family: 'Nunito', sans-serif;
      font-size: 1rem; font-weight: 800;
      cursor: pointer;
      transition: background .2s, transform .2s;
      width: 100%;
    }
    .form-submit:hover { background: #ffc107; transform: translateY(-2px); }

    .toast {
      display: none;
      background: var(--teal); color: var(--white);
      padding: .8rem 1.4rem; border-radius: 50px;
      font-weight: 700; font-size: .9rem;
      margin-top: .5rem; text-align: center;
    }

    /* ─── FOOTER ─── */
    footer {
      background: #0d0d1a;
      color: #888;
      text-align: center;
      padding: 1.8rem 5vw;
      font-size: .85rem; font-weight: 600;
    }
    footer a { color: var(--yellow); text-decoration: none; }
    .footer-logo {
      font-family: 'Baloo 2', cursive;
      font-size: 1.4rem; font-weight: 800;
      color: var(--white); margin-bottom: .4rem;
    }
    .footer-logo span { color: var(--orange); }

    /* ─── SCROLL ANIMATIONS ─── */
    .reveal {
      opacity: 0; transform: translateY(30px);
      transition: opacity .6s ease, transform .6s ease;
    }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    /* ─── RESPONSIVE ─── */
    @media (max-width: 900px) {
      .about-grid, .contact-grid { grid-template-columns: 1fr; gap: 2.5rem; }
      .hero-image { display: none; }
    }
    @media (max-width: 680px) {
      .nav-links { display: none; position: absolute; top: 70px; left: 0; right: 0;
        background: var(--white); flex-direction: column; padding: 1.5rem 5vw;
        box-shadow: 0 10px 30px rgba(0,0,0,.1); }
      .nav-links.open { display: flex; }
      .hamburger { display: flex; }
      .why-grid { grid-template-columns: 1fr; }
      .form-row { grid-template-columns: 1fr; }
      #home { flex-direction: column; }
    }
  </style>
</head>
<body>

<!-- ─── NAVBAR ─── -->
<nav>
  <a class="nav-logo" href="#home">Score<span>va</span></a>
  <ul class="nav-links" id="navLinks">
    <li><a href="#home">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#courses">Courses</a></li>
    <li><a href="#contact" class="nav-cta">Enroll Now</a></li>
  </ul>
  <div class="hamburger" id="hamburger" onclick="toggleNav()">
    <span></span><span></span><span></span>
  </div>
</nav>

<!-- ─── HERO ─── -->
<section id="home">
  <div class="hero-blobs">
    <div class="blob blob-1"></div>
    <div class="blob blob-2"></div>
    <div class="blob blob-3"></div>
  </div>

  <div class="hero-content">
    <div class="hero-badge">🎓 Admissions Open 2025–26</div>
    <h1 class="hero-title">
      Learn Smarter.<br>
      Score <span class="highlight">Higher.</span>
    </h1>
    <p class="hero-sub">
      Scoreva Tuition Classes offers expert coaching in Mathematics, Science &amp; English — helping students build strong foundations and ace their exams.
    </p>
    <div class="hero-btns">
      <a href="#courses" class="btn btn-primary">Explore Courses</a>
      <a href="#contact" class="btn btn-secondary">Get In Touch</a>
    </div>
  </div>

  <div class="hero-image">
    <div class="hero-card-stack">
      <div class="big-circle">Scoreva<br>Tuition</div>
      <div class="stat-card card-students">
        <div class="num">500+</div>
        <div class="lbl">Happy Students</div>
      </div>
      <div class="stat-card card-pass">
        <div class="num">97%</div>
        <div class="lbl">Pass Rate</div>
      </div>
      <div class="stat-card card-subjects">
        <div class="num">3</div>
        <div class="lbl">Core Subjects</div>
      </div>
    </div>
  </div>
</section>

<!-- ─── ABOUT ─── -->
<section id="about">
  <p class="section-tag reveal">Who We Are</p>
  <h2 class="section-title reveal">Building Tomorrow's<br>Top Scorers — Today</h2>
  <div class="about-grid">
    <div class="reveal">
      <p class="section-sub">
        At <strong>Scoreva Tuition Classes</strong>, we believe every student has the potential to excel. Our experienced teachers provide personalised attention, structured learning, and a supportive environment to help students thrive — from foundational concepts to exam excellence.
      </p>
      <div class="about-pills">
        <span class="pill pill-orange">Small Batch Sizes</span>
        <span class="pill pill-blue">Expert Teachers</span>
        <span class="pill pill-teal">Regular Tests</span>
        <span class="pill pill-purple">Doubt Sessions</span>
        <span class="pill pill-orange">Study Material Provided</span>
        <span class="pill pill-blue">Parent Updates</span>
      </div>
    </div>
    <div class="why-grid reveal">
      <div class="why-item">
        <span class="why-icon">👩‍🏫</span>
        <div>
          <h4>Experienced Faculty</h4>
          <p>Teachers with 10+ years of classroom experience.</p>
        </div>
      </div>
      <div class="why-item">
        <span class="why-icon">📊</span>
        <div>
          <h4>Progress Tracking</h4>
          <p>Monthly tests and detailed performance reports.</p>
        </div>
      </div>
      <div class="why-item">
        <span class="why-icon">🏆</span>
        <div>
          <h4>Proven Results</h4>
          <p>Hundreds of top scorers across schools every year.</p>
        </div>
      </div>
      <div class="why-item">
        <span class="why-icon">💬</span>
        <div>
          <h4>Doubt Clearing</h4>
          <p>Dedicated sessions so no question goes unanswered.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ─── COURSES ─── -->
<section id="courses">
  <p class="section-tag reveal">What We Teach</p>
  <h2 class="section-title reveal">Our Courses</h2>
  <p class="section-sub reveal">
    Structured programmes for Classes 6–10 covering the three pillars of academic success.
  </p>
  <div class="courses-grid">

    <div class="course-card reveal">
      <div class="course-banner math-banner">📐</div>
      <div class="course-body">
        <div class="course-level">Class 6 – 10</div>
        <h3>Mathematics</h3>
        <p>From arithmetic to algebra, geometry and beyond — we make maths logical, clear, and even fun.</p>
        <div class="course-tags">
          <span class="ctag">Algebra</span>
          <span class="ctag">Geometry</span>
          <span class="ctag">Trigonometry</span>
          <span class="ctag">Statistics</span>
        </div>
        <a href="#contact" class="course-enroll">Enroll Now →</a>
      </div>
    </div>

    <div class="course-card reveal">
      <div class="course-banner sci-banner">🔬</div>
      <div class="course-body">
        <div class="course-level">Class 6 – 10</div>
        <h3>Science</h3>
        <p>Physics, Chemistry &amp; Biology taught with experiments, diagrams, and concept-first explanations.</p>
        <div class="course-tags">
          <span class="ctag">Physics</span>
          <span class="ctag">Chemistry</span>
          <span class="ctag">Biology</span>
          <span class="ctag">Practicals</span>
        </div>
        <a href="#contact" class="course-enroll">Enroll Now →</a>
      </div>
    </div>

    <div class="course-card reveal">
      <div class="course-banner eng-banner">📖</div>
      <div class="course-body">
        <div class="course-level">Class 6 – 10</div>
        <h3>English</h3>
        <p>Grammar, comprehension, writing skills and literature — building confident communicators.</p>
        <div class="course-tags">
          <span class="ctag">Grammar</span>
          <span class="ctag">Writing</span>
          <span class="ctag">Literature</span>
          <span class="ctag">Comprehension</span>
        </div>
        <a href="#contact" class="course-enroll">Enroll Now →</a>
      </div>
    </div>

    <div class="course-card reveal">
      <div class="course-banner found-banner">🌟</div>
      <div class="course-body">
        <div class="course-level">Class 6 – 7 · Combo</div>
        <h3>Foundation Batch</h3>
        <p>All three subjects bundled into one comprehensive programme — perfect for junior students.</p>
        <div class="course-tags">
          <span class="ctag">Maths</span>
          <span class="ctag">Science</span>
          <span class="ctag">English</span>
          <span class="ctag">Best Value</span>
        </div>
        <a href="#contact" class="course-enroll">Enroll Now →</a>
      </div>
    </div>

  </div>
</section>

<!-- ─── TESTIMONIALS ─── -->
<section id="testimonials">
  <p class="section-tag reveal">Student Stories</p>
  <h2 class="section-title reveal">What Our Students Say</h2>
  <div class="testimonials-grid">

    <div class="tcard reveal">
      <div class="stars">★★★★★</div>
      <p class="tcard-text">My Maths marks jumped from 65 to 94 after joining Scoreva. The teachers explain every concept so clearly!</p>
      <div class="tcard-author">
        <div class="tcard-avatar av-orange">A</div>
        <div>
          <div class="tcard-name">Arjun Sharma</div>
          <div class="tcard-grade">Class 9 · Maths</div>
        </div>
      </div>
    </div>

    <div class="tcard reveal">
      <div class="stars">★★★★★</div>
      <p class="tcard-text">Science always felt hard, but here I actually understand WHY things work. The doubt sessions are a lifesaver.</p>
      <div class="tcard-author">
        <div class="tcard-avatar av-teal">P</div>
        <div>
          <div class="tcard-name">Priya Nair</div>
          <div class="tcard-grade">Class 8 · Science</div>
        </div>
      </div>
    </div>

    <div class="tcard reveal">
      <div class="stars">★★★★★</div>
      <p class="tcard-text">The English course helped me write essays I'm actually proud of. I scored an A in my board exams!</p>
      <div class="tcard-author">
        <div class="tcard-avatar av-blue">R</div>
        <div>
          <div class="tcard-name">Rohan Mehta</div>
          <div class="tcard-grade">Class 10 · English</div>
        </div>
      </div>
    </div>

  </div>
</section>

<!-- ─── CONTACT ─── -->
<section id="contact">
  <p class="section-tag reveal">Get In Touch</p>
  <h2 class="section-title reveal">Ready to Start Your<br>Journey with Scoreva?</h2>
  <p class="section-sub reveal">Fill in the form and we'll get back to you within 24 hours.</p>

  <div class="contact-grid">
    <div class="contact-info reveal">
      <div class="cinfo-item">
        <div class="cinfo-icon">📍</div>
        <div>
          <div class="cinfo-label">Address</div>
          <div class="cinfo-val">123, Knowledge Lane, Your City – 000000</div>
        </div>
      </div>
      <div class="cinfo-item">
        <div class="cinfo-icon">📞</div>
        <div>
          <div class="cinfo-label">Phone</div>
          <div class="cinfo-val">+91 98765 43210</div>
        </div>
      </div>
      <div class="cinfo-item">
        <div class="cinfo-icon">✉️</div>
        <div>
          <div class="cinfo-label">Email</div>
          <div class="cinfo-val">hello@scoreva.com</div>
        </div>
      </div>
      <div class="cinfo-item">
        <div class="cinfo-icon">🕐</div>
        <div>
          <div class="cinfo-label">Batch Timings</div>
          <div class="cinfo-val">Mon–Sat · 7 AM–8 PM</div>
        </div>
      </div>
    </div>

    <div class="contact-form reveal">
      <div class="form-row">
        <input type="text" id="fname" placeholder="Your Name" />
        <input type="tel"  id="phone" placeholder="Phone Number" />
      </div>
      <input type="email" id="email" placeholder="Email Address" />
      <select id="course">
        <option value="" disabled selected>Select a Course</option>
        <option>Mathematics (Class 6–10)</option>
        <option>Science (Class 6–10)</option>
        <option>English (Class 6–10)</option>
        <option>Foundation Batch (All 3 Subjects)</option>
      </select>
      <textarea id="message" placeholder="Any questions or message for us?"></textarea>
      <button class="form-submit" onclick="submitForm()">Send Enquiry 🚀</button>
      <div class="toast" id="toast">✅ Thanks! We'll reach out shortly.</div>
    </div>
  </div>
</section>

<!-- ─── FOOTER ─── -->
<footer>
  <div class="footer-logo">Score<span>va</span> Tuition Classes</div>
  <p>© 2025 Scoreva. All rights reserved. · Made with ❤️ for every student's success.</p>
</footer>

<script>
  /* ── Nav toggle ── */
  function toggleNav() {
    document.getElementById('navLinks').classList.toggle('open');
  }

  /* Close nav on link click (mobile) */
  document.querySelectorAll('.nav-links a').forEach(a => {
    a.addEventListener('click', () => {
      document.getElementById('navLinks').classList.remove('open');
    });
  });

  /* ── Scroll reveal ── */
  const reveals = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        observer.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  reveals.forEach(r => observer.observe(r));

  /* ── Form submission ── */
  function submitForm() {
    const name   = document.getElementById('fname').value.trim();
    const phone  = document.getElementById('phone').value.trim();
    const course = document.getElementById('course').value;
    if (!name || !phone || !course) {
      alert('Please fill in your name, phone number, and course selection.');
      return;
    }
    const toast = document.getElementById('toast');
    toast.style.display = 'block';
    // Clear fields
    ['fname','phone','email','message'].forEach(id => document.getElementById(id).value = '');
    document.getElementById('course').selectedIndex = 0;
    setTimeout(() => { toast.style.display = 'none'; }, 4000);
  }
</script>
</body>
</html># index.html
