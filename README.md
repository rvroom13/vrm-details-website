:root {
  --red: #D00000;
  --red-dark: #A00000;
  --red-glow: rgba(208, 0, 0, 0.35);
  --bg: #0A0A0A;
  --bg-card: #111111;
  --bg-card-hover: #1A1A1A;
  --white: #FFFFFF;
  --gray-100: #F0F0F0;
  --gray-300: #B0B0B0;
  --gray-500: #707070;
  --gray-700: #2A2A2A;
  --font-display: 'Bebas Neue', sans-serif;
  --font-body: 'Barlow', sans-serif;
}

html {
  scroll-behavior: smooth;
  scroll-padding-top: 70px;
}

body {
  font-family: var(--font-body);
  background: var(--bg);
  color: var(--gray-100);
  line-height: 1.6;
  overflow-x: hidden;
}

/* Noise texture overlay */
body::after {
  content: '';
  position: fixed;
  inset: 0;
  pointer-events: none;
  z-index: 9999;
  opacity: 0.03;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
  background-repeat: repeat;
  background-size: 256px 256px;
}

::selection {
  background: var(--red);
  color: var(--white);
}

img { max-width: 100%; display: block; }
a { text-decoration: none; color: inherit; }
ul { list-style: none; }

.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 24px;
}

/* ===== ANIMATIONS ===== */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(40px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes slideDown {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes pulse {
  0%, 100% { box-shadow: 0 0 0 0 var(--red-glow); }
  50% { box-shadow: 0 0 20px 5px var(--red-glow); }
}

.reveal {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}

.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}

.reveal-delay-1 { transition-delay: 0.1s; }
.reveal-delay-2 { transition-delay: 0.2s; }
.reveal-delay-3 { transition-delay: 0.3s; }
.reveal-delay-4 { transition-delay: 0.4s; }

/* ===== BUTTONS ===== */
.btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  font-family: var(--font-display);
  font-size: 1.15rem;
  letter-spacing: 2px;
  padding: 14px 36px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s ease;
  text-transform: uppercase;
}

.btn-primary {
  background: var(--red);
  color: var(--white);
  box-shadow: 0 4px 20px var(--red-glow);
}

.btn-primary:hover {
  background: var(--red-dark);
  transform: translateY(-2px);
  box-shadow: 0 6px 30px var(--red-glow);
}

.btn-outline {
  background: transparent;
  color: var(--white);
  border: 2px solid var(--red);
}

.btn-outline:hover {
  background: var(--red);
  transform: translateY(-2px);
}

/* ===== SECTION HEADING ===== */
.section-heading {
  text-align: center;
  margin-bottom: 60px;
}

.section-heading h2 {
  font-family: var(--font-display);
  font-size: clamp(2.2rem, 5vw, 3.5rem);
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--white);
  margin-bottom: 12px;
}

.section-heading .accent-line {
  width: 60px;
  height: 3px;
  background: var(--red);
  margin: 0 auto 20px;
}

.section-heading p {
  color: var(--gray-300);
  max-width: 600px;
  margin: 0 auto;
  font-size: 1.05rem;
  font-weight: 300;
}

section {
  padding: 100px 0;
}

/* ===== NAVBAR ===== */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 1000;
  padding: 20px 0;
  transition: all 0.4s ease;
}

.navbar.scrolled {
  background: rgba(10, 10, 10, 0.95);
  backdrop-filter: blur(12px);
  padding: 12px 0;
  box-shadow: 0 2px 30px rgba(0, 0, 0, 0.5);
}

.navbar .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.nav-logo {
  font-family: var(--font-display);
  font-size: 1.8rem;
  letter-spacing: 4px;
  color: var(--white);
  text-transform: uppercase;
}

.nav-logo span {
  color: var(--red);
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 32px;
}

.nav-links a {
  font-family: var(--font-body);
  font-size: 0.85rem;
  font-weight: 500;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: var(--gray-300);
  transition: color 0.3s ease;
  position: relative;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--red);
  transition: width 0.3s ease;
}

.nav-links a:hover,
.nav-links a.active {
  color: var(--white);
}

.nav-links a:hover::after,
.nav-links a.active::after {
  width: 100%;
}

