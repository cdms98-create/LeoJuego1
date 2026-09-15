# LeoJuego1 <!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>LeoJuego – Aprender a leer es un juego</title>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@400;600;700;800&family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet"/>
<style>
/* ====================================================
   TOKENS — paleta viva para niños 🎨
   ==================================================== */
:root{
  --board:#6B21A8;        /* morado intenso (fondo nav/hero) */
  --chalk:#FFFFFF;        /* blanco puro */
  --sun:#FFE000;          /* amarillo eléctrico */
  --mint:#00D97E;         /* verde lima vivo */
  --coral:#FF3D6B;        /* rosa-rojo vibrante */
  --sky:#00B4FF;          /* azul eléctrico */
  --violet:#A855F7;       /* violeta brillante */
  --orange:#FF7A00;       /* naranja cálido */
  --page:#FFF9EC;         /* fondo cálido tipo papel amarillo suave */
  --ink:#2D1654;          /* texto: morado muy oscuro */
  --soft:#7C5C9B;         /* texto secundario morado suave */
  --white:#FFFFFF;
  --r-sm:10px;
  --r-md:18px;
  --r-lg:28px;
  --r-xl:40px;
  --f-display:'Baloo 2',cursive;
  --f-body:'Poppins',sans-serif;
  --shadow-card:0 4px 24px rgba(107,33,168,.12);
  --shadow-pop:0 16px 48px rgba(107,33,168,.22);
}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:var(--f-body);background:var(--page);color:var(--ink);overflow-x:hidden;line-height:1.6}
/* fondo con patrón de puntos suaves */
body::after{content:'';position:fixed;inset:0;pointer-events:none;z-index:-1;
  background-image:radial-gradient(circle,rgba(107,33,168,.06) 1px,transparent 1px);
  background-size:28px 28px;}
img{max-width:100%;display:block}
a{text-decoration:none;color:inherit}
button{font-family:var(--f-body);cursor:pointer}

/* ====================================================
   SCROLLBAR
   ==================================================== */
::-webkit-scrollbar{width:6px}
::-webkit-scrollbar-track{background:#f5e6ff}
::-webkit-scrollbar-thumb{background:linear-gradient(var(--coral),var(--violet));border-radius:6px}

/* ====================================================
   NAV
   ==================================================== */
#nav{
  position:fixed;top:0;left:0;right:0;z-index:900;
  height:62px;
  background:var(--board);
  display:flex;align-items:center;justify-content:space-between;
  padding:0 5%;
}
.nav-brand{
  font-family:var(--f-display);font-size:1.75rem;font-weight:800;
  color:var(--sun);display:flex;align-items:center;gap:8px;
}
.nav-brand sup{font-size:.6rem;background:var(--mint);color:var(--board);
  border-radius:6px;padding:2px 6px;font-family:var(--f-body);font-weight:700;vertical-align:top;margin-top:6px}
.nav-links{display:flex;align-items:center;gap:2px}
.nav-links a{
  color:rgba(247,243,233,.7);font-size:.8rem;font-weight:600;
  padding:6px 11px;border-radius:var(--r-sm);transition:.2s;
}
.nav-links a:hover{background:rgba(255,255,255,.1);color:var(--chalk)}
.nav-wa{
  background:var(--mint);color:var(--board)!important;
  font-weight:700!important;padding:7px 15px!important;border-radius:40px!important;
}
.nav-wa:hover{background:#2fc49a!important;color:var(--board)!important}
.hamburger{display:none;flex-direction:column;gap:4px;background:none;border:none;padding:4px;cursor:pointer}
.hamburger span{width:22px;height:2.5px;background:var(--chalk);border-radius:4px;display:block;transition:.25s}
.mob-nav{
  display:none;position:fixed;top:62px;left:0;right:0;
  background:var(--board);z-index:899;flex-direction:column;
  padding:14px 5% 20px;gap:4px;border-top:1px solid rgba(255,255,255,.08);
}
.mob-nav.open{display:flex}
.mob-nav a{color:var(--chalk);font-weight:600;padding:11px 14px;border-radius:12px;background:rgba(255,255,255,.05)}

/* ====================================================
   HERO — fondo degradado vivo para niños
   ==================================================== */
#hero{
  min-height:100vh;
  background:linear-gradient(135deg,#6B21A8 0%,#A855F7 40%,#FF3D6B 75%,#FF7A00 100%);
  padding:100px 5% 60px;
  display:grid;
  grid-template-columns:1fr 1fr;
  align-items:center;
  gap:48px;
  position:relative;
  overflow:hidden;
}
/* burbujas decorativas */
#hero::before{
  content:'';position:absolute;inset:0;
  background:radial-gradient(circle at 80% 20%,rgba(255,224,0,.18) 0%,transparent 50%),
             radial-gradient(circle at 15% 80%,rgba(0,212,126,.15) 0%,transparent 45%);
  pointer-events:none;
}
.hero-ring{
  position:absolute;border-radius:50%;
  border:3px solid rgba(255,224,0,.20);
  pointer-events:none;
}
.hero-ring:nth-child(1){width:420px;height:420px;top:-100px;right:-80px}
.hero-ring:nth-child(2){width:260px;height:260px;bottom:80px;left:-60px}
.hero-ring:nth-child(3){width:140px;height:140px;bottom:200px;right:15%}

.hero-left{position:relative;z-index:2}
.hero-tag{
  display:inline-flex;align-items:center;gap:8px;
  background:rgba(255,224,0,.22);border:2px solid rgba(255,224,0,.55);
  color:var(--sun);border-radius:40px;padding:5px 16px;
  font-size:.78rem;font-weight:700;margin-bottom:22px;
}
.hero-left h1{
  font-family:var(--f-display);font-size:clamp(2.6rem,5.5vw,4.2rem);
  color:var(--chalk);line-height:1.08;font-weight:800;margin-bottom:18px;
}
.hero-left h1 .hi{color:var(--sun)}
.hero-left p{
  font-size:clamp(.92rem,1.8vw,1.08rem);color:rgba(247,243,233,.72);
  line-height:1.75;max-width:480px;margin-bottom:34px;
}
.hero-btns{display:flex;gap:12px;flex-wrap:wrap}
.btn-sun{
  background:var(--sun);color:var(--board);
  font-weight:700;font-size:.95rem;padding:13px 26px;
  border-radius:40px;border:none;transition:.22s;
  box-shadow:0 4px 20px rgba(245,197,24,.35);
  display:inline-flex;align-items:center;gap:8px;
}
.btn-sun:hover{transform:translateY(-3px);box-shadow:0 8px 32px rgba(245,197,24,.5)}
.btn-ghost{
  background:transparent;color:var(--chalk);
  border:2px solid rgba(247,243,233,.3);font-weight:600;font-size:.95rem;
  padding:12px 24px;border-radius:40px;transition:.22s;
  display:inline-flex;align-items:center;gap:8px;
}
.btn-ghost:hover{background:rgba(255,255,255,.08);border-color:rgba(247,243,233,.6)}

