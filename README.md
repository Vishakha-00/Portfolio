<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Vishakha Dhiman — Portfolio</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
:root {
  --bg: #050810;
  --bg2: #080d1a;
  --surface: rgba(255,255,255,0.04);
  --surface2: rgba(255,255,255,0.07);
  --border: rgba(255,255,255,0.08);
  --border2: rgba(120,160,255,0.2);
  --cyan: #00d4ff;
  --blue: #4f7cff;
  --violet: #9b5dff;
  --pink: #ff5fa0;
  --text: #e8eaf5;
  --muted: #7a80a0;
  --font-display: 'Syne', sans-serif;
  --font-body: 'DM Sans', sans-serif;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--font-body);
  font-size: 16px;
  line-height: 1.6;
  overflow-x: hidden;
}

/* ── LOADER ── */
#loader {
  position: fixed; inset: 0; z-index: 9999;
  background: var(--bg);
  display: flex; flex-direction: column; align-items: center; justify-content: center;
  transition: opacity .6s ease, visibility .6s ease;
}
#loader.hide { opacity: 0; visibility: hidden; }
.loader-ring {
  width: 64px; height: 64px;
  border: 3px solid var(--border);
  border-top-color: var(--cyan);
  border-radius: 50%;
  animation: spin 1s linear infinite;
}
.loader-text {
  margin-top: 20px;
  font-family: var(--font-display);
  font-size: 13px;
  letter-spacing: .3em;
  color: var(--muted);
  text-transform: uppercase;
}
@keyframes spin { to { transform: rotate(360deg); } }

/* ── CANVAS BG ── */
#canvas-bg {
  position: fixed; inset: 0; z-index: 0;
  pointer-events: none;
}

/* ── SCROLL REVEAL ── */
.reveal {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity .8s cubic-bezier(.22,1,.36,1), transform .8s cubic-bezier(.22,1,.36,1);
}
.reveal.visible { opacity: 1; transform: none; }
.reveal-left { opacity: 0; transform: translateX(-40px); transition: opacity .8s cubic-bezier(.22,1,.36,1), transform .8s cubic-bezier(.22,1,.36,1); }
.reveal-left.visible { opacity: 1; transform: none; }
.reveal-right { opacity: 0; transform: translateX(40px); transition: opacity .8s cubic-bezier(.22,1,.36,1), transform .8s cubic-bezier(.22,1,.36,1); }
.reveal-right.visible { opacity: 1; transform: none; }
.delay-1 { transition-delay: .1s; }
.delay-2 { transition-delay: .2s; }
.delay-3 { transition-delay: .3s; }
.delay-4 { transition-delay: .4s; }
.delay-5 { transition-delay: .5s; }

/* ── NAVBAR ── */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  padding: 0 5%;
  height: 70px;
  display: flex; align-items: center; justify-content: space-between;
  background: rgba(5,8,16,.7);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
  transition: background .3s;
}
.nav-logo {
  font-family: var(--font-display);
  font-size: 22px;
  font-weight: 800;
  background: linear-gradient(135deg, var(--cyan), var(--violet));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -.02em;
}
.nav-links {
  display: flex; gap: 2rem; list-style: none;
}
.nav-links a {
  color: var(--muted);
  text-decoration: none;
  font-size: 14px;
  font-weight: 500;
  letter-spacing: .03em;
  transition: color .3s;
  position: relative;
}
.nav-links a::after {
  content: '';
  position: absolute; bottom: -4px; left: 0; right: 0;
  height: 1px;
  background: var(--cyan);
  transform: scaleX(0);
  transition: transform .3s;
}
.nav-links a:hover { color: var(--text); }
.nav-links a:hover::after { transform: scaleX(1); }
.nav-toggle {
  display: none;
  flex-direction: column; gap: 5px;
  cursor: pointer; background: none; border: none;
}
.nav-toggle span {
  display: block; width: 24px; height: 2px;
  background: var(--text);
  border-radius: 2px;
  transition: transform .3s, opacity .3s;
}

/* ── MAIN WRAPPER ── */
main { position: relative; z-index: 1; }

/* ── SECTION BASE ── */
section {
  padding: 100px 5%;
  position: relative;
}
.section-label {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: .25em;
  text-transform: uppercase;
  color: var(--cyan);
  margin-bottom: 12px;
}
.section-title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -.02em;
  margin-bottom: 16px;
}
.section-sub {
  color: var(--muted);
  font-size: 16px;
  max-width: 540px;
  margin-bottom: 60px;
  font-weight: 300;
}

/* ── GLOW DIVIDER ── */
.glow-divider {
  width: 100%; height: 1px;
  background: linear-gradient(90deg, transparent, var(--blue), var(--violet), transparent);
  margin: 0;
  opacity: .4;
}

