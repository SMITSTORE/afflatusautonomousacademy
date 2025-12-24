<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>AFFLATUS AUTONOMOUS ACADEMY | Learn Languages</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800&display=swap" rel="stylesheet">

  <style>
    /* ========================
       VARIABLES & RESET
       ======================== */
    :root{
      --primary-color: #ff0000;
      --dark-bg: #0a0a14;
      --card-bg: rgba(26,26,46,0.85);
      --glass-bg: rgba(255,255,255,0.03);
      --muted: #aaaaaa;
      --white: #ffffff;
      --max-width: 1200px;
      --radius: 14px;
      --glass-border: rgba(255,255,255,0.04);
      --shadow-1: 0 6px 30px rgba(0,0,0,0.6);
      --accent-glow: 0 10px 60px rgba(255,0,0,0.18);
    }

    *{box-sizing:border-box;margin:0;padding:0}
    html,body{height:100%}
    body{
      font-family:"Montserrat",system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial;
      background: linear-gradient(180deg,#05050a 0%, #0a0a14 60%);
      color:var(--white);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      overflow-x:hidden;
      line-height:1.5;
    }

    a{color:inherit;text-decoration:none}
    ul{list-style:none}

    .container{width:90%;max-width:var(--max-width);margin:0 auto}
    .section-padding{padding:80px 0}
    .text-red{color:var(--primary-color)}
    .text-center{text-align:center}

    /* ========================
       HEADER / NAV
       ======================== */
    header{
      position:fixed;left:0;right:0;top:0;z-index:1400;
      background: linear-gradient(180deg, rgba(10,10,20,0.75), rgba(10,10,20,0.35));
      backdrop-filter: blur(8px);
      border-bottom:1px solid rgba(255,255,255,0.03);
      box-shadow: 0 8px 40px rgba(0,0,0,0.6);
    }
    .nav-inner{display:flex;align-items:center;justify-content:space-between;padding:14px 0}
    .logo{font-weight:800;letter-spacing:1px;font-size:1.25rem}
    .logo .academy{color:var(--primary-color);font-weight:900;margin-left:6px}

    .nav-links{display:flex;gap:28px;align-items:center}
    .nav-links a{
      font-weight:600;font-size:0.88rem;text-transform:uppercase;opacity:0.92;padding:8px 10px;border-radius:8px;
      transition:all 270ms cubic-bezier(.2,.9,.2,1);
    }
    .nav-links a:hover{color:var(--primary-color);transform:translateY(-3px)}
    .cta-small{padding:8px 16px;border-radius:999px;background:transparent;border:1px solid rgba(255,255,255,0.06)}
    .menu-toggle{display:none;font-size:1.6rem;cursor:pointer;padding:6px 8px}

    /* Back button area (hidden normally) */
    .page-back { display: none; gap: 10px; align-items: center; }
    .page-title { color: var(--muted); font-weight:700; font-size:0.95rem; margin-left: 8px; }

    /* ========================
       PAGE TRANSITION ANIMATIONS (HIGH)
       ======================== */
    .page {
      min-height: 100vh;
      padding-top: 100px; /* account for fixed header */
      opacity: 1;
      transform: translateY(0) scale(1);
      transition: opacity .6s cubic-bezier(.2,.9,.2,1), transform .7s cubic-bezier(.2,.9,.2,1);
    }
    .page-enter { opacity: 0; transform: translateY(20px) scale(.995); }
    .page-enter-active { opacity: 1; transform: translateY(0) scale(1); }
    .page-exit { opacity: 1; transform: translateY(0) scale(1); }
    .page-exit-active { opacity: 0; transform: translateY(-18px) scale(.995); }

    /* ========================
       HERO — premium glass + parallax
       ======================== */
    #hero{
      padding-top:140px;padding-bottom:120px;
      min-height:78vh;
      display:flex;align-items:center;justify-content:center;
      background-image:
        linear-gradient(180deg, rgba(10,10,20,0.6), rgba(10,10,20,0.6)),
        url('https://images.unsplash.com/photo-1543269865-cbf427effbad?ixlib=rb-1.2.1&auto=format&fit=crop&w=2000&q=80');
      background-size:cover;background-position:center;
      position:relative;overflow:hidden;
    }

    #hero::after{
      content:"";position:absolute;inset:0;
      background: radial-gradient(800px 400px at 10% 20%, rgba(255,0,0,0.06), transparent 8%),
                  radial-gradient(700px 350px at 90% 80%, rgba(255,0,0,0.04), transparent 10%);
      pointer-events:none;mix-blend-mode:overlay;
    }

    .hero-inner{position:relative;z-index:2;display:flex;gap:40px;align-items:center;justify-content:center;flex-wrap:wrap;width:100%}
    .hero-card{
      background: linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02));
      border: 1px solid var(--glass-border);
      box-shadow: var(--shadow-1);
      padding:36px;border-radius:20px;max-width:980px;width:100%;
      display:flex;gap:24px;align-items:center;justify-content:space-between;backdrop-filter: blur(6px);
      transform:translateY(0);
      transition: transform 0.6s cubic-bezier(.2,.9,.2,1), box-shadow .4s;
    }
    .hero-card:hover{transform:translateY(-10px);box-shadow:var(--accent-glow), 0 30px 80px rgba(0,0,0,0.6)}

    .hero-copy{flex:1;min-width:260px}
    .hero-title{font-size:2.2rem;font-weight:800;line-height:1.05;margin-bottom:10px;letter-spacing:0.6px}
    .hero-sub{color:var(--muted);font-size:1rem;max-width:720px;margin-bottom:18px}
    .hero-actions{display:flex;gap:14px;flex-wrap:wrap}

    .btn{
      display:inline-flex;align-items:center;justify-content:center;
      padding:12px 26px;border-radius:999px;font-weight:800;text-transform:uppercase;
      letter-spacing:0.6px;border:none;cursor:pointer;background:var(--primary-color);color:white;
      box-shadow: 0 6px 28px rgba(255,0,0,0.12), 0 2px 8px rgba(0,0,0,0.5);
      transition:transform 240ms, box-shadow 240ms, filter 240ms;
      will-change:transform;
    }
    .btn:hover{transform:translateY(-6px) scale(1.02);filter:brightness(1.02)}
    .btn-outline{
      background:transparent;border:2px solid rgba(255,255,255,0.08);color:var(--white);padding:10px 22px;
      box-shadow:none;
    }
    .btn-outline:hover{background:linear-gradient(180deg, rgba(255,255,255,0.03), rgba(255,255,255,0.02))}

    .hero-media{width:300px;min-width:220px;display:flex;align-items:center;justify-content:center}
    .hero-media .badge{
      width:100%;height:180px;border-radius:12px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      display:flex;align-items:center;justify-content:center;flex-direction:column;padding:18px;border:1px solid rgba(255,255,255,0.03)
    }
    .hero-media h4{font-size:1.05rem;margin-bottom:6px}
    .hero-media p{font-size:0.9rem;color:var(--muted)}

    /* ========================
       MEMORIES GALLERY STYLES
       ======================== */
    .memories-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 20px;
      padding-top: 30px;
    }
    .memory-item {
      overflow: hidden;
      border-radius: var(--radius);
      border: 1px solid var(--glass-border);
      background: var(--card-bg);
      transition: transform 0.4s ease;
    }
    .memory-item img {
      width: 100%;
      height: 250px;
      object-fit: cover;
      display: block;
      transition: transform 0.6s ease;
    }
    .memory-item:hover img {
      transform: scale(1.1);
    }
    .memory-item:hover {
      box-shadow: var(--accent-glow);
    }
    .mem-logo {
      width: 120px;
      margin-bottom: 20px;
      filter: drop-shadow(0 0 10px rgba(255,0,0,0.3));
    }

    /* ========================
       STATS ROW
       ======================== */
    #stats{background:linear-gradient(90deg, var(--primary-color), rgba(255,0,0,0.85));padding:28px 0;margin-top:-6px}
    .stats-grid{display:flex;justify-content:space-around;align-items:center;gap:18px;flex-wrap:wrap}
    .stat-item{text-align:center;color:#fff;min-width:140px}
    .stat-item h3{font-size:1.8rem;font-weight:900;letter-spacing:0.6px}
    .stat-item p{font-size:0.9rem;opacity:0.95;font-weight:700;letter-spacing:0.8px}

    /* ========================
       FEATURES / COURSES / LOCATIONS
       ======================== */
    .section-title{font-size:1.9rem;font-weight:900;display:inline-block;margin-bottom:18px;letter-spacing:1px}
    .section-title::after{content:"";display:block;width:60px;height:5px;background:var(--primary-color);border-radius:3px;margin:10px auto 0}

    .features-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:24px}
    .feature-box{
      background:var(--card-bg);padding:20px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);
      transition:transform .6s cubic-bezier(.2,.9,.2,1),box-shadow .4s;box-shadow:0 8px 28px rgba(0,0,0,0.45);
    }
    .feature-box:hover{transform:translateY(-10px);box-shadow:var(--accent-glow), 0 30px 80px rgba(0,0,0,0.7)}
    .feature-icon{font-size:2rem;margin-bottom:12px}
    .feature-title{font-weight:800;font-size:1.05rem;margin-bottom:8px}
    .feature-text{color:var(--muted);font-size:0.95rem}

    .courses-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:22px;margin-top:20px}
    .course-card{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      padding:22px;border-radius:12px;border:1px solid rgba(255,255,255,0.03);text-align:center;
      transition:transform .6s,box-shadow .4s;padding-bottom:28px;box-shadow:0 12px 40px rgba(0,0,0,0.6)
    }
    .course-card:hover{transform:translateY(-14px);box-shadow:var(--accent-glow), 0 40px 110px rgba(0,0,0,0.75)}
    .flag-icon{font-size:2.6rem;margin-bottom:12px}
    .course-title{font-weight:800;font-size:1.1rem;margin-bottom:8px}
    .course-card p{color:var(--muted);font-size:0.95rem}

    /* Locations */
    .locations-container{display:flex;gap:20px;flex-wrap:wrap;justify-content:center}
    .location-box{flex:1;min-width:260px;max-width:460px;padding:26px;border-radius:12px;background:var(--card-bg);border-left:5px solid var(--primary-color);box-shadow:0 14px 40px rgba(0,0,0,0.6)}
    .location-box h3{font-size:1.15rem;margin-bottom:8px}
    .location-box p{color:var(--muted);margin-bottom:12px}

    /* Contact */
    .contact-container{display:grid;grid-template-columns:1fr 1fr;gap:36px;align-items:start}
    .contact-info h4{color:var(--primary-color);font-size:1rem;margin-bottom:8px}
    .contact-form input,.contact-form textarea{
      width:100%;padding:12px;border-radius:8px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:var(--white);
      resize:vertical;font-family:inherit;margin-bottom:12px
    }
    .contact-form input:focus,.contact-form textarea:focus{outline:none;box-shadow:0 6px 24px rgba(255,0,0,0.06);border-color:var(--primary-color)}

    /* Footer */
    footer{padding:48px 0;background:#05050a;border-top:1px solid rgba(255,255,255,0.02);margin-top:40px}
    .footer-inner{display:flex;flex-direction:column;align-items:center;gap:10px}
    .footer-inner p{color:var(--muted)}

    /* ========================
       ANIMATIONS (HIGH)
       ======================== */
    .fade-up{opacity:0;transform:translateY(18px);animation:fup .8s ease forwards}
    .stagger-1{animation-delay:0.08s}
    .stagger-2{animation-delay:0.18s}
    .stagger-3{animation-delay:0.28s}
    @keyframes fup{to{opacity:1;transform:none}}

    @keyframes floaty{0%{transform:translateY(0)}50%{transform:translateY(-12px)}100%{transform:translateY(0)}}
    .floaty{animation:floaty 5.5s ease-in-out infinite}

    .glowPulse{position:relative;transition:box-shadow .35s}
    .glowPulse:hover{box-shadow:0 12px 60px rgba(255,0,0,0.14), inset 0 0 30px rgba(255,0,0,0.03)}

    /* ========================
       RESPONSIVE BREAKPOINTS
       ======================== */
    @media (max-width:1100px){
      .hero-card{padding:28px;border-radius:16px}
      .hero-title{font-size:1.85rem}
      .hero-media{width:260px}
    }
    @media (max-width:900px){
      .nav-links{gap:18px}
      .hero-title{font-size:1.6rem}
      .hero-sub{font-size:0.95rem}
      #hero{padding-top:120px;padding-bottom:90px}
      .hero-inner{flex-direction:column;align-items:stretch}
      .hero-media{order:2;margin-top:12px}
      .hero-card{flex-direction:column;align-items:flex-start}
      .hero-media .badge{height:140px}
      .contact-container{grid-template-columns:1fr}
      .sections { padding: 60px 0; }
    }
    @media (max-width:700px){
      header{padding:8px 0}
      .menu-toggle{display:block}
      .nav-links{
        position:fixed;left:0;right:0;top:64px;background:rgba(10,10,20,0.98);flex-direction:column;align-items:center;padding:18px;
        transform:translateY(-140%);transition:transform .45s cubic-bezier(.2,.9,.2,1);box-shadow:0 40px 80px rgba(0,0,0,0.7)
      }
      .nav-links.show{transform:translateY(0)}
      .nav-links a{padding:12px 16px;width:100%;text-align:center;border-radius:10px}
      .hero-title{font-size:1.4rem}
      .hero-media{width:100%}
      .hero-media .badge{height:120px}
      .btn{width:100%}
      .container{width:94%}
      .location-box{max-width:100%}
    }
    @media (max-width:420px){
      .hero-card{padding:18px;border-radius:12px}
      .hero-title{font-size:1.2rem}
      .hero-sub{font-size:0.9rem}
      .feature-title{font-size:1rem}
      .course-title{font-size:1rem}
      .section-padding{padding:40px 0}
    }

    /* prefers reduced motion — turn off animations */
    @media (prefers-reduced-motion: reduce){
      .fade-up,.floaty{animation:none !important;transform:none !important}
      .hero-card,.feature-box,.course-card{transition:none !important}
    }

    /* small helpers */
    .mt-12{margin-top:12px}
    .mb-18{margin-bottom:18px}
    .muted{color:var(--muted)}
  </style>
</head>

<body>
  <header>
    <div class="container nav-inner">
      <div style="display:flex;align-items:center;gap:12px">
        <div class="page-back" id="pageBackWrap">
          <button class="btn btn-outline" id="pageBackBtn" aria-hidden="true" onclick="history.back()">← Back</button>
          <div class="page-title" id="pageTitle"></div>
        </div>

        <div class="logo">AFFLATUS <span class="academy">ACADEMY</span></div>
      </div>

      <nav>
        <div class="nav-links" id="navLinks">
          <a href="#" onclick="showMain();return false" class="stagger-1">Home</a>
          <a href="#why-us" onclick="showMain();return false" class="stagger-2">Why Us</a>
          <a href="#" onclick="showCourses();return false" class="stagger-3">Courses</a>
          <a href="#" onclick="showMemories();return false" class="stagger-1">Memories</a>
          <a href="#locations" onclick="showMain();return false" class="stagger-1">Locations</a>
          <a href="#" onclick="showContact();return false" class="stagger-2">Contact</a>
        </div>
      </nav>

      <div style="display:flex;gap:12px;align-items:center">
        <button class="cta-small" onclick="showContact()">Enquire</button>
        <div class="menu-toggle" id="menuToggle" onclick="toggleMenu()">☰</div>
      </div>
    </div>
  </header>

  <main>

    <section id="home-page" class="page page-enter-active" aria-labelledby="home">
      <div id="main-view" class="page-content">
        <section id="hero" aria-label="Hero">
          <div class="container hero-inner fade-up">
            <div class="hero-card">

              <div class="hero-copy">
                <h1 class="hero-title">EMPOWER YOUR FUTURE<br/><span class="text-red">WITH LANGUAGE</span></h1>
                <p class="hero-sub">Join Afflatus Autonomous Academy to master English, Spanish, German, French, and Japanese. Open doors to global opportunities today.</p>

                <div class="hero-actions">
                  <button class="btn glowPulse" onclick="showCourses()">Explore Courses</button>
                  <button class="btn btn-outline" onclick="showMemories()">View Our Memories</button>
                </div>
              </div>

              <div class="hero-media floaty" aria-hidden="true">
                <div class="badge">
                  <h4>Trusted • ISO 9001</h4>
                  <p class="muted">500+ Students • National Board</p>
                </div>
              </div>

            </div>
          </div>
        </section>

        <section id="stats" aria-hidden="false">
          <div class="container">
            <div class="stats-grid">
              <div class="stat-item fade-up stagger-1"><h3>500+</h3><p>Students Taught</p></div>
              <div class="stat-item fade-up stagger-2"><h3>ISO</h3><p>9001 Certified</p></div>
              <div class="stat-item fade-up stagger-3"><h3>AICPE</h3><p>Nationally Certified</p></div>
            </div>
          </div>
        </section>

        <section id="why-us" class="section-padding">
          <div class="container">
            <div class="text-center mb-18">
              <h2 class="section-title">Why Choose <span class="text-red">Afflatus?</span></h2>
              <p class="muted">We provide a world-class environment to master foreign languages with recognized certifications.</p>
            </div>

            <div class="features-grid">
              <div class="feature-box fade-up stagger-1">
                <div class="feature-icon">🎖️</div>
                <div class="feature-title">Double Certified</div>
                <div class="feature-text">We are an <strong>ISO 9001:2001</strong> certified academy and recognized by the <strong>AICPE National Board</strong>.</div>
              </div>

              <div class="feature-box fade-up stagger-2">
                <div class="feature-icon">👨‍🏫</div>
                <div class="feature-title">Top Mentors</div>
                <div class="feature-text">Learn from industry experts with years of experience in teaching foreign languages effectively.</div>
              </div>

              <div class="feature-box fade-up stagger-3">
                <div class="feature-icon">🏫</div>
                <div class="feature-title">Wide Campus</div>
                <div class="feature-text">Enjoy our spacious campus equipped with all modern amenities and a perfect environment for learning.</div>
              </div>

              <div class="feature-box fade-up stagger-1">
                <div class="feature-icon">🎓</div>
                <div class="feature-title">Student Success</div>
                <div class="feature-text">We have successfully trained <strong>500+ students</strong>, helping them achieve their career and travel goals.</div>
              </div>
            </div>
          </div>
        </section>

        <section id="locations" class="section-padding">
          <div class="container">
            <div class="text-center mb-18">
              <h2 class="section-title">Our <span class="text-red">Locations</span></h2>
            </div>

            <div class="locations-container">
              <div class="location-box fade-up stagger-1">
                <h3>📍 NAGPUR</h3>
                <p>The Orange City Hub. Experience world-class classroom facilities.</p>
                <div style="display:flex;gap:10px;margin-top:12px;flex-wrap:wrap">
                  <a class="btn" href="https://maps.app.goo.gl/uoFMXB2y6ufPkuf48" target="_blank">View Map</a>
                  <a class="btn btn-outline" href="https://www.google.com/maps/dir/?api=1&destination=https://maps.app.goo.gl/uoFMXB2y6ufPkuf48" target="_blank">Get Directions</a>
                </div>
              </div>

              <div class="location-box fade-up stagger-2">
                <h3>📍 BHANDARA</h3>
                <p>Bringing expert language education closer to your home.</p>
                <div style="display:flex;gap:10px;margin-top:12px;flex-wrap:wrap">
                  <a class="btn" href="https://maps.app.goo.gl/52jQYjFWiV1HkGxA6" target="_blank">View Map</a>
                  <a class="btn btn-outline" href="http