.nav-cta {
  font-family: var(--font-display) !important;
  background: var(--red);
  color: var(--white) !important;
  padding: 8px 22px;
  border-radius: 3px;
  letter-spacing: 2px !important;
  font-size: 0.9rem !important;
  transition: all 0.3s ease !important;
}

.nav-cta::after { display: none !important; }

.nav-cta:hover {
  background: var(--red-dark) !important;
  color: var(--white) !important;
}

/* Mobile menu toggle */
.menu-toggle {
  display: none;
  flex-direction: column;
  gap: 5px;
  cursor: pointer;
  padding: 5px;
  z-index: 1001;
}

.menu-toggle span {
  display: block;
  width: 28px;
  height: 2px;
  background: var(--white);
  transition: all 0.3s ease;
  transform-origin: center;
}

.menu-toggle.open span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.menu-toggle.open span:nth-child(2) {
  opacity: 0;
}

.menu-toggle.open span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* ===== HERO ===== */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 120px 24px 80px;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  inset: 0;
  background:
    radial-gradient(ellipse at 20% 80%, rgba(208, 0, 0, 0.08) 0%, transparent 50%),
    radial-gradient(ellipse at 80% 20%, rgba(208, 0, 0, 0.05) 0%, transparent 50%),
    radial-gradient(ellipse at center, rgba(10, 10, 10, 0) 0%, var(--bg) 70%);
  z-index: 1;
}

/* Animated grid lines */
.hero-grid {
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(208, 0, 0, 0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(208, 0, 0, 0.04) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(ellipse at center, black 20%, transparent 70%);
  -webkit-mask-image: radial-gradient(ellipse at center, black 20%, transparent 70%);
}

.hero-content {
  position: relative;
  z-index: 2;
  animation: fadeUp 1s ease forwards;
}

.hero-badge {
  display: inline-block;
  font-family: var(--font-body);
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 4px;
  text-transform: uppercase;
  color: var(--red);
  border: 1px solid rgba(208, 0, 0, 0.3);
  padding: 8px 20px;
  margin-bottom: 30px;
  animation: fadeIn 1s ease 0.3s both;
}

.hero h1 {
  font-family: var(--font-display);
  font-size: clamp(4rem, 12vw, 9rem);
  letter-spacing: 8px;
  text-transform: uppercase;
  color: var(--white);
  line-height: 0.95;
  margin-bottom: 8px;
}

.hero h1 span {
  display: block;
  color: var(--red);
  font-size: 0.45em;
  letter-spacing: 12px;
}

.hero-tagline {
  font-size: clamp(1rem, 2.5vw, 1.3rem);
  color: var(--gray-300);
  font-weight: 300;
  margin-bottom: 40px;
  letter-spacing: 1px;
  animation: fadeIn 1s ease 0.5s both;
}

.hero-buttons {
  display: flex;
  gap: 16px;
  justify-content: center;
  flex-wrap: wrap;
  animation: fadeIn 1s ease 0.7s both;
}

.scroll-indicator {
  position: absolute;
  bottom: 30px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 2;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 8px;
  animation: fadeIn 1s ease 1.2s both;
}

.scroll-indicator span {
  font-size: 0.7rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--gray-500);
}

.scroll-line {
  width: 1px;
  height: 40px;
  background: linear-gradient(to bottom, var(--red), transparent);
  animation: pulse 2s ease infinite;
}

/* ===== ABOUT ===== */
#about {
  background: linear-gradient(180deg, var(--bg) 0%, #0D0D0D 100%);
}

.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.about-visual {
  position: relative;
  height: 400px;
  border-radius: 8px;
  overflow: hidden;
  background: var(--bg-card);
  border: 1px solid var(--gray-700);
}

.about-visual-inner {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background:
    radial-gradient(circle at 30% 50%, rgba(208, 0, 0, 0.1) 0%, transparent 50%),
    linear-gradient(135deg, #0F0F0F, #1A1A1A);
}

.about-visual-text {
  font-family: var(--font-display);
  font-size: 6rem;
  letter-spacing: 6px;
  color: rgba(208, 0, 0, 0.12);
  text-transform: uppercase;
  user-select: none;
}

.about-stats {
  display: flex;
  gap: 30px;
  margin-top: 30px;
}

.stat {
  text-align: center;
}

.stat-number {
  font-family: var(--font-display);
  font-size: 2.5rem;
  color: var(--red);
  letter-spacing: 2px;
}

.stat-label {
  font-size: 0.8rem;
  color: var(--gray-500);
  text-transform: uppercase;
  letter-spacing: 1px;
}

.about-text h3 {
  font-family: var(--font-display);
  font-size: 2rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 20px;
}

.about-text h3 span {
  color: var(--red);
}

.about-text p {
  color: var(--gray-300);
  font-weight: 300;
  margin-bottom: 16px;
  line-height: 1.8;
}

/* ===== SERVICES ===== */
#services {
  background: #0D0D0D;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 24px;
}