/* ── HERO ── */
#hero {
  min-height: 100vh;
  display: flex; align-items: center;
  padding-top: 70px;
  overflow: hidden;
  position: relative;
}
.hero-inner {
  display: grid;
  grid-template-columns: 1fr auto;
  gap: 60px;
  align-items: center;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
.hero-badge {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 6px 16px;
  border: 1px solid var(--border2);
  border-radius: 100px;
  font-size: 12px;
  font-weight: 500;
  color: var(--cyan);
  background: rgba(0,212,255,.06);
  margin-bottom: 24px;
  animation: fadeDown .8s ease both;
}
.hero-badge-dot {
  width: 6px; height: 6px;
  border-radius: 50%;
  background: var(--cyan);
  animation: pulse 2s ease infinite;
}
@keyframes pulse {
  0%,100% { opacity: 1; transform: scale(1); }
  50% { opacity: .4; transform: scale(1.4); }
}
.hero-name {
  font-family: var(--font-display);
  font-size: clamp(3rem, 7vw, 5.5rem);
  font-weight: 800;
  line-height: .95;
  letter-spacing: -.04em;
  margin-bottom: 16px;
  animation: fadeUp .9s ease .1s both;
}
.hero-name .highlight {
  background: linear-gradient(135deg, var(--cyan) 0%, var(--violet) 60%, var(--pink) 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.hero-role {
  font-size: clamp(1rem, 2.5vw, 1.3rem);
  color: var(--muted);
  font-weight: 300;
  margin-bottom: 12px;
  animation: fadeUp .9s ease .2s both;
}
.hero-typing {
  font-family: var(--font-display);
  font-size: clamp(1.2rem, 2.5vw, 1.6rem);
  font-weight: 700;
  min-height: 1.8em;
  margin-bottom: 32px;
  animation: fadeUp .9s ease .3s both;
}
.hero-typing .cursor {
  display: inline-block;
  width: 3px; height: 1.1em;
  background: var(--cyan);
  margin-left: 4px;
  vertical-align: text-bottom;
  animation: blink .9s step-end infinite;
}
@keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: 0; } }
.hero-desc {
  color: var(--muted);
  font-size: 15px;
  font-weight: 300;
  max-width: 480px;
  margin-bottom: 40px;
  line-height: 1.8;
  animation: fadeUp .9s ease .4s both;
}
.hero-ctas {
  display: flex; gap: 16px; flex-wrap: wrap;
  animation: fadeUp .9s ease .5s both;
}
.btn {
  display: inline-flex; align-items: center; gap: 8px;
  padding: 12px 28px;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: transform .25s, box-shadow .25s, background .25s;
  text-decoration: none;
  border: none;
  letter-spacing: .02em;
  font-family: var(--font-body);
}
.btn-primary {
  background: linear-gradient(135deg, var(--cyan), var(--blue));
  color: #fff;
  box-shadow: 0 4px 30px rgba(79,124,255,.35);
}
.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 40px rgba(79,124,255,.55);
}
.btn-outline {
  background: var(--surface);
  color: var(--text);
  border: 1px solid var(--border2);
}
.btn-outline:hover {
  background: var(--surface2);
  transform: translateY(-2px);
  border-color: var(--cyan);
  color: var(--cyan);
}
.hero-avatar-wrap {
  position: relative;
  animation: fadeLeft .9s ease .3s both;
}
.hero-avatar-ring {
  width: 300px; height: 300px;
  border-radius: 50%;
  position: relative;
}
.hero-avatar-ring::before {
  content: '';
  position: absolute; inset: -4px;
  border-radius: 50%;
  background: conic-gradient(var(--cyan), var(--violet), var(--pink), var(--cyan));
  animation: spin 6s linear infinite;
  z-index: -1;
}
.hero-avatar-ring::after {
  content: '';
  position: absolute; inset: -20px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(0,212,255,.15), transparent 70%);
}
.hero-avatar {
  width: 300px; height: 300px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--bg2), #0d1530);
  border: 3px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  overflow: hidden;
  position: relative;
}
.avatar-initial {
  font-family: var(--font-display);
  font-size: 96px;
  font-weight: 800;
  background: linear-gradient(135deg, var(--cyan), var(--violet));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1;
}
.hero-scroll {
  position: absolute;
  bottom: 36px; left: 50%;
  transform: translateX(-50%);
  display: flex; flex-direction: column; align-items: center; gap: 8px;
  animation: fadeUp 1s ease 1.2s both;
}
.hero-scroll span {
  font-size: 11px;
  letter-spacing: .2em;
  color: var(--muted);
  text-transform: uppercase;
}
.scroll-line {
  width: 1px; height: 40px;
  background: linear-gradient(to bottom, var(--muted), transparent);
  animation: scrollPulse 2s ease infinite;
}
@keyframes scrollPulse {
  0%,100% { opacity: .3; transform: scaleY(1); }
  50% { opacity: 1; transform: scaleY(1.2); }
}
@keyframes fadeUp { from { opacity:0; transform:translateY(30px); } to { opacity:1; transform:none; } }
@keyframes fadeDown { from { opacity:0; transform:translateY(-20px); } to { opacity:1; transform:none; } }
@keyframes fadeLeft { from { opacity:0; transform:translateX(40px); } to { opacity:1; transform:none; } }

/* ── ABOUT ── */
#about { background: var(--bg2); }
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 80px;
  align-items: start;
  max-width: 1200px;
  margin: 0 auto;
}
.about-body {
  color: var(--muted);
  font-size: 15px;
  font-weight: 300;
  line-height: 1.9;
  margin-bottom: 24px;
}
.about-stats {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-top: 40px;
}
.stat-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 24px 20px;
  text-align: center;
  transition: border-color .3s, transform .3s, box-shadow .3s;
}
.stat-card:hover {
  border-color: var(--blue);
  transform: translateY(-4px);
  box-shadow: 0 8px 40px rgba(79,124,255,.15);
}
.stat-number {
  font-family: var(--font-display);
  font-size: 2rem;
  font-weight: 800;
  background: linear-gradient(135deg, var(--cyan), var(--violet));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  display: block;
}
.stat-label {
  font-size: 12px;
  color: var(--muted);
  font-weight: 400;
  margin-top: 4px;
}
.objective-card {
  background: var(--surface);
  border: 1px solid var(--border2);
  border-radius: 20px;
  padding: 32px;
  position: relative;
  overflow: hidden;
}
.objective-card::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--cyan), var(--violet));
}
.objective-title {
  font-family: var(--font-display);
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 16px;
  color: var(--text);
}
.objective-text {
  color: var(--muted);
  font-size: 14px;
  line-height: 1.8;
  font-weight: 300;
}
.info-list {
  margin-top: 28px;
  display: flex;
  flex-direction: column;
  gap: 14px;
}
.info-item {
  display: flex; align-items: center; gap: 14px;
  font-size: 14px;
  color: var(--muted);
}
.info-item i {
  color: var(--cyan);
  width: 20px;
  font-size: 14px;
}
.info-item a { color: var(--muted); text-decoration: none; }
.info-item a:hover { color: var(--cyan); }

