<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>NowaNest — Natural Food | Makhana, Dry Fruits & More</title>
  <meta name="description" content="NowaNest brings you premium quality natural foods — Makhana, Almonds, Cashews & Raisins. Naturally sourced, lovingly packed.">
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;0,700;1,400;1,500&family=Nunito:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    /* ═══════════════════════════════════════
       CSS VARIABLES & RESET
    ═══════════════════════════════════════ */
    :root {
      --parchment: #FAF7F0;
      --cream: #F5F0E3;
      --warm-white: #FEFCF8;
      --bark: #3D2B1F;
      --bark-light: #5C4033;
      --leaf: #4A7C3F;
      --leaf-light: #6BA358;
      --leaf-pale: #E8F0E4;
      --honey: #D4920B;
      --honey-light: #F0C75E;
      --honey-pale: #FDF5E0;
      --orange-warm: #E8843C;
      --blush: #F2D4C2;
      --shadow-soft: rgba(61, 43, 31, 0.06);
      --shadow-medium: rgba(61, 43, 31, 0.1);
      --text-primary: #2A1F14;
      --text-secondary: #6B5B4E;
      --text-muted: #9A8B7C;
      --radius-sm: 12px;
      --radius-md: 20px;
      --radius-lg: 32px;
      --radius-xl: 48px;
    }

    *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

    html { scroll-behavior: smooth; scroll-padding-top: 80px; }

    body {
      font-family: 'Nunito', sans-serif;
      background: var(--parchment);
      color: var(--text-primary);
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
    }

    /* subtle grain */
    body::after {
      content: '';
      position: fixed;
      inset: 0;
      pointer-events: none;
      opacity: 0.025;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");
      z-index: 9999;
    }

    h1, h2, h3, h4 {
      font-family: 'Cormorant Garamond', serif;
      font-weight: 600;
      line-height: 1.15;
    }

    img { max-width: 100%; display: block; }
    a { text-decoration: none; color: inherit; }

    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 clamp(1.25rem, 4vw, 3rem);
    }

    /* ═══════════════════════════════════════
       NAVIGATION
    ═══════════════════════════════════════ */
    .nav {
      position: fixed;
      top: 0;
      width: 100%;
      z-index: 1000;
      padding: 1rem 0;
      transition: all 0.4s ease;
    }

    .nav.scrolled {
      background: rgba(250, 247, 240, 0.92);
      backdrop-filter: blur(16px);
      box-shadow: 0 1px 20px var(--shadow-soft);
    }

    .nav-inner {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 clamp(1.25rem, 4vw, 3rem);
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .nav-logo {
      display: flex;
      align-items: center;
      gap: 0.6rem;
    }

    .nav-logo img {
      height: 44px;
      width: auto;
      border-radius: 50%;
    }

    .nav-logo-text {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.45rem;
      font-weight: 700;
      color: var(--bark);
    }

    .nav-logo-text span { color: var(--leaf); }

    .nav-links {
      display: flex;
      gap: 2.25rem;
      list-style: none;
      align-items: center;
    }

    .nav-links a {
      font-size: 0.82rem;
      font-weight: 600;
      letter-spacing: 0.07em;
      text-transform: uppercase;
      color: var(--text-secondary);
      transition: color 0.3s;
      position: relative;
    }

    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -4px;
      left: 0;
      width: 0;
      height: 2px;
      background: var(--leaf);
      border-radius: 2px;
      transition: width 0.3s ease;
    }

    .nav-links a:hover { color: var(--leaf); }
    .nav-links a:hover::after { width: 100%; }

    .nav-cta {
      padding: 0.6rem 1.5rem;
      background: var(--leaf);
      color: white !important;
      border-radius: 100px;
      font-size: 0.8rem !important;
      font-weight: 600;
      letter-spacing: 0.06em;
      transition: all 0.3s;
    }

    .nav-cta::after { display: none !important; }
    .nav-cta:hover { background: var(--bark) !important; color: white !important; transform: translateY(-1px); }

    /* Mobile hamburger */
    .hamburger {
      display: none;
      flex-direction: column;
      gap: 5px;
      cursor: pointer;
      padding: 4px;
      background: none;
      border: none;
    }

    .hamburger span {
      width: 24px;
      height: 2px;
      background: var(--bark);
      border-radius: 2px;
      transition: all 0.3s;
    }

    /* ═══════════════════════════════════════
       HERO
    ═══════════════════════════════════════ */
    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      position: relative;
      overflow: hidden;
      padding-top: 80px;
    }

    /* Organic blob shapes in background */
    .hero-blob {
      position: absolute;
      border-radius: 50%;
      filter: blur(80px);
      opacity: 0.18;
      pointer-events: none;
    }

    .hero-blob-1 {
      width: 500px;
      height: 500px;
      background: var(--leaf-light);
      top: -10%;
      right: 10%;
      animation: blobFloat 12s ease-in-out infinite;
    }

    .hero-blob-2 {
      width: 350px;
      height: 350px;
      background: var(--honey-light);
      bottom: 5%;
      left: 5%;
      animation: blobFloat 10s ease-in-out infinite reverse;
    }

    .hero-blob-3 {
      width: 250px;
      height: 250px;
      background: var(--blush);
      top: 30%;
      right: 35%;
      animation: blobFloat 14s ease-in-out infinite 2s;
    }

    @keyframes blobFloat {
      0%, 100% { transform: translate(0, 0) scale(1); }
      33% { transform: translate(20px, -30px) scale(1.05); }
      66% { transform: translate(-15px, 15px) scale(0.97); }
    }

    .hero-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 4rem;
      align-items: center;
      position: relative;
      z-index: 2;
    }

    .hero-content { animation: heroFadeIn 1s ease-out; }

    @keyframes heroFadeIn {
      from { opacity: 0; transform: translateY(40px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      padding: 0.4rem 1rem 0.4rem 0.5rem;
      background: var(--leaf-pale);
      border-radius: 100px;
      font-size: 0.72rem;
      font-weight: 700;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--leaf);
      margin-bottom: 1.75rem;
    }

    .hero-badge::before {
      content: '🌿';
      font-size: 1rem;
    }

    .hero h1 {
      font-size: clamp(2.8rem, 5.5vw, 4.5rem);
      letter-spacing: -0.02em;
      color: var(--bark);
      margin-bottom: 1.25rem;
    }

    .hero h1 em {
      font-style: italic;
      color: var(--leaf);
    }

    .hero-subtitle {
      font-size: 1.1rem;
      line-height: 1.75;
      color: var(--text-secondary);
      max-width: 480px;
      margin-bottom: 2.25rem;
      font-weight: 400;
    }

    .hero-actions {
      display: flex;
      gap: 1rem;
      align-items: center;
      flex-wrap: wrap;
    }

    .btn {
      display: inline-flex;
      align-items: center;
      gap: 0.6rem;
      padding: 0.9rem 2rem;
      border-radius: 100px;
      font-family: 'Nunito', sans-serif;
      font-size: 0.88rem;
      font-weight: 600;
      letter-spacing: 0.03em;
      border: none;
      cursor: pointer;
      transition: all 0.35s ease;
    }

    .btn-primary {
      background: var(--leaf);
      color: white;
    }

    .btn-primary:hover {
      background: var(--bark);
      transform: translateY(-2px);
      box-shadow: 0 8px 28px rgba(74, 124, 63, 0.2);
    }

    .btn-outline {
      background: transparent;
      color: var(--bark);
      border: 1.5px solid rgba(61, 43, 31, 0.18);
    }

    .btn-outline:hover {
      border-color: var(--leaf);
      color: var(--leaf);
      transform: translateY(-2px);
    }

    .hero-visual {
      display: flex;
      justify-content: center;
      align-items: center;
      animation: heroFadeIn 1s ease-out 0.3s both;
    }

    .hero-logo-showcase {
      position: relative;
      width: 100%;
      max-width: 420px;
    }

    .hero-logo-showcase img {
      width: 100%;
      filter: drop-shadow(0 20px 60px rgba(61, 43, 31, 0.12));
      animation: gentleBounce 4s ease-in-out infinite;
    }

    @keyframes gentleBounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-12px); }
    }

    /* Decorative ring behind logo */
    .hero-logo-showcase::before {
      content: '';
      position: absolute;
      inset: -20px;
      border-radius: 50%;
      border: 2px dashed rgba(74, 124, 63, 0.12);
      animation: spinSlow 30s linear infinite;
    }

    @keyframes spinSlow { to { transform: rotate(360deg); } }

    /* trust bar */
    .trust-bar {
      margin-top: 3rem;
      padding-top: 2rem;
      border-top: 1px solid rgba(61, 43, 31, 0.06);
      display: flex;
      gap: 2.5rem;
      flex-wrap: wrap;
    }

    .trust-item {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      font-size: 0.8rem;
      color: var(--text-muted);
      font-weight: 500;
    }

    .trust-item .icon {
      width: 32px;
      height: 32px;
      background: var(--honey-pale);
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
    }

    /* ═══════════════════════════════════════
       PRODUCTS SECTION
    ═══════════════════════════════════════ */
    .products {
      padding: 7rem 0;
      background: var(--warm-white);
      position: relative;
    }

    /* Top wave divider */
    .wave-divider {
      position: absolute;
      top: -1px;
      left: 0;
      width: 100%;
      overflow: hidden;
      line-height: 0;
    }

    .wave-divider svg {
      width: 100%;
      height: 60px;
      display: block;
    }

    .section-header {
      text-align: center;
      margin-bottom: 4rem;
    }

    .section-tag {
      display: inline-flex;
      align-items: center;
      gap: 0.75rem;
      font-size: 0.7rem;
      font-weight: 700;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      color: var(--leaf);
      margin-bottom: 1rem;
    }

    .section-tag::before, .section-tag::after {
      content: '';
      width: 30px;
      height: 1.5px;
      background: var(--leaf);
      opacity: 0.4;
    }

    .section-header h2 {
      font-size: clamp(2rem, 4vw, 3rem);
      color: var(--bark);
      margin-bottom: 1rem;
    }

    .section-header p {
      font-size: 1.05rem;
      color: var(--text-secondary);
      max-width: 560px;
      margin: 0 auto;
      line-height: 1.7;
    }

    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 1.75rem;
    }

    .product-card {
      background: var(--parchment);
      border-radius: var(--radius-md);
      padding: 2.25rem 1.75rem;
      text-align: center;
      border: 1px solid rgba(61, 43, 31, 0.04);
      transition: all 0.4s ease;
      position: relative;
      overflow: hidden;
    }

    .product-card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 60px;
      height: 3px;
      background: linear-gradient(90deg, var(--leaf), var(--honey));
      border-radius: 0 0 4px 4px;
      opacity: 0;
      transition: opacity 0.3s, width 0.3s;
    }

    .product-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 16px 48px var(--shadow-medium);
    }

    .product-card:hover::before { opacity: 1; width: 100%; }

    .product-emoji {
      font-size: 3.5rem;
      margin-bottom: 1.25rem;
      display: block;
      transition: transform 0.4s;
    }

    .product-card:hover .product-emoji { transform: scale(1.15) rotate(-5deg); }

    .product-card h3 {
      font-size: 1.35rem;
      margin-bottom: 0.5rem;
      color: var(--bark);
    }

    .product-card .tagline {
      font-size: 0.78rem;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      color: var(--leaf);
      margin-bottom: 0.75rem;
    }

    .product-card p {
      font-size: 0.9rem;
      line-height: 1.65;
      color: var(--text-secondary);
    }

    .product-badge {
      display: inline-block;
      padding: 0.25rem 0.75rem;
      background: var(--honey-pale);
      color: var(--honey);
      font-size: 0.68rem;
      font-weight: 700;
      border-radius: 100px;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      margin-top: 1rem;
    }

    .product-badge.coming { background: var(--leaf-pale); color: var(--leaf); }

    /* ═══════════════════════════════════════
       BENEFITS
    ═══════════════════════════════════════ */
    .benefits {
      padding: 7rem 0;
      position: relative;
    }

    .benefits-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 2rem;
      margin-top: 3.5rem;
    }

    .benefit-card {
      display: flex;
      gap: 1.25rem;
      padding: 1.75rem;
      background: var(--warm-white);
      border-radius: var(--radius-md);
      border: 1px solid rgba(61, 43, 31, 0.04);
      transition: all 0.35s;
    }

    .benefit-card:hover {
      transform: translateX(6px);
      box-shadow: -4px 4px 24px var(--shadow-soft);
    }

    .benefit-icon {
      flex-shrink: 0;
      width: 52px;
      height: 52px;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.5rem;
    }

    .benefit-icon.green { background: var(--leaf-pale); }
    .benefit-icon.gold { background: var(--honey-pale); }
    .benefit-icon.blush { background: var(--blush); }

    .benefit-content h3 {
      font-size: 1.2rem;
      margin-bottom: 0.4rem;
      color: var(--bark);
    }

    .benefit-content p {
      font-size: 0.88rem;
      line-height: 1.65;
      color: var(--text-secondary);
    }

    /* ═══════════════════════════════════════
       STORY
    ═══════════════════════════════════════ */
    .story {
      padding: 7rem 0;
      background: var(--cream);
      position: relative;
      overflow: hidden;
    }

    .story-inner {
      display: grid;
      grid-template-columns: 1fr 1.2fr;
      gap: 4rem;
      align-items: center;
    }

    .story-visual {
      position: relative;
    }

    .story-img-frame {
      background: var(--warm-white);
      border-radius: var(--radius-lg);
      padding: 2.5rem;
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 20px 60px var(--shadow-soft);
      position: relative;
    }

    .story-img-frame img {
      width: 260px;
      height: auto;
      animation: gentleBounce 5s ease-in-out infinite;
    }

    /* Decorative leaf accents */
    .story-img-frame::before {
      content: '🍃';
      position: absolute;
      top: -16px;
      right: -16px;
      font-size: 2rem;
      animation: spinSlow 20s linear infinite;
    }

    .story-img-frame::after {
      content: '🌾';
      position: absolute;
      bottom: -12px;
      left: -12px;
      font-size: 1.8rem;
      animation: spinSlow 25s linear infinite reverse;
    }

    .story-content .section-tag { margin-bottom: 1rem; }

    .story-content h2 {
      font-size: clamp(2rem, 3.5vw, 2.8rem);
      color: var(--bark);
      margin-bottom: 1.5rem;
    }

    .story-content h2 em {
      font-style: italic;
      color: var(--leaf);
    }

    .story-text {
      font-size: 1rem;
      line-height: 1.85;
      color: var(--text-secondary);
      margin-bottom: 1.5rem;
    }

    .story-values {
      display: flex;
      gap: 2rem;
      margin-top: 2rem;
      flex-wrap: wrap;
    }

    .story-value {
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .story-value .dot {
      width: 10px;
      height: 10px;
      border-radius: 50%;
    }

    .story-value .dot.g { background: var(--leaf); }
    .story-value .dot.o { background: var(--orange-warm); }
    .story-value .dot.h { background: var(--honey); }

    .story-value span {
      font-size: 0.85rem;
      font-weight: 600;
      color: var(--bark-light);
    }

    /* ═══════════════════════════════════════
       PARTNERS
    ═══════════════════════════════════════ */
    .partners {
      padding: 7rem 0;
      text-align: center;
    }

    .partners-subtitle {
      font-size: 1.05rem;
      color: var(--text-secondary);
      max-width: 520px;
      margin: 0 auto 3.5rem;
      line-height: 1.7;
    }

    .partners-logos {
      display: flex;
      justify-content: center;
      gap: 2.5rem;
      flex-wrap: wrap;
      align-items: center;
      margin-bottom: 3rem;
    }

    .partner-tile {
      padding: 1.5rem 2.5rem;
      background: var(--warm-white);
      border-radius: var(--radius-md);
      border: 1px solid rgba(61, 43, 31, 0.05);
      transition: all 0.35s;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.75rem;
      min-width: 160px;
    }

    .partner-tile:hover {
      transform: translateY(-4px);
      box-shadow: 0 12px 36px var(--shadow-soft);
      border-color: var(--leaf);
    }

    .partner-tile .p-icon {
      font-size: 2rem;
    }

    .partner-tile .p-name {
      font-family: 'Cormorant Garamond', serif;
      font-size: 1.15rem;
      font-weight: 700;
      color: var(--bark);
    }

    .partner-tile .p-type {
      font-size: 0.72rem;
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--text-muted);
    }

    .partners-note {
      font-size: 0.9rem;
      color: var(--text-muted);
      font-style: italic;
      margin-top: 1rem;
    }

    /* ═══════════════════════════════════════
       CONTACT
    ═══════════════════════════════════════ */
    .contact {
      padding: 0 0 5rem;
    }

    .contact-card {
      background: var(--bark);
      color: var(--cream);
      border-radius: var(--radius-xl);
      padding: clamp(3rem, 6vw, 5rem);
      position: relative;
      overflow: hidden;
    }

    .contact-card::before {
      content: '';
      position: absolute;
      width: 500px;
      height: 500px;
      border-radius: 50%;
      background: radial-gradient(circle, var(--leaf) 0%, transparent 70%);
      opacity: 0.06;
      top: -200px;
      right: -150px;
    }

    .contact-card::after {
      content: '';
      position: absolute;
      width: 300px;
      height: 300px;
      border-radius: 50%;
      background: radial-gradient(circle, var(--honey) 0%, transparent 70%);
      opacity: 0.06;
      bottom: -100px;
      left: -50px;
    }

    .contact-inner {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 3rem;
      position: relative;
      z-index: 2;
    }

    .contact-info .section-tag { color: var(--honey-light); }

    .contact-info h2 {
      font-size: clamp(2rem, 3.5vw, 2.8rem);
      color: var(--cream);
      margin-bottom: 1.25rem;
    }

    .contact-info p {
      font-size: 1rem;
      line-height: 1.75;
      opacity: 0.65;
      margin-bottom: 2rem;
    }

    .contact-detail {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 1.25rem;
    }

    .contact-detail .cd-icon {
      width: 44px;
      height: 44px;
      border-radius: 12px;
      background: rgba(255,255,255,0.08);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      flex-shrink: 0;
    }

    .contact-detail .cd-text {
      font-size: 0.92rem;
      opacity: 0.8;
    }

    .contact-detail .cd-label {
      font-size: 0.7rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      opacity: 0.45;
      margin-bottom: 0.15rem;
    }

    .contact-form {
      display: flex;
      flex-direction: column;
      gap: 1rem;
    }

    .form-group {
      display: flex;
      flex-direction: column;
      gap: 0.35rem;
    }

    .form-group label {
      font-size: 0.72rem;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      opacity: 0.5;
    }

    .form-group input,
    .form-group textarea {
      background: rgba(255,255,255,0.07);
      border: 1px solid rgba(255,255,255,0.1);
      border-radius: var(--radius-sm);
      padding: 0.85rem 1rem;
      font-family: 'Nunito', sans-serif;
      font-size: 0.92rem;
      color: var(--cream);
      transition: all 0.3s;
      outline: none;
    }

    .form-group input::placeholder,
    .form-group textarea::placeholder {
      color: rgba(255,255,255,0.25);
    }

    .form-group input:focus,
    .form-group textarea:focus {
      border-color: var(--leaf-light);
      background: rgba(255,255,255,0.1);
    }

    .form-group textarea { resize: vertical; min-height: 110px; }

    .btn-submit {
      padding: 1rem 2rem;
      background: var(--leaf);
      color: white;
      border: none;
      border-radius: 100px;
      font-family: 'Nunito', sans-serif;
      font-size: 0.9rem;
      font-weight: 700;
      cursor: pointer;
      transition: all 0.3s;
      letter-spacing: 0.03em;
      margin-top: 0.5rem;
    }

    .btn-submit:hover {
      background: var(--honey);
      transform: translateY(-2px);
      box-shadow: 0 8px 24px rgba(212, 146, 11, 0.25);
    }

    /* ═══════════════════════════════════════
       FOOTER
    ═══════════════════════════════════════ */
    .footer {
      padding: 3rem 0;
      border-top: 1px solid rgba(61, 43, 31, 0.06);
    }

    .footer-inner {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 1rem;
    }

    .footer-brand {
      display: flex;
      align-items: center;
      gap: 0.5rem;
    }

    .footer-brand img {
      height: 32px;
      border-radius: 50%;
    }

    .footer-brand span {
      font-family: 'Cormorant Garamond', serif;
      font-weight: 700;
      font-size: 1.1rem;
      color: var(--bark);
    }

    .footer-copy {
      font-size: 0.8rem;
      color: var(--text-muted);
    }

    .footer-social {
      display: flex;
      gap: 0.75rem;
    }

    .footer-social a {
      width: 36px;
      height: 36px;
      border-radius: 10px;
      background: var(--cream);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
      transition: all 0.3s;
    }

    .footer-social a:hover {
      background: var(--leaf);
      transform: translateY(-2px);
    }

    /* ═══════════════════════════════════════
       SCROLL REVEAL
    ═══════════════════════════════════════ */
    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }

    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.35s; }

    /* ═══════════════════════════════════════
       RESPONSIVE
    ═══════════════════════════════════════ */
    @media (max-width: 900px) {
      .hero-inner { grid-template-columns: 1fr; text-align: center; }
      .hero-subtitle { margin-left: auto; margin-right: auto; }
      .hero-actions { justify-content: center; }
      .hero-visual { order: -1; }
      .hero-logo-showcase { max-width: 280px; margin: 0 auto; }
      .trust-bar { justify-content: center; }
      .story-inner { grid-template-columns: 1fr; }
      .story-visual { display: flex; justify-content: center; }
      .story-img-frame img { width: 200px; }
      .contact-inner { grid-template-columns: 1fr; }
    }

    @media (max-width: 640px) {
      .nav-links { display: none; }
      .hamburger { display: flex; }
      section, .products, .benefits, .partners, .story { padding: 4.5rem 0; }
      .products-grid { grid-template-columns: 1fr 1fr; gap: 1rem; }
      .product-card { padding: 1.5rem 1rem; }
      .product-emoji { font-size: 2.5rem; }
      .benefits-grid { grid-template-columns: 1fr; }
      .partner-tile { min-width: 130px; padding: 1rem 1.5rem; }
      .contact-card { border-radius: var(--radius-lg); padding: 2rem 1.5rem; }
      .story-values { gap: 1rem; }
    }
  </style>