.service-card {
  background: var(--bg-card);
  border: 1px solid var(--gray-700);
  border-radius: 8px;
  padding: 36px 28px;
  transition: all 0.4s ease;
  position: relative;
  overflow: hidden;
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: var(--red);
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.4s ease;
}

.service-card:hover {
  background: var(--bg-card-hover);
  border-color: rgba(208, 0, 0, 0.3);
  transform: translateY(-4px);
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
}

.service-card:hover::before {
  transform: scaleX(1);
}

.service-icon {
  width: 48px;
  height: 48px;
  border-radius: 8px;
  background: rgba(208, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px;
}

.service-icon svg {
  width: 24px;
  height: 24px;
  stroke: var(--red);
  fill: none;
  stroke-width: 1.5;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.service-card h3 {
  font-family: var(--font-display);
  font-size: 1.4rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 8px;
  color: var(--white);
}

.service-card .service-subtitle {
  color: var(--gray-500);
  font-size: 0.85rem;
  font-weight: 300;
  margin-bottom: 18px;
}

.pricing-table {
  margin-bottom: 20px;
}

.pricing-row {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
}

.pricing-row:last-child {
  border-bottom: none;
}

.pricing-row .vehicle-type {
  color: var(--gray-300);
  font-size: 0.9rem;
  font-weight: 300;
}

.pricing-row .vehicle-price {
  font-family: var(--font-display);
  font-size: 1.2rem;
  color: var(--red);
  letter-spacing: 1px;
}

.service-card p {
  color: var(--gray-300);
  font-weight: 300;
  font-size: 0.95rem;
  line-height: 1.7;
}

.service-section-label {
  font-family: var(--font-display);
  font-size: 0.8rem;
  letter-spacing: 3px;
  color: var(--red);
  text-align: center;
  margin: 18px 0 10px;
  text-transform: uppercase;
}

.service-includes {
  margin-top: 0;
  padding-top: 0;
}

.service-includes li {
  color: var(--gray-300);
  font-size: 0.85rem;
  font-weight: 300;
  padding: 4px 0;
  display: flex;
  align-items: center;
  gap: 8px;
}

.service-includes li::before {
  content: '';
  width: 5px;
  height: 5px;
  background: var(--red);
  border-radius: 50%;
  flex-shrink: 0;
}

/* Popular badge */
.service-card.popular {
  border-color: rgba(208, 0, 0, 0.4);
}

.popular-badge {
  position: absolute;
  top: 16px;
  right: 16px;
  background: var(--red);
  color: var(--white);
  font-family: var(--font-display);
  font-size: 0.7rem;
  letter-spacing: 2px;
  padding: 4px 12px;
  border-radius: 3px;
  text-transform: uppercase;
}

/* Monthly badge */
.monthly-badge {
  position: absolute;
  top: 16px;
  right: 16px;
  background: #C8960E;
  color: var(--white);
  font-family: var(--font-display);
  font-size: 0.7rem;
  letter-spacing: 2px;
  padding: 4px 12px;
  border-radius: 3px;
  text-transform: uppercase;
}

.service-card.monthly {
  border-color: rgba(200, 150, 14, 0.4);
}

.service-card.monthly::before {
  background: #C8960E;
}

.service-note {
  margin-top: 16px;
  padding: 12px;
  background: rgba(200, 150, 14, 0.06);
  border: 1px solid rgba(200, 150, 14, 0.15);
  border-radius: 4px;
  color: var(--gray-300);
  font-size: 0.8rem;
  font-weight: 300;
  font-style: italic;
  line-height: 1.6;
}

/* Add-ons bar */
.addons-bar {
  margin-top: 40px;
  background: var(--bg-card);
  border: 1px solid var(--gray-700);
  border-radius: 8px;
  padding: 28px 32px;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 12px 32px;
}

.addons-bar h3 {
  font-family: var(--font-display);
  font-size: 1.1rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--white);
  margin-right: 8px;
}

.addon-chip {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 8px 16px;
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  font-size: 0.9rem;
  color: var(--gray-300);
  font-weight: 300;
}

.addon-chip .addon-price {
  font-family: var(--font-display);
  color: var(--red);
  font-size: 1rem;
  letter-spacing: 1px;
}

/* ===== WHY CHOOSE US ===== */
#why {
  background: var(--bg);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
}