/* ── SKILLS ── */
#skills {
  max-width: 1200px;
  margin: 0 auto;
  padding: 100px 5%;
}
.skills-container { max-width: 1200px; margin: 0 auto; }
.skills-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
}
.skills-col-title {
  font-family: var(--font-display);
  font-size: 16px;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 28px;
  display: flex; align-items: center; gap: 10px;
}
.skills-col-title i { color: var(--cyan); }
.skill-item { margin-bottom: 24px; }
.skill-info {
  display: flex; justify-content: space-between;
  margin-bottom: 8px;
}
.skill-name {
  font-size: 14px;
  font-weight: 500;
  color: var(--text);
}
.skill-pct {
  font-size: 13px;
  font-weight: 600;
  color: var(--cyan);
  font-family: var(--font-display);
}
.skill-bar-bg {
  height: 6px;
  background: var(--surface2);
  border-radius: 100px;
  overflow: hidden;
}
.skill-bar-fill {
  height: 100%;
  border-radius: 100px;
  background: linear-gradient(90deg, var(--cyan), var(--violet));
  width: 0;
  transition: width 1.2s cubic-bezier(.22,1,.36,1);
  box-shadow: 0 0 12px rgba(0,212,255,.5);
}
.tools-grid {
  margin-top: 60px;
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
}
.tool-chip {
  padding: 8px 18px;
  border: 1px solid var(--border);
  border-radius: 100px;
  font-size: 13px;
  font-weight: 500;
  color: var(--muted);
  background: var(--surface);
  transition: border-color .3s, color .3s, background .3s, transform .3s, box-shadow .3s;
  cursor: default;
}
.tool-chip:hover {
  border-color: var(--cyan);
  color: var(--cyan);
  background: rgba(0,212,255,.06);
  transform: translateY(-2px);
  box-shadow: 0 4px 20px rgba(0,212,255,.15);
}

/* ── PROJECTS ── */
#projects { background: var(--bg2); }
.projects-container { max-width: 1200px; margin: 0 auto; }
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}
.project-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 20px;
  overflow: hidden;
  transition: border-color .3s, transform .4s cubic-bezier(.22,1,.36,1), box-shadow .4s;
  position: relative;
}
.project-card:hover {
  border-color: rgba(79,124,255,.5);
  transform: translateY(-8px);
  box-shadow: 0 20px 60px rgba(0,0,0,.4), 0 0 40px rgba(79,124,255,.12);
}
.project-thumb {
  width: 100%; height: 180px;
  position: relative;
  overflow: hidden;
}
.project-thumb-inner {
  width: 100%; height: 100%;
  display: flex; align-items: center; justify-content: center;
  font-size: 52px;
  transition: transform .5s ease;
}
.project-card:hover .project-thumb-inner { transform: scale(1.08); }
.project-body { padding: 24px; }
.project-name {
  font-family: var(--font-display);
  font-size: 17px;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 10px;
}
.project-desc {
  font-size: 13px;
  color: var(--muted);
  line-height: 1.7;
  font-weight: 300;
  margin-bottom: 16px;
}
.project-tags {
  display: flex; flex-wrap: wrap; gap: 8px;
  margin-bottom: 20px;
}
.tag {
  padding: 4px 12px;
  border-radius: 100px;
  font-size: 11px;
  font-weight: 600;
  letter-spacing: .04em;
  background: rgba(79,124,255,.12);
  color: var(--blue);
  border: 1px solid rgba(79,124,255,.2);
}
.project-links {
  display: flex; gap: 12px;
}
.project-link {
  display: inline-flex; align-items: center; gap: 6px;
  font-size: 13px;
  font-weight: 500;
  color: var(--muted);
  text-decoration: none;
  transition: color .3s;
}
.project-link:hover { color: var(--cyan); }

/* ── EXPERIENCE / TIMELINE ── */
#experience { max-width: 1200px; margin: 0 auto; padding: 100px 5%; }
.timeline {
  position: relative;
  padding-left: 40px;
  max-width: 800px;
  margin: 0 auto;
}
.timeline::before {
  content: '';
  position: absolute;
  left: 0; top: 0; bottom: 0;
  width: 1px;
  background: linear-gradient(to bottom, var(--cyan), var(--violet), transparent);
}
.tl-item {
  position: relative;
  margin-bottom: 40px;
  animation: fadeUp .8s ease both;
}
.tl-dot {
  position: absolute;
  left: -47px; top: 4px;
  width: 14px; height: 14px;
  border-radius: 50%;
  background: var(--bg);
  border: 2px solid var(--cyan);
  box-shadow: 0 0 12px var(--cyan);
  transition: transform .3s;
}
.tl-item:hover .tl-dot { transform: scale(1.4); }
.tl-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 18px;
  padding: 28px 32px;
  position: relative;
  overflow: hidden;
  transition: border-color .3s, box-shadow .3s;
}
.tl-card:hover {
  border-color: var(--border2);
  box-shadow: 0 0 30px rgba(79,124,255,.1);
}
.tl-card::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, var(--cyan), transparent);
  opacity: 0;
  transition: opacity .3s;
}
.tl-card:hover::before { opacity: 1; }
.tl-meta {
  display: flex; gap: 12px; flex-wrap: wrap;
  margin-bottom: 8px;
}
.tl-badge {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: .06em;
  text-transform: uppercase;
  color: var(--cyan);
  background: rgba(0,212,255,.08);
  padding: 4px 12px;
  border-radius: 100px;
  border: 1px solid rgba(0,212,255,.2);
}
.tl-date {
  font-size: 12px;
  color: var(--muted);
  font-weight: 400;
  display: flex; align-items: center; gap: 6px;
}
.tl-title {
  font-family: var(--font-display);
  font-size: 18px;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 4px;
}
.tl-org {
  font-size: 14px;
  color: var(--violet);
  font-weight: 500;
  margin-bottom: 12px;
}
.tl-desc {
  font-size: 13px;
  color: var(--muted);
  line-height: 1.8;
  font-weight: 300;
}

