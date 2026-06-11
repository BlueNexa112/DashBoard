<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Blue.Nexa — Solusi Kebutuhan Digital</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;500;600;700&family=Syne:wght@700;800&display=swap" rel="stylesheet" />
  <style>
    /* ── RESET & BASE ── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --blue-neon:   #00d4ff;
      --blue-mid:    #0099cc;
      --blue-deep:   #003566;
      --blue-dark:   #00111f;
      --black:       #020c13;
      --white:       #f0faff;
      --glass-bg:    rgba(0, 50, 90, 0.25);
      --glass-border:rgba(0, 212, 255, 0.18);
      --glow-sm:     0 0 10px rgba(0,212,255,0.4);
      --glow-md:     0 0 24px rgba(0,212,255,0.5);
      --glow-lg:     0 0 50px rgba(0,212,255,0.35);
      --card-shadow: 0 8px 40px rgba(0,0,0,0.5), 0 0 0 1px var(--glass-border);
      --font-display: 'Syne', sans-serif;
      --font-body:    'Space Grotesk', sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      font-family: var(--font-body);
      background: var(--black);
      color: var(--white);
      overflow-x: hidden;
      min-height: 100vh;
    }

    /* ── PARTICLES CANVAS ── */
    #particles-canvas {
      position: fixed;
      inset: 0;
      z-index: 0;
      pointer-events: none;
    }

    /* ── BACKGROUND GRADIENT ── */
    .bg-gradient {
      position: fixed;
      inset: 0;
      z-index: 0;
      background:
        radial-gradient(ellipse 80% 60% at 20% -10%, rgba(0,80,160,0.28) 0%, transparent 60%),
        radial-gradient(ellipse 60% 50% at 80% 110%, rgba(0,50,120,0.22) 0%, transparent 55%),
        linear-gradient(180deg, #020c13 0%, #00111f 40%, #001a30 70%, #020c13 100%);
      pointer-events: none;
    }

    /* ── LAYOUT WRAPPER ── */
    .page { position: relative; z-index: 1; }

    section { position: relative; }

    .container {
      max-width: 1160px;
      margin: 0 auto;
      padding: 0 24px;
    }

    /* ── GLASSMORPHISM ── */
    .glass {
      background: var(--glass-bg);
      backdrop-filter: blur(18px);
      -webkit-backdrop-filter: blur(18px);
      border: 1px solid var(--glass-border);
      border-radius: 20px;
    }

    /* ── SCROLL FADE-IN ── */
    .reveal {
      opacity: 0;
      transform: translateY(32px);
      transition: opacity 0.65s ease, transform 0.65s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    /* ════════════════════════════════
       HERO
    ════════════════════════════════ */
    #hero {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      text-align: center;
      padding: 80px 24px 60px;
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(0,212,255,0.08);
      border: 1px solid rgba(0,212,255,0.3);
      border-radius: 100px;
      padding: 6px 18px;
      font-size: 0.78rem;
      font-weight: 500;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--blue-neon);
      margin-bottom: 36px;
      animation: fadeDown 0.8s ease both;
    }

    .hero-badge::before {
      content: '';
      width: 7px; height: 7px;
      border-radius: 50%;
      background: var(--blue-neon);
      box-shadow: var(--glow-sm);
      animation: pulse 2s infinite;
    }

    .hero-title {
      font-family: var(--font-display);
      font-size: clamp(3.2rem, 12vw, 9rem);
      font-weight: 800;
      line-height: 1;
      letter-spacing: -0.02em;
      color: var(--white);
      text-shadow:
        0 0 30px rgba(0,212,255,0.6),
        0 0 70px rgba(0,212,255,0.35),
        0 0 120px rgba(0,100,200,0.25);
      animation: fadeUp 1s ease 0.2s both;
    }

    .hero-title span {
      color: var(--blue-neon);
    }

    .hero-dot {
      display: inline-block;
      width: 14px; height: 14px;
      border-radius: 50%;
      background: var(--blue-neon);
      box-shadow: var(--glow-md);
      vertical-align: middle;
      margin: 0 2px;
      animation: fadeUp 1s ease 0.3s both;
    }

    .hero-tagline {
      margin-top: 28px;
      font-size: clamp(1.05rem, 2.5vw, 1.35rem);
      font-weight: 600;
      color: var(--blue-neon);
      letter-spacing: 0.01em;
      animation: fadeUp 1s ease 0.4s both;
    }

    .hero-desc {
      margin-top: 16px;
      max-width: 560px;
      font-size: clamp(0.9rem, 2vw, 1.05rem);
      line-height: 1.7;
      color: rgba(200,235,255,0.65);
      animation: fadeUp 1s ease 0.55s both;
    }

    .hero-btns {
      margin-top: 44px;
      display: flex;
      gap: 16px;
      flex-wrap: wrap;
      justify-content: center;
      animation: fadeUp 1s ease 0.7s both;
    }

    .btn-primary {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 14px 32px;
      background: linear-gradient(135deg, var(--blue-neon), var(--blue-mid));
      color: #000;
      font-family: var(--font-body);
      font-weight: 700;
      font-size: 0.95rem;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      text-decoration: none;
      box-shadow: 0 0 24px rgba(0,212,255,0.45), 0 4px 20px rgba(0,0,0,0.4);
      transition: transform 0.2s, box-shadow 0.2s;
    }

    .btn-primary:hover {
      transform: translateY(-3px) scale(1.03);
      box-shadow: 0 0 36px rgba(0,212,255,0.65), 0 8px 30px rgba(0,0,0,0.5);
    }

    .btn-secondary {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 14px 32px;
      background: var(--glass-bg);
      backdrop-filter: blur(12px);
      color: var(--blue-neon);
      font-family: var(--font-body);
      font-weight: 600;
      font-size: 0.95rem;
      border: 1px solid rgba(0,212,255,0.35);
      border-radius: 12px;
      cursor: pointer;
      text-decoration: none;
      transition: transform 0.2s, box-shadow 0.2s, background 0.2s;
    }

    .btn-secondary:hover {
      transform: translateY(-3px) scale(1.03);
      background: rgba(0,212,255,0.12);
      box-shadow: var(--glow-sm), 0 8px 30px rgba(0,0,0,0.4);
    }

    /* scroll indicator */
    .scroll-hint {
      margin-top: 64px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      color: rgba(0,212,255,0.4);
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      animation: fadeUp 1s ease 1s both;
    }

    .scroll-hint .chevrons span {
      display: block;
      width: 10px; height: 10px;
      border-right: 2px solid rgba(0,212,255,0.5);
      border-bottom: 2px solid rgba(0,212,255,0.5);
      transform: rotate(45deg);
      margin: -4px auto;
      animation: scrollBounce 1.8s infinite;
    }
    .scroll-hint .chevrons span:nth-child(2) { animation-delay: 0.15s; opacity: 0.6; }
    .scroll-hint .chevrons span:nth-child(3) { animation-delay: 0.30s; opacity: 0.35; }

    /* ════════════════════════════════
       STATS
    ════════════════════════════════ */
    #stats {
      padding: 0 24px 100px;
    }

    .stats-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 20px;
    }

    .stat-card {
      padding: 32px 24px;
      text-align: center;
      box-shadow: var(--card-shadow);
      transition: transform 0.3s, box-shadow 0.3s;
      position: relative;
      overflow: hidden;
    }

    .stat-card::before {
      content: '';
      position: absolute;
      top: 0; left: 50%;
      transform: translateX(-50%);
      width: 60%; height: 1px;
      background: linear-gradient(90deg, transparent, var(--blue-neon), transparent);
    }

    .stat-card:hover {
      transform: translateY(-6px);
      box-shadow: var(--glow-sm), 0 16px 50px rgba(0,0,0,0.6), 0 0 0 1px rgba(0,212,255,0.25);
    }

    .stat-icon {
      font-size: 1.8rem;
      margin-bottom: 12px;
      filter: drop-shadow(0 0 8px rgba(0,212,255,0.5));
    }

    .stat-number {
      font-family: var(--font-display);
      font-size: clamp(1.8rem, 4vw, 2.6rem);
      font-weight: 800;
      color: var(--blue-neon);
      text-shadow: var(--glow-sm);
      line-height: 1;
    }

    .stat-label {
      margin-top: 8px;
      font-size: 0.82rem;
      color: rgba(200,235,255,0.55);
      letter-spacing: 0.04em;
    }

    /* ════════════════════════════════
       PRODUCTS
    ════════════════════════════════ */
    #products {
      padding: 0 24px 110px;
    }

    .section-header {
      text-align: center;
      margin-bottom: 60px;
    }

    .section-eyebrow {
      display: inline-block;
      font-size: 0.75rem;
      font-weight: 600;
      letter-spacing: 0.18em;
      text-transform: uppercase;
      color: var(--blue-neon);
      margin-bottom: 14px;
    }

    .section-title {
      font-family: var(--font-display);
      font-size: clamp(1.8rem, 5vw, 2.8rem);
      font-weight: 800;
      line-height: 1.1;
      color: var(--white);
    }

    .section-desc {
      margin-top: 14px;
      font-size: 1rem;
      color: rgba(200,235,255,0.55);
      max-width: 500px;
      margin-left: auto;
      margin-right: auto;
      line-height: 1.7;
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 22px;
    }

    .product-card {
      padding: 36px 28px;
      box-shadow: var(--card-shadow);
      cursor: pointer;
      text-decoration: none;
      color: inherit;
      display: block;
      transition: transform 0.3s cubic-bezier(.22,.68,0,1.2), box-shadow 0.3s;
      position: relative;
      overflow: hidden;
    }

    .product-card::after {
      content: '';
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, rgba(0,212,255,0.06) 0%, transparent 60%);
      opacity: 0;
      transition: opacity 0.3s;
      pointer-events: none;
    }

    .product-card:hover {
      transform: translateY(-8px) scale(1.02);
      box-shadow: var(--glow-md), 0 20px 60px rgba(0,0,0,0.6), 0 0 0 1px rgba(0,212,255,0.3);
    }

    .product-card:hover::after { opacity: 1; }

    .product-icon {
      font-size: 2.4rem;
      margin-bottom: 18px;
      display: block;
      filter: drop-shadow(0 0 10px rgba(0,212,255,0.45));
      transition: transform 0.3s;
    }

    .product-card:hover .product-icon {
      transform: scale(1.12);
    }

    .product-name {
      font-family: var(--font-display);
      font-size: 1.12rem;
      font-weight: 700;
      color: var(--white);
      margin-bottom: 10px;
    }

    .product-desc {
      font-size: 0.875rem;
      color: rgba(200,235,255,0.55);
      line-height: 1.65;
    }

    .product-cta {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      margin-top: 20px;
      font-size: 0.82rem;
      font-weight: 600;
      color: var(--blue-neon);
      letter-spacing: 0.04em;
      opacity: 0;
      transform: translateX(-6px);
      transition: opacity 0.25s, transform 0.25s;
    }

    .product-card:hover .product-cta {
      opacity: 1;
      transform: translateX(0);
    }

    /* ════════════════════════════════
       TESTIMONIAL
    ════════════════════════════════ */
    #testimoni {
      padding: 0 24px 110px;
    }

    .testi-box {
      padding: 64px 48px;
      text-align: center;
      box-shadow: var(--card-shadow);
      position: relative;
      overflow: hidden;
    }

    .testi-box::before {
      content: '';
      position: absolute;
      top: -60px; left: 50%;
      transform: translateX(-50%);
      width: 300px; height: 300px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(0,212,255,0.08) 0%, transparent 70%);
      pointer-events: none;
    }

    .testi-icon {
      font-size: 3rem;
      margin-bottom: 20px;
      display: block;
    }

    .testi-title {
      font-family: var(--font-display);
      font-size: clamp(1.5rem, 4vw, 2.2rem);
      font-weight: 800;
      color: var(--white);
      margin-bottom: 14px;
    }

    .testi-desc {
      font-size: 1rem;
      color: rgba(200,235,255,0.55);
      max-width: 480px;
      margin: 0 auto 36px;
      line-height: 1.7;
    }

    /* ════════════════════════════════
       FEATURES
    ════════════════════════════════ */
    #features {
      padding: 0 24px 110px;
    }

    .features-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 22px;
    }

    .feature-card {
      padding: 30px 26px;
      box-shadow: var(--card-shadow);
      transition: transform 0.3s, box-shadow 0.3s;
    }

    .feature-card:hover {
      transform: translateY(-5px);
      box-shadow: var(--glow-sm), 0 16px 50px rgba(0,0,0,0.55), 0 0 0 1px rgba(0,212,255,0.22);
    }

    .feature-icon {
      font-size: 2rem;
      margin-bottom: 14px;
      display: block;
      filter: drop-shadow(0 0 8px rgba(0,212,255,0.4));
    }

    .feature-name {
      font-family: var(--font-display);
      font-size: 1rem;
      font-weight: 700;
      color: var(--white);
      margin-bottom: 8px;
    }

    .feature-text {
      font-size: 0.85rem;
      color: rgba(200,235,255,0.52);
      line-height: 1.6;
    }

    /* ════════════════════════════════
       FOOTER
    ════════════════════════════════ */
    footer {
      position: relative;
      padding: 70px 24px 40px;
      border-top: 1px solid rgba(0,212,255,0.1);
    }

    footer::before {
      content: '';
      position: absolute;
      top: 0; left: 0; right: 0;
      height: 1px;
      background: linear-gradient(90deg, transparent, var(--blue-neon), transparent);
      opacity: 0.5;
    }

    .footer-inner {
      max-width: 1160px;
      margin: 0 auto;
    }

    .footer-brand {
      font-family: var(--font-display);
      font-size: clamp(2.2rem, 7vw, 4.5rem);
      font-weight: 800;
      color: var(--white);
      text-shadow: 0 0 30px rgba(0,212,255,0.45), 0 0 70px rgba(0,212,255,0.2);
      margin-bottom: 48px;
      letter-spacing: -0.02em;
    }

    .footer-brand span { color: var(--blue-neon); }

    .footer-cols {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 40px;
      margin-bottom: 48px;
    }

    .footer-col-title {
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: var(--blue-neon);
      margin-bottom: 18px;
    }

    .footer-links {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .footer-links li a {
      text-decoration: none;
      color: rgba(200,235,255,0.55);
      font-size: 0.9rem;
      transition: color 0.2s;
    }

    .footer-links li a:hover { color: var(--blue-neon); }

    .footer-bottom {
      padding-top: 28px;
      border-top: 1px solid rgba(0,212,255,0.08);
      font-size: 0.8rem;
      color: rgba(200,235,255,0.3);
      text-align: center;
    }

    /* ════════════════════════════════
       DIVIDER LINE
    ════════════════════════════════ */
    .section-line {
      width: 60px; height: 3px;
      background: linear-gradient(90deg, var(--blue-neon), transparent);
      border-radius: 4px;
      margin: 16px auto 0;
    }

    /* ════════════════════════════════
       ANIMATIONS
    ════════════════════════════════ */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(24px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes fadeDown {
      from { opacity: 0; transform: translateY(-16px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50%       { opacity: 0.5; transform: scale(0.8); }
    }

    @keyframes scrollBounce {
      0%, 100% { transform: rotate(45deg) translateY(0); opacity: 1; }
      50%       { transform: rotate(45deg) translateY(4px); opacity: 0.5; }
    }

    /* ════════════════════════════════
       RESPONSIVE
    ════════════════════════════════ */
    @media (max-width: 900px) {
      .stats-grid      { grid-template-columns: repeat(2, 1fr); }
      .products-grid   { grid-template-columns: repeat(2, 1fr); }
      .features-grid   { grid-template-columns: repeat(2, 1fr); }
    }

    @media (max-width: 580px) {
      .stats-grid      { grid-template-columns: repeat(2, 1fr); gap: 14px; }
      .products-grid   { grid-template-columns: 1fr; }
      .features-grid   { grid-template-columns: 1fr; }
      .footer-cols     { grid-template-columns: 1fr; }
      .testi-box       { padding: 40px 24px; }
      .stat-card       { padding: 24px 16px; }
    }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        animation-duration: 0.01ms !important;
        transition-duration: 0.01ms !important;
      }
    }
  </style>
</head>
<body>

<canvas id="particles-canvas"></canvas>
<div class="bg-gradient"></div>

<div class="page">

  <!-- ══ HERO ══ -->
  <section id="hero">
    <span class="hero-badge">Toko Digital Premium</span>

    <h1 class="hero-title">
      BLUE<span class="hero-dot"></span><span>NEXA</span>
    </h1>

    <p class="hero-tagline">Solusi Kebutuhan Digital Terpercaya, Cepat, dan Terjangkau.</p>

    <p class="hero-desc">
      Menyediakan berbagai produk digital berkualitas untuk memenuhi kebutuhan online Anda
      dengan proses cepat dan pelayanan responsif.
    </p>

    <div class="hero-btns">
      <a href="#products" class="btn-primary">🚀 Lihat Produk</a>
      <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="btn-secondary">📞 Hubungi Admin</a>
    </div>

    <div class="scroll-hint">
      <div class="chevrons">
        <span></span><span></span><span></span>
      </div>
      Scroll
    </div>
  </section>

  <!-- ══ STATS ══ -->
  <section id="stats">
    <div class="container">
      <div class="stats-grid">

        <div class="stat-card glass reveal">
          <div class="stat-icon">📦</div>
          <div class="stat-number" id="stat-stock">—</div>
          <div class="stat-label">Stock Tersedia</div>
        </div>

        <div class="stat-card glass reveal" style="transition-delay:0.1s">
          <div class="stat-icon">✅</div>
          <div class="stat-number">47</div>
          <div class="stat-label">Pesanan Berhasil</div>
        </div>

        <div class="stat-card glass reveal" style="transition-delay:0.2s">
          <div class="stat-icon">👥</div>
          <div class="stat-number" id="stat-customers">—</div>
          <div class="stat-label">Pelanggan Aktif</div>
        </div>

        <div class="stat-card glass reveal" style="transition-delay:0.3s">
          <div class="stat-icon">🕒</div>
          <div class="stat-number" style="font-size:clamp(1.1rem,2.5vw,1.5rem)">24 Jam</div>
          <div class="stat-label">Layanan Online</div>
        </div>

      </div>
    </div>
  </section>

  <!-- ══ PRODUCTS ══ -->
  <section id="products">
    <div class="container">
      <div class="section-header reveal">
        <span class="section-eyebrow">Produk Kami</span>
        <h2 class="section-title">Produk Digital Pilihan</h2>
        <div class="section-line"></div>
        <p class="section-desc">Temukan berbagai produk digital berkualitas tinggi yang selalu diperbarui untuk kebutuhan Anda.</p>
      </div>

      <div class="products-grid">

        <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="product-card glass reveal">
          <span class="product-icon">📁</span>
          <div class="product-name">FileFF</div>
          <p class="product-desc">Kumpulan file Free Fire lengkap dan siap digunakan. Update rutin untuk performa terbaik.</p>
          <span class="product-cta">Pesan Sekarang →</span>
        </a>

        <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="product-card glass reveal" style="transition-delay:0.08s">
          <span class="product-icon">😂</span>
          <div class="product-name">Backsound Meme 200+</div>
          <p class="product-desc">Ratusan backsound meme viral untuk editing video. Selalu diperbarui mengikuti tren terkini.</p>
          <span class="product-cta">Pesan Sekarang →</span>
        </a>

        <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="product-card glass reveal" style="transition-delay:0.16s">
          <span class="product-icon">📈</span>
          <div class="product-name">Suntik Sosmed</div>
          <p class="product-desc">Layanan followers, likes, views, dan engagement untuk semua platform media sosial populer.</p>
          <span class="product-cta">Pesan Sekarang →</span>
        </a>

        <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="product-card glass reveal" style="transition-delay:0.24s">
          <span class="product-icon">💰</span>
          <div class="product-name">Game Penghasil Uang</div>
          <p class="product-desc">Berbagai aplikasi dan game penghasil uang terpercaya dengan penghasilan nyata.</p>
          <span class="product-cta">Pesan Sekarang →</span>
        </a>

        <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="product-card glass reveal" style="transition-delay:0.32s">
          <span class="product-icon">🌐</span>
          <div class="product-name">Web Nokos</div>
          <p class="product-desc">Website penyedia nomor virtual dari berbagai negara. Aman, cepat, dan mudah digunakan.</p>
          <span class="product-cta">Pesan Sekarang →</span>
        </a>

        <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="product-card glass reveal" style="transition-delay:0.40s">
          <span class="product-icon">🚀</span>
          <div class="product-name">Web Suntik Sosmed</div>
          <p class="product-desc">Website panel otomatis untuk semua kebutuhan sosial media. Proses instan dan terpercaya.</p>
          <span class="product-cta">Pesan Sekarang →</span>
        </a>

        <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener" class="product-card glass reveal" style="grid-column: 1 / -1; transition-delay:0.48s">
          <span class="product-icon">📦</span>
          <div class="product-name">Produk Digital Lainnya</div>
          <p class="product-desc">Berbagai kebutuhan digital lainnya yang selalu diperbarui. Hubungi admin untuk info produk terbaru yang belum tercantum di sini.</p>
          <span class="product-cta">Tanya Admin →</span>
        </a>

      </div>
    </div>
  </section>

  <!-- ══ TESTIMONI ══ -->
  <section id="testimoni">
    <div class="container">
      <div class="testi-box glass reveal">
        <span class="testi-icon">💬</span>
        <h2 class="testi-title">Bukti Transaksi Pelanggan</h2>
        <p class="testi-desc">
          Lihat berbagai bukti transaksi dan pengalaman pelanggan yang telah
          menggunakan layanan Blue.Nexa.
        </p>
        <a href="https://whatsapp.com/channel/xxxxxxxx" target="_blank" rel="noopener" class="btn-primary">
          📲 Lihat Testimoni
        </a>
      </div>
    </div>
  </section>

  <!-- ══ FEATURES ══ -->
  <section id="features">
    <div class="container">
      <div class="section-header reveal">
        <span class="section-eyebrow">Inilah Dia</span>
        <h2 class="section-title">Keunggulan Blue.Nexa</h2>
        <div class="section-line"></div>
      </div>

      <div class="features-grid">

        <div class="feature-card glass reveal">
          <span class="feature-icon">⚡</span>
          <div class="feature-name">Proses Cepat</div>
          <p class="feature-text">Pesanan diproses dengan cepat tanpa menunggu lama. Layanan kilat untuk kepuasan Anda.</p>
        </div>

        <div class="feature-card glass reveal" style="transition-delay:0.08s">
          <span class="feature-icon">🔒</span>
          <div class="feature-name">Aman & Terpercaya</div>
          <p class="feature-text">Keamanan pelanggan menjadi prioritas utama kami. Transaksi aman dan data terlindungi.</p>
        </div>

        <div class="feature-card glass reveal" style="transition-delay:0.16s">
          <span class="feature-icon">💎</span>
          <div class="feature-name">Produk Berkualitas</div>
          <p class="feature-text">Produk selalu diperbarui dan terjamin kualitasnya. Hanya menyediakan yang terbaik.</p>
        </div>

        <div class="feature-card glass reveal" style="transition-delay:0.24s">
          <span class="feature-icon">📞</span>
          <div class="feature-name">Support Responsif</div>
          <p class="feature-text">Admin siap membantu kapan saja. Respon cepat untuk setiap pertanyaan dan kendala Anda.</p>
        </div>

        <div class="feature-card glass reveal" style="transition-delay:0.32s">
          <span class="feature-icon">💰</span>
          <div class="feature-name">Harga Bersahabat</div>
          <p class="feature-text">Produk berkualitas dengan harga yang terjangkau. Nilai terbaik untuk setiap rupiah Anda.</p>
        </div>

        <div class="feature-card glass reveal" style="transition-delay:0.40s">
          <span class="feature-icon">🌐</span>
          <div class="feature-name">Akses Mudah</div>
          <p class="feature-text">Dapat diakses dari berbagai perangkat kapan saja dan di mana saja dengan mudah.</p>
        </div>

      </div>
    </div>
  </section>

  <!-- ══ FOOTER ══ -->
  <footer>
    <div class="footer-inner">
      <div class="footer-brand">BLUE<span>.</span>NEXA</div>

      <div class="footer-cols">
        <div>
          <div class="footer-col-title">Layanan</div>
          <ul class="footer-links">
            <li><a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener">FileFF</a></li>
            <li><a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener">Backsound Meme 200+</a></li>
            <li><a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener">Suntik Sosmed</a></li>
            <li><a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener">Web Nokos</a></li>
            <li><a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener">Web Suntik Sosmed</a></li>
          </ul>
        </div>
        <div>
          <div class="footer-col-title">Kontak</div>
          <ul class="footer-links">
            <li>
              <a href="https://wa.me/62882XXXXXXXX" target="_blank" rel="noopener">
                📱 WhatsApp Admin 0882××××
              </a>
            </li>
          </ul>
        </div>
      </div>

      <div class="footer-bottom">
        © 2026 Blue.Nexa. All Rights Reserved.
      </div>
    </div>
  </footer>

</div><!-- /page -->

<script>
/* ── RANDOM STATS ── */
(function () {
  const stock = Math.floor(Math.random() * (200 - 50 + 1)) + 50;
  const customers = Math.floor(Math.random() * (12 - 4 + 1)) + 4;
  document.getElementById('stat-stock').textContent = stock;
  document.getElementById('stat-customers').textContent = customers;
})();

/* ── SCROLL REVEAL ── */
(function () {
  const els = document.querySelectorAll('.reveal');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        io.unobserve(e.target);
      }
    });
  }, { threshold: 0.12 });
  els.forEach(el => io.observe(el));
})();