.feature {
  text-align: center;
  padding: 40px 20px;
  border-radius: 8px;
  border: 1px solid transparent;
  transition: all 0.4s ease;
}

.feature:hover {
  border-color: var(--gray-700);
  background: var(--bg-card);
}

.feature-icon {
  width: 64px;
  height: 64px;
  border-radius: 50%;
  background: rgba(208, 0, 0, 0.08);
  border: 1px solid rgba(208, 0, 0, 0.2);
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 20px;
  transition: all 0.4s ease;
}

.feature:hover .feature-icon {
  background: rgba(208, 0, 0, 0.15);
  border-color: var(--red);
  transform: scale(1.05);
}

.feature-icon svg {
  width: 28px;
  height: 28px;
  stroke: var(--red);
  fill: none;
  stroke-width: 1.5;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.feature h3 {
  font-family: var(--font-display);
  font-size: 1.2rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 10px;
  color: var(--white);
}

.feature p {
  color: var(--gray-300);
  font-weight: 300;
  font-size: 0.9rem;
  line-height: 1.6;
}

/* ===== SERVICE AREA ===== */
#area {
  background: #0D0D0D;
}

.area-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: start;
}

.area-text h3 {
  font-family: var(--font-display);
  font-size: 1.8rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 16px;
}

.area-text p {
  color: var(--gray-300);
  font-weight: 300;
  line-height: 1.8;
  margin-bottom: 24px;
}

.area-list {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
}

.area-list li {
  display: flex;
  align-items: center;
  gap: 10px;
  color: var(--gray-300);
  font-weight: 300;
  font-size: 0.95rem;
}

.area-list li::before {
  content: '';
  width: 8px;
  height: 8px;
  border: 2px solid var(--red);
  border-radius: 50%;
  flex-shrink: 0;
}

.area-map-container {
  position: relative;
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid var(--gray-700);
}

.area-map-container iframe {
  display: block;
  width: 100%;
  height: 450px;
  border: 0;
  filter: grayscale(0.6) brightness(0.7) contrast(1.2);
  transition: filter 0.4s ease;
}

.area-map-container:hover iframe {
  filter: grayscale(0.3) brightness(0.8) contrast(1.1);
}

.area-map-label {
  position: absolute;
  top: 16px;
  left: 16px;
  background: rgba(10, 10, 10, 0.9);
  backdrop-filter: blur(8px);
  padding: 8px 16px;
  border-radius: 4px;
  border: 1px solid var(--gray-700);
  font-family: var(--font-display);
  font-size: 0.85rem;
  letter-spacing: 2px;
  color: var(--red);
  text-transform: uppercase;
  z-index: 2;
  pointer-events: none;
}

.area-legend {
  margin-top: 16px;
  display: flex;
  gap: 20px;
  flex-wrap: wrap;
}

.area-legend-item {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 0.8rem;
  color: var(--gray-300);
  font-weight: 300;
}

.area-legend-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  flex-shrink: 0;
}

.area-legend-dot.active { background: var(--red); }
.area-legend-dot.inactive { background: var(--gray-500); opacity: 0.5; }

/* ===== CONTACT / BOOK ===== */
#contact {
  background: var(--bg);
}

.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.2fr;
  gap: 60px;
  align-items: start;
}

.contact-info h3 {
  font-family: var(--font-display);
  font-size: 1.8rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 16px;
}

.contact-info > p {
  color: var(--gray-300);
  font-weight: 300;
  line-height: 1.8;
  margin-bottom: 30px;
}

.contact-detail {
  display: flex;
  align-items: center;
  gap: 16px;
  padding: 16px 0;
  border-bottom: 1px solid var(--gray-700);
}

.contact-detail:last-of-type {
  border-bottom: none;
}