/* ── CERTIFICATIONS ── */
#certifications { background: var(--bg2); }
.cert-container { max-width: 1200px; margin: 0 auto; }
.cert-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}
.cert-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 18px;
  padding: 28px 24px;
  position: relative;
  overflow: hidden;
  transition: border-color .3s, transform .4s, box-shadow .4s;
  cursor: default;
}
.cert-card:hover {
  border-color: rgba(155,93,255,.4);
  transform: translateY(-6px);
  box-shadow: 0 16px 50px rgba(0,0,0,.3), 0 0 30px rgba(155,93,255,.1);
}
.cert-icon {
  font-size: 28px;
  margin-bottom: 16px;
}
.cert-title {
  font-family: var(--font-display);
  font-size: 15px;
  font-weight: 700;
  color: var(--text);
  margin-bottom: 8px;
}
.cert-issuer {
  font-size: 13px;
  color: var(--violet);
  font-weight: 500;
  margin-bottom: 6px;
}
.cert-date {
  font-size: 12px;
  color: var(--muted);
}
.cert-glow {
  position: absolute;
  top: -40px; right: -40px;
  width: 120px; height: 120px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(155,93,255,.18), transparent 70%);
  pointer-events: none;
}

/* ── CONTACT ── */
#contact { max-width: 1200px; margin: 0 auto; padding: 100px 5%; }
.contact-grid {
  display: grid;
  grid-template-columns: 1fr 1.6fr;
  gap: 60px;
}
.contact-info { display: flex; flex-direction: column; gap: 24px; }
.contact-info-item {
  display: flex; align-items: flex-start; gap: 16px;
}
.contact-icon-box {
  width: 44px; height: 44px;
  border-radius: 12px;
  background: var(--surface);
  border: 1px solid var(--border2);
  display: flex; align-items: center; justify-content: center;
  color: var(--cyan);
  font-size: 16px;
  flex-shrink: 0;
  transition: background .3s, box-shadow .3s;
}
.contact-info-item:hover .contact-icon-box {
  background: rgba(0,212,255,.1);
  box-shadow: 0 0 20px rgba(0,212,255,.2);
}
.contact-info-label {
  font-size: 12px;
  font-weight: 600;
  letter-spacing: .1em;
  text-transform: uppercase;
  color: var(--muted);
  margin-bottom: 4px;
}
.contact-info-value {
  font-size: 14px;
  color: var(--text);
  font-weight: 400;
}
.contact-info-value a { color: var(--text); text-decoration: none; }
.contact-info-value a:hover { color: var(--cyan); }
.socials {
  display: flex; gap: 12px;
  margin-top: 12px;
}
.social-btn {
  width: 42px; height: 42px;
  border-radius: 12px;
  background: var(--surface);
  border: 1px solid var(--border);
  display: flex; align-items: center; justify-content: center;
  color: var(--muted);
  font-size: 16px;
  text-decoration: none;
  transition: border-color .3s, color .3s, background .3s, transform .3s, box-shadow .3s;
}
.social-btn:hover {
  border-color: var(--cyan);
  color: var(--cyan);
  background: rgba(0,212,255,.08);
  transform: translateY(-3px);
  box-shadow: 0 8px 24px rgba(0,212,255,.2);
}
.contact-form {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 24px;
  padding: 40px;
  position: relative;
  overflow: hidden;
}
.contact-form::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--cyan), var(--violet), transparent);
}
.form-group { margin-bottom: 20px; }
.form-row { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
label {
  display: block;
  font-size: 12px;
  font-weight: 600;
  letter-spacing: .08em;
  text-transform: uppercase;
  color: var(--muted);
  margin-bottom: 8px;
}
input, textarea {
  width: 100%;
  padding: 12px 16px;
  background: rgba(255,255,255,.04);
  border: 1px solid var(--border);
  border-radius: 10px;
  color: var(--text);
  font-family: var(--font-body);
  font-size: 14px;
  outline: none;
  transition: border-color .3s, box-shadow .3s;
}
input::placeholder, textarea::placeholder { color: var(--muted); }
input:focus, textarea:focus {
  border-color: var(--cyan);
  box-shadow: 0 0 0 3px rgba(0,212,255,.08);
}
textarea { resize: vertical; min-height: 120px; }
.btn-full { width: 100%; justify-content: center; padding: 14px; font-size: 15px; }
.form-status {
  margin-top: 12px;
  font-size: 13px;
  color: var(--cyan);
  text-align: center;
  min-height: 20px;
}

/* ── FOOTER ── */
footer {
  text-align: center;
  padding: 40px 5%;
  border-top: 1px solid var(--border);
  color: var(--muted);
  font-size: 13px;
  font-weight: 300;
  position: relative;
  z-index: 1;
}
footer .footer-name {
  font-family: var(--font-display);
  font-weight: 700;
  background: linear-gradient(135deg, var(--cyan), var(--violet));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
.footer-heart { color: var(--pink); }

/* ── GRADIENT DECORATIONS ── */
.glow-orb {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
  filter: blur(100px);
  opacity: .25;
}

/* ── MOBILE NAV ── */
.mobile-menu {
  display: none;
  flex-direction: column;
  position: fixed;
  top: 70px; left: 0; right: 0;
  background: rgba(5,8,16,.97);
  backdrop-filter: blur(20px);
  padding: 24px 5%;
  border-bottom: 1px solid var(--border);
  z-index: 99;
  gap: 4px;
  animation: slideDown .25s ease;
}
@keyframes slideDown { from { opacity:0; transform:translateY(-10px); } to { opacity:1; transform:none; } }
.mobile-menu a {
  color: var(--muted);
  text-decoration: none;
  font-size: 16px;
  font-weight: 500;
  padding: 12px 0;
  border-bottom: 1px solid var(--border);
  display: block;
  transition: color .2s;
}
.mobile-menu a:last-child { border-bottom: none; }
.mobile-menu a:hover { color: var(--cyan); }

/* ── RESPONSIVE ── */
@media (max-width: 1024px) {
  .hero-inner { grid-template-columns: 1fr; gap: 40px; }
  .hero-avatar-wrap { display: none; }
  .about-grid { grid-template-columns: 1fr; gap: 40px; }
  .projects-grid { grid-template-columns: 1fr 1fr; }
  .cert-grid { grid-template-columns: 1fr 1fr; }
}
@media (max-width: 768px) {
  .nav-links { display: none; }
  .nav-toggle { display: flex; }
  .skills-grid { grid-template-columns: 1fr; }
  .projects-grid { grid-template-columns: 1fr; }
  .cert-grid { grid-template-columns: 1fr 1fr; }
  .contact-grid { grid-template-columns: 1fr; }
  .form-row { grid-template-columns: 1fr; }
  .about-stats { grid-template-columns: 1fr 1fr 1fr; }
  section { padding: 70px 5%; }
}
@media (max-width: 480px) {
  .cert-grid { grid-template-columns: 1fr; }
  .about-stats { grid-template-columns: repeat(3,1fr); gap: 10px; }
  .hero-ctas { flex-direction: column; }
  .btn { width: 100%; justify-content: center; }
}

/* ── CURSOR GLOW ── */
.cursor-glow {
  position: fixed;
  width: 300px; height: 300px;
  border-radius: 50%;
  pointer-events: none;
  z-index: 0;
  background: radial-gradient(circle, rgba(79,124,255,.06), transparent 70%);
  transform: translate(-50%, -50%);
  transition: left .1s ease, top .1s ease;
}
</style>
</head>
<body>

<!-- LOADER -->
<div id="loader">
  <div class="loader-ring"></div>
  <p class="loader-text">Loading Portfolio</p>
</div>

<!-- CURSOR GLOW -->
<div class="cursor-glow" id="cursorGlow"></div>

<!-- CANVAS -->
<canvas id="canvas-bg"></canvas>

<!-- NAV -->
<nav id="navbar">
  <span class="nav-logo">VD.</span>
  <ul class="nav-links" id="navLinks">
    <li><a href="#hero">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#skills">Skills</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#experience">Education</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
  <button class="nav-toggle" id="navToggle" aria-label="Menu">
    <span></span><span></span><span></span>
  </button>
</nav>
<div class="mobile-menu" id="mobileMenu" style="display:none;">
  <a href="#hero" onclick="closeMobileMenu()">Home</a>
  <a href="#about" onclick="closeMobileMenu()">About</a>
  <a href="#skills" onclick="closeMobileMenu()">Skills</a>
  <a href="#projects" onclick="closeMobileMenu()">Projects</a>
  <a href="#experience" onclick="closeMobileMenu()">Education</a>
  <a href="#certifications" onclick="closeMobileMenu()">Achievements</a>
  <a href="#contact" onclick="closeMobileMenu()">Contact</a>
</div>

<main>

<!-- ── HERO ── -->
<section id="hero">
  <div class="glow-orb" style="width:600px;height:600px;background:radial-gradient(circle,rgba(79,124,255,1),rgba(155,93,255,1));top:-200px;right:-100px;"></div>
  <div class="glow-orb" style="width:400px;height:400px;background:radial-gradient(circle,rgba(0,212,255,1),transparent);bottom:50px;left:-100px;"></div>
  <div class="hero-inner">
    <div class="hero-content">
      <div class="hero-badge"><span class="hero-badge-dot"></span> Available for opportunities</div>
      <h1 class="hero-name">
        Hi, I'm<br>
        <span class="highlight">Vishakha<br>Dhiman</span>
      </h1>
      <p class="hero-role">BCA Student — AI &amp; Machine Learning</p>
      <div class="hero-typing">
        <span id="typingText"></span><span class="cursor"></span>
      </div>
      <p class="hero-desc">
        Passionate developer and tech enthusiast building elegant solutions at the intersection of design and engineering. Currently pursuing BCA in AI &amp; ML at MMDU.
      </p>
      <div class="hero-ctas">
        <a href="#projects" class="btn btn-primary"><i class="fas fa-rocket"></i> View My Work</a>
        <a href="#contact" class="btn btn-outline"><i class="fas fa-paper-plane"></i> Get In Touch</a>
      </div>
    </div>
    <div class="hero-avatar-wrap">
      <div class="hero-avatar-ring">
        <div class="hero-avatar">
          <span class="avatar-initial">V</span>
        </div>
      </div>
    </div>
  </div>
  <div class="hero-scroll">
    <span>Scroll</span>
    <div class="scroll-line"></div>
  </div>
</section>

<div class="glow-divider"></div>

<!-- ── ABOUT ── -->
<section id="about">
  <div class="glow-orb" style="width:500px;height:500px;background:radial-gradient(circle,rgba(155,93,255,.7),transparent);top:50px;right:-150px;"></div>
  <div class="about-grid" style="max-width:1200px;margin:0 auto;">
    <div>
      <p class="section-label reveal">About Me</p>
      <h2 class="section-title reveal delay-1">Crafting Code,<br>Creating Impact</h2>
      <p class="about-body reveal delay-2">
        I'm <strong>Vishakha Dhiman</strong>, a dedicated BCA student specialising in Artificial Intelligence & Machine Learning at Maharishi Markandeshwar Deemed University. My journey in tech is driven by curiosity and a passion for building things that matter.
      </p>
      <p class="about-body reveal delay-3">
        I thrive at the crossroads of logic and creativity — writing clean code, solving real-world problems, and continuously levelling up my skillset.
      </p>
      <div class="info-list reveal delay-4">
        <div class="info-item"><i class="fas fa-map-marker-alt"></i> Ambala, Haryana, India</div>
        <div class="info-item"><i class="fas fa-envelope"></i> <a href="mailto:vishakhad970@gmail.com">vishakhad970@gmail.com</a></div>
        <div class="info-item"><i class="fab fa-linkedin"></i> <a href="https://www.linkedin.com/in/vishakha-dhiman" target="_blank">linkedin.com/in/vishakha-dhiman</a></div>
        <div class="info-item"><i class="fab fa-github"></i> <a href="https://github.com/Vishakha-00" target="_blank">github.com/Vishakha-00</a></div>
      </div>
      <div class="about-stats reveal delay-5">
        <div class="stat-card">
          <span class="stat-number">3+</span>
          <span class="stat-label">Projects</span>
        </div>
        <div class="stat-card">
          <span class="stat-number">5+</span>
          <span class="stat-label">Technologies</span>
        </div>
        <div class="stat-card">
          <span class="stat-number">∞</span>
          <span class="stat-label">Curiosity</span>
        </div>
      </div>
    </div>
    <div class="reveal-right">
      <div class="objective-card">
        <div class="objective-title">🎯 Career Objective</div>
        <div class="objective-text">
          To leverage my skills in software development and AI/ML to contribute meaningfully to innovative teams. I aim to grow as a full-stack developer while exploring the intersection of intelligent systems and user-centric design — building products that are both smart and beautifully functional.
        </div>
      </div>
      <div style="margin-top:24px;" class="objective-card">
        <div class="objective-title">🎓 Education</div>
        <div style="display:flex;flex-direction:column;gap:8px;margin-top:4px;">
          <div style="font-size:15px;font-weight:600;color:var(--text)">BCA — AI &amp; Machine Learning</div>
          <div style="font-size:14px;color:var(--violet);font-weight:500">Maharishi Markandeshwar Deemed University (MMDU)</div>
          <div style="font-size:13px;color:var(--muted)">2022 – 2025 · Ambala, Haryana</div>
          <div style="font-size:13px;color:var(--muted);margin-top:8px;line-height:1.7">Studying core subjects including Data Structures, DBMS, Operating Systems, Machine Learning fundamentals, and Software Engineering.</div>
        </div>
      </div>
    </div>
  </div>
</section>

<div class="glow-divider"></div>

<!-- ── SKILLS ── -->
<section id="skills">
  <div class="skills-container">
    <p class="section-label reveal">Technical Skills</p>
    <h2 class="section-title reveal delay-1">Tools &amp; Technologies</h2>
    <p class="section-sub reveal delay-2">A curated set of languages, frameworks, and tools I work with.</p>
    <div class="skills-grid">
      <div class="reveal">
        <div class="skills-col-title"><i class="fas fa-code"></i> Languages</div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">HTML5</span><span class="skill-pct">90%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="90"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">CSS3</span><span class="skill-pct">85%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="85"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">JavaScript</span><span class="skill-pct">75%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="75"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">Java</span><span class="skill-pct">80%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="80"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">Python</span><span class="skill-pct">72%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="72"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">SQL</span><span class="skill-pct">78%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="78"></div></div>
        </div>
      </div>
      <div class="reveal delay-2">
        <div class="skills-col-title"><i class="fas fa-layer-group"></i> Concepts &amp; Areas</div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">Object-Oriented Programming</span><span class="skill-pct">85%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="85"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">Data Structures &amp; Algorithms</span><span class="skill-pct">75%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="75"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">Database Management</span><span class="skill-pct">78%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="78"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">Web Development</span><span class="skill-pct">82%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="82"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">Machine Learning Basics</span><span class="skill-pct">65%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="65"></div></div>
        </div>
        <div class="skill-item">
          <div class="skill-info"><span class="skill-name">UI/UX Principles</span><span class="skill-pct">70%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar-fill" data-width="70"></div></div>
        </div>
      </div>
    </div>
    <div class="tools-grid reveal">
      <span class="tool-chip">Git &amp; GitHub</span>
      <span class="tool-chip">VS Code</span>
      <span class="tool-chip">MySQL</span>
      <span class="tool-chip">Eclipse IDE</span>
      <span class="tool-chip">IntelliJ IDEA</span>
      <span class="tool-chip">Figma</span>
      <span class="tool-chip">Jupyter Notebook</span>
      <span class="tool-chip">NumPy</span>
      <span class="tool-chip">Pandas</span>
      <span class="tool-chip">Linux</span>
      <span class="tool-chip">REST APIs</span>
      <span class="tool-chip">Responsive Design</span>
    </div>
  </div>
</section>

<div class="glow-divider"></div>

<!-- ── PROJECTS ── -->
<section id="projects">
  <div class="projects-container">
    <p class="section-label reveal">My Work</p>
    <h2 class="section-title reveal delay-1">Featured Projects</h2>
    <p class="section-sub reveal delay-2">A selection of projects that showcase my skills and problem-solving approach.</p>
    <div class="projects-grid">

      <!-- Project 1 -->
      <div class="project-card reveal delay-1">
        <div class="project-thumb" style="background:linear-gradient(135deg,#0a1628,#1a2a50);">
          <div class="project-thumb-inner">🎓</div>
        </div>
        <div class="project-body">
          <div class="project-name">College Event Management System</div>
          <div class="project-desc">A full-featured web application for managing college events — from scheduling and registration to notifications. Streamlines event coordination for students and administrators.</div>
          <div class="project-tags">
            <span class="tag">HTML</span>
            <span class="tag">CSS</span>
            <span class="tag">JavaScript</span>
          </div>
          <div class="project-links">
            <a href="https://github.com/Vishakha-00" target="_blank" class="project-link"><i class="fab fa-github"></i> Source Code</a>
          </div>
        </div>
      </div>

      <!-- Project 2 -->
      <div class="project-card reveal delay-2">
        <div class="project-thumb" style="background:linear-gradient(135deg,#0a1628,#1a1040);">
          <div class="project-thumb-inner">🔢</div>
        </div>
        <div class="project-body">
          <div class="project-name">Java Calculator</div>
          <div class="project-desc">A clean and functional GUI-based calculator built in Java using Swing. Supports all basic and scientific operations with a polished, responsive interface.</div>
          <div class="project-tags">
            <span class="tag">Java</span>
            <span class="tag">Swing</span>
          </div>
          <div class="project-links">
            <a href="https://github.com/Vishakha-00" target="_blank" class="project-link"><i class="fab fa-github"></i> Source Code</a>
          </div>
        </div>
      </div>

      <!-- Project 3 -->
      <div class="project-card reveal delay-3">
        <div class="project-thumb" style="background:linear-gradient(135deg,#0a1628,#0d2030);">
          <div class="project-thumb-inner">🧠</div>
        </div>
        <div class="project-body">
          <div class="project-name">Smart Quiz Engine</div>
          <div class="project-desc">An intelligent quiz platform with dynamic question generation, timer functionality, real-time scoring, and performance analytics. Designed for interactive learning experiences.</div>
          <div class="project-tags">
            <span class="tag">Python</span>
            <span class="tag">JavaScript</span>
            <span class="tag">HTML/CSS</span>
            <span class="tag">SQL</span>
          </div>
          <div class="project-links">
            <a href="https://github.com/Vishakha-00" target="_blank" class="project-link"><i class="fab fa-github"></i> Source Code</a>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<div class="glow-divider"></div>

<!-- ── EXPERIENCE / EDUCATION ── -->
<section id="experience">
  <p class="section-label reveal" style="text-align:center;">Journey</p>
  <h2 class="section-title reveal delay-1" style="text-align:center;">Education &amp; Experience</h2>
  <p class="section-sub reveal delay-2" style="text-align:center;margin:0 auto 60px;">My academic path and learning milestones.</p>
  <div class="timeline">
    <div class="tl-item reveal">
      <div class="tl-dot"></div>
      <div class="tl-card">
        <div class="tl-meta">
          <span class="tl-badge">Current</span>
          <span class="tl-date"><i class="fas fa-calendar"></i> 2024 – 2027</span>
        </div>
        <div class="tl-title">Bachelor of Computer Applications</div>
        <div class="tl-org">Maharishi Markandeshwar Deemed University (MMDU)</div>
        <div class="tl-desc">Specialisation in Artificial Intelligence &amp; Machine Learning. Core coursework includes Python for Data Science, Java Programming, DBMS, Operating Systems, Computer Networks, and Software Engineering principles.</div>
      </div>
    </div>
    <div class="tl-item reveal delay-1">
      <div class="tl-dot"></div>
      <div class="tl-card">
        <div class="tl-meta">
          <span class="tl-badge">Completed</span>
          <span class="tl-date"><i class="fas fa-calendar"></i> 2023 – 2024</span>
        </div>
        <div class="tl-title">Senior Secondary Education (12th)</div>
        <div class="tl-org">Science Stream — Haryana Board</div>
        <div class="tl-desc">Completed senior secondary education with Physics, Chemistry, Mathematics, and Computer Science. Developed a strong foundation in analytical thinking and problem-solving.</div>
      </div>
    </div>
    <div class="tl-item reveal delay-2">
      <div class="tl-dot"></div>
      <div class="tl-card">
        <div class="tl-meta">
          <span class="tl-badge">Milestone</span>
        </div>
        <div class="tl-title">First Full-Stack Project</div>
        <div class="tl-org">Self-Initiated Learning &amp; Development</div>
        <div class="tl-desc">Built the College Event Management System — a milestone project combining frontend, backend and database skills. This project cemented my passion for building complete, end-to-end solutions.</div>
      </div>
    </div>
  </div>
</section>

<div class="glow-divider"></div>

<!-- ── CERTIFICATIONS ── -->


<!-- ── CONTACT ── -->
<section id="contact">
  <p class="section-label reveal">Get In Touch</p>
  <h2 class="section-title reveal delay-1">Let's Connect</h2>
  <p class="section-sub reveal delay-2">Have an opportunity or just want to say hi? My inbox is always open.</p>
  <div class="contact-grid">
    <div class="contact-info reveal-left">
      <div class="contact-info-item">
        <div class="contact-icon-box"><i class="fas fa-envelope"></i></div>
        <div>
          <div class="contact-info-label">Email</div>
          <div class="contact-info-value"><a href="mailto:vishakhad970@gmail.com">vishakhad970@gmail.com</a></div>
        </div>
      </div>
      <div class="contact-info-item">
        <div class="contact-icon-box"><i class="fas fa-map-marker-alt"></i></div>
        <div>
          <div class="contact-info-label">Location</div>
          <div class="contact-info-value">Ambala, Haryana, India</div>
        </div>
      </div>
      <div class="contact-info-item">
        <div class="contact-icon-box"><i class="fab fa-linkedin"></i></div>
        <div>
          <div class="contact-info-label">LinkedIn</div>
          <div class="contact-info-value"><a href="https://www.linkedin.com/in/vishakha-dhiman" target="_blank">linkedin.com/in/vishakha-dhiman</a></div>
        </div>
      </div>
      <div class="contact-info-item">
        <div class="contact-icon-box"><i class="fab fa-github"></i></div>
        <div>
          <div class="contact-info-label">GitHub</div>
          <div class="contact-info-value"><a href="https://github.com/Vishakha-00" target="_blank">github.com/Vishakha-00</a></div>
        </div>
      </div>
      <div>
        <div class="contact-info-label" style="margin-bottom:12px;">Follow Me</div>
        <div class="socials">
          <a href="https://github.com/Vishakha-00" target="_blank" class="social-btn" title="GitHub"><i class="fab fa-github"></i></a>
          <a href="https://www.linkedin.com/in/vishakha-dhiman" target="_blank" class="social-btn" title="LinkedIn"><i class="fab fa-linkedin"></i></a>
          <a href="mailto:vishakhad970@gmail.com" class="social-btn" title="Email"><i class="fas fa-envelope"></i></a>
        </div>
      </div>
    </div>
    <div class="contact-form reveal-right">
      <div class="form-row">
        <div class="form-group">
          <label for="fname">First Name</label>
          <input type="text" id="fname" placeholder="John">
        </div>
        <div class="form-group">
          <label for="lname">Last Name</label>
          <input type="text" id="lname" placeholder="Doe">
        </div>
      </div>
      <div class="form-group">
        <label for="femail">Email Address</label>
        <input type="email" id="femail" placeholder="john@example.com">
      </div>
      <div class="form-group">
        <label for="fsubject">Subject</label>
        <input type="text" id="fsubject" placeholder="Internship Opportunity">
      </div>
      <div class="form-group">
        <label for="fmessage">Message</label>
        <textarea id="fmessage" placeholder="Hi Vishakha, I'd love to connect..."></textarea>
      </div>
      <button class="btn btn-primary btn-full" onclick="handleFormSubmit()">
        <i class="fas fa-paper-plane"></i> Send Message
      </button>
      <div class="form-status" id="formStatus"></div>
    </div>
  </div>
</section>

</main>

<!-- ── FOOTER ── -->
<footer>
  <p>Designed &amp; Built with <span class="footer-heart">♥</span> by <span class="footer-name">Vishakha Dhiman</span> &nbsp;·&nbsp; © 2025</p>
</footer>

<script>
// ── LOADER
window.addEventListener('load', () => {
  setTimeout(() => {
    document.getElementById('loader').classList.add('hide');
  }, 1200);
});

// ── CANVAS PARTICLES
const canvas = document.getElementById('canvas-bg');
const ctx = canvas.getContext('2d');
let W, H, particles = [];

function resizeCanvas() {
  W = canvas.width = window.innerWidth;
  H = canvas.height = window.innerHeight;
}

function Particle() {
  this.x = Math.random() * W;
  this.y = Math.random() * H;
  this.r = Math.random() * 1.5 + 0.3;
  this.vx = (Math.random() - .5) * .3;
  this.vy = (Math.random() - .5) * .3;
  this.alpha = Math.random() * .5 + .1;
  this.color = ['rgba(0,212,255,', 'rgba(79,124,255,', 'rgba(155,93,255,'][Math.floor(Math.random()*3)];
}

Particle.prototype.update = function() {
  this.x += this.vx;
  this.y += this.vy;
  if (this.x < 0 || this.x > W) this.vx *= -1;
  if (this.y < 0 || this.y > H) this.vy *= -1;
};

Particle.prototype.draw = function() {
  ctx.beginPath();
  ctx.arc(this.x, this.y, this.r, 0, Math.PI * 2);
  ctx.fillStyle = this.color + this.alpha + ')';
  ctx.fill();
};

function initParticles() {
  particles = [];
  const count = Math.min(120, Math.floor(W * H / 12000));
  for (let i = 0; i < count; i++) particles.push(new Particle());
}

function connectParticles() {
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const d = Math.sqrt(dx * dx + dy * dy);
      if (d < 120) {
        ctx.beginPath();
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.strokeStyle = `rgba(79,124,255,${0.08 * (1 - d/120)})`;
        ctx.lineWidth = .5;
        ctx.stroke();
      }
    }
  }
}