/* Hero illustration: fichas de letras */
.hero-right{
  position:relative;z-index:2;
  display:flex;align-items:center;justify-content:center;
}
.letter-board{
  display:grid;grid-template-columns:repeat(4,80px);
  grid-template-rows:repeat(3,80px);
  gap:10px;
}
.lb-tile{
  border-radius:14px;display:flex;flex-direction:column;
  align-items:center;justify-content:center;
  font-family:var(--f-display);font-size:2.4rem;font-weight:800;
  color:var(--board);cursor:default;transition:transform .3s;
  box-shadow:0 4px 0 rgba(0,0,0,.15);
  animation:tileIn .6s ease both;
}
.lb-tile:nth-child(1){background:var(--sun);animation-delay:.05s}
.lb-tile:nth-child(2){background:var(--mint);animation-delay:.1s}
.lb-tile:nth-child(3){background:var(--coral);animation-delay:.15s}
.lb-tile:nth-child(4){background:var(--sky);animation-delay:.2s}
.lb-tile:nth-child(5){background:var(--violet);color:#fff;animation-delay:.25s}
.lb-tile:nth-child(6){background:var(--chalk);animation-delay:.3s}
.lb-tile:nth-child(7){background:var(--sun);animation-delay:.35s}
.lb-tile:nth-child(8){background:var(--mint);animation-delay:.4s}
.lb-tile:nth-child(9){background:var(--coral);animation-delay:.45s}
.lb-tile:nth-child(10){background:var(--sky);animation-delay:.5s}
.lb-tile:nth-child(11){background:var(--violet);color:#fff;animation-delay:.55s}
.lb-tile:nth-child(12){background:var(--sun);animation-delay:.6s}
.lb-tile span.small{font-size:.7rem;font-weight:600;opacity:.7;font-family:var(--f-body);line-height:1}
@keyframes tileIn{from{opacity:0;transform:translateY(20px) scale(.8)}to{opacity:1;transform:translateY(0) scale(1)}}
.lb-tile:hover{transform:translateY(-5px) rotate(-3deg)}

@media(max-width:768px){
  #hero{grid-template-columns:1fr;padding:88px 5% 50px;text-align:center}
  .hero-left p{margin:0 auto 28px}
  .hero-btns{justify-content:center}
  .hero-right{margin-top:20px}
  .letter-board{grid-template-columns:repeat(4,60px);grid-template-rows:repeat(3,60px);gap:7px}
  .lb-tile{font-size:1.8rem;border-radius:10px}
  .nav-links{display:none}
  .hamburger{display:flex}
}

/* ====================================================
   SHARED
   ==================================================== */
.sec{padding:80px 5%}
.sec-white{background:var(--white)}
.sec-dark{background:linear-gradient(135deg,#2D1654,#6B21A8)}
.sec-board{background:linear-gradient(135deg,#1a0833,#3d1278)}

.sec-head{text-align:center;margin-bottom:52px}
.sec-head h2{font-family:var(--f-display);font-size:clamp(1.75rem,3.5vw,2.6rem);
  font-weight:800;color:var(--board);margin-bottom:10px;line-height:1.15}
.sec-dark .sec-head h2,.sec-board .sec-head h2{color:var(--chalk)}
.sec-head p{font-size:.97rem;color:var(--soft);max-width:560px;margin:0 auto}
.sec-dark .sec-head p,.sec-board .sec-head p{color:rgba(247,243,233,.6)}

/* pills */
.pill{
  display:inline-block;padding:4px 14px;border-radius:40px;
  font-size:.72rem;font-weight:700;margin-bottom:12px;
}
.pill-sun{background:#FFE000;color:#5a3a00;font-weight:800}
.pill-mint{background:#00D97E;color:#003d22;font-weight:800}
.pill-coral{background:#FF3D6B;color:#fff;font-weight:800}
.pill-sky{background:#00B4FF;color:#003d5a;font-weight:800}
.pill-violet{background:#A855F7;color:#fff;font-weight:800}
.pill-w{background:rgba(255,255,255,.25);color:#fff;font-weight:800}

/* shared button */
.btn-board{background:var(--board);color:#fff;font-weight:700;
  font-size:.92rem;padding:12px 24px;border-radius:40px;border:none;
  transition:.2s;display:inline-flex;align-items:center;gap:8px;
  box-shadow:0 4px 14px rgba(107,33,168,.3)}
.btn-board:hover{background:#7c3aed;transform:translateY(-2px);box-shadow:0 8px 22px rgba(107,33,168,.45)}
.btn-mint{background:var(--mint);color:#003d22;font-weight:700;
  font-size:.92rem;padding:12px 24px;border-radius:40px;border:none;
  transition:.2s;display:inline-flex;align-items:center;gap:8px;
  box-shadow:0 4px 14px rgba(0,217,126,.35)}
.btn-mint:hover{background:#00c06e;transform:translateY(-2px)}
.btn-coral{background:var(--coral);color:#fff;font-weight:700;
  font-size:.92rem;padding:12px 24px;border-radius:40px;border:none;
  transition:.2s;display:inline-flex;align-items:center;gap:8px;
  box-shadow:0 4px 14px rgba(255,61,107,.35)}
.btn-coral:hover{background:#e8204f;transform:translateY(-2px)}

/* ====================================================
   REGISTRO + SUPABASE
   ==================================================== */
#registro{background:linear-gradient(160deg,#fff9ec 0%,#fce7ff 100%)}
.reg-wrap{max-width:680px;margin:0 auto}
.reg-card{
  background:#fff;border-radius:var(--r-lg);
  padding:38px;border:3px solid rgba(168,85,247,.15);
  box-shadow:0 8px 40px rgba(168,85,247,.12);
}
.reg-card h3{font-family:var(--f-display);font-size:1.5rem;color:var(--board);margin-bottom:6px}
.reg-card .sub{color:var(--soft);font-size:.88rem;margin-bottom:26px;line-height:1.65}
.fgrid{display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:14px}
@media(max-width:520px){.fgrid{grid-template-columns:1fr}}
.fg{display:flex;flex-direction:column;gap:5px}
.fg label{font-size:.78rem;font-weight:700;color:var(--board)}
.fg input,.fg select{
  padding:11px 14px;border:2.5px solid #e8d5ff;border-radius:var(--r-sm);
  font-family:var(--f-body);font-size:.93rem;color:var(--ink);background:#fdfaff;
  outline:none;transition:.2s;
}
.fg input:focus,.fg select:focus{border-color:var(--violet);box-shadow:0 0 0 3px rgba(168,85,247,.12)}
.fg input::placeholder{color:#c4a8e0}
.acomp-opts{display:flex;gap:10px;margin-top:4px}
.acomp-btn{
  flex:1;padding:11px;border-radius:var(--r-sm);border:2.5px solid #e8d5ff;
  background:#fdfaff;font-family:var(--f-body);font-weight:700;font-size:.88rem;
  color:var(--soft);cursor:pointer;transition:.2s;text-align:center;
}
.acomp-btn.sel{border-color:var(--violet);background:var(--violet);color:#fff}
.supa-note{
  background:linear-gradient(135deg,#f0fff4,#e0f8ff);
  border:2px solid #6ee7b7;border-radius:12px;
  padding:14px 16px;font-size:.8rem;color:#065f46;margin-bottom:18px;
  line-height:1.65;
}
.supa-note strong{color:#047857}
.supa-note code{background:#d1fae5;padding:2px 6px;border-radius:4px;font-size:.78rem}
.reg-ok{display:none;text-align:center;padding:20px 0}
.reg-ok .big{font-size:4rem;display:block;animation:pop .5s ease}
@keyframes pop{0%{transform:scale(0)}65%{transform:scale(1.2)}100%{transform:scale(1)}}
.reg-ok h4{font-family:var(--f-display);font-size:1.7rem;color:var(--board);margin:10px 0 6px}
.reg-ok p{color:var(--soft);font-size:.9rem;margin-bottom:18px}
.users-log{margin-top:22px;padding-top:18px;border-top:2px dashed #e8d5ff;display:none}
.users-log h5{font-weight:700;font-size:.82rem;color:var(--board);margin-bottom:10px}
.u-chip{
  display:inline-flex;align-items:center;gap:6px;
  padding:4px 12px;border-radius:40px;font-size:.77rem;font-weight:700;margin:3px;
}
.uc-doc{background:#a855f7;color:#fff}
.uc-cuid{background:#00D97E;color:#003d22}

/* ====================================================
   ACTIVIDADES — LETRAS CON SONIDO
   ==================================================== */
#actividades{background:linear-gradient(160deg,#fff9ec 0%,#fff0fc 100%)}
.act-tabs{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;margin-bottom:42px}
.act-tab{
  padding:8px 20px;border-radius:40px;border:2.5px solid #e8d5ff;
  background:#fff;font-weight:700;font-size:.83rem;color:var(--soft);
  cursor:pointer;transition:.2s;
}
.act-tab.on,.act-tab:hover{background:linear-gradient(135deg,var(--board),var(--violet));color:#fff;border-color:transparent;box-shadow:0 4px 16px rgba(107,33,168,.3)}
.act-pane{display:none}
.act-pane.show{display:block}

/* Fichas de letras */
.letters-deck{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(86px,1fr));
  gap:10px;
}
.letter-tile{
  background:#fff;border-radius:16px;
  padding:12px 8px 10px;text-align:center;
  border-top:6px solid var(--coral);
  box-shadow:0 4px 0 rgba(0,0,0,.10),var(--shadow-card);
  transition:transform .2s,box-shadow .2s;
  user-select:none;
}
.letter-tile:nth-child(7n+1){border-top-color:var(--coral)}
.letter-tile:nth-child(7n+2){border-top-color:var(--mint)}
.letter-tile:nth-child(7n+3){border-top-color:var(--sky)}
.letter-tile:nth-child(7n+4){border-top-color:var(--violet)}
.letter-tile:nth-child(7n+5){border-top-color:var(--sun);border-top-width:6px}
.letter-tile:nth-child(7n+6){border-top-color:var(--orange)}
.letter-tile:nth-child(7n+0){border-top-color:var(--coral)}
.letter-tile.speaking{transform:scale(1.14) rotate(-3deg);box-shadow:0 8px 28px rgba(255,61,107,.35)}
.lt-char{font-family:var(--f-display);font-size:2rem;font-weight:800;color:var(--board);line-height:1;display:block}
.lt-min{font-size:.65rem;font-weight:700;color:var(--soft);display:block;margin-bottom:7px}
.lt-snd{
  background:none;border:none;font-size:1.1rem;cursor:pointer;
  padding:3px 8px;border-radius:30px;transition:.2s;display:block;margin:0 auto;
}
.lt-snd:hover{background:rgba(168,85,247,.12)}
.lt-ex{font-size:.62rem;color:var(--soft);font-weight:700;margin-top:4px}
.letters-hint{
  text-align:center;background:#fff;border-radius:14px;padding:18px;
  border:2.5px dashed #e8d5ff;margin-bottom:24px;
  font-size:.9rem;color:var(--soft);
}

/* Act cards */
.act-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px}
.act-card{
  background:#fff;border-radius:var(--r-md);padding:26px 22px;
  box-shadow:var(--shadow-card);border-left:6px solid var(--violet);
  transition:transform .22s,box-shadow .22s;
}
.act-card:hover{transform:translateY(-5px);box-shadow:0 12px 36px rgba(107,33,168,.15)}
.act-card.c-coral{border-left-color:var(--coral)}
.act-card.c-mint{border-left-color:var(--mint)}
.act-card.c-sky{border-left-color:var(--sky)}
.act-card.c-violet{border-left-color:var(--violet)}
.act-card .ico{font-size:2.2rem;margin-bottom:10px}
.act-card h3{font-family:var(--f-display);font-size:1.2rem;color:var(--board);margin-bottom:7px}
.act-card p{font-size:.85rem;color:var(--soft);line-height:1.65}

/* ====================================================
   JUEGOS
   ==================================================== */
#juegos{background:linear-gradient(160deg,#fff0fc 0%,#e8f9ff 100%)}
.games-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:22px}
.game-card{
  border-radius:var(--r-lg);overflow:hidden;
  box-shadow:var(--shadow-card);transition:.25s;
}
.game-card:hover{transform:translateY(-8px) rotate(-1deg);box-shadow:var(--shadow-pop)}
.gc-top{padding:28px;text-align:center}
.gc-t1{background:linear-gradient(135deg,#6B21A8,#A855F7)}
.gc-t2{background:linear-gradient(135deg,#FF3D6B,#FF7A00)}
.gc-t3{background:linear-gradient(135deg,#00B4FF,#00D97E)}
.gc-t4{background:linear-gradient(135deg,#FFE000,#FF7A00)}
.gc-t5{background:linear-gradient(135deg,#FF3D6B,#A855F7)}
.gc-t6{background:linear-gradient(135deg,#00D97E,#00B4FF)}
.gc-t7{background:linear-gradient(135deg,#A855F7,#FF3D6B)}
.gc-t8{background:linear-gradient(135deg,#FF7A00,#FFE000)}
.gc-top .em{font-size:3.2rem;display:block;margin-bottom:10px}
.gc-top h3{font-family:var(--f-display);font-size:1.35rem;color:#fff;font-weight:800}
.gc-body{background:#fff;padding:20px 22px}
.gc-body p{font-size:.85rem;color:var(--soft);margin-bottom:15px;line-height:1.55}
.gc-level{font-size:.72rem;font-weight:700;margin-bottom:14px;display:flex;align-items:center;gap:6px;color:var(--soft)}
.gc-dot{width:8px;height:8px;border-radius:50%;display:inline-block}
.dl-g{background:var(--mint)}.dl-y{background:var(--orange)}.dl-r{background:var(--coral)}
.gc-play{
  width:100%;padding:11px;border-radius:40px;border:none;
  font-weight:700;font-size:.9rem;color:#fff;transition:.2s;
  box-shadow:0 4px 12px rgba(0,0,0,.15);
}
.gp1{background:linear-gradient(135deg,#6B21A8,#A855F7)}
.gp2{background:linear-gradient(135deg,#FF3D6B,#FF7A00)}
.gp3{background:linear-gradient(135deg,#00B4FF,#00D97E)}
.gp4{background:linear-gradient(135deg,#FF7A00,#FFE000);color:var(--ink)}
.gp5{background:linear-gradient(135deg,#FF3D6B,#A855F7)}
.gp6{background:linear-gradient(135deg,#00D97E,#00B4FF)}
.gp7{background:linear-gradient(135deg,#A855F7,#FF3D6B)}
.gp8{background:linear-gradient(135deg,#FF7A00,#FFE000);color:var(--ink)}
.gc-play:hover{opacity:.9;transform:scale(1.04)}

/* ====================================================
   MODAL JUEGO
   ==================================================== */
.overlay{
  display:none;position:fixed;inset:0;z-index:1000;
  background:rgba(75,0,130,.55);backdrop-filter:blur(8px);
  align-items:center;justify-content:center;padding:16px;
}
.overlay.open{display:flex}
.modal{
  background:#fff;border-radius:var(--r-xl);padding:36px;
  max-width:560px;width:100%;max-height:90vh;overflow-y:auto;
  position:relative;animation:mup .28s ease;
}
@keyframes mup{from{transform:translateY(28px);opacity:0}to{transform:translateY(0);opacity:1}}
.m-x{
  position:absolute;top:14px;right:16px;
  width:32px;height:32px;border-radius:50%;background:var(--page);
  border:none;font-size:1.1rem;cursor:pointer;
  display:flex;align-items:center;justify-content:center;transition:.2s;
}
.m-x:hover{background:#dde2ee}
.m-h1{font-family:var(--f-display);font-size:1.75rem;color:var(--board);margin-bottom:3px;font-weight:800}
.m-sub{color:var(--soft);font-size:.87rem;margin-bottom:18px}
.m-score-bar{
  display:flex;justify-content:space-between;align-items:center;
  background:var(--page);border-radius:10px;padding:9px 14px;
  margin-bottom:16px;font-weight:700;font-size:.85rem;color:var(--board);
}
.m-pts{font-family:var(--f-display);font-size:1.3rem;color:var(--coral)}
.m-prog{height:8px;background:#dde2ee;border-radius:40px;overflow:hidden;margin-bottom:18px}
.m-prog-fill{height:100%;background:var(--mint);border-radius:40px;transition:width .5s ease}
.m-fb{min-height:34px;text-align:center;font-family:var(--f-display);font-size:1.15rem;margin-bottom:10px;transition:.2s}
.fb-ok{color:var(--mint)}.fb-no{color:var(--coral)}
/* game elements */
.big-w{font-family:var(--f-display);font-size:2.8rem;text-align:center;color:var(--board);
  margin:14px 0;letter-spacing:2px;font-weight:800}
.em-big{font-size:5rem;text-align:center;display:block;margin:8px 0}
.sub-w{font-family:var(--f-display);font-size:1.8rem;text-align:center;color:var(--board);margin:6px 0}
.opts-row{display:flex;flex-wrap:wrap;gap:9px;justify-content:center;margin-bottom:12px}
.opt{
  padding:9px 20px;border-radius:40px;border:2.5px solid #e8d5ff;
  background:#fff;font-family:var(--f-display);font-size:1.1rem;
  cursor:pointer;transition:.2s;color:var(--board);
}
.opt:hover{border-color:var(--violet);background:#faf0ff;transform:scale(1.04)}
.opt.ok{background:var(--mint);color:#003d22;border-color:#00a862;font-weight:800}
.opt.no{background:var(--coral);color:#fff;border-color:#cc1840}
.opts-2x2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.opt-big{
  padding:14px;border-radius:16px;border:2.5px solid #e8d5ff;
  background:#fff;font-family:var(--f-display);font-size:1.3rem;
  cursor:pointer;transition:.2s;color:var(--board);text-align:center;
}
.opt-big:hover{border-color:var(--violet);background:#faf0ff;transform:scale(1.04)}
.opt-big.ok{background:#d1fae5;border-color:var(--mint)}
.opt-big.no{background:#fee2e2;border-color:var(--coral)}
/* memory */
.mem-g{display:grid;grid-template-columns:repeat(4,1fr);gap:8px;margin-bottom:14px}
.mem-c{
  aspect-ratio:1;border-radius:12px;
  background:linear-gradient(135deg,var(--board),var(--violet));
  color:#fff;font-size:1.3rem;display:flex;align-items:center;justify-content:center;
  cursor:pointer;border:none;transition:.25s;box-shadow:0 3px 10px rgba(107,33,168,.25);
}
.mem-c.flip,.mem-c.done{background:#fff;border:3px solid var(--mint);color:var(--board)}
.mem-c.done{opacity:.5;cursor:default}
.mem-c:hover:not(.done){transform:scale(1.08) rotate(-2deg)}
/* syllable builder */
.syl-bank{display:flex;flex-wrap:wrap;gap:8px;justify-content:center;margin-bottom:12px}
.syl-chip{
  padding:9px 18px;border-radius:40px;
  background:linear-gradient(135deg,var(--board),var(--violet));color:#fff;
  font-family:var(--f-display);font-size:1.05rem;cursor:pointer;
  transition:.2s;box-shadow:0 3px 12px rgba(107,33,168,.3);
}
.syl-chip:hover{background:linear-gradient(135deg,var(--coral),#FF7A00);transform:scale(1.06)}
.syl-chip.used{opacity:.3;pointer-events:none}
.drop-z{
  min-height:54px;border:2.5px dashed #e8d5ff;border-radius:14px;
  padding:10px 12px;display:flex;flex-wrap:wrap;gap:8px;align-items:center;
  margin-bottom:12px;background:#fdfaff;transition:.2s;
}
.placed{
  padding:7px 16px;border-radius:40px;
  background:linear-gradient(135deg,var(--sky),#0060D0);color:#fff;
  font-family:var(--f-display);font-size:.98rem;cursor:pointer;transition:.2s;
}
.placed:hover{background:linear-gradient(135deg,var(--coral),#FF7A00)}
.hint-txt{color:#d4b8f0;font-size:.82rem;align-self:center;margin:auto}
.game-action-row{display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-top:6px}
.restart{
  width:100%;padding:12px;border-radius:40px;border:none;
  background:linear-gradient(135deg,var(--board),var(--violet));
  color:#fff;font-weight:700;font-size:.95rem;
  cursor:pointer;margin-top:12px;transition:.2s;
  box-shadow:0 4px 14px rgba(107,33,168,.3);
}
.restart:hover{opacity:.9;transform:translateY(-2px)}
.end-card{text-align:center;padding:16px 0}
.end-em{font-size:4.5rem;display:block;animation:pop .5s ease}
.end-h{font-family:var(--f-display);font-size:2rem;color:var(--board);margin:10px 0 6px}
.end-msg{color:var(--soft);font-size:.9rem;background:linear-gradient(135deg,#fff9ec,#fce7ff);
  border-radius:14px;padding:14px;margin-bottom:18px;line-height:1.65;border:2px solid #e8d5ff}
.end-btns{display:flex;gap:10px;justify-content:center;flex-wrap:wrap}

/* ====================================================
   AVANCES
   ==================================================== */
#avances{background:linear-gradient(160deg,#fff9ec 0%,#fce7ff 100%)}
.av-layout{display:grid;grid-template-columns:290px 1fr;gap:26px;align-items:start}
@media(max-width:820px){.av-layout{grid-template-columns:1fr}}
.av-form{
  background:linear-gradient(160deg,#6B21A8,#A855F7);
  border-radius:var(--r-lg);padding:28px;color:#fff;position:sticky;top:74px;
  box-shadow:0 8px 32px rgba(107,33,168,.35);
}
.av-form h3{font-family:var(--f-display);font-size:1.35rem;color:var(--sun);margin-bottom:6px}
.av-form p{font-size:.83rem;opacity:.8;margin-bottom:20px;line-height:1.65}
.af-g{margin-bottom:13px}
.af-g label{display:block;font-size:.78rem;font-weight:700;opacity:.85;margin-bottom:5px}
.af-inp{
  width:100%;padding:10px 13px;border:none;border-radius:10px;
  font-family:var(--f-body);font-size:.9rem;
  background:rgba(255,255,255,.18);color:#fff;outline:none;transition:.2s;
}
.af-inp::placeholder{color:rgba(255,255,255,.45)}
.af-inp:focus{background:rgba(255,255,255,.28)}
.af-inp option{background:#6B21A8;color:#fff}
.av-search{
  width:100%;padding:12px;border-radius:40px;border:none;
  background:var(--sun);color:var(--ink);font-weight:800;font-size:.95rem;
  cursor:pointer;margin-top:4px;transition:.2s;
  box-shadow:0 4px 16px rgba(255,224,0,.4);
}
.av-search:hover{background:#f0d800;transform:translateY(-2px);box-shadow:0 8px 24px rgba(255,224,0,.5)}
.av-panel{background:#fff;border-radius:var(--r-lg);padding:28px;box-shadow:0 4px 24px rgba(107,33,168,.10)}
.av-empty{text-align:center;padding:40px 0;color:#c9a8e8}
.av-empty .em{font-size:4rem;display:block;margin-bottom:12px}
.av-student{display:flex;align-items:center;gap:14px;
  background:linear-gradient(135deg,#fff9ec,#fce7ff);
  padding:14px 18px;border-radius:14px;margin-bottom:20px;border:2px solid #e8d5ff}
.av-av{width:48px;height:48px;border-radius:50%;
  background:linear-gradient(135deg,var(--sun),var(--orange));
  display:flex;align-items:center;justify-content:center;font-size:1.4rem;flex-shrink:0}
.av-nm{font-weight:800;color:var(--board);font-size:1rem}
.av-meta{font-size:.8rem;color:var(--soft)}
.metrics{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:20px}
@media(max-width:460px){.metrics{grid-template-columns:1fr 1fr}}
.met-box{background:linear-gradient(135deg,#fff9ec,#fce7ff);border-radius:12px;padding:14px;text-align:center;border:2px solid #e8d5ff}
.met-v{font-family:var(--f-display);font-size:1.85rem;font-weight:800}
.met-l{font-size:.68rem;font-weight:700;color:var(--soft);text-transform:none;letter-spacing:.3px}
.mv-coral{color:var(--coral)}.mv-mint{color:#00a862}.mv-sky{color:#0060D0}
.sk-title{font-weight:800;font-size:.88rem;color:var(--board);margin-bottom:11px}
.sk-row{margin-bottom:11px}
.sk-lbl{display:flex;justify-content:space-between;font-size:.8rem;font-weight:600;margin-bottom:4px;color:var(--ink)}
.sk-bar{height:13px;background:#ede0ff;border-radius:40px;overflow:hidden}
.sk-fill{height:100%;border-radius:40px;width:0;transition:width 1.1s ease}
.sf-coral{background:linear-gradient(90deg,var(--coral),var(--orange))}
.sf-mint{background:linear-gradient(90deg,var(--mint),var(--sky))}
.sf-sky{background:linear-gradient(90deg,var(--sky),var(--violet))}
.sf-violet{background:linear-gradient(90deg,var(--violet),var(--coral))}
.badges-w{display:flex;flex-wrap:wrap;gap:8px;margin-top:14px}
.badge{display:flex;align-items:center;gap:5px;padding:6px 14px;border-radius:40px;
  background:linear-gradient(135deg,#fff9ec,#fce7ff);
  font-size:.78rem;font-weight:700;color:var(--board);border:2px solid #e8d5ff}

/* ====================================================
   CHAT CTA
   ==================================================== */
#chat{
  background:linear-gradient(135deg,#FFE000 0%,#FF7A00 50%,#FF3D6B 100%);
  padding:70px 5%;text-align:center;
}
#chat h2{font-family:var(--f-display);font-size:clamp(1.8rem,3.5vw,2.6rem);
  color:var(--white);margin-bottom:12px;font-weight:800;text-shadow:0 2px 8px rgba(0,0,0,.18)}
#chat p{color:rgba(255,255,255,.88);font-size:1rem;max-width:500px;margin:0 auto 30px}
.wa-btn{
  display:inline-flex;align-items:center;gap:13px;
  background:var(--white);color:var(--board);padding:17px 36px;
  border-radius:40px;font-weight:800;font-size:1.1rem;
  box-shadow:0 8px 30px rgba(0,0,0,.2);transition:.25s;
  animation:glow 2.5s ease-in-out infinite;
}
@keyframes glow{0%,100%{box-shadow:0 8px 30px rgba(0,0,0,.2)}50%{box-shadow:0 16px 50px rgba(0,0,0,.35)}}
.wa-btn:hover{transform:scale(1.06) translateY(-4px);background:#fff9ec}
.wa-btn .wa-ico{font-size:1.6rem}

/* ====================================================
   SEMANAS DOCENTE
   ==================================================== */
#docentes{background:linear-gradient(160deg,#e8f9ff 0%,#fff9ec 100%)}
.wk-tabs{display:flex;gap:8px;justify-content:center;flex-wrap:wrap;margin-bottom:30px}
.wk-tab{
  padding:8px 20px;border-radius:40px;border:2.5px solid var(--sky);
  background:#fff;font-weight:700;font-size:.82rem;color:#0060D0;cursor:pointer;transition:.2s;
}
.wk-tab.on{background:linear-gradient(135deg,var(--sky),#0060D0);color:#fff;border-color:transparent;
  box-shadow:0 4px 16px rgba(0,180,255,.35)}
.wk-pane{display:none}
.wk-pane.show{display:block}
.wk-header{
  background:linear-gradient(135deg,var(--board),var(--violet));
  border-radius:16px;padding:18px 24px;margin-bottom:18px;
  box-shadow:0 4px 18px rgba(107,33,168,.25);
}
.wk-header h3{font-family:var(--f-display);font-size:1.3rem;color:var(--sun);margin-bottom:3px}
.wk-header p{color:rgba(255,255,255,.7);font-size:.84rem}
.wk-tasks{display:flex;flex-direction:column;gap:11px;margin-bottom:24px}
.wk-task{
  background:#fff;border-radius:14px;padding:16px 20px;
  border-left:5px solid var(--sky);transition:.2s;
  box-shadow:0 2px 12px rgba(0,180,255,.10);
}
.wk-task:hover{transform:translateX(5px);border-left-color:var(--violet)}
.wk-task h4{font-weight:800;color:var(--board);font-size:.95rem;margin-bottom:4px}
.wk-task p{font-size:.84rem;color:var(--soft);line-height:1.6;margin-bottom:9px}
.wk-tags{display:flex;gap:8px;flex-wrap:wrap}
.wk-tag{font-size:.72rem;font-weight:700;padding:3px 12px;border-radius:40px}
.wt-b{background:#cff4ff;color:#0060D0}.wt-g{background:#d1fae5;color:#065f46}.wt-n{background:#ede0ff;color:var(--board)}
.upload-box{background:#fff;border-radius:var(--r-lg);padding:28px;max-width:700px;margin:0 auto;
  box-shadow:0 4px 24px rgba(0,180,255,.12);border:2px solid #cff4ff}
.upload-box h3{font-family:var(--f-display);font-size:1.35rem;color:var(--board);margin-bottom:5px}
.upload-box p{color:var(--soft);font-size:.86rem;margin-bottom:18px}
.ub-row{display:flex;gap:11px;flex-wrap:wrap;margin-bottom:11px}
.ub-inp{
  flex:1;min-width:130px;padding:10px 14px;border:2.5px solid #cff4ff;
  border-radius:var(--r-sm);font-family:var(--f-body);font-size:.9rem;
  outline:none;transition:.2s;background:#f8feff;
}
.ub-inp:focus{border-color:var(--sky);box-shadow:0 0 0 3px rgba(0,180,255,.12)}
.ub-sel{
  width:100%;padding:10px 14px;border:2.5px solid #cff4ff;border-radius:var(--r-sm);
  font-family:var(--f-body);font-size:.9rem;outline:none;
  transition:.2s;background:#f8feff;margin-bottom:11px;
}
.ub-sel:focus{border-color:var(--sky)}
.ub-ta{
  width:100%;padding:12px;border:2.5px solid #cff4ff;border-radius:var(--r-sm);
  font-family:var(--f-body);font-size:.9rem;resize:vertical;
  min-height:96px;outline:none;transition:.2s;background:#f8feff;margin-bottom:13px;
}
.ub-ta:focus{border-color:var(--sky)}

/* ====================================================
   VIDEOS
   ==================================================== */
#videos{background:var(--board)}
.vids-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:20px}
.vid-card{background:rgba(255,255,255,.08);border-radius:var(--r-md);overflow:hidden;cursor:pointer;transition:.3s;border:2px solid rgba(255,255,255,.1)}
.vid-card:hover{transform:translateY(-6px);box-shadow:0 20px 50px rgba(0,0,0,.4)}
.vid-thumb{position:relative;aspect-ratio:16/9;overflow:hidden;background:#111a33}
.vid-thumb img{width:100%;height:100%;object-fit:cover;transition:.35s}
.vid-card:hover .vid-thumb img{transform:scale(1.06)}
.vid-play-ring{position:absolute;inset:0;display:flex;align-items:center;justify-content:center}
.vid-play-ring div{
  width:50px;height:50px;border-radius:50%;background:rgba(255,255,255,.9);
  display:flex;align-items:center;justify-content:center;
  font-size:1.2rem;transition:.2s;box-shadow:0 4px 18px rgba(0,0,0,.3);
}
.vid-card:hover .vid-play-ring div{background:var(--sun);transform:scale(1.12)}
.vid-dur{position:absolute;bottom:7px;right:8px;background:rgba(0,0,0,.72);
  color:#fff;font-size:.68rem;font-weight:700;padding:2px 7px;border-radius:5px}
.vid-info{padding:15px}
.vid-info h4{font-family:var(--f-display);font-size:1.05rem;color:#fff;margin-bottom:4px}
.vid-info p{font-size:.78rem;color:rgba(255,255,255,.48);line-height:1.5}
/* vid modal */
.vmod{background:#000;border-radius:16px;overflow:hidden;max-width:760px;width:100%;position:relative}
.vmod iframe{width:100%;aspect-ratio:16/9;border:none;display:block}
.vmod-x{position:absolute;top:9px;right:10px;background:rgba(255,255,255,.15);border:none;
  border-radius:50%;width:32px;height:32px;font-size:1rem;color:#fff;
  cursor:pointer;z-index:10;display:flex;align-items:center;justify-content:center;transition:.2s}
.vmod-x:hover{background:rgba(255,255,255,.3)}

/* ====================================================
   FOOTER
   ==================================================== */
footer{
  background:linear-gradient(135deg,#2D1654 0%,#6B21A8 100%);
  color:rgba(255,255,255,.65);padding:48px 5% 26px;text-align:center;
}
.foot-logo{font-family:var(--f-display);font-size:1.9rem;color:var(--sun);margin-bottom:8px}
footer p{font-size:.82rem;margin-top:10px}
.foot-links{display:flex;gap:14px;justify-content:center;flex-wrap:wrap;margin-top:16px}
.foot-links a{color:rgba(255,255,255,.4);font-weight:700;font-size:.8rem;transition:.2s}
.foot-links a:hover{color:var(--sun)}

/* ====================================================
   TOAST
   ==================================================== */
.toast{
  position:fixed;bottom:20px;left:50%;
  transform:translateX(-50%) translateY(70px);
  padding:11px 24px;border-radius:40px;font-weight:700;font-size:.88rem;
  z-index:9999;transition:.32s;pointer-events:none;box-shadow:0 6px 24px rgba(0,0,0,.16);
}
.toast.vis{transform:translateX(-50%) translateY(0)}
.t-ok{background:linear-gradient(135deg,var(--mint),var(--sky));color:#fff}
.t-warn{background:linear-gradient(135deg,var(--coral),var(--orange));color:#fff}
.t-info{background:linear-gradient(135deg,var(--board),var(--violet));color:#fff}

/* ====================================================
   RESPONSIVE EXTRAS
   ==================================================== */
@media(max-width:768px){
  .sec{padding:60px 4%}
  .games-grid{grid-template-columns:1fr 1fr}
}
@media(max-width:480px){
  .games-grid{grid-template-columns:1fr}
  .metrics{grid-template-columns:1fr 1fr}
  .letter-board{grid-template-columns:repeat(3,60px);grid-template-rows:repeat(4,60px)}
}
</style>
</head>
<body>

<!-- ========================================
   NAV
   ======================================== -->
<nav id="nav">
  <div class="nav-brand">🦁 LeoJuego <sup>EDU</sup></div>
  <div class="nav-links">
    <a href="#registro">Registro</a>
    <a href="#actividades">Actividades</a>
    <a href="#juegos">Juegos</a>
    <a href="#avances">Avances</a>
    <a href="#docentes">Docentes</a>
    <a href="#videos">Videos</a>
    <a class="nav-wa" href="https://wa.link/5v4gc0" target="_blank" rel="noopener">💬 Chat</a>
  </div>
  <button class="hamburger" onclick="toggleMob()" aria-label="Menú">
    <span></span><span></span><span></span>
  </button>
</nav>
<div class="mob-nav" id="mobNav">
  <a href="#registro" onclick="closeMob()">👤 Registro</a>
  <a href="#actividades" onclick="closeMob()">📚 Actividades</a>
  <a href="#juegos" onclick="closeMob()">🎮 Juegos</a>
  <a href="#avances" onclick="closeMob()">📊 Avances</a>
  <a href="#docentes" onclick="closeMob()">👩‍🏫 Docentes</a>
  <a href="#videos" onclick="closeMob()">🎥 Videos</a>
  <a href="https://wa.link/5v4gc0" target="_blank" style="background:var(--mint);color:var(--board)">💬 Chat con Docentes</a>
</div>

<!-- ========================================
   HERO
   ======================================== -->
<section id="hero">
  <span class="hero-ring"></span>
  <span class="hero-ring"></span>
  <span class="hero-ring"></span>
  <div class="hero-left">
    <div class="hero-tag">✨ Educación Inicial · Primera Infancia</div>
    <h1>Aprender a leer<br>es un <span class="hi">juego</span></h1>
    <p>LeoJuego es el espacio donde cada letra cobra vida. Actividades, juegos y seguimiento de avances para estudiantes, familias y docentes.</p>
    <div class="hero-btns">
      <button class="btn-sun" onclick="scrollTo('#juegos')">🎮 Empezar a jugar</button>
      <button class="btn-ghost" onclick="scrollTo('#registro')">👤 Registrarse</button>
    </div>
  </div>
  <div class="hero-right">
    <div class="letter-board">
      <div class="lb-tile">A<span class="small">árbol</span></div>
      <div class="lb-tile">E<span class="small">estrella</span></div>
      <div class="lb-tile">M<span class="small">mamá</span></div>
      <div class="lb-tile">P<span class="small">pato</span></div>
      <div class="lb-tile">I<span class="small">iguana</span></div>
      <div class="lb-tile">L<span class="small">luna</span></div>
      <div class="lb-tile">O<span class="small">oso</span></div>
      <div class="lb-tile">S<span class="small">sol</span></div>
      <div class="lb-tile">U<span class="small">uva</span></div>
      <div class="lb-tile">T<span class="small">toro</span></div>
      <div class="lb-tile">N<span class="small">nube</span></div>
      <div class="lb-tile">R<span class="small">rana</span></div>
    </div>
  </div>
</section>

<!-- ========================================
   REGISTRO
   ======================================== -->
<section id="registro" class="sec sec-white">
  <div class="sec-head">
    <span class="pill pill-violet">👤 Regístrate gratis</span>
    <h2>Crea tu cuenta en LeoJuego</h2>
    <p>Lleva el seguimiento de tus avances. El acompañante puede ser docente o padre de familia.</p>
  </div>
  <div class="reg-wrap">
    <div class="reg-card">
      <div id="regForm">
        <h3>📝 Formulario de registro</h3>
        <p class="sub">Completa los datos del estudiante y de quien lo acompaña en esta experiencia de aprendizaje virtual.</p>
        <div class="fgrid">
          <div class="fg"><label>Nombre del estudiante *</label><input id="rNom" type="text" placeholder="Ej: Valentina Ruiz"/></div>
          <div class="fg"><label>Edad *</label><input id="rEdad" type="number" placeholder="5 o 6" min="3" max="10"/></div>
        </div>
        <div class="fgrid">
          <div class="fg"><label>Grado / Nivel *</label>
            <select id="rGrado">
              <option value="">Seleccionar...</option>
              <option>Pre-Jardín</option><option>Jardín</option>
              <option>Transición</option><option>Grado 1°</option>
            </select>
          </div>
          <div class="fg"><label>Institución (opcional)</label><input id="rInst" type="text" placeholder="Nombre del colegio"/></div>
        </div>
        <div class="fg" style="margin-bottom:14px">
          <label>Nombre de quien acompaña *</label>
          <input id="rAcomp" type="text" placeholder="Nombre completo del acompañante"/>
        </div>
        <div class="fg" style="margin-bottom:14px">
          <label>Correo electrónico *</label>
          <input id="rEmail" type="email" placeholder="correo@ejemplo.com"/>
        </div>
        <div class="fg" style="margin-bottom:18px">
          <label>El acompañante es *</label>
          <div class="acomp-opts">
            <button class="acomp-btn" id="btnDoc" onclick="setRol('docente')">👩‍🏫 Docente</button>
            <button class="acomp-btn" id="btnCuid" onclick="setRol('cuidador')">👨‍👩‍👧 Padre / Cuidador</button>
          </div>
        </div>
        <div class="supa-note">
          <strong>📡 Integración con Supabase</strong><br>
          Los datos se envían automáticamente a tu base de datos Supabase. Para activarlo:<br>
          1. Crea una tabla <code>registros</code> en tu proyecto de Supabase.<br>
          2. Reemplaza <code>SUPABASE_URL</code> y <code>SUPABASE_ANON_KEY</code> en el script al final de este archivo.<br>
          3. ¡Listo! Cada registro llega a tu panel de Supabase en tiempo real.
        </div>
        <button class="btn-board" style="width:100%;justify-content:center;padding:13px" onclick="registrar()">🚀 Registrarme en LeoJuego</button>
      </div>
      <div class="reg-ok" id="regOk">
        <span class="big" id="regIco">🎉</span>
        <h4 id="regMsgH">¡Bienvenido a LeoJuego!</h4>
        <p id="regMsgP">Datos guardados correctamente. ¡Explora los juegos y actividades!</p>
        <button class="btn-board" onclick="newReg()">➕ Registrar otro estudiante</button>
      </div>
      <div class="users-log" id="usersLog">
        <h5>Registros en esta sesión</h5>
        <div id="usersChips"></div>
      </div>
    </div>
  </div>
</section>

<!-- ========================================
   ACTIVIDADES
   ======================================== -->
<section id="actividades" class="sec">
  <div class="sec-head">
    <span class="pill pill-sun">📚 Para todos</span>
    <h2>Actividades de lectura</h2>
    <p>Letras con sonido, ideas para casa, rondas y acompañamiento familiar.</p>
  </div>
  <div class="act-tabs">
    <button class="act-tab on" onclick="showActTab('letras',this)">🔤 Sonido de letras</button>
    <button class="act-tab" onclick="showActTab('ideas',this)">💡 Ideas en casa</button>
    <button class="act-tab" onclick="showActTab('rondas',this)">🎵 Rondas y rimas</button>
    <button class="act-tab" onclick="showActTab('familia',this)">🏠 Acompañamiento</button>
  </div>

  <div class="act-pane show" id="pLetras">
    <div class="letters-hint">🔊 Toca el <strong>parlante</strong> de cada letra para escuchar su sonido. ¡Repite en voz alta!</div>
    <div class="letters-deck" id="lettersDeck"></div>
  </div>

  <div class="act-pane" id="pIdeas">
    <div class="act-grid">
      <div class="act-card"><div class="ico">📖</div><h3>Lectura en voz alta</h3><p>Lee cuentos cortos 10 minutos al día. Usa voces distintas para cada personaje y pausa para preguntar qué pasará después.</p></div>
      <div class="act-card c-coral"><div class="ico">🖼️</div><h3>Lectura de imágenes</h3><p>Muestra láminas ilustradas y pide al niño que invente una historia. Estimula vocabulario oral e imaginación creativa.</p></div>
      <div class="act-card c-mint"><div class="ico">🌍</div><h3>Letras en el entorno</h3><p>Busquen letras en letreros, envases y libros del hogar. Relacionen cada letra con objetos cotidianos cercanos al niño.</p></div>
      <div class="act-card c-sky"><div class="ico">✂️</div><h3>Álbum de letras</h3><p>Recorta letras de revistas para crear un álbum personal. Asocia cada letra con imágenes pegadas a su alrededor.</p></div>
      <div class="act-card c-violet"><div class="ico">🌟</div><h3>Diario del lector</h3><p>Con dibujos y garabatos el niño registra lo que "leyó" hoy. Celebra cada intento y valora su esfuerzo de expresión.</p></div>
      <div class="act-card c-coral"><div class="ico">🎨</div><h3>Escritura creativa</h3><p>Escribe el nombre del niño con arena, pintura o plastilina. Fortalece la motricidad fina y el reconocimiento de letras.</p></div>
    </div>
  </div>

  <div class="act-pane" id="pRondas">
    <div class="act-grid">
      <div class="act-card"><div class="ico">🎵</div><h3>Rondas fonológicas</h3><p>Canta "A, E, I, O, U" aplaudiendo cada vocal. Ayuda a reconocer sonidos y prepara la conciencia fonológica base.</p></div>
      <div class="act-card c-mint"><div class="ico">🌀</div><h3>Trabalenguas</h3><p>"Pablito clavó un clavito..." Practica diariamente para mejorar pronunciación, fluidez verbal y articulación de sonidos.</p></div>
      <div class="act-card c-coral"><div class="ico">🐾</div><h3>Rimas de animales</h3><p>Inventa rimas con animales: "La rana Mariana toca campana." Refuerza reconocimiento de sonidos finales iguales.</p></div>
      <div class="act-card c-sky"><div class="ico">👏</div><h3>Palmadas por sílabas</h3><p>Palmea cada sílaba al decir una palabra: MA-RI-PO-SA (4 palmadas). Actividad ideal para grupos pequeños en clase.</p></div>
    </div>
  </div>

  <div class="act-pane" id="pFamilia">
    <div class="act-grid">
      <div class="act-card"><div class="ico">🏠</div><h3>Sonidos del hogar</h3><p>Escuchen juntos sonidos del hogar (agua, timbre, pasos) e identifiquen qué objeto los produce. Conecta el sonido con la palabra.</p></div>
      <div class="act-card c-coral"><div class="ico">🛒</div><h3>Lista del mercado</h3><p>En el mercado, identifiquen productos que inicien con la misma letra. Convierte las compras en una búsqueda de letras divertida.</p></div>
      <div class="act-card c-mint"><div class="ico">📦</div><h3>Caja de palabras</h3><p>Llena una caja con objetos pequeños. El niño los saca, los nombra y busca la letra inicial en un abecedario ilustrado.</p></div>
      <div class="act-card c-sky"><div class="ico">🌙</div><h3>Cuento de buenas noches</h3><p>Antes de dormir, lee un cuento breve. Pide al niño que señale una letra que reconoce en la página. Solo 5 minutos.</p></div>
    </div>
  </div>
</section>

<!-- ========================================
   JUEGOS GAMIFICADOS
   ======================================== -->
<section id="juegos" class="sec sec-white">
  <div class="sec-head">
    <span class="pill pill-coral">🎮 Jugar</span>
    <h2>Juegos interactivos</h2>
    <p>Ocho juegos para niños de 5 a 6 años: vocales, consonantes, sílabas, palabras y el gran circuito final.</p>
  </div>
  <div class="games-grid">
    <div class="game-card">
      <div class="gc-top gc-t1"><span class="em">🎵</span><h3>Reconoce las Vocales</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-g"></span>Nivel inicial</div>
        <p>Escucha la palabra y elige qué vocal está al inicio. ¡Aprende A, E, I, O, U jugando!</p>
        <button class="gc-play gp1" onclick="openGame('vocales')">▶ Jugar</button></div>
    </div>
    <div class="game-card">
      <div class="gc-top gc-t2"><span class="em">🔡</span><h3>Consonantes M y P</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-g"></span>Nivel inicial</div>
        <p>Identifica si la palabra empieza con M o con P. Practica las consonantes más usadas en primeras lecturas.</p>
        <button class="gc-play gp2" onclick="openGame('consonantes')">▶ Jugar</button></div>
    </div>
    <div class="game-card">
      <div class="gc-top gc-t3"><span class="em">👂</span><h3>Sonido Inicial</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-y"></span>Nivel medio</div>
        <p>Mira la imagen e identifica el sonido con el que comienza esa palabra. ¡Agudiza tu oído!</p>
        <button class="gc-play gp3" onclick="openGame('sonidoInicial')">▶ Jugar</button></div>
    </div>
    <div class="game-card">
      <div class="gc-top gc-t4"><span class="em">🃏</span><h3>Memoria Fonema-Grafema</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-y"></span>Nivel medio</div>
        <p>Encuentra las parejas: letra mayúscula con minúscula, o imagen con su letra inicial. ¡Entrena tu memoria!</p>
        <button class="gc-play gp4" onclick="openGame('memoria')">▶ Jugar</button></div>
    </div>
    <div class="game-card">
      <div class="gc-top gc-t5"><span class="em">🧩</span><h3>Sílabas MA-ME-MI-MO-MU</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-y"></span>Nivel medio</div>
        <p>Forma palabras usando las sílabas directas de la letra M. ¡Toca las sílabas en el orden correcto!</p>
        <button class="gc-play gp5" onclick="openGame('silabasM')">▶ Jugar</button></div>
    </div>
    <div class="game-card">
      <div class="gc-top gc-t6"><span class="em">🔤</span><h3>Sílabas PA-PE-PI-PO-PU</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-y"></span>Nivel medio</div>
        <p>Construye palabras usando las sílabas directas de la letra P. ¡Toca el orden correcto!</p>
        <button class="gc-play gp6" onclick="openGame('silabasP')">▶ Jugar</button></div>
    </div>
    <div class="game-card">
      <div class="gc-top gc-t7"><span class="em">🖼️</span><h3>Palabra e Imagen</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-r"></span>Nivel avanzado</div>
        <p>Une cada palabra sencilla con su imagen correspondiente. Practica lectura y comprensión visual.</p>
        <button class="gc-play gp7" onclick="openGame('palabraImagen')">▶ Jugar</button></div>
    </div>
    <div class="game-card">
      <div class="gc-top gc-t8"><span class="em">🏆</span><h3>Circuito de Retos</h3></div>
      <div class="gc-body"><div class="gc-level"><span class="gc-dot dl-r"></span>Reto integral</div>
        <p>¡El gran reto! Integra vocales, consonantes, sílabas y palabras en un circuito completo de LeoJuego.</p>
        <button class="gc-play gp8" onclick="openGame('circuito')">▶ Jugar</button></div>
    </div>
  </div>
</section>

<!-- MODAL JUEGOS -->
<div class="overlay" id="gameOverlay">
  <div class="modal">
    <button class="m-x" onclick="closeGame()">✕</button>
    <div id="gameContent"></div>
  </div>
</div>

<!-- ========================================
   AVANCES
   ======================================== -->
<section id="avances" class="sec">
  <div class="sec-head">
    <span class="pill pill-mint">📊 Seguimiento</span>
    <h2>Avances del estudiante</h2>
    <p>Padres y docentes pueden consultar el progreso lector de cada niño en tiempo real.</p>
  </div>
  <div class="av-layout">
    <div class="av-form">
      <h3>Consultar progreso</h3>
      <p>Ingresa los datos del estudiante para ver su reporte de avance.</p>
      <div class="af-g"><label>Nombre del estudiante</label><input class="af-inp" id="avNom" type="text" placeholder="Ej: Valentina Ruiz"/></div>
      <div class="af-g"><label>Rol</label>
        <select class="af-inp" id="avRol">
          <option value="">Seleccionar...</option>
          <option>Docente</option><option>Padre / Madre de familia</option><option>Cuidador</option>
        </select>
      </div>
      <div class="af-g"><label>Grado</label>
        <select class="af-inp" id="avGrado">
          <option value="">Seleccionar...</option>
          <option>Pre-Jardín</option><option>Jardín</option>
          <option>Transición</option><option>Grado 1°</option>
        </select>
      </div>
      <button class="av-search" onclick="searchAv()">🔎 Ver avances</button>
    </div>
    <div class="av-panel" id="avPanel">
      <div class="av-empty"><span class="em">📋</span><p>Consulta el progreso de un estudiante ingresando su nombre arriba.</p></div>
    </div>
  </div>
</section>

<!-- ========================================
   CHAT CTA
   ======================================== -->
<section id="chat">
  <h2>¿Tienes alguna duda?</h2>
  <p>Comunícate directamente con los docentes de LeoJuego para resolver preguntas sobre el aprendizaje de tu hijo.</p>
  <a class="wa-btn" href="https://wa.link/5v4gc0" target="_blank" rel="noopener">
    <span class="wa-ico">💬</span> Chat con Docentes
  </a>
</section>

<!-- ========================================
   SEMANAS DOCENTE
   ======================================== -->
<section id="docentes" class="sec sec-white">
  <div class="sec-head">
    <span class="pill pill-sky">👩‍🏫 Zona docente</span>
    <h2>Trabajo en casa por semanas</h2>
    <p>Guías publicadas cada 3 semanas con actividades de lectura para reforzar en el hogar.</p>
  </div>
  <div class="wk-tabs">
    <button class="wk-tab on" onclick="showWk(1,this)">Semanas 1–3</button>
    <button class="wk-tab" onclick="showWk(2,this)">Semanas 4–6</button>
    <button class="wk-tab" onclick="showWk(3,this)">Semanas 7–9</button>
    <button class="wk-tab" onclick="showWk(4,this)">Semanas 10–12</button>
  </div>
  <div class="wk-pane show" id="wk1">
    <div class="wk-header"><h3>📅 Semanas 1–3 · Reconocimiento vocal</h3><p>Primer período · Conciencia fonológica inicial</p></div>
    <div class="wk-tasks" id="twk1">
      <div class="wk-task"><h4>Las vocales en casa</h4><p>Canta la canción de las vocales señalando objetos del hogar que inicien con cada una. 3 veces por semana, 10 minutos.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 1</span><span class="wk-tag wt-g">Transición</span><span class="wk-tag wt-n">Profa. Ana</span></div></div>
      <div class="wk-task"><h4>Álbum de imágenes vocales</h4><p>Recorta imágenes que inicien con cada vocal. Pégalas en una hoja y decóralas juntos en familia.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 2</span><span class="wk-tag wt-g">Jardín</span><span class="wk-tag wt-n">Profa. Mariana</span></div></div>
      <div class="wk-task"><h4>Trazos de vocales</h4><p>Practica el trazo de las vocales en arena o plastilina. Fortalece la motricidad fina y el reconocimiento visual de letras.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 3</span><span class="wk-tag wt-g">Pre-Jardín</span><span class="wk-tag wt-n">Profa. Luz</span></div></div>
    </div>
  </div>
  <div class="wk-pane" id="wk2">
    <div class="wk-header"><h3>📅 Semanas 4–6 · Consonantes M y P</h3><p>Segundo período · Letras M, P y sílabas directas</p></div>
    <div class="wk-tasks" id="twk2">
      <div class="wk-task"><h4>La letra M en casa</h4><p>Identifiquen objetos que inicien con M: mesa, mano, maíz. Dibujen cada objeto y escriban la letra M a su lado.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 4</span><span class="wk-tag wt-g">Transición</span><span class="wk-tag wt-n">Profa. Ana</span></div></div>
      <div class="wk-task"><h4>La letra P con papá y mamá</h4><p>Identifiquen objetos con P: pato, pan, papá, piso. Repitan las sílabas PA-PE-PI-PO-PU aplaudiendo cada una.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 5</span><span class="wk-tag wt-g">Jardín</span><span class="wk-tag wt-n">Profa. Mariana</span></div></div>
      <div class="wk-task"><h4>Sílabas MA-ME-MI con tarjetas</h4><p>Crea tarjetas con sílabas de la M. Forma palabras combinándolas: MANO, MIMO, MESA, MIEL.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 6</span><span class="wk-tag wt-g">Grado 1°</span><span class="wk-tag wt-n">Profa. Luz</span></div></div>
    </div>
  </div>
  <div class="wk-pane" id="wk3">
    <div class="wk-header"><h3>📅 Semanas 7–9 · Sílabas y palabras sencillas</h3><p>Tercer período · Formación y lectura de palabras con imágenes</p></div>
    <div class="wk-tasks" id="twk3">
      <div class="wk-task"><h4>Sílabas PA-PE-PI-PO-PU</h4><p>Forma palabras con tarjetas de la letra P: PATO, PIPA, PUMA. Escríbelas y dibuja la imagen junto a cada una.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 7</span><span class="wk-tag wt-g">Transición</span><span class="wk-tag wt-n">Profa. Ana</span></div></div>
      <div class="wk-task"><h4>Palabras con imagen</h4><p>Imprime palabras simples (MAMA, PIPA, MAPA). El niño lee y señala la imagen correcta entre tres opciones.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 8</span><span class="wk-tag wt-g">Jardín</span><span class="wk-tag wt-n">Profa. Mariana</span></div></div>
    </div>
  </div>
  <div class="wk-pane" id="wk4">
    <div class="wk-header"><h3>📅 Semanas 10–12 · Comprensión y circuito final</h3><p>Cuarto período · Comprensión, asociación y retos integradores</p></div>
    <div class="wk-tasks" id="twk4">
      <div class="wk-task"><h4>Mi primer libro</h4><p>Dobla 4 hojas para crear un mini libro. El niño ilustra y dicta una oración para cada página. Léanlo juntos cada noche.</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 10</span><span class="wk-tag wt-g">Grado 1°</span><span class="wk-tag wt-n">Profa. Ana</span></div></div>
      <div class="wk-task"><h4>Circuito en familia</h4><p>Realicen el circuito de retos de LeoJuego juntos: vocales → consonantes → sílabas → palabras. ¡Celebren cada logro!</p><div class="wk-tags"><span class="wk-tag wt-b">Sem. 12</span><span class="wk-tag wt-g">Todos los niveles</span><span class="wk-tag wt-n">Equipo LeoJuego</span></div></div>
    </div>
  </div>

  <div class="upload-box" style="margin-top:40px">
    <h3>📤 Publicar nueva actividad</h3>
    <p>Docentes: agrega una guía para que las familias trabajen en casa.</p>
    <select class="ub-sel" id="ubPeriod">
      <option value="">Seleccionar período...</option>
      <option value="1">Semanas 1–3</option><option value="2">Semanas 4–6</option>
      <option value="3">Semanas 7–9</option><option value="4">Semanas 10–12</option>
    </select>
    <div class="ub-row">
      <input class="ub-inp" id="ubTitle" type="text" placeholder="Título de la actividad"/>
      <input class="ub-inp" id="ubTeacher" type="text" placeholder="Nombre del docente"/>
    </div>
    <div class="ub-row">
      <input class="ub-inp" id="ubGrade" type="text" placeholder="Grado"/>
      <input class="ub-inp" id="ubWeekNum" type="text" placeholder="Semana (ej: Sem. 5)"/>
    </div>
    <textarea class="ub-ta" id="ubDesc" placeholder="Instrucciones, materiales y descripción de la actividad..."></textarea>
    <button class="btn-board" onclick="publishTask()">📤 Publicar actividad</button>
  </div>
</section>

<!-- ========================================
   VIDEOS
   ======================================== -->
<section id="videos" class="sec sec-board">
  <div class="sec-head">
    <span class="pill pill-w">🎥 Ver y aprender</span>
    <h2>Videos para reforzar en casa</h2>
    <p>Haz clic para reproducir directamente. Perfectos para niños y familias.</p>
  </div>
  <div class="vids-grid">
    <div class="vid-card" onclick="playVid('https://www.youtube.com/embed/_cROLKGHvys?autoplay=1')">
      <div class="vid-thumb"><img src="https://img.youtube.com/vi/_cROLKGHvys/hqdefault.jpg" alt="Sílabas"/>
        <div class="vid-play-ring"><div>▶</div></div><div class="vid-dur">Short</div></div>
      <div class="vid-info"><h4>🔤 Las sílabas con música</h4><p>Aprende a dividir palabras en sílabas con esta dinámica canción.</p></div>
    </div>
    <div class="vid-card" onclick="playVid('https://www.youtube.com/embed/7gbXrkiSpZ8?autoplay=1')">
      <div class="vid-thumb"><img src="https://img.youtube.com/vi/7gbXrkiSpZ8/hqdefault.jpg" alt="Lectura"/>
        <div class="vid-play-ring"><div>▶</div></div><div class="vid-dur">Video</div></div>
      <div class="vid-info"><h4>📚 Aprendiendo a leer</h4><p>Recurso completo para iniciarse en la lectura desde cero con los niños.</p></div>
    </div>
    <div class="vid-card" onclick="playVid('https://www.youtube.com/embed/n6_SSEJHadQ?autoplay=1')">
      <div class="vid-thumb"><img src="https://img.youtube.com/vi/n6_SSEJHadQ/hqdefault.jpg" alt="Vocales"/>
        <div class="vid-play-ring"><div>▶</div></div><div class="vid-dur">Video</div></div>
      <div class="vid-info"><h4>🗣️ Las vocales cantadas</h4><p>Aprende las vocales con canciones animadas y fáciles de memorizar.</p></div>
    </div>
    <div class="vid-card" onclick="playVid('https://www.youtube.com/embed/POfN48xnVJs?autoplay=1')">
      <div class="vid-thumb"><img src="https://img.youtube.com/vi/POfN48xnVJs/hqdefault.jpg" alt="Abecedario"/>
        <div class="vid-play-ring"><div>▶</div></div><div class="vid-dur">~3 min</div></div>
      <div class="vid-info"><h4>🔡 El abecedario completo</h4><p>Canción del abecedario con imágenes coloridas para niños de 4 a 6 años.</p></div>
    </div>
    <div class="vid-card" onclick="playVid('https://www.youtube.com/embed/fzUGF5n4EhU?autoplay=1')">
      <div class="vid-thumb"><img src="https://img.youtube.com/vi/fzUGF5n4EhU/hqdefault.jpg" alt="Fonemas"/>
        <div class="vid-play-ring"><div>▶</div></div><div class="vid-dur">~4 min</div></div>
      <div class="vid-info"><h4>👂 Conciencia fonológica</h4><p>Actividades para reconocer sonidos iniciales y finales en palabras.</p></div>
    </div>
    <div class="vid-card" onclick="playVid('https://www.youtube.com/embed/4-zPNZrfP5k?autoplay=1')">
      <div class="vid-thumb"><img src="https://img.youtube.com/vi/4-zPNZrfP5k/hqdefault.jpg" alt="Cuento"/>
        <div class="vid-play-ring"><div>▶</div></div><div class="vid-dur">~5 min</div></div>
      <div class="vid-info"><h4>📖 El León y el Ratón</h4><p>Cuento clásico narrado con ilustraciones. Ideal para antes de dormir.</p></div>
    </div>
  </div>
</section>

<!-- VIDEO MODAL -->
<div class="overlay" id="vidOverlay">
  <div class="vmod">
    <button class="vmod-x" onclick="closeVid()">✕</button>
    <iframe id="vidFrame" src="" allowfullscreen allow="autoplay;encrypted-media"></iframe>
  </div>
</div>

<!-- ========================================
   FOOTER
   ======================================== -->
<footer>
  <div class="foot-logo">🦁 LeoJuego</div>
  <p>Plataforma educativa para la lectura en primera infancia.<br>Diseñada con ❤️ para niños, familias y docentes.</p>
  <div class="foot-links">
    <a href="#registro">Registro</a><a href="#actividades">Actividades</a>
    <a href="#juegos">Juegos</a><a href="#avances">Avances</a>
    <a href="#docentes">Docentes</a><a href="#videos">Videos</a>
    <a href="https://wa.link/5v4gc0" target="_blank">💬 Chat</a>
  </div>
  <p style="margin-top:18px">© 2025 LeoJuego — Todos los derechos reservados</p>
</footer>

<div class="toast" id="toast"></div>

<!-- ========================================
   JAVASCRIPT
   ======================================== -->
<script>
/* ==========================================
   SUPABASE CONFIG — reemplaza tus valores
   ========================================== */
const SUPABASE_URL  = 'https://TU_PROYECTO.supabase.co';
const SUPABASE_KEY  = 'TU_SUPABASE_ANON_KEY';

async function supabaseInsert(table, data){
  try{
    const res = await fetch(`${SUPABASE_URL}/rest/v1/${table}`,{
      method:'POST',
      headers:{
        'apikey': SUPABASE_KEY,
        'Authorization': `Bearer ${SUPABASE_KEY}`,
        'Content-Type': 'application/json',
        'Prefer':'return=representation'
      },
      body: JSON.stringify(data)
    });
    return res.ok;
  }catch(e){ return false; }
}

/* ==========================================
   UTILS
   ========================================== */
const $  = id => document.getElementById(id);
const shuffle = a => [...a].sort(() => Math.random() - .5);

function scrollTo(sel){
  const el = document.querySelector(sel);
  if(el) el.scrollIntoView({behavior:'smooth'});
}
function toggleMob(){ $('mobNav').classList.toggle('open'); }
function closeMob(){ $('mobNav').classList.remove('open'); }

function toast(msg, type='ok'){
  const t = $('toast');
  t.textContent = msg;
  t.className = `toast t-${type} vis`;
  setTimeout(() => t.className = 'toast', 3000);
}
function disableAll(sel){ document.querySelectorAll(sel).forEach(b => b.disabled = true); }

/* ==========================================
   NAV SCROLL
   ========================================== */
window.addEventListener('scroll', () => {
  $('nav').style.boxShadow = scrollY > 30 ? '0 4px 24px rgba(0,0,0,.18)' : 'none';
});

/* ==========================================
   LETRAS CON SONIDO
   ========================================== */
const LETRAS_DATA = [
  {l:'A',ex:'Árbol',s:'a'},{l:'B',ex:'Barco',s:'be'},{l:'C',ex:'Casa',s:'ce'},
  {l:'D',ex:'Dado',s:'de'},{l:'E',ex:'Elefante',s:'e'},{l:'F',ex:'Flor',s:'efe'},
  {l:'G',ex:'Gato',s:'ge'},{l:'H',ex:'Hoja',s:'ache'},{l:'I',ex:'Iguana',s:'i'},
  {l:'J',ex:'Jaguar',s:'jota'},{l:'K',ex:'Kiwi',s:'ka'},{l:'L',ex:'Luna',s:'ele'},
  {l:'M',ex:'Mariposa',s:'eme'},{l:'N',ex:'Nube',s:'ene'},{l:'Ñ',ex:'Ñame',s:'eñe'},
  {l:'O',ex:'Oso',s:'o'},{l:'P',ex:'Pato',s:'pe'},{l:'Q',ex:'Queso',s:'cu'},
  {l:'R',ex:'Rana',s:'erre'},{l:'S',ex:'Sol',s:'ese'},{l:'T',ex:'Toro',s:'te'},
  {l:'U',ex:'Uva',s:'u'},{l:'V',ex:'Vaca',s:'ve'},{l:'W',ex:'Waffle',s:'doble ve'},
  {l:'X',ex:'Xilófono',s:'equis'},{l:'Y',ex:'Yoyo',s:'ye'},{l:'Z',ex:'Zapato',s:'zeta'}
];

function buildLetters(){
  const g = $('lettersDeck'); g.innerHTML = '';
  LETRAS_DATA.forEach(item => {
    const d = document.createElement('div');
    d.className = 'letter-tile';
    d.innerHTML = `<span class="lt-char">${item.l}</span>
      <span class="lt-min">${item.l.toLowerCase()}</span>
      <button class="lt-snd" onclick="speakLetter('${item.s}',this)" title="Escuchar sonido">🔊</button>
      <div class="lt-ex">${item.ex}</div>`;
    g.appendChild(d);
  });
}
buildLetters();

let activeUtter = null;
function speakLetter(sound, btn){
  if(activeUtter) speechSynthesis.cancel();
  document.querySelectorAll('.letter-tile').forEach(t => t.classList.remove('speaking'));
  btn.closest('.letter-tile').classList.add('speaking');
  if(!('speechSynthesis' in window)){
    toast('Tu navegador no soporta audio. Prueba en Chrome.','warn');
    btn.closest('.letter-tile').classList.remove('speaking');
    return;
  }
  const u = new SpeechSynthesisUtterance(sound);
  u.lang = 'es-ES'; u.rate = .65; u.pitch = 1.2; u.volume = 1;
  u.onend = () => { btn.closest('.letter-tile').classList.remove('speaking'); activeUtter = null; };
  activeUtter = u;
  speechSynthesis.speak(u);
}

/* ==========================================
   ACT TABS
   ========================================== */
function showActTab(id, btn){
  const map = {letras:'pLetras',ideas:'pIdeas',rondas:'pRondas',familia:'pFamilia'};
  document.querySelectorAll('.act-pane').forEach(p => p.classList.remove('show'));
  document.querySelectorAll('.act-tab').forEach(b => b.classList.remove('on'));
  $(map[id]).classList.add('show');
  btn.classList.add('on');
}

/* ==========================================
   REGISTRO + SUPABASE
   ========================================== */
let regUsers = [], rolSel = '';
function setRol(r){
  rolSel = r;
  $('btnDoc').classList.toggle('sel', r === 'docente');
  $('btnCuid').classList.toggle('sel', r === 'cuidador');
}
async function registrar(){
  const nom   = $('rNom').value.trim();
  const edad  = $('rEdad').value.trim();
  const grado = $('rGrado').value;
  const acomp = $('rAcomp').value.trim();
  const email = $('rEmail').value.trim();
  if(!nom||!edad||!grado||!acomp||!email||!rolSel){
    toast('Completa todos los campos obligatorios','warn'); return;
  }
  const payload = {
    nombre: nom, edad: parseInt(edad), grado, acompanante: acomp,
    email, rol: rolSel, institucion: $('rInst').value.trim(),
    fecha: new Date().toISOString()
  };
  // Enviar a Supabase
  const ok = await supabaseInsert('registros', payload);
  regUsers.push({...payload, ok});

  $('regForm').style.display = 'none';
  $('regIco').textContent = rolSel === 'docente' ? '👩‍🏫' : '🎉';
  $('regMsgH').textContent = `¡Bienvenido, ${nom}!`;
  $('regMsgP').textContent = ok
    ? `Datos guardados en Supabase ✅. Acompañado por ${acomp} (${rolSel === 'docente' ? 'Docente' : 'Padre/Cuidador'}).`
    : `Registro local guardado (configura Supabase para persistencia). Acompañado por ${acomp}.`;
  $('regOk').style.display = 'block';
  updateChips();
  toast(ok ? '✅ Registro guardado en Supabase' : '✅ Registro guardado localmente');
}
function newReg(){
  $('regForm').style.display = 'block';
  $('regOk').style.display = 'none';
  ['rNom','rEdad','rAcomp','rEmail','rInst'].forEach(id => $(id).value = '');
  $('rGrado').value = '';
  rolSel = '';
  $('btnDoc').classList.remove('sel');
  $('btnCuid').classList.remove('sel');
}
function updateChips(){
  const w = $('usersChips'); w.innerHTML = '';
  regUsers.forEach(u => {
    const c = document.createElement('span');
    c.className = `u-chip ${u.rol === 'docente' ? 'uc-doc' : 'uc-cuid'}`;
    c.textContent = `${u.nombre} (${u.grado})`;
    w.appendChild(c);
  });
  $('usersLog').style.display = 'block';
}

/* ==========================================
   SEMANAS DOCENTE
   ========================================== */
function showWk(n, btn){
  document.querySelectorAll('.wk-pane').forEach(p => p.classList.remove('show'));
  document.querySelectorAll('.wk-tab').forEach(b => b.classList.remove('on'));
  $('wk'+n).classList.add('show');
  btn.classList.add('on');
}
function publishTask(){
  const period = $('ubPeriod').value;
  const title  = $('ubTitle').value.trim();
  const desc   = $('ubDesc').value.trim();
  const teacher= $('ubTeacher').value.trim();
  const grade  = $('ubGrade').value.trim();
  const weekN  = $('ubWeekNum').value.trim();
  if(!period||!title||!desc){ toast('Selecciona período, título y descripción','warn'); return; }
  const today = new Date().toLocaleDateString('es-CO',{day:'2-digit',month:'short',year:'numeric'});
  const card = document.createElement('div'); card.className = 'wk-task';
  card.innerHTML = `<h4>${title}</h4><p>${desc}</p>
    <div class="wk-tags">
      <span class="wk-tag wt-b">${weekN||today}</span>
      ${grade?`<span class="wk-tag wt-g">${grade}</span>`:''}
      ${teacher?`<span class="wk-tag wt-n">${teacher}</span>`:''}
    </div>`;
  $('twk'+period).prepend(card);
  const tabs = document.querySelectorAll('.wk-tab');
  showWk(parseInt(period), tabs[parseInt(period)-1]);
  ['ubTitle','ubDesc','ubTeacher','ubGrade','ubWeekNum'].forEach(id => $(id).value = '');
  $('ubPeriod').value = '';
  toast('✅ Actividad publicada');
}

/* ==========================================
   AVANCES
   ========================================== */
function searchAv(){
  const nom   = $('avNom').value.trim();
  const rol   = $('avRol').value;
  const grado = $('avGrado').value || 'Transición';
  if(!nom){ toast('Ingresa el nombre del estudiante','warn'); return; }
  if(!rol){ toast('Selecciona tu rol','warn'); return; }
  const d = {
    act:   Math.floor(Math.random()*12)+8,
    games: Math.floor(Math.random()*8)+3,
    days:  Math.floor(Math.random()*18)+5,
    p: {
      voc: Math.floor(Math.random()*35)+60,
      cons:Math.floor(Math.random()*35)+50,
      sil: Math.floor(Math.random()*30)+55,
      pal: Math.floor(Math.random()*40)+40
    },
    badges:['⭐ Estrella Lectora','🎯 Constancia','📖 10 Lecturas','🔤 Abecedario'].slice(0,Math.floor(Math.random()*3)+2)
  };
  $('avPanel').innerHTML = `
    <h3 style="font-family:var(--f-display);font-size:1.3rem;color:var(--board);margin-bottom:16px">Reporte: ${nom}</h3>
    <div class="av-student">
      <div class="av-av">🦁</div>
      <div><div class="av-nm">${nom}</div><div class="av-meta">📚 ${grado} · Nivel en progreso</div></div>
    </div>
    <div class="metrics">
      <div class="met-box"><div class="met-v mv-coral">${d.act}</div><div class="met-l">Actividades</div></div>
      <div class="met-box"><div class="met-v mv-mint">${d.games}</div><div class="met-l">Juegos/sem</div></div>
      <div class="met-box"><div class="met-v mv-sky">${d.days}</div><div class="met-l">Días activo</div></div>
    </div>
    <div class="sk-title">Progreso por habilidad</div>
    ${skBar('🗣️ Vocales y fonemas',d.p.voc,'sf-coral')}
    ${skBar('🔡 Consonantes M y P',d.p.cons,'sf-sky')}
    ${skBar('🔤 Sílabas directas',d.p.sil,'sf-mint')}
    ${skBar('📖 Palabras y comprensión',d.p.pal,'sf-violet')}
    <div class="sk-title" style="margin-top:16px">Logros obtenidos</div>
    <div class="badges-w">${d.badges.map(b=>`<div class="badge">${b}</div>`).join('')}</div>`;
  setTimeout(() => {
    document.querySelectorAll('.sk-fill').forEach(b => { b.style.width = b.dataset.w + '%'; });
  }, 80);
  toast(`✅ Avances de ${nom} cargados`);
}
function skBar(label, val, cls){
  return `<div class="sk-row">
    <div class="sk-lbl"><span>${label}</span><span>${val}%</span></div>
    <div class="sk-bar"><div class="sk-fill ${cls}" data-w="${val}" style="width:0%"></div></div>
  </div>`;
}

/* ==========================================
   VIDEOS
   ========================================== */
function playVid(url){ $('vidFrame').src = url; $('vidOverlay').classList.add('open'); }
function closeVid(){ $('vidFrame').src = ''; $('vidOverlay').classList.remove('open'); }
$('vidOverlay').addEventListener('click', e => { if(e.target === $('vidOverlay')) closeVid(); });

/* ==========================================
   GAME ENGINE
   ========================================== */
function openGame(id){ $('gameContent').innerHTML = ''; $('gameOverlay').classList.add('open'); GAMES[id](); }
function closeGame(){ $('gameOverlay').classList.remove('open'); $('gameContent').innerHTML = ''; speechSynthesis.cancel(); }
$('gameOverlay').addEventListener('click', e => { if(e.target === $('gameOverlay')) closeGame(); });

function gRender(html){ $('gameContent').innerHTML = html; }
function gFb(msg, ok){
  const fb = $('gfb');
  if(fb){ fb.textContent = msg; fb.className = `m-fb ${ok?'fb-ok':'fb-no'}`; }
}
function gDisable(sel){ document.querySelectorAll(sel).forEach(b => b.disabled = true); }

function scoreBar(cur, total){
  return `<div class="m-score-bar"><span>Pregunta ${cur}/${total}</span><span class="m-pts" id="mpts">0 pts</span></div>
          <div class="m-prog"><div class="m-prog-fill" style="width:${Math.round((cur-1)/total*100)}%"></div></div>`;
}

function endScreen(title, score, max, fn){
  const pct = Math.round(score/max*100);
  const em  = pct>=80?'🌟':pct>=50?'⭐':'💪';
  const msg = pct>=80?'¡Resultado sobresaliente! Sigue practicando para ser un lector experto.'
             :pct>=50?'¡Buen trabajo! Practica un poco más para mejorar tu puntaje.'
             :'¡Sigue intentándolo! Cada intento te hace mejor lector.';
  gRender(`<div class="end-card">
    <span class="end-em">${em}</span>
    <div class="end-h">${title}</div>
    <div style="font-size:.9rem;color:var(--soft);margin:6px 0 16px">
      Puntaje: <strong>${score} de ${max}</strong> · ${pct}% de aciertos
    </div>
    <div class="end-msg">${msg}</div>
    <div class="end-btns">
      <button class="btn-mint" onclick="(${fn.toString()})()">🔄 Jugar de nuevo</button>
      <button class="btn-coral" onclick="closeGame()">✕ Cerrar</button>
    </div>
  </div>`);
}

/* ===== JUEGO 1: VOCALES ===== */
const VOCAL_Q = [
  {w:'ÁRBOL',a:'A'},{w:'ELEFANTE',a:'E'},{w:'IGUANA',a:'I'},{w:'OSO',a:'O'},{w:'UVA',a:'U'},
  {w:'AGUILA',a:'A'},{w:'ESTRELLA',a:'E'},{w:'ISLA',a:'I'},{w:'OJO',a:'O'},{w:'UNIFORME',a:'U'},
  {w:'ABEJA',a:'A'},{w:'ENERO',a:'E'}
];
let vI=0,vS=0;
function gameVocales(){ vI=0;vS=0;rVocal(); }
function rVocal(){
  if(vI>=VOCAL_Q.length){ endScreen('🎵 ¡Vocales completadas!',vS,VOCAL_Q.length,gameVocales); return; }
  const d=VOCAL_Q[vI];
  gRender(`<div class="m-h1">🎵 Reconoce las vocales</div>
    <div class="m-sub">¿Con qué vocal empieza esta palabra?</div>
    ${scoreBar(vI+1,VOCAL_Q.length)}
    <div class="big-w">${d.w}</div>
    <div class="opts-row" id="opts">
      ${shuffle(['A','E','I','O','U']).map(v=>`<button class="opt" onclick="ansV(this,'${v}','${d.a}')">${v}</button>`).join('')}
    </div>
    <div class="m-fb" id="gfb"></div>`);
}
function ansV(btn,r,c){
  gDisable('.opt');
  if(r===c){btn.classList.add('ok');vS++;gFb('✅ ¡Correcto!',true);}
  else{btn.classList.add('no');document.querySelectorAll('.opt').forEach(b=>{if(b.textContent===c)b.classList.add('ok')});gFb(`❌ Era la vocal ${c}`,false);}
  setTimeout(()=>{vI++;rVocal();},1300);
}

/* ===== JUEGO 2: CONSONANTES M y P ===== */
const CONS_Q=[
  {w:'MARIPOSA',a:'M'},{w:'PATO',a:'P'},{w:'MAMÁ',a:'M'},{w:'PELOTA',a:'P'},
  {w:'MESA',a:'M'},{w:'PIPA',a:'P'},{w:'MANO',a:'M'},{w:'PUMA',a:'P'},
  {w:'MONO',a:'M'},{w:'PIANO',a:'P'},{w:'MULA',a:'M'},{w:'PAVO',a:'P'}
];
let cI=0,cS=0;
function gameConsonantes(){ cI=0;cS=0;rCons(); }
function rCons(){
  if(cI>=CONS_Q.length){ endScreen('🔡 ¡Consonantes dominadas!',cS,CONS_Q.length,gameConsonantes); return; }
  const d=CONS_Q[cI];
  gRender(`<div class="m-h1">🔡 Consonantes M y P</div>
    <div class="m-sub">¿Con qué consonante empieza esta palabra?</div>
    ${scoreBar(cI+1,CONS_Q.length)}
    <div class="big-w">${d.w}</div>
    <div class="opts-row" id="opts">
      <button class="opt" onclick="ansC(this,'M','${d.a}')">M</button>
      <button class="opt" onclick="ansC(this,'P','${d.a}')">P</button>
    </div>
    <div class="m-fb" id="gfb"></div>`);
}
function ansC(btn,r,c){
  gDisable('.opt');
  if(r===c){btn.classList.add('ok');cS++;gFb('✅ ¡Muy bien!',true);}
  else{btn.classList.add('no');document.querySelectorAll('.opt').forEach(b=>{if(b.textContent===c)b.classList.add('ok')});gFb(`❌ Era la ${c}`,false);}
  setTimeout(()=>{cI++;rCons();},1300);
}

/* ===== JUEGO 3: SONIDO INICIAL ===== */
const SI_Q=[
  {e:'🍎',n:'Manzana',o:['M','P','S','T'],c:'M'},{e:'🐱',n:'Gato',o:['G','B','C','R'],c:'G'},
  {e:'🌙',n:'Luna',o:['N','L','D','F'],c:'L'},{e:'🐘',n:'Elefante',o:['A','E','I','O'],c:'E'},
  {e:'🦋',n:'Mariposa',o:['M','N','R','S'],c:'M'},{e:'🍕',n:'Pizza',o:['P','Q','T','V'],c:'P'},
  {e:'🌸',n:'Flor',o:['F','H','J','K'],c:'F'},{e:'🚀',n:'Cohete',o:['C','G','K','X'],c:'C'},
  {e:'🌈',n:'Arcoíris',o:['A','I','O','U'],c:'A'},{e:'🐸',n:'Rana',o:['R','N','M','T'],c:'R'},
];
let siI=0,siS=0;
function gameSonidoInicial(){ siI=0;siS=0;rSI(); }
function rSI(){
  if(siI>=SI_Q.length){ endScreen('👂 ¡Oídos entrenados!',siS,SI_Q.length,gameSonidoInicial); return; }
  const d=SI_Q[siI];
  gRender(`<div class="m-h1">👂 Sonido inicial</div>
    <div class="m-sub">¿Con qué letra empieza esta imagen?</div>
    ${scoreBar(siI+1,SI_Q.length)}
    <span class="em-big">${d.e}</span>
    <div class="sub-w">${d.n}</div>
    <div class="opts-2x2" id="opts">
      ${shuffle([...d.o]).map(o=>`<button class="opt-big" onclick="ansSI(this,'${o}','${d.c}')">${o}</button>`).join('')}
    </div>
    <div class="m-fb" id="gfb"></div>`);
}
function ansSI(btn,r,c){
  gDisable('.opt-big');
  if(r===c){btn.classList.add('ok');siS++;gFb('✅ ¡Correcto!',true);}
  else{btn.classList.add('no');document.querySelectorAll('.opt-big').forEach(b=>{if(b.textContent===c)b.classList.add('ok')});gFb(`❌ Era la letra ${c}`,false);}
  setTimeout(()=>{siI++;rSI();},1300);
}

/* ===== JUEGO 4: MEMORIA ===== */
const MEM_PAIRS=['A','B','C','D','E','F','G','H'];
let mCards=[],mFlipped=[],mMatched=0,mLock=false;
function gameMemoria(){
  mMatched=0;mFlipped=[];mLock=false;
  const pool=shuffle([...MEM_PAIRS,...MEM_PAIRS]);
  mCards=pool.map((l,i)=>({id:i,l,f:false,done:false}));
  rMem();
}
function rMem(){
  gRender(`<div class="m-h1">🃏 Memoria fonema-grafema</div>
    <div class="m-sub">Encuentra las parejas de letras iguales</div>
    <div class="m-score-bar"><span>Pares: ${mMatched}/${MEM_PAIRS.length}</span><span class="m-pts">${mMatched*10} pts</span></div>
    <div class="mem-g">
      ${mCards.map(c=>`<button class="mem-c ${c.f||c.done?'flip':''} ${c.done?'done':''}"
        onclick="flipM(${c.id})">${c.f||c.done?c.l:'?'}</button>`).join('')}
    </div>
    <div class="m-fb" id="gfb"></div>`);
  if(mMatched===MEM_PAIRS.length) setTimeout(()=>endScreen('🃏 ¡Memoria perfecta!',mMatched*10,MEM_PAIRS.length*10,gameMemoria),400);
}
function flipM(id){
  if(mLock)return; const c=mCards[id]; if(c.f||c.done)return;
  c.f=true; mFlipped.push(id); rMem();
  if(mFlipped.length===2){
    mLock=true; const[a,b]=mFlipped;
    if(mCards[a].l===mCards[b].l){mCards[a].done=mCards[b].done=true;mMatched++;mFlipped=[];mLock=false;rMem();}
    else setTimeout(()=>{mCards[a].f=mCards[b].f=false;mFlipped=[];mLock=false;rMem();},900);
  }
}

/* ===== JUEGO 5: SÍLABAS M ===== */
const SILS_M=[
  {word:'MAMÁ',syls:['MA','MÁ'],pool:['MA','MÁ','ME','MI','MO','MU']},
  {word:'MIEL',syls:['MIEL'],pool:['MO','MIEL','MU','ME','MI']},
  {word:'MANO',syls:['MA','NO'],pool:['MA','NO','ME','MU','MO','NA']},
  {word:'MESA',syls:['ME','SA'],pool:['ME','SA','MA','MI','MU','SO']},
  {word:'MIMO',syls:['MI','MO'],pool:['MI','MO','MA','ME','MU','PO']},
  {word:'MULA',syls:['MU','LA'],pool:['MU','LA','MA','ME','MI','LO']},
];
let smI=0,smS=0,smPlaced=[];
function gameSilabasM(){ smI=0;smS=0;rSilM(); }
function rSilM(){
  if(smI>=SILS_M.length){ endScreen('🧩 ¡Sílabas M dominadas!',smS,SILS_M.length,gameSilabasM); return; }
  smPlaced=[]; const d=SILS_M[smI];
  gRender(`<div class="m-h1">🧩 Sílabas MA-ME-MI-MO-MU</div>
    <div class="m-sub">Toca las sílabas en orden para formar la palabra</div>
    ${scoreBar(smI+1,SILS_M.length)}
    <div class="sub-w">¿Cómo se escribe <strong>${d.word}</strong>?</div>
    <div class="drop-z" id="dropZ"><span class="hint-txt" id="dropH">Toca sílabas para construir</span></div>
    <div class="syl-bank" id="sylBank">
      ${shuffle([...d.pool]).map(s=>`<button class="syl-chip" id="sm-${s.replace(/[^A-Z]/g,'_')}" onclick="addSylM('${s}','${d.syls.join('')}')">${s}</button>`).join('')}
    </div>
    <div class="game-action-row">
      <button class="btn-board" style="max-width:140px;padding:10px 18px" onclick="rSilM()">↩ Limpiar</button>
      <button class="btn-mint" style="max-width:140px;padding:10px 18px" onclick="checkSilM('${d.word}','${d.syls.join('')}')">✅ Verificar</button>
    </div>
    <div class="m-fb" id="gfb"></div>`);
}
function addSylM(s, target){
  const key = `sm-${s.replace(/[^A-Z]/g,'_')}`;
  const btn = $(key); if(!btn||btn.classList.contains('used'))return;
  btn.classList.add('used'); smPlaced.push(s);
  const z=$('dropZ'),h=$('dropH'); if(h)h.style.display='none';
  const p=document.createElement('button'); p.className='placed'; p.textContent=s;
  p.onclick=()=>{p.remove();smPlaced=smPlaced.filter(x=>x!==s);btn.classList.remove('used');if(!z.querySelector('.placed')&&h)h.style.display='block';};
  z.appendChild(p);
}
function checkSilM(word,correct){
  const formed=smPlaced.join('');
  if(formed===correct){smS++;gFb('✅ ¡Correcto! '+word,true);setTimeout(()=>{smI++;rSilM();},1400);}
  else gFb('❌ Intenta de nuevo. Pista: '+word,false);
}

/* ===== JUEGO 6: SÍLABAS P ===== */
const SILS_P=[
  {word:'PATO',syls:['PA','TO'],pool:['PA','TO','PE','PI','PO','PU','MA']},
  {word:'PIPA',syls:['PI','PA'],pool:['PI','PA','PE','PU','PO','MA','LA']},
  {word:'PUMA',syls:['PU','MA'],pool:['PU','MA','PA','PE','PI','MO','NA']},
  {word:'PEMO',syls:['PE','MO'],pool:['PE','MO','PA','PI','PU','ME','NO']},
  {word:'POLO',syls:['PO','LO'],pool:['PO','LO','PA','PE','PI','PU','SO']},
  {word:'PINO',syls:['PI','NO'],pool:['PI','NO','PA','PE','PO','PU','MO']},
];
let spI=0,spS=0,spPlaced=[];
function gameSilabasP(){ spI=0;spS=0;rSilP(); }
function rSilP(){
  if(spI>=SILS_P.length){ endScreen('🔤 ¡Sílabas P dominadas!',spS,SILS_P.length,gameSilabasP); return; }
  spPlaced=[]; const d=SILS_P[spI];
  gRender(`<div class="m-h1">🔤 Sílabas PA-PE-PI-PO-PU</div>
    <div class="m-sub">Forma la palabra tocando las sílabas en orden</div>
    ${scoreBar(spI+1,SILS_P.length)}
    <div class="sub-w">¿Cómo se escribe <strong>${d.word}</strong>?</div>
    <div class="drop-z" id="dropZ"><span class="hint-txt" id="dropH">Toca sílabas en orden</span></div>
    <div class="syl-bank" id="sylBank">
      ${shuffle([...d.pool]).map(s=>`<button class="syl-chip" id="sp-${s}" onclick="addSylP('${s}','${d.syls.join('')}')">${s}</button>`).join('')}
    </div>
    <div class="game-action-row">
      <button class="btn-board" style="max-width:140px;padding:10px 18px" onclick="rSilP()">↩ Limpiar</button>
      <button class="btn-mint" style="max-width:140px;padding:10px 18px" onclick="checkSilP('${d.word}','${d.syls.join('')}')">✅ Verificar</button>
    </div>
    <div class="m-fb" id="gfb"></div>`);
}
function addSylP(s,target){
  const btn=$(`sp-${s}`); if(!btn||btn.classList.contains('used'))return;
  btn.classList.add('used'); spPlaced.push(s);
  const z=$('dropZ'),h=$('dropH'); if(h)h.style.display='none';
  const p=document.createElement('button'); p.className='placed'; p.textContent=s;
  p.onclick=()=>{p.remove();spPlaced=spPlaced.filter(x=>x!==s);btn.classList.remove('used');if(!z.querySelector('.placed')&&h)h.style.display='block';};
  z.appendChild(p);
}
function checkSilP(word,correct){
  const formed=spPlaced.join('');
  if(formed===correct){spS++;gFb('✅ ¡Correcto! '+word,true);setTimeout(()=>{spI++;rSilP();},1400);}
  else gFb('❌ Intenta de nuevo',false);
}

/* ===== JUEGO 7: PALABRA-IMAGEN ===== */
const PI_Q=[
  {w:'MANO',o:['🤚','🐱','🌙','🍕'],c:0},{w:'LUNA',o:['🌸','🌙','🍎','🚀'],c:1},
  {w:'PATO',o:['🐸','🦋','🐥','🌈'],c:2},{w:'SOL',o:['🌙','⭐','☀️','🌸'],c:2},
  {w:'FLOR',o:['🌸','🌙','🍎','🐱'],c:0},{w:'PIPA',o:['🎺','🎻','🪗','🪘'],c:0},
  {w:'GATO',o:['🐘','🐸','🦋','🐱'],c:3},{w:'MARIPOSA',o:['🦋','🐱','🌙','🍕'],c:0},
];
let piI=0,piS=0;
function gamePalabraImagen(){ piI=0;piS=0;rPI(); }
function rPI(){
  if(piI>=PI_Q.length){ endScreen('🖼️ ¡Palabras e imágenes!',piS,PI_Q.length,gamePalabraImagen); return; }
  const d=PI_Q[piI];
  gRender(`<div class="m-h1">🖼️ Palabra e imagen</div>
    <div class="m-sub">Elige la imagen que corresponde a la palabra</div>
    ${scoreBar(piI+1,PI_Q.length)}
    <div class="big-w">${d.w}</div>
    <div class="opts-2x2" id="opts">
      ${d.o.map((o,i)=>`<button class="opt-big" style="font-size:2.3rem;padding:16px" onclick="ansPI(this,${i},${d.c})">${o}</button>`).join('')}
    </div>
    <div class="m-fb" id="gfb"></div>`);
}
function ansPI(btn,r,c){
  gDisable('.opt-big');
  if(r===c){btn.classList.add('ok');piS++;gFb('✅ ¡Correcto!',true);}
  else{btn.classList.add('no');document.querySelectorAll('.opt-big')[c].classList.add('ok');gFb('❌ Esa no era',false);}
  setTimeout(()=>{piI++;rPI();},1300);
}

/* ===== JUEGO 8: CIRCUITO INTEGRAL ===== */
const CIRCUIT=[
  {type:'vocal',w:'ESTRELLA',a:'E'},
  {type:'cons',w:'MARIPOSA',a:'M'},
  {type:'si',e:'🍎',n:'Manzana',o:['M','P','S','T'],c:'M'},
  {type:'pi',w:'LUNA',opts:['🌸','🌙','🍎','🚀'],c:1},
  {type:'vocal',w:'IGUANA',a:'I'},
  {type:'cons',w:'PATO',a:'P'},
  {type:'si',e:'🐱',n:'Gato',o:['G','B','C','R'],c:'G'},
  {type:'pi',w:'SOL',opts:['🌙','⭐','☀️','🌸'],c:2},
  {type:'vocal',w:'OSO',a:'O'},
  {type:'cons',w:'MONO',a:'M'},
];
let cirI=0,cirS=0;
function gameCircuito(){ cirI=0;cirS=0;rCirc(); }
function rCirc(){
  if(cirI>=CIRCUIT.length){ endScreen('🏆 ¡Circuito completado!',cirS,CIRCUIT.length,gameCircuito); return; }
  const d=CIRCUIT[cirI];
  const pct=Math.round(cirI/CIRCUIT.length*100);
  let body='';
  if(d.type==='vocal'){
    body=`<div class="big-w">${d.w}</div>
      <div style="font-size:.85rem;color:var(--soft);text-align:center;margin-bottom:10px">¿Con qué vocal empieza?</div>
      <div class="opts-row" id="opts">${shuffle(['A','E','I','O','U']).map(v=>`<button class="opt" onclick="ansCirc(this,'${v}','${d.a}')">${v}</button>`).join('')}</div>`;
  }else if(d.type==='cons'){
    body=`<div class="big-w">${d.w}</div>
      <div style="font-size:.85rem;color:var(--soft);text-align:center;margin-bottom:10px">¿M o P?</div>
      <div class="opts-row" id="opts">
        <button class="opt" onclick="ansCirc(this,'M','${d.a}')">M</button>
        <button class="opt" onclick="ansCirc(this,'P','${d.a}')">P</button>
      </div>`;
  }else if(d.type==='si'){
    body=`<span class="em-big">${d.e}</span><div class="sub-w">${d.n}</div>
      <div class="opts-2x2" id="opts">${shuffle([...d.o]).map(o=>`<button class="opt-big" onclick="ansCirc(this,'${o}','${d.c}')">${o}</button>`).join('')}</div>`;
  }else{
    body=`<div class="big-w">${d.w}</div>
      <div class="opts-2x2" id="opts">${d.opts.map((o,i)=>`<button class="opt-big" style="font-size:2rem" onclick="ansCircPI(this,${i},${d.c})">${o}</button>`).join('')}</div>`;
  }
  gRender(`<div class="m-h1">🏆 Circuito de retos</div>
    <div class="m-sub">Reto ${cirI+1} de ${CIRCUIT.length} · ${pct}% completado</div>
    <div class="m-score-bar"><span>Aciertos: ${cirS}</span><span class="m-pts">${cirS*10} pts</span></div>
    <div class="m-prog"><div class="m-prog-fill" style="width:${pct}%"></div></div>
    ${body}
    <div class="m-fb" id="gfb"></div>`);
}
function ansCirc(btn,r,c){
  gDisable('.opt,.opt-big');
  if(r===c){btn.classList.add('ok');cirS++;gFb('✅ ¡Excelente!',true);}
  else{btn.classList.add('no');document.querySelectorAll('.opt,.opt-big').forEach(b=>{if(b.textContent===c)b.classList.add('ok')});gFb(`❌ Era ${c}`,false);}
  setTimeout(()=>{cirI++;rCirc();},1300);
}
function ansCircPI(btn,r,c){
  gDisable('.opt-big');
  if(r===c){btn.classList.add('ok');cirS++;gFb('✅ ¡Excelente!',true);}
  else{btn.classList.add('no');document.querySelectorAll('.opt-big')[c].classList.add('ok');gFb('❌ No era esa',false);}
  setTimeout(()=>{cirI++;rCirc();},1300);
}

const GAMES={
  vocales:gameVocales, consonantes:gameConsonantes, sonidoInicial:gameSonidoInicial,
  memoria:gameMemoria, silabasM:gameSilabasM, silabasP:gameSilabasP,
  palabraImagen:gamePalabraImagen, circuito:gameCircuito
};
</script>
</body>
</html>