.contact-detail-icon {
  width: 44px;
  height: 44px;
  border-radius: 8px;
  background: rgba(208, 0, 0, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.contact-detail-icon svg {
  width: 20px;
  height: 20px;
  stroke: var(--red);
  fill: none;
  stroke-width: 1.5;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.contact-detail-text {
  font-size: 0.85rem;
  color: var(--gray-500);
  text-transform: uppercase;
  letter-spacing: 1px;
}

.contact-detail-value {
  color: var(--white);
  font-weight: 500;
  font-size: 1.05rem;
}

.contact-detail a {
  transition: color 0.3s ease;
}

.contact-detail a:hover {
  color: var(--red);
}

/* Calendly embed in contact info */
.calendly-section {
  margin-top: 30px;
  padding-top: 24px;
  border-top: 1px solid var(--gray-700);
}

.calendly-section h4 {
  font-family: var(--font-display);
  font-size: 1.2rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--white);
  margin-bottom: 12px;
}

.calendly-section p {
  color: var(--gray-500);
  font-size: 0.85rem;
  font-weight: 300;
  margin-bottom: 16px;
}

.calendly-btn {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 24px;
  background: rgba(208, 0, 0, 0.1);
  border: 1px solid rgba(208, 0, 0, 0.3);
  border-radius: 4px;
  color: var(--red);
  font-family: var(--font-display);
  font-size: 1rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 0.3s ease;
}

.calendly-btn:hover {
  background: var(--red);
  color: var(--white);
}

.calendly-btn svg {
  width: 18px;
  height: 18px;
  stroke: currentColor;
  fill: none;
  stroke-width: 1.5;
}

/* Form */
.contact-form {
  background: var(--bg-card);
  border: 1px solid var(--gray-700);
  border-radius: 8px;
  padding: 40px;
}

.contact-form h3 {
  font-family: var(--font-display);
  font-size: 1.5rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 24px;
}

.form-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

.form-group {
  margin-bottom: 16px;
}

.form-group label {
  display: block;
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: var(--gray-300);
  margin-bottom: 8px;
}

.form-group input,
.form-group select,
.form-group textarea {
  width: 100%;
  background: var(--bg);
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  padding: 14px 16px;
  color: var(--white);
  font-family: var(--font-body);
  font-size: 0.95rem;
  transition: border-color 0.3s ease;
  outline: none;
}

.form-group input::placeholder,
.form-group textarea::placeholder {
  color: var(--gray-500);
}

.form-group input:focus,
.form-group select:focus,
.form-group textarea:focus {
  border-color: var(--red);
}

.form-group select {
  appearance: none;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' fill='%23707070' viewBox='0 0 16 16'%3E%3Cpath d='M8 11L3 6h10z'/%3E%3C/svg%3E");
  background-repeat: no-repeat;
  background-position: right 16px center;
  padding-right: 40px;
  cursor: pointer;
}

.form-group select option {
  background: var(--bg-card);
  color: var(--white);
}

.form-group textarea {
  resize: vertical;
  min-height: 100px;
}

/* ===== SEARCHABLE DROPDOWN ===== */
.search-select {
  position: relative;
}

.search-select-trigger {
  width: 100%;
  background: var(--bg);
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  padding: 14px 40px 14px 16px;
  color: var(--white);
  font-family: var(--font-body);
  font-size: 0.95rem;
  cursor: pointer;
  transition: border-color 0.3s ease;
  outline: none;
  text-align: left;
  position: relative;
}

.search-select-trigger::after {
  content: '';
  position: absolute;
  right: 16px;
  top: 50%;
  transform: translateY(-50%);
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 6px solid var(--gray-500);
  transition: transform 0.3s ease;
}

.search-select-trigger.open::after {
  transform: translateY(-50%) rotate(180deg);
}

.search-select-trigger:focus,
.search-select.open .search-select-trigger {
  border-color: var(--red);
}

.search-select-trigger .placeholder {
  color: var(--gray-500);
}

.search-select-dropdown {
  display: none;
  position: absolute;
  top: calc(100% + 4px);
  left: 0;
  right: 0;
  background: var(--bg-card);
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  max-height: 240px;
  overflow: hidden;
  z-index: 100;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
}

.search-select.open .search-select-dropdown {
  display: block;
}

.search-select-search {
  width: 100%;
  padding: 12px 16px;
  background: var(--bg);
  border: none;
  border-bottom: 1px solid var(--gray-700);
  color: var(--white);
  font-family: var(--font-body);
  font-size: 0.9rem;
  outline: none;
}

.search-select-search::placeholder {
  color: var(--gray-500);
}

.search-select-options {
  max-height: 190px;
  overflow-y: auto;
}

.search-select-options::-webkit-scrollbar {
  width: 6px;
}

.search-select-options::-webkit-scrollbar-track {
  background: var(--bg-card);
}

.search-select-options::-webkit-scrollbar-thumb {
  background: var(--gray-700);
  border-radius: 3px;
}

.search-select-option {
  padding: 10px 16px;
  cursor: pointer;
  font-size: 0.9rem;
  color: var(--gray-300);
  transition: background 0.2s ease, color 0.2s ease;
}

.search-select-option:hover {
  background: rgba(208, 0, 0, 0.1);
  color: var(--white);
}

.search-select-option.selected {
  color: var(--red);
  font-weight: 500;
}

.search-select-option.hidden {
  display: none;
}

/* ===== MULTI-SELECT ADDONS ===== */
.multi-select {
  position: relative;
}

.multi-select-trigger {
  width: 100%;
  background: var(--bg);
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  padding: 10px 40px 10px 12px;
  min-height: 48px;
  cursor: pointer;
  transition: border-color 0.3s ease;
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  align-items: center;
  position: relative;
}

.multi-select-trigger::after {
  content: '';
  position: absolute;
  right: 16px;
  top: 50%;
  transform: translateY(-50%);
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-top: 6px solid var(--gray-500);
  transition: transform 0.3s ease;
}

.multi-select.open .multi-select-trigger::after {
  transform: translateY(-50%) rotate(180deg);
}

.multi-select.open .multi-select-trigger,
.multi-select-trigger:focus {
  border-color: var(--red);
}

.multi-select-trigger .placeholder {
  color: var(--gray-500);
  font-size: 0.95rem;
  font-family: var(--font-body);
}

.multi-select-tag {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  background: rgba(208, 0, 0, 0.15);
  border: 1px solid rgba(208, 0, 0, 0.3);
  color: var(--white);
  font-size: 0.8rem;
  padding: 4px 10px;
  border-radius: 3px;
  font-family: var(--font-body);
}

.multi-select-tag .remove-tag {
  cursor: pointer;
  font-size: 1rem;
  line-height: 1;
  color: var(--gray-300);
  transition: color 0.2s ease;
}

.multi-select-tag .remove-tag:hover {
  color: var(--red);
}

.multi-select-dropdown {
  display: none;
  position: absolute;
  top: calc(100% + 4px);
  left: 0;
  right: 0;
  background: var(--bg-card);
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  max-height: 220px;
  overflow-y: auto;
  z-index: 100;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.4);
}

.multi-select.open .multi-select-dropdown {
  display: block;
}

.multi-select-option {
  padding: 10px 16px;
  cursor: pointer;
  font-size: 0.9rem;
  color: var(--gray-300);
  transition: background 0.2s ease, color 0.2s ease;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.multi-select-option:hover {
  background: rgba(208, 0, 0, 0.1);
  color: var(--white);
}

.multi-select-option.selected {
  color: var(--red);
  background: rgba(208, 0, 0, 0.05);
}

.multi-select-option .addon-price-tag {
  font-family: var(--font-display);
  color: var(--red);
  font-size: 0.9rem;
  letter-spacing: 1px;
}

/* ===== CALENDAR PICKER ===== */
.calendar-picker {
  background: var(--bg);
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  padding: 16px;
  transition: border-color 0.3s ease;
}

.calendar-picker:focus-within {
  border-color: var(--red);
}

.calendar-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}

.calendar-header h4 {
  font-family: var(--font-display);
  font-size: 1.1rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--white);
}