</head>
<body>

  <!-- ══════════ NAVIGATION ══════════ -->
  <nav class="nav" id="nav">
    <div class="nav-inner">
      <a href="#" class="nav-logo">
        <img src="images/logo-circle.png" alt="NowaNest Logo">
        <div class="nav-logo-text">Nowa<span>Nest</span></div>
      </a>
      <ul class="nav-links">
        <li><a href="#products">Products</a></li>
        <li><a href="#benefits">Benefits</a></li>
        <li><a href="#story">Our Story</a></li>
        <li><a href="#partners">Partners</a></li>
        <li><a href="#contact" class="nav-cta">Get in Touch</a></li>
      </ul>
      <button class="hamburger" id="hamburger" aria-label="Menu">
        <span></span><span></span><span></span>
      </button>
    </div>
  </nav>

  <!-- ══════════ HERO ══════════ -->
  <section class="hero">
    <div class="hero-blob hero-blob-1"></div>
    <div class="hero-blob hero-blob-2"></div>
    <div class="hero-blob hero-blob-3"></div>
    <div class="container">
      <div class="hero-inner">
        <div class="hero-content">
          <div class="hero-badge">100% Natural Goodness</div>
          <h1>Nature's Best,<br>Nestled for <em>You</em></h1>
          <p class="hero-subtitle">Premium Makhana, dry fruits & natural snacks — carefully sourced, lovingly packed. Bringing wholesome nourishment from India's heartland straight to your home.</p>
          <div class="hero-actions">
            <a href="#products" class="btn btn-primary">
              Explore Products
              <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3"/></svg>
            </a>
            <a href="#story" class="btn btn-outline">Our Story</a>
          </div>
          <div class="trust-bar">
            <div class="trust-item">
              <div class="icon">🌾</div>
              <span>Farm Fresh</span>
            </div>
            <div class="trust-item">
              <div class="icon">✅</div>
              <span>Quality Tested</span>
            </div>
            <div class="trust-item">
              <div class="icon">📦</div>
              <span>Pan-India Delivery</span>
            </div>
          </div>
        </div>
        <div class="hero-visual">
          <div class="hero-logo-showcase">
            <img src="images/logo-icon.png" alt="NowaNest - Natural Food Characters">
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══════════ PRODUCTS ══════════ -->
  <section class="products" id="products">
    <div class="wave-divider">
      <svg viewBox="0 0 1200 60" preserveAspectRatio="none" fill="var(--warm-white)">
        <path d="M0,0 C300,60 900,0 1200,50 L1200,0 L0,0 Z" fill="var(--parchment)"/>
      </svg>
    </div>
    <div class="container">
      <div class="section-header reveal">
        <div class="section-tag">Our Offerings</div>
        <h2>Naturally Nourishing</h2>
        <p>Every product at NowaNest is chosen with care — pure, natural, and packed with the goodness your body deserves.</p>
      </div>
      <div class="products-grid">
        <div class="product-card reveal reveal-delay-1">
          <span class="product-emoji">🫘</span>
          <h3>Makhana</h3>
          <div class="tagline">Fox Nuts · Our Star</div>
          <p>Light, crunchy, and incredibly nutritious — our premium Makhana is sourced from Bihar's finest farms. A guilt-free snack for every mood.</p>
          <span class="product-badge">Bestseller</span>
        </div>
        <div class="product-card reveal reveal-delay-2">
          <span class="product-emoji">🍇</span>
          <h3>Kishmish</h3>
          <div class="tagline">Golden Raisins</div>
          <p>Sweet, plump, and sun-kissed raisins that add natural sweetness to your cereals, desserts, or just a handful on the go.</p>
          <span class="product-badge">Premium Grade</span>
        </div>
        <div class="product-card reveal reveal-delay-3">
          <span class="product-emoji">🌰</span>
          <h3>Almonds</h3>
          <div class="tagline">Badam · Brain Food</div>
          <p>Carefully selected, full-bodied almonds — rich in Vitamin E and healthy fats. A timeless classic for daily health.</p>
          <span class="product-badge">Premium Grade</span>
        </div>
        <div class="product-card reveal reveal-delay-4">
          <span class="product-emoji">🥜</span>
          <h3>Cashews</h3>
          <div class="tagline">Kaju · Creamy Crunch</div>
          <p>Whole, creamy cashews that melt in your mouth. Perfect for cooking, baking, or enjoying straight from the pack.</p>
          <span class="product-badge">Premium Grade</span>
        </div>
      </div>
      <!-- Flavoured Makhana teaser -->
      <div style="text-align:center; margin-top:3rem;" class="reveal">
        <div style="display:inline-flex; align-items:center; gap:0.75rem; padding:1rem 2rem; background:var(--leaf-pale); border-radius:100px; border:1px dashed var(--leaf);">
          <span style="font-size:1.3rem;">✨</span>
          <span style="font-size:0.88rem; font-weight:600; color:var(--leaf);">Flavoured Makhana Range — Coming Soon! Peri-Peri, Cheese, Pudina & more</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ══════════ BENEFITS ══════════ -->
  <section class="benefits" id="benefits">
    <div class="container">
      <div class="section-header reveal">
        <div class="section-tag">Why NowaNest</div>
        <h2>Goodness You Can Trust</h2>
        <p>We don't just sell food — we nurture a promise of purity, nutrition, and love in every pack.</p>
      </div>
      <div class="benefits-grid">
        <div class="benefit-card reveal reveal-delay-1">
          <div class="benefit-icon green">💪</div>
          <div class="benefit-content">
            <h3>Rich in Protein</h3>
            <p>Makhana and dry fruits are natural protein powerhouses — ideal for fitness-conscious snackers and growing families alike.</p>
          </div>
        </div>
        <div class="benefit-card reveal reveal-delay-2">
          <div class="benefit-icon gold">❤️</div>
          <div class="benefit-content">
            <h3>Heart Healthy</h3>
            <p>Almonds and cashews are loaded with healthy fats that support heart health and keep cholesterol in check, naturally.</p>
          </div>
        </div>
        <div class="benefit-card reveal reveal-delay-3">
          <div class="benefit-icon blush">🧘</div>
          <div class="benefit-content">
            <h3>Low Calorie Snacking</h3>
            <p>Makhana is one of the lightest, lowest-calorie snacks nature has to offer — guilt-free munching at its finest.</p>
          </div>
        </div>
        <div class="benefit-card reveal reveal-delay-1">
          <div class="benefit-icon green">🌿</div>
          <div class="benefit-content">
            <h3>No Preservatives</h3>
            <p>What you see is what you get — real food without added chemicals, artificial colours, or preservatives. Pure and simple.</p>
          </div>
        </div>
        <div class="benefit-card reveal reveal-delay-2">
          <div class="benefit-icon gold">🧠</div>
          <div class="benefit-content">
            <h3>Boosts Immunity</h3>
            <p>Packed with antioxidants, magnesium, and essential minerals that help strengthen immunity and keep you energised all day.</p>
          </div>
        </div>
        <div class="benefit-card reveal reveal-delay-3">
          <div class="benefit-icon blush">👶</div>
          <div class="benefit-content">
            <h3>Safe for All Ages</h3>
            <p>From toddlers to grandparents — our products are gentle, wholesome, and loved across every generation.</p>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══════════ OUR STORY ══════════ -->
  <section class="story" id="story">
    <div class="container">
      <div class="story-inner">
        <div class="story-visual reveal">
          <div class="story-img-frame">
            <img src="images/logo-full.png" alt="NowaNest Natural Food">
          </div>
        </div>
        <div class="story-content reveal">
          <div class="section-tag">Our Story</div>
          <h2>Born from a Love<br>for <em>Real Food</em></h2>
          <p class="story-text">NowaNest started with a simple belief — that the food we eat should be as close to nature as possible. Growing up in India's heartland, we witnessed the incredible richness of our farms and the age-old wisdom of natural snacking.</p>
          <p class="story-text">We noticed that while the world moved towards processed, packaged junk, the treasures of our land — Makhana from Bihar, golden raisins, crunchy almonds — were being overlooked. NowaNest was born to change that.</p>
          <p class="story-text">Today, we work directly with local farmers, ensure fair trade practices, and bring you food that's been cared for at every step — from the farm to your family's table. Every pack carries the warmth of a nest and the promise of nature.</p>
          <div class="story-values">
            <div class="story-value"><div class="dot g"></div><span>Farm-Direct Sourcing</span></div>
            <div class="story-value"><div class="dot o"></div><span>Fair Trade</span></div>
            <div class="story-value"><div class="dot h"></div><span>Family-First Values</span></div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══════════ PARTNERS ══════════ -->
  <section class="partners" id="partners">
    <div class="container">
      <div class="section-header reveal">
        <div class="section-tag">Where to Find Us</div>
        <h2>Available on Your<br>Favourite Platforms</h2>
      </div>
      <p class="partners-subtitle reveal">We've partnered with India's leading quick-commerce and e-commerce platforms so that NowaNest goodness is just a tap away.</p>
      <div class="partners-logos reveal">
        <div class="partner-tile">
          <div class="p-icon">🟠</div>
          <div class="p-name">Swiggy</div>
          <div class="p-type">Instamart</div>
        </div>
        <div class="partner-tile">
          <div class="p-icon">🟡</div>
          <div class="p-name">Flipkart</div>
          <div class="p-type">Quick Commerce</div>
        </div>
        <div class="partner-tile">
          <div class="p-icon">🟢</div>
          <div class="p-name">Zepto</div>
          <div class="p-type">10-Minute Delivery</div>
        </div>
        <div class="partner-tile">
          <div class="p-icon">🔵</div>
          <div class="p-name">Amazon</div>
          <div class="p-type">Fresh & Pantry</div>
        </div>
        <div class="partner-tile">
          <div class="p-icon">🟣</div>
          <div class="p-name">Blinkit</div>
          <div class="p-type">Instant Delivery</div>
        </div>
      </div>
      <p class="partners-note reveal">🤝 Interested in stocking NowaNest? <a href="#contact" style="color:var(--leaf); font-weight:700; text-decoration:underline;">Become a retail partner →</a></p>
    </div>
  </section>

  <!-- ══════════ CONTACT ══════════ -->
  <section class="contact" id="contact">
    <div class="container">
      <div class="contact-card reveal">
        <div class="contact-inner">
          <div class="contact-info">
            <div class="section-tag">Say Hello</div>
            <h2>Let's Build<br>Something Together</h2>
            <p>Whether you're a customer, a retailer, or just curious about NowaNest — we'd love to hear from you.</p>
            <div class="contact-detail">
              <div class="cd-icon">📧</div>
              <div>
                <div class="cd-label">Email</div>
                <div class="cd-text">hello@nowanest.com</div>
              </div>
            </div>
            <div class="contact-detail">
              <div class="cd-icon">📱</div>
              <div>
                <div class="cd-label">Phone</div>
                <div class="cd-text">+91 98XXX XXXXX</div>
              </div>
            </div>
            <div class="contact-detail">
              <div class="cd-icon">📍</div>
              <div>
                <div class="cd-label">Based In</div>
                <div class="cd-text">India</div>
              </div>
            </div>
          </div>
          <form class="contact-form" onsubmit="event.preventDefault(); alert('Thank you! We will get back to you soon 🌿');">
            <div class="form-group">
              <label>Your Name</label>
              <input type="text" placeholder="Full name" required>
            </div>
            <div class="form-group">
              <label>Email Address</label>
              <input type="email" placeholder="you@example.com" required>
            </div>
            <div class="form-group">
              <label>Subject</label>
              <input type="text" placeholder="Partnership / Enquiry / Feedback">
            </div>
            <div class="form-group">
              <label>Message</label>
              <textarea placeholder="Tell us what's on your mind..."></textarea>
            </div>
            <button type="submit" class="btn-submit">Send Message →</button>
          </form>
        </div>
      </div>
    </div>
  </section>

  <!-- ══════════ FOOTER ══════════ -->
  <footer class="footer">
    <div class="container">
      <div class="footer-inner">
        <div class="footer-brand">
          <img src="images/logo-circle.png" alt="NowaNest">
          <span>NowaNest</span>
        </div>
        <div class="footer-copy">© 2025 NowaNest Natural Food. Made with 🤎 in India.</div>
        <div class="footer-social">
          <a href="#" title="Instagram">📸</a>
          <a href="#" title="Facebook">📘</a>
          <a href="#" title="Twitter">🐦</a>
        </div>
      </div>
    </div>
  </footer>

  <!-- ══════════ SCRIPTS ══════════ -->
  <script>
    // Navbar scroll effect
    const nav = document.getElementById('nav');
    window.addEventListener('scroll', () => {
      nav.classList.toggle('scrolled', window.scrollY > 50);
    });

    // Scroll reveal
    const revealObserver = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
        }
      });
    }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });

    document.querySelectorAll('.reveal').forEach(el => revealObserver.observe(el));

    // Simple mobile menu (toggle nav links visibility)
    const hamburger = document.getElementById('hamburger');
    const navLinks = document.querySelector('.nav-links');
    let menuOpen = false;

    hamburger.addEventListener('click', () => {
      menuOpen = !menuOpen;
      if (menuOpen) {
        navLinks.style.display = 'flex';
        navLinks.style.flexDirection = 'column';
        navLinks.style.position = 'absolute';
        navLinks.style.top = '100%';
        navLinks.style.left = '0';
        navLinks.style.right = '0';
        navLinks.style.background = 'rgba(250,247,240,0.97)';
        navLinks.style.backdropFilter = 'blur(16px)';
        navLinks.style.padding = '1.5rem';
        navLinks.style.gap = '1.25rem';
        navLinks.style.boxShadow = '0 12px 32px rgba(61,43,31,0.08)';
        navLinks.style.borderRadius = '0 0 20px 20px';
        navLinks.style.alignItems = 'center';
      } else {
        navLinks.style.display = '';
        navLinks.style.cssText = '';
      }
    });

    // Close mobile menu on link click
    navLinks.querySelectorAll('a').forEach(link => {
      link.addEventListener('click', () => {
        if (menuOpen) {
          menuOpen = false;
          navLinks.style.display = '';
          navLinks.style.cssText = '';
        }
      });
    });

    // Smooth scroll for anchor links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        const target = document.querySelector(this.getAttribute('href'));
        if (target) {
          e.preventDefault();
          target.scrollIntoView({ behavior: 'smooth' });
        }
      });
    });
  </script>

</body>
</html>
