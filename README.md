# WebsiteTest   
<!--
personal-website.html
Updated: Added project subcategories ("University Projects") and comments explaining how to move projects between categories.
Instructions: Open this file in the canvas to view the full HTML. In this file I include clear comment markers (SEARCH FOR: "<!-- MAIN PROJECTS START -->", "<!-- SUBCATEGORY: UNIVERSITY START -->") showing changed/added parts.


<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Xena Getmanovich — Portfolio</title>

  <!-- Google Font -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

  <!-- Bootstrap 5 -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">

  <!-- AOS (Animate On Scroll) -->
  <link href="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.css" rel="stylesheet">

  <!-- Font Awesome (icons) -->
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

  <style>
    :root{
      --cream: #fffaf2;
      --text: #3b3b3b;
      --accent: #b89f82; /* brown accent as requested */
      --muted: #7b6f63;
      --radius: 12px;
      --container-w: 880px;
    }

    html,body{height:100%}
    body{
      margin:0;
      font-family: 'Poppins', system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background:var(--cream);
      color:var(--text);
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      line-height:1.55;
    }

    /* Container wrapper */
    .wrap{
      max-width:var(--container-w);
      margin:0 auto;
      padding:28px 20px 80px;
    }

    /* NAV */
    .navbar{
      background:transparent;
      transition: background-color .32s ease, box-shadow .32s ease;
    }
    .navbar.scrolled{
      background: rgba(255,250,242,0.98);
      box-shadow: 0 6px 18px rgba(30,25,20,0.06);
      backdrop-filter: blur(4px);
    }
    .brand-name{
      font-weight:700;
      color:var(--text);
      letter-spacing:0.2px;
    }
    .nav-link{
      color:var(--muted) !important;
      font-weight:600;
    }
    .nav-link:hover{ color:var(--text) !important; }

    /* HERO */
    .hero{
      text-align:center;
      padding:48px 18px;
    }
    .profile-wrap{
      display:flex;
      align-items:center;
      justify-content:center;
      margin-bottom:20px;
    }
    .profile{
      width:150px;
      height:150px;
      border-radius:50%;
      background:linear-gradient(180deg, rgba(184,159,130,0.12), rgba(184,159,130,0.05));
      display:block;
      overflow:hidden;
      border:4px solid rgba(184,159,130,0.16);
      box-shadow: 0 6px 24px rgba(22,20,18,0.06);
      transition: transform .28s cubic-bezier(.2,.9,.2,1), box-shadow .28s;
      will-change: transform;
    }
    .profile img{ width:100%; height:100%; object-fit:cover; display:block; }

    .hero h1{
      margin:12px 0 6px;
      font-weight:700;
      font-size:28px;
    }
    .hero .subtitle{
      margin:0 auto 14px;
      max-width:760px;
      color:var(--muted);
      font-weight:400;
    }

    .socials a{
      color:var(--muted);
      margin:0 8px;
      display:inline-block;
      width:44px;height:44px;border-radius:10px;
      line-height:44px;text-align:center;
      transition: background .18s, color .18s, transform .18s;
    }
    .socials a:hover{
      color:var(--text);
      background: rgba(184,159,130,0.06);
      transform:translateY(-4px);
    }

    /* SECTION TITLES */
    .section-title{
      text-align:center;
      margin:42px 0 18px;
      font-size:20px;
      font-weight:700;
      position:relative;
    }
    .section-title:after{
      content:"";
      width:60px;
      height:4px;
      background:var(--accent);
      display:block;
      margin:12px auto 0;
      border-radius:8px;
      opacity:.95;
    }

    /* PROJECT CARD (single-column) */
    .project{
      background:transparent;
      border-radius:var(--radius);
      padding:20px 12px 28px;
      margin:18px 0;
      text-align:center;
    }
    .project-title{
      font-weight:700;
      font-size:18px;
      margin-bottom:10px;
    }
    .tags{
      display:flex;
      gap:8px;
      justify-content:center;
      flex-wrap:wrap;
      margin-bottom:12px;
    }
    .tag-pill{
      padding:8px 12px;
      border-radius:999px;
      background:rgba(184,159,130,0.08);
      color:var(--muted);
      font-weight:600;
      font-size:13px;
      border:1px solid rgba(184,159,130,0.06);
    }
    .project-desc{
      color:var(--muted);
      margin:0 auto 14px;
      max-width:720px;
    }
    .media-wrap{
      width:85%;
      margin:0 auto;
      border-radius:12px;
      overflow:hidden;
      box-shadow: 0 10px 30px rgba(22,20,18,0.04);
      transition: transform .4s cubic-bezier(.2,.9,.2,1), box-shadow .3s;
      will-change: transform;
      background:#fff;
    }
    .media-wrap img, .media-wrap video{
      display:block;
      width:100%;
      height:auto;
      transform-origin:center center;
    }
    .divider{
      height:1px;
      background:rgba(0,0,0,0.04);
      margin-top:18px;
      margin-bottom:8px;
    }

    /* SUBCATEGORY LABEL */
    .subcat-label{
      text-transform:uppercase;
      font-size:12px;
      letter-spacing:1px;
      color:var(--muted);
      text-align:center;
      margin-top:24px;
      margin-bottom:8px;
    }

    /* CONTACT */
    .contact{
      text-align:center;
      padding:26px 10px;
    }
    .contact .icons a{ margin:0 10px; color:var(--muted); font-size:20px; }
    .contact .icons a:hover{ color:var(--text); transform:translateY(-3px); }

    /* FOOTER */
    footer{
      text-align:center;
      margin-top:28px;
      color:var(--muted);
      font-size:13px;
      padding:18px 10px 40px;
    }

    /* Responsive adjustments */
    @media (max-width:767px){
      .profile{ width:130px;height:130px; }
      .media-wrap{ width:95%; }
      .wrap{ padding:18px 14px 60px; }
      .hero h1{ font-size:22px; }
    }
  </style>
</head>
<body>

  

  <!-- PAGE WRAPPER -->
  <main class="wrap" role="main">

    <footer>
      © 2025 Xena Getmanovich — Built with ❤️ using Bootstrap.
    </footer>

  </main>

  <!-- SCRIPTS -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/aos@2.3.4/dist/aos.js"></script>

  <script>
    // Initialize AOS for subtle fade animations
    AOS.init({
      duration: 700,
      easing: 'ease-out-cubic',
      once: true,
      offset: 80,
    });

    // Navbar background toggle on scroll
    (function() {
      const nav = document.getElementById('mainNav');
      const offset = 20;
      function check(){
        if(window.scrollY > offset) nav.classList.add('scrolled');
        else nav.classList.remove('scrolled');
      }
      check();
      window.addEventListener('scroll', check);
    })();

  </script>
</body>
</html>