.calendar-nav {
  display: flex;
  gap: 8px;
}

.calendar-nav button {
  background: rgba(208, 0, 0, 0.1);
  border: 1px solid rgba(208, 0, 0, 0.2);
  color: var(--red);
  width: 32px;
  height: 32px;
  border-radius: 4px;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.1rem;
  transition: all 0.2s ease;
}

.calendar-nav button:hover {
  background: var(--red);
  color: var(--white);
}

.calendar-weekdays {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 4px;
  margin-bottom: 8px;
}

.calendar-weekdays span {
  text-align: center;
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: var(--gray-500);
  padding: 4px;
}

.calendar-days {
  display: grid;
  grid-template-columns: repeat(7, 1fr);
  gap: 4px;
}

.calendar-day {
  text-align: center;
  padding: 8px 4px;
  font-size: 0.85rem;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.2s ease;
  color: var(--gray-300);
  background: transparent;
  border: 1px solid transparent;
}

.calendar-day:hover:not(.disabled):not(.empty) {
  background: rgba(208, 0, 0, 0.15);
  border-color: rgba(208, 0, 0, 0.3);
  color: var(--white);
}

.calendar-day.selected {
  background: var(--red);
  color: var(--white);
  font-weight: 600;
}

.calendar-day.today {
  border-color: var(--red);
}