/* ── PARTICLES ── */
(function () {
  const canvas = document.getElementById('particles-canvas');
  const ctx = canvas.getContext('2d');
  let W, H, particles = [], raf;

  function resize() {
    W = canvas.width  = window.innerWidth;
    H = canvas.height = window.innerHeight;
  }

  function Particle() {
    this.reset = function () {
      this.x  = Math.random() * W;
      this.y  = Math.random() * H;
      this.r  = Math.random() * 1.6 + 0.3;
      this.vx = (Math.random() - 0.5) * 0.22;
      this.vy = (Math.random() - 0.5) * 0.22;
      this.a  = Math.random() * 0.45 + 0.08;
      this.da = (Math.random() - 0.5) * 0.003;
    };
    this.reset();
    this.y = Math.random() * H; // spread initial Y
  }

  function init() {
    const N = Math.min(Math.floor((W * H) / 12000), 100);
    particles = Array.from({ length: N }, () => new Particle());
  }

  function draw() {
    ctx.clearRect(0, 0, W, H);
    particles.forEach(p => {
      p.x += p.vx; p.y += p.vy;
      p.a += p.da;
      if (p.a <= 0 || p.a >= 0.6) p.da *= -1;
      if (p.x < -5 || p.x > W + 5 || p.y < -5 || p.y > H + 5) p.reset();

      ctx.beginPath();
      ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
      ctx.fillStyle = `rgba(0,212,255,${p.a})`;
      ctx.shadowBlur = 6;
      ctx.shadowColor = 'rgba(0,212,255,0.5)';
      ctx.fill();
      ctx.shadowBlur = 0;
    });
    raf = requestAnimationFrame(draw);
  }

  window.addEventListener('resize', () => { resize(); init(); });
  resize();
  init();
  draw();
})();
</script>
</body>
</html>