function animateCanvas() {
  ctx.clearRect(0, 0, W, H);
  particles.forEach(p => { p.update(); p.draw(); });
  connectParticles();
  requestAnimationFrame(animateCanvas);
}

resizeCanvas();
initParticles();
animateCanvas();
window.addEventListener('resize', () => { resizeCanvas(); initParticles(); });

// ── CURSOR GLOW
const glow = document.getElementById('cursorGlow');
document.addEventListener('mousemove', e => {
  glow.style.left = e.clientX + 'px';
  glow.style.top = e.clientY + 'px';
});

// ── TYPING
const phrases = [
  'Web Developer',
  'Java Programmer',
  'Python Enthusiast',
  'AI/ML Explorer',
  'Problem Solver',
  'Tech Learner'
];
let pi = 0, ci = 0, deleting = false;
const el = document.getElementById('typingText');

function type() {
  const cur = phrases[pi];
  if (!deleting) {
    el.textContent = cur.slice(0, ++ci);
    if (ci === cur.length) { deleting = true; setTimeout(type, 2000); return; }
  } else {
    el.textContent = cur.slice(0, --ci);
    if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
  }
  setTimeout(type, deleting ? 50 : 100);
}
setTimeout(type, 1500);

// ── SCROLL REVEAL
const revealEls = document.querySelectorAll('.reveal, .reveal-left, .reveal-right');
const revealObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) { e.target.classList.add('visible'); }
  });
}, { threshold: 0.12 });
revealEls.forEach(el => revealObs.observe(el));