.calendar-day.disabled {
  color: var(--gray-700);
  cursor: not-allowed;
}

.calendar-day.empty {
  cursor: default;
}

.time-slots {
  margin-top: 16px;
  padding-top: 16px;
  border-top: 1px solid var(--gray-700);
}

.time-slots-label {
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  color: var(--gray-300);
  margin-bottom: 10px;
}

.time-slots-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(90px, 1fr));
  gap: 8px;
}

.time-slot {
  padding: 8px 4px;
  text-align: center;
  font-size: 0.8rem;
  color: var(--gray-300);
  border: 1px solid var(--gray-700);
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.2s ease;
}

.time-slot:hover {
  border-color: rgba(208, 0, 0, 0.4);
  background: rgba(208, 0, 0, 0.1);
  color: var(--white);
}

.time-slot.selected {
  background: var(--red);
  border-color: var(--red);
  color: var(--white);
  font-weight: 500;
}

.time-slot.disabled {
  color: var(--gray-700);
  cursor: not-allowed;
  border-color: rgba(42, 42, 42, 0.5);
}

.calendar-availability-note {
  margin-top: 12px;
  font-size: 0.75rem;
  color: var(--gray-500);
  font-weight: 300;
  line-height: 1.6;
}

/* ===== REQUIRED CHECKBOX ===== */
.form-checkbox {
  display: flex;
  align-items: flex-start;
  gap: 12px;
  margin-bottom: 20px;
  cursor: pointer;
}

.form-checkbox input[type="checkbox"] {
  width: 20px;
  height: 20px;
  min-width: 20px;
  accent-color: var(--red);
  cursor: pointer;
  margin-top: 2px;
}

.form-checkbox label {
  font-size: 0.9rem;
  color: var(--gray-300);
  font-weight: 400;
  cursor: pointer;
  line-height: 1.5;
  letter-spacing: 0;
  text-transform: none;
  margin-bottom: 0;
}

.form-checkbox label .required-star {
  color: var(--red);
  font-weight: 700;
}

/* ===== FORM SUMMARY MODAL ===== */
.summary-overlay {
  display: none;
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.85);
  backdrop-filter: blur(8px);
  z-index: 2000;
  align-items: center;
  justify-content: center;
  padding: 24px;
}

.summary-overlay.active {
  display: flex;
}

.summary-modal {
  background: var(--bg-card);
  border: 1px solid var(--gray-700);
  border-radius: 8px;
  padding: 36px;
  max-width: 520px;
  width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  animation: fadeUp 0.3s ease;
}

.summary-modal h3 {
  font-family: var(--font-display);
  font-size: 1.5rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--white);
  margin-bottom: 24px;
  text-align: center;
}

.summary-row {
  display: flex;
  justify-content: space-between;
  padding: 12px 0;
  border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  gap: 16px;
}

.summary-row:last-of-type {
  border-bottom: none;
}

.summary-label {
  font-size: 0.8rem;
  font-weight: 600;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: var(--gray-500);
  flex-shrink: 0;
}

.summary-value {
  color: var(--white);
  font-size: 0.95rem;
  text-align: right;
  word-break: break-word;
}

.summary-buttons {
  display: flex;
  gap: 12px;
  margin-top: 28px;
}

.summary-buttons button {
  flex: 1;
  padding: 14px 20px;
  border-radius: 4px;
  font-family: var(--font-display);
  font-size: 1rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  cursor: pointer;
  transition: all 0.3s ease;
}

.btn-back {
  background: transparent;
  border: 1px solid var(--gray-700);
  color: var(--gray-300);
}

.btn-back:hover {
  border-color: var(--white);
  color: var(--white);
}

.btn-confirm {
  background: var(--red);
  border: none;
  color: var(--white);
  box-shadow: 0 4px 20px var(--red-glow);
}

.btn-confirm:hover {
  background: var(--red-dark);
}

.form-submit {
  width: 100%;
  font-family: var(--font-display);
  font-size: 1.1rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  padding: 16px;
  background: var(--red);
  color: var(--white);
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: 8px;
}

.form-submit:hover {
  background: var(--red-dark);
  box-shadow: 0 4px 20px var(--red-glow);
}

/* ===== FOOTER ===== */
.footer {
  background: #050505;
  border-top: 1px solid var(--gray-700);
  padding: 60px 0 30px;
}

.footer-grid {
  display: grid;
  grid-template-columns: 2fr 1fr 1fr;
  gap: 40px;
  margin-bottom: 40px;
}

.footer-brand .nav-logo {
  margin-bottom: 16px;
  display: inline-block;
}

.footer-brand p {
  color: var(--gray-500);
  font-weight: 300;
  font-size: 0.95rem;
  line-height: 1.7;
  max-width: 350px;
}

.footer-social {
  display: flex;
  gap: 12px;
  margin-top: 20px;
}

.footer-social a {
  width: 40px;
  height: 40px;
  border-radius: 8px;
  border: 1px solid var(--gray-700);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
}

.footer-social a:hover {
  border-color: var(--red);
  background: rgba(208, 0, 0, 0.1);
}

.footer-social a svg {
  width: 18px;
  height: 18px;
  fill: var(--gray-300);
  transition: fill 0.3s ease;
}

.footer-social a:hover svg {
  fill: var(--red);
}

.footer-col h4 {
  font-family: var(--font-display);
  font-size: 1rem;
  letter-spacing: 2px;
  text-transform: uppercase;
  color: var(--white);
  margin-bottom: 20px;
}

.footer-col a {
  display: block;
  color: var(--gray-500);
  font-weight: 300;
  font-size: 0.9rem;
  padding: 5px 0;
  transition: color 0.3s ease;
}

.footer-col a:hover {
  color: var(--red);
}

.footer-bottom {
  border-top: 1px solid var(--gray-700);
  padding-top: 24px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.footer-bottom p {
  color: var(--gray-500);
  font-size: 0.85rem;
  font-weight: 300;
}

/* ===== MOBILE RESPONSIVE ===== */
@media (max-width: 1024px) {
  .features-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 768px) {
  section { padding: 70px 0; }

  .menu-toggle { display: flex; }

  .nav-links {
    position: fixed;
    inset: 0;
    background: rgba(10, 10, 10, 0.98);
    backdrop-filter: blur(20px);
    flex-direction: column;
    justify-content: center;
    gap: 28px;
    opacity: 0;
    visibility: hidden;
    transition: all 0.4s ease;
  }

  .nav-links.open {
    opacity: 1;
    visibility: visible;
  }

  .nav-links a {
    font-size: 1.2rem;
    letter-spacing: 3px;
  }

  .about-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .about-visual { height: 250px; }

  .about-stats {
    justify-content: center;
  }

  .services-grid {
    grid-template-columns: 1fr;
    max-width: 400px;
    margin: 0 auto;
  }

  .features-grid {
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .feature { padding: 24px 12px; }

  .area-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .area-map-container iframe { height: 300px; }

  .contact-grid {
    grid-template-columns: 1fr;
    gap: 40px;
  }

  .contact-form { padding: 28px 20px; }

  .form-row { grid-template-columns: 1fr; }

  .footer-grid {
    grid-template-columns: 1fr;
    gap: 30px;
  }

  .footer-bottom {
    flex-direction: column;
    gap: 8px;
    text-align: center;
  }

  .hero h1 {
    letter-spacing: 4px;
  }

  .summary-modal { padding: 24px 16px; }
  .summary-buttons { flex-direction: column; }
}

@media (max-width: 480px) {
  .features-grid {
    grid-template-columns: 1fr;
  }

  .area-list {
    grid-template-columns: 1fr;
  }

  .about-stats {
    flex-direction: column;
    align-items: center;
  }

  .time-slots-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