// ── SKILL BARS
const barObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.skill-bar-fill').forEach(bar => {
        bar.style.width = bar.dataset.width + '%';
      });
    }
  });
}, { threshold: 0.2 });
const skillsSection = document.getElementById('skills');
if (skillsSection) barObs.observe(skillsSection);

// ── MOBILE NAV
const toggle = document.getElementById('navToggle');
const mobileMenu = document.getElementById('mobileMenu');
let menuOpen = false;

toggle.addEventListener('click', () => {
  menuOpen = !menuOpen;
  mobileMenu.style.display = menuOpen ? 'flex' : 'none';
  const spans = toggle.querySelectorAll('span');
  if (menuOpen) {
    spans[0].style.transform = 'rotate(45deg) translate(5px,5px)';
    spans[1].style.opacity = '0';
    spans[2].style.transform = 'rotate(-45deg) translate(5px,-5px)';
  } else {
    spans.forEach(s => { s.style.transform = ''; s.style.opacity = ''; });
  }
});

function closeMobileMenu() {
  menuOpen = false;
  mobileMenu.style.display = 'none';
  const spans = toggle.querySelectorAll('span');
  spans.forEach(s => { s.style.transform = ''; s.style.opacity = ''; });
}

// ── CONTACT FORM
function handleFormSubmit() {
  const name = document.getElementById('fname').value.trim();
  const email = document.getElementById('femail').value.trim();
  const msg = document.getElementById('fmessage').value.trim();
  const status = document.getElementById('formStatus');
  if (!name || !email || !msg) {
    status.style.color = 'var(--pink)';
    status.textContent = '⚠️ Please fill in all required fields.';
    return;
  }
  status.style.color = 'var(--cyan)';
  status.textContent = '✅ Message sent! I\'ll get back to you soon.';
  setTimeout(() => status.textContent = '', 4000);
}

// ── ACTIVE NAV
const sections = document.querySelectorAll('section[id]');
const navAs = document.querySelectorAll('.nav-links a');
window.addEventListener('scroll', () => {
  let cur = '';
  sections.forEach(s => {
    if (window.scrollY >= s.offsetTop - 120) cur = s.id;
  });
  navAs.forEach(a => {
    a.style.color = a.getAttribute('href') === '#' + cur ? 'var(--text)' : '';
  });
});
</script>
</body>
</html># Portfolio
