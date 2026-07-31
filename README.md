<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Assets Lab — Comunidade de Assets & Design no Discord</title>
<link rel="icon" href="https://cdn.discordapp.com/attachments/1517004676745265172/1531244925398810695/Assets_Lab_Icon.png?ex=6a6dc877&is=6a6c76f7&hm=62c8d219d61f261f0397fa36627c82d7b05e75b1668437ed94ad40285792a742&">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@400;600;800;900&family=Space+Grotesk:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
/* ===================== BASE ===================== */
:root{
  --roxo:#8B5CF6;--roxo-2:#7C3AED;--roxo-neon:#B79CFF;--roxo-glow:rgba(139,92,246,.45);
  --discord:#5865F2;--discord-glow:rgba(88,101,242,.45);
  --preto:#050508;--preto-2:#0B0B13;--preto-3:#12121D;
  --branco:#F4F2FF;--cinza:#8E93A6;--borda:rgba(139,92,246,.22);
  --disp:'Unbounded',sans-serif;--body:'Space Grotesk',sans-serif;
  --ease:cubic-bezier(.22,1,.36,1);
}
*{margin:0;padding:0;box-sizing:border-box}
html{scroll-behavior:smooth}
body{background:var(--preto);color:var(--branco);font-family:var(--body);font-size:16px;line-height:1.6;overflow-x:hidden}
body::before{content:"";position:fixed;inset:0;z-index:0;pointer-events:none;
  background:radial-gradient(900px 600px at -8% -10%,rgba(124,58,237,.22),transparent 60%),
  radial-gradient(800px 700px at 108% 110%,rgba(88,101,242,.13),transparent 60%),
  radial-gradient(500px 400px at 85% 8%,rgba(183,156,255,.07),transparent 60%)}
body::after{content:"";position:fixed;inset:0;z-index:9995;pointer-events:none;opacity:.05;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E")}
::selection{background:var(--roxo);color:#0a0a10}
::-webkit-scrollbar{width:10px}::-webkit-scrollbar-track{background:var(--preto)}
::-webkit-scrollbar-thumb{background:#282838;border:2px solid var(--preto)}::-webkit-scrollbar-thumb:hover{background:var(--roxo)}
img{display:block;max-width:100%}a{color:inherit}button{font-family:inherit}
:focus-visible{outline:2px solid var(--roxo);outline-offset:3px}
.wrap{max-width:1240px;margin:0 auto;padding:0 24px;position:relative;z-index:2}
section{scroll-margin-top:90px}
.img-fallback{background:linear-gradient(135deg,#7C3AED 0%,#1a1a2e 100%)!important;display:grid;place-items:center;min-height:120px}
.img-fallback::after{content:"ASSETS LAB";font-family:var(--disp);font-size:.8rem;color:rgba(255,255,255,.25);letter-spacing:.2em}

/* ===================== PRELOADER ===================== */
#preloader{position:fixed;inset:0;background:var(--preto);z-index:10000;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:22px;transition:transform .8s cubic-bezier(.76,0,.24,1)}
#preloader.done{transform:translateY(-101%)}
.pre-icon{width:72px;height:72px;border-radius:22px;animation:preBlur 1s .1s var(--ease) both;box-shadow:0 0 40px var(--roxo-glow)}
.pre-logo{font-family:var(--disp);font-weight:900;font-size:clamp(1.6rem,5vw,2.6rem);letter-spacing:.02em;animation:preBlur 1s .25s var(--ease) both}
.pre-logo span{color:var(--roxo)}
.pre-bar{width:min(260px,56vw);height:2px;background:rgba(255,255,255,.12);overflow:hidden}
.pre-bar i{display:block;height:100%;width:0;background:var(--roxo);animation:load 1.3s ease forwards}
@keyframes load{to{width:100%}}
@keyframes preBlur{from{opacity:0;filter:blur(18px);transform:translateY(22px) scale(.9)}to{opacity:1;filter:blur(0);transform:none}}

/* ===================== PROGRESSO / RASTRO ===================== */
#progress{position:fixed;top:0;left:0;height:3px;width:0;background:var(--roxo);box-shadow:0 0 14px var(--roxo-glow);z-index:9999}
.trail{position:fixed;width:10px;height:10px;border-radius:50%;background:var(--roxo);filter:blur(6px);pointer-events:none;z-index:9994;transform:translate(-50%,-50%);animation:trailFade .6s ease-out forwards}
@keyframes trailFade{to{opacity:0;transform:translate(-50%,-50%) scale(.2)}}

/* ===================== TICKER ===================== */
.ticker{background:var(--roxo);color:#0a0a10;overflow:hidden;position:relative;z-index:2}
.ticker-track{display:flex;width:max-content;animation:mq 26s linear infinite}
.ticker span{font-family:var(--disp);font-weight:600;font-size:.66rem;letter-spacing:.18em;padding:.55rem 1.4rem;white-space:nowrap}
@keyframes mq{to{transform:translateX(-50%)}}

/* ===================== NAV ===================== */
#nav{position:sticky;top:0;z-index:900;background:rgba(5,5,8,.72);backdrop-filter:blur(14px);border-bottom:1px solid var(--borda);transition:.4s}
#nav.scrolled{background:rgba(5,5,8,.93)}
.nav-in{max-width:1240px;margin:0 auto;padding:16px 24px;display:flex;align-items:center;gap:28px;transition:.4s}
#nav.scrolled .nav-in{padding:10px 24px}
.logo{display:flex;align-items:center;gap:12px;text-decoration:none}
.logo img{width:40px;height:40px;border-radius:12px;transition:.4s var(--ease)}
.logo:hover img{transform:rotate(-8deg) scale(1.08)}
.logo b{font-family:var(--disp);font-weight:900;font-size:1.05rem;letter-spacing:.01em}
.logo b span{color:var(--roxo)}
.links{display:flex;gap:26px;margin-left:16px}
.links a{text-decoration:none;color:var(--cinza);font-weight:500;font-size:.9rem;position:relative;transition:.3s}
.links a::after{content:"";position:absolute;left:0;bottom:-5px;width:0;height:2px;background:var(--roxo);transition:width .35s var(--ease)}
.links a:hover{color:var(--branco)}.links a:hover::after{width:100%}
.nav-acts{margin-left:auto;display:flex;align-items:center;gap:12px}
.btn-discord{
  display:inline-flex;align-items:center;gap:10px;background:var(--discord);color:#fff;
  font-family:var(--disp);font-size:.7rem;font-weight:600;letter-spacing:.08em;text-transform:uppercase;
  padding:.85rem 1.4rem;text-decoration:none;position:relative;overflow:hidden;transition:.35s var(--ease);
  clip-path:polygon(0 0,100% 0,100% calc(100% - 10px),calc(100% - 10px) 100%,0 100%);
}
.btn-discord img{width:18px;height:18px;filter:brightness(10)}
.btn-discord::after{content:"";position:absolute;top:0;left:-80%;width:50%;height:100%;background:linear-gradient(105deg,transparent,rgba(255,255,255,.4),transparent);transform:skewX(-20deg);transition:left .55s ease}
.btn-discord:hover{background:#4752c4;transform:translateY(-3px);box-shadow:0 12px 30px -8px var(--discord-glow)}
.btn-discord:hover::after{left:140%}
.hamburger{display:none;width:42px;height:42px;background:none;border:1px solid rgba(255,255,255,.16);cursor:pointer;flex-direction:column;align-items:center;justify-content:center;gap:5px}
.hamburger span{width:18px;height:2px;background:var(--branco);transition:.35s var(--ease)}
.hamburger.open span:nth-child(1){transform:translateY(7px) rotate(45deg)}
.hamburger.open span:nth-child(2){opacity:0}
.hamburger.open span:nth-child(3){transform:translateY(-7px) rotate(-45deg)}
.mobile-menu{display:none;flex-direction:column;border-top:1px solid var(--borda);max-height:0;overflow:hidden;transition:max-height .5s var(--ease)}
.mobile-menu.open{max-height:340px}
.mobile-menu a{padding:16px 24px;text-decoration:none;color:var(--branco);font-family:var(--disp);font-size:.82rem;border-bottom:1px solid rgba(255,255,255,.05);transition:.3s}
.mobile-menu a:hover{color:var(--roxo-neon);padding-left:34px}

/* ===================== BOTÕES ===================== */
.btn{font-family:var(--disp);font-size:.75rem;font-weight:600;letter-spacing:.1em;text-transform:uppercase;padding:1.05rem 1.7rem;display:inline-flex;align-items:center;gap:.7rem;cursor:pointer;text-decoration:none;position:relative;overflow:hidden;transition:.35s var(--ease);border:0}
.btn-solid{background:var(--roxo);color:#0a0a10;clip-path:polygon(0 0,100% 0,100% calc(100% - 12px),calc(100% - 12px) 100%,0 100%)}
.btn-solid::after{content:"";position:absolute;top:0;left:-80%;width:50%;height:100%;background:linear-gradient(105deg,transparent,rgba(255,255,255,.6),transparent);transform:skewX(-20deg);transition:left .55s ease}
.btn-solid:hover{background:var(--roxo-neon);transform:translateY(-3px)}.btn-solid:hover::after{left:140%}
.btn-ghost{background:transparent;border:1px solid rgba(255,255,255,.28);color:var(--branco)}
.btn-ghost:hover{border-color:var(--roxo);color:var(--roxo-neon);background:rgba(139,92,246,.08);transform:translateY(-3px)}
.btn-big{padding:1.3rem 2.6rem;font-size:.85rem}

/* ===================== HERO ===================== */
.hero{position:relative;min-height:94vh;display:flex;align-items:center;overflow:hidden;z-index:1}
.hero-bg{position:absolute;inset:0;z-index:0}
.hero-grid{position:absolute;inset:0;
  background-image:linear-gradient(rgba(139,92,246,.06) 1px,transparent 1px),linear-gradient(90deg,rgba(139,92,246,.06) 1px,transparent 1px);
  background-size:56px 56px;
  -webkit-mask-image:radial-gradient(ellipse 80% 70% at 50% 40%,#000 30%,transparent 75%);mask-image:radial-gradient(ellipse 80% 70% at 50% 40%,#000 30%,transparent 75%)}
.orb{position:absolute;border-radius:50%;filter:blur(70px);opacity:.5}
.o1{width:420px;height:420px;background:var(--roxo-2);top:-120px;right:8%;animation:orbFloat 12s ease-in-out infinite}
.o2{width:300px;height:300px;background:#3730A3;bottom:-80px;left:-60px;animation:orbFloat 16s ease-in-out infinite reverse}
.o3{width:160px;height:160px;background:var(--roxo-neon);top:38%;left:42%;opacity:.22;animation:orbFloat 9s ease-in-out infinite}
@keyframes orbFloat{0%,100%{transform:translate(0,0)}50%{transform:translate(40px,-40px)}}
.hero-in{max-width:1240px;margin:0 auto;padding:80px 24px 60px;position:relative;z-index:2;display:grid;grid-template-columns:1fr 1.1fr;gap:50px;align-items:center;width:100%}
.eyebrow{display:inline-flex;align-items:center;gap:10px;font-family:var(--disp);font-size:.64rem;letter-spacing:.26em;color:var(--roxo-neon);border:1px solid var(--borda);padding:.6rem 1rem;opacity:0;animation:fadeUp .8s 1.45s var(--ease) forwards}
.eyebrow i{width:8px;height:8px;background:#22c55e;border-radius:50%;box-shadow:0 0 12px #22c55e;animation:blink 1.6s infinite}
@keyframes blink{50%{opacity:.3}}
.hero h1{font-family:var(--disp);font-weight:900;font-size:clamp(2.6rem,6.6vw,5.2rem);line-height:1;letter-spacing:-.01em;margin:24px 0 20px;text-transform:uppercase}
.line{display:block;overflow:hidden;padding-bottom:.06em}
.line-in{display:inline-block;transform:translateY(115%);animation:lineUp 1s var(--ease) forwards}
.l1{animation-delay:1.55s}.l2{animation-delay:1.7s}
@keyframes lineUp{to{transform:translateY(0)}}
.stroke{color:transparent;-webkit-text-stroke:2px var(--roxo)}
.lead{color:var(--cinza);max-width:46ch;font-size:1.05rem;opacity:0;animation:fadeUp .8s 1.9s var(--ease) forwards}
.hero-cta{display:flex;gap:16px;flex-wrap:wrap;margin-top:32px;opacity:0;animation:fadeUp .8s 2.05s var(--ease) forwards}
.hero-stats{display:flex;gap:0;margin-top:44px;opacity:0;animation:fadeUp .8s 2.2s var(--ease) forwards}
.stat{padding:0 26px;border-left:1px solid var(--borda)}
.stat:first-child{padding-left:0;border-left:0}
.stat strong{font-family:var(--disp);font-weight:800;font-size:1.6rem;display:block}
.stat span{font-size:.76rem;color:var(--cinza);letter-spacing:.05em}
@keyframes fadeUp{from{opacity:0;transform:translateY(24px);filter:blur(6px)}to{opacity:1;transform:none;filter:blur(0)}}

/* --- visual do hero (banner) --- */
.hero-stage{position:relative;display:grid;place-items:center;perspective:1000px}
.ring{position:absolute;border-radius:50%;left:50%;top:50%;translate:-50% -50%}
.r1{width:420px;height:420px;border:1.5px dashed rgba(139,92,246,.35);animation:spin 32s linear infinite}
.r2{width:560px;height:560px;border:1px solid rgba(255,255,255,.06);animation:spinR 50s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}@keyframes spinR{to{transform:rotate(-360deg)}}
.glow{position:absolute;width:440px;height:340px;border-radius:50%;background:radial-gradient(circle,var(--roxo-glow),transparent 65%);filter:blur(50px);animation:pulse 5s ease-in-out infinite}
@keyframes pulse{50%{transform:scale(1.15);opacity:.7}}
.swoosh{position:absolute;width:130%;height:70px;left:-15%;top:46%;background:linear-gradient(90deg,transparent,var(--roxo) 30%,#fff 50%,var(--roxo) 70%,transparent);filter:blur(24px);transform:rotate(-18deg);opacity:.35;animation:swooshMove 5s ease-in-out infinite}
.sw2{height:36px;top:58%;opacity:.18;animation-delay:-2.5s}
@keyframes swooshMove{0%,100%{transform:rotate(-18deg) translateX(-6%);opacity:.25}50%{transform:rotate(-18deg) translateX(6%);opacity:.5}}
.banner-wrap{position:relative;z-index:3;will-change:transform}
.banner-frame{
  border:1px solid var(--borda);background:var(--preto-3);overflow:hidden;
  box-shadow:0 40px 80px -20px rgba(0,0,0,.6),0 0 60px -10px var(--roxo-glow);
  animation:bannerIn 1.2s var(--ease) 1.75s both,float 7s ease-in-out 3.1s infinite;
  transform-style:preserve-3d;
}
.banner-bar{display:flex;align-items:center;gap:7px;padding:12px 16px;border-bottom:1px solid var(--borda);background:rgba(5,5,8,.6)}
.banner-bar i{width:10px;height:10px;border-radius:50%}
.banner-bar i:nth-child(1){background:#ff5f57}.banner-bar i:nth-child(2){background:#febc2e}.banner-bar i:nth-child(3){background:#28c840}
.banner-bar span{margin-left:auto;font-size:.62rem;color:var(--cinza);letter-spacing:.1em;font-family:var(--disp)}
.banner-frame img{width:100%;aspect-ratio:16/9;object-fit:cover}
@keyframes bannerIn{0%{opacity:0;transform:scale(.72) translateY(60px) rotateX(12deg);filter:blur(26px)}55%{filter:blur(0)}100%{opacity:1;transform:scale(1) translateY(0) rotateX(0);filter:blur(0)}}
@keyframes float{0%,100%{transform:translateY(0) rotateX(0)}50%{transform:translateY(-16px) rotateX(1.5deg)}}
.chip{position:absolute;z-index:4;background:rgba(11,11,19,.88);backdrop-filter:blur(8px);border:1px solid var(--borda);padding:.65rem 1rem;font-size:.78rem;color:var(--cinza);opacity:0;animation:fadeUp .7s var(--ease) forwards;white-space:nowrap}
.chip strong,.chip em{color:var(--branco);font-style:normal}
.chip .roxo{color:var(--roxo-neon)}.chip .green{color:#22c55e}
.chip-1{top:6%;right:2%;animation-delay:2.4s}
.chip-2{bottom:10%;left:-4%;animation-delay:2.55s}
.chip-3{bottom:-4%;right:8%;background:var(--discord);border-color:var(--discord);color:#fff;font-family:var(--disp);font-size:.6rem;letter-spacing:.1em;font-weight:600;animation-delay:2.7s}
/* mini server card */
.server-card{
  position:absolute;z-index:5;top:-6%;left:-8%;background:rgba(11,11,19,.92);backdrop-filter:blur(10px);
  border:1px solid var(--borda);padding:14px 18px;display:flex;align-items:center;gap:12px;
  opacity:0;animation:fadeUp .7s 2.85s var(--ease) forwards;
}
.server-card img{width:40px;height:40px;border-radius:12px}
.server-card .sc-name{font-family:var(--disp);font-size:.72rem;font-weight:600}
.server-card .sc-members{font-size:.68rem;color:var(--cinza);display:flex;align-items:center;gap:5px}
.server-card .sc-members i{width:7px;height:7px;background:#22c55e;border-radius:50%;display:inline-block}
.scroll-hint{position:absolute;left:50%;bottom:20px;translate:-50% 0;z-index:3;text-decoration:none;color:var(--cinza);font-size:.66rem;letter-spacing:.3em;text-transform:uppercase;display:flex;flex-direction:column;align-items:center;gap:10px;opacity:0;animation:fadeUp .8s 3s forwards}
.scroll-hint span{width:1px;height:44px;background:linear-gradient(var(--roxo),transparent);position:relative;overflow:hidden}
.scroll-hint span::after{content:"";position:absolute;top:-10px;left:0;width:1px;height:12px;background:#fff;animation:drip 1.6s ease-in-out infinite}
@keyframes drip{to{top:50px}}

/* ===================== FAIXA ===================== */
.strip{border-block:1px solid var(--borda);padding:24px 0;overflow:hidden;position:relative;z-index:1;background:rgba(11,11,19,.4)}
.strip-track{display:flex;width:max-content;animation:mq 32s linear infinite}
.strip-group{display:flex;align-items:center;gap:2.4rem;padding-right:2.4rem}
.strip-group span{font-family:var(--disp);font-weight:800;font-size:clamp(1.6rem,3vw,2.6rem);text-transform:uppercase;white-space:nowrap}
.s-solid{color:var(--roxo)}.s-outline{color:transparent;-webkit-text-stroke:1.5px rgba(244,242,255,.5)}
.strip-group i{color:var(--roxo);font-style:normal;font-size:1.2rem}

/* ===================== SEÇÕES ===================== */
.sec{padding:104px 0;position:relative;z-index:1}
.kicker{font-size:.72rem;letter-spacing:.3em;text-transform:uppercase;color:var(--cinza);margin-bottom:14px}
.kicker b{color:var(--roxo);font-weight:700}
.sec-row{display:flex;align-items:flex-end;justify-content:space-between;gap:24px;flex-wrap:wrap}
h2{font-family:var(--disp);font-weight:800;font-size:clamp(1.8rem,3.8vw,2.8rem);line-height:1.1;text-transform:uppercase}
.out{color:transparent;-webkit-text-stroke:1.5px var(--roxo)}
.rv{opacity:0;transform:translateY(36px);filter:blur(10px);transition:opacity .9s var(--ease),transform .9s var(--ease),filter .9s var(--ease)}
.rv.in{opacity:1;transform:none;filter:blur(0)}

/* ===================== FEATURES (BENTO) ===================== */
.bento{display:grid;grid-template-columns:repeat(3,1fr);grid-template-rows:auto auto;gap:18px;margin-top:48px}
.bento-item{
  background:var(--preto-3);border:1px solid var(--borda);padding:32px 28px;position:relative;overflow:hidden;
  transition:transform .45s var(--ease),border-color .45s,box-shadow .45s;
}
.bento-item:hover{transform:translateY(-7px);border-color:var(--roxo);box-shadow:0 24px 50px -20px var(--roxo-glow)}
.bento-item::before{content:"";position:absolute;top:-40%;right:-30%;width:200px;height:200px;background:radial-gradient(circle,rgba(139,92,246,.12),transparent 70%);pointer-events:none}
.b-big{grid-column:span 2}
.b-tall{grid-row:span 2;display:flex;flex-direction:column;justify-content:space-between}
.bento-icon{font-size:2rem;margin-bottom:16px;display:block}
.bento-item h3{font-family:var(--disp);font-weight:600;font-size:1.05rem;margin-bottom:10px;text-transform:uppercase}
.bento-item p{color:var(--cinza);font-size:.9rem;line-height:1.65}
.bento-tag{display:inline-block;margin-top:16px;font-family:var(--disp);font-size:.58rem;letter-spacing:.16em;color:var(--roxo-neon);border:1px solid var(--borda);padding:.4rem .8rem;text-transform:uppercase}

/* ===================== CATEGORIAS ===================== */
.cats{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:48px}
.cat{position:relative;overflow:hidden;border:1px solid var(--borda);text-decoration:none;color:#fff;height:200px;transition:border-color .4s}
.cat:hover{border-color:var(--roxo)}
.cat img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover;transition:transform .9s var(--ease),filter .5s}
.cat:hover img{transform:scale(1.1);filter:saturate(1.2) brightness(.85)}
.cat::after{content:"";position:absolute;inset:0;background:linear-gradient(to top,rgba(5,5,8,.92) 0%,rgba(5,5,8,.2) 50%,transparent 75%)}
.cat-info{position:absolute;left:18px;right:18px;bottom:16px;z-index:2;display:flex;align-items:flex-end;gap:12px}
.cat-info h3{font-family:var(--disp);font-weight:800;font-size:1.1rem;text-transform:uppercase}
.cat-count{font-size:.68rem;color:var(--roxo-neon);letter-spacing:.14em;text-transform:uppercase;display:block;margin-bottom:3px}
.cat-arrow{margin-left:auto;width:36px;height:36px;flex-shrink:0;display:grid;place-items:center;border:1px solid rgba(255,255,255,.4);font-size:1rem;transition:.4s var(--ease)}
.cat:hover .cat-arrow{background:var(--roxo);border-color:var(--roxo);color:#0a0a10;transform:rotate(-45deg)}

/* ===================== SHOWCASE ===================== */
.tabs{display:flex;gap:6px;flex-wrap:wrap}
.tab{background:none;border:1px solid transparent;color:var(--cinza);font-weight:600;font-size:.86rem;padding:.5rem 1.1rem;cursor:pointer;transition:.3s}
.tab:hover{color:var(--branco)}
.tab.active{background:var(--roxo);color:#0a0a10;clip-path:polygon(0 0,100% 0,100% calc(100% - 8px),calc(100% - 8px) 100%,0 100%)}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(256px,1fr));gap:22px;margin-top:44px}
.card{background:var(--preto-3);border:1px solid var(--borda);position:relative;transition:transform .45s var(--ease),border-color .45s,box-shadow .45s;animation:cardIn .7s var(--ease) both;animation-delay:var(--d,0ms)}
@keyframes cardIn{from{opacity:0;transform:translateY(32px) scale(.97);filter:blur(12px)}to{opacity:1;transform:none;filter:blur(0)}}
.card:hover{transform:translateY(-9px);border-color:var(--roxo);box-shadow:0 26px 55px -22px var(--roxo-glow)}
.card-media{position:relative;aspect-ratio:16/10;overflow:hidden;background:#16161f}
.card-media img{width:100%;height:100%;object-fit:cover;transition:transform .6s var(--ease)}
.card:hover .card-media img{animation:snap .55s var(--ease) both}
@keyframes snap{0%{transform:scale(1.2) translateX(8%);filter:blur(12px)}100%{transform:scale(1.1) translateX(0);filter:blur(0)}}
.flag{position:absolute;top:12px;left:12px;z-index:2;font-family:var(--disp);font-size:.56rem;font-weight:600;letter-spacing:.14em;padding:.4rem .6rem}
.b-novo{background:var(--roxo);color:#0a0a10}.b-hot{background:#fff;color:#0a0a10}.b-free{background:#22c55e;color:#0a0a10}
.dl-btn{position:absolute;left:0;right:0;bottom:0;z-index:2;border:0;cursor:pointer;background:var(--roxo);color:#0a0a10;font-family:var(--disp);font-size:.66rem;font-weight:600;letter-spacing:.12em;text-transform:uppercase;padding:.9rem;transform:translateY(105%);transition:transform .4s var(--ease),background .3s}
.card:hover .dl-btn{transform:none}
.dl-btn:hover{background:#fff}
@media(hover:none){.dl-btn{transform:none}}
.card-info{padding:16px 18px}
.card-cat{font-size:.64rem;letter-spacing:.22em;text-transform:uppercase;color:var(--roxo-neon)}
.card-info h3{font-family:var(--disp);font-weight:600;font-size:.92rem;margin:7px 0 5px}
.card-meta{font-size:.8rem;color:var(--cinza);display:flex;align-items:center;gap:14px}
.card-meta span{display:flex;align-items:center;gap:4px}
.vazio{grid-column:1/-1;text-align:center;color:var(--cinza);padding:60px 0}

/* ===================== COUNTDOWN ===================== */
.drop{background:var(--roxo-2);position:relative;overflow:hidden;z-index:1}
.drop::before{content:"";position:absolute;inset:0;background:repeating-linear-gradient(-55deg,rgba(0,0,0,.07) 0 2px,transparent 2px 26px)}
.drop-in{display:grid;grid-template-columns:1.1fr .9fr;gap:48px;align-items:center;padding:96px 24px}
.drop .kicker{color:rgba(0,0,0,.55)}.drop .kicker b{color:#0a0a10}
.drop-title{font-family:var(--disp);font-weight:900;font-size:clamp(2.4rem,5.5vw,4.2rem);line-height:.95;color:#0a0a10;text-transform:uppercase;margin-bottom:18px}
.drop-title span{color:#fff}
.drop-copy>p{color:rgba(0,0,0,.7);max-width:44ch;font-weight:500}
.drop-copy .btn{margin-top:28px}
.btn-black{background:#0a0a10;color:#fff}.btn-black:hover{background:#fff;color:#0a0a10;transform:translateY(-3px)}
.drop-right{display:flex;flex-direction:column;align-items:center;gap:30px}
.drop-visual{position:relative}
.drop-visual img{width:min(400px,76vw);border:1px solid rgba(0,0,0,.2);box-shadow:0 30px 60px rgba(0,0,0,.4);transform:rotate(-6deg);animation:float 6s ease-in-out infinite;position:relative;z-index:2}
.sw3{position:absolute;width:150%;height:60px;left:-25%;top:44%;z-index:1;background:linear-gradient(90deg,transparent,#fff 35%,#0a0a10 50%,#fff 65%,transparent);filter:blur(22px);opacity:.3;transform:rotate(-6deg);animation:swooshMove 4.5s ease-in-out infinite}
.count{display:flex;gap:12px}
.cd{background:#0a0a10;color:#fff;min-width:84px;padding:16px 10px 12px;text-align:center;clip-path:polygon(0 0,100% 0,100% calc(100% - 10px),calc(100% - 10px) 100%,0 100%)}
.cd strong{font-family:var(--disp);font-weight:800;font-size:2rem;display:block;line-height:1}
.cd span{font-size:.6rem;letter-spacing:.24em;text-transform:uppercase;color:rgba(255,255,255,.55)}
.drop-tape{background:#0a0a10;overflow:hidden;position:relative;z-index:2}
.tape-track{display:flex;width:max-content;animation:mq 20s linear infinite}
.drop-tape span{font-family:var(--disp);font-size:.68rem;font-weight:600;letter-spacing:.22em;color:#fff;padding:.8rem 1.6rem;white-space:nowrap}
.drop-tape i{color:var(--roxo);font-style:normal}

/* ===================== REVIEWS ===================== */
.rev-marquee{overflow:hidden;margin-top:50px;-webkit-mask-image:linear-gradient(90deg,transparent,#000 8%,#000 92%,transparent);mask-image:linear-gradient(90deg,transparent,#000 8%,#000 92%,transparent)}
.rev-track{display:flex;gap:20px;width:max-content;animation:mq 48s linear infinite}
.rev-marquee:hover .rev-track{animation-play-state:paused}
.rev{width:340px;flex-shrink:0;background:var(--preto-3);border:1px solid var(--borda);padding:26px;position:relative;transition:.35s}
.rev:hover{border-color:var(--roxo);transform:translateY(-6px)}
.rev::before{content:"“";font-family:var(--disp);font-size:3.2rem;color:var(--roxo);position:absolute;top:6px;right:18px;opacity:.5;line-height:1}
.rev p{color:var(--cinza);font-size:.92rem;margin:10px 0 18px}
.rev-foot{display:flex;align-items:center;gap:12px}
.avatar{width:42px;height:42px;border-radius:50%;background:rgba(139,92,246,.15);border:1px solid var(--roxo);color:var(--roxo-neon);display:grid;place-items:center;font-family:var(--disp);font-weight:800;font-size:.72rem}
.rev-foot strong{display:block;font-size:.88rem}.rev-foot span{font-size:.74rem;color:var(--cinza)}
.stars{color:var(--roxo);letter-spacing:2px}

/* ===================== CTA ===================== */
.cta{position:relative;overflow:hidden;padding:130px 0;text-align:center;z-index:1;border-top:1px solid var(--borda)}
.cta::before{content:"ASSETS LAB";position:absolute;top:50%;left:50%;translate:-50% -50%;font-family:var(--disp);font-weight:900;font-size:16vw;white-space:nowrap;color:transparent;-webkit-text-stroke:1px rgba(139,92,246,.1);pointer-events:none}
.cta-icon{width:80px;height:80px;border-radius:24px;margin:0 auto 28px;box-shadow:0 0 50px var(--roxo-glow);animation:float 5s ease-in-out infinite}
.cta h2{font-size:clamp(2rem,5vw,3.4rem);margin-bottom:16px}
.cta p{color:var(--cinza);max-width:50ch;margin:0 auto 36px;font-size:1.05rem}
.cta .btn-discord{font-size:.82rem;padding:1.2rem 2.4rem}
.cta-note{display:block;margin-top:20px;font-size:.78rem;color:var(--cinza);letter-spacing:.06em}

/* ===================== FOOTER ===================== */
footer{background:#040407;border-top:1px solid var(--borda);position:relative;z-index:1}
.foot-grid{display:grid;grid-template-columns:1.8fr 1fr 1fr 1.2fr;gap:44px;padding:66px 24px 46px}
.foot-brand{display:flex;flex-direction:column;gap:0}
.foot-brand .logo{margin-bottom:16px}
.foot-brand p{color:var(--cinza);font-size:.88rem;max-width:32ch;margin-bottom:20px}
.socials{display:flex;gap:10px}
.soc{width:40px;height:40px;display:grid;place-items:center;border:1px solid rgba(255,255,255,.18);color:var(--branco);text-decoration:none;font-family:var(--disp);font-size:.6rem;font-weight:800;transition:.3s}
.soc:hover{background:var(--roxo);border-color:var(--roxo);color:#0a0a10;transform:translateY(-4px) rotate(-6deg)}
.foot-col h4{font-family:var(--disp);font-size:.74rem;font-weight:600;letter-spacing:.18em;text-transform:uppercase;margin-bottom:18px;color:var(--roxo-neon)}
.foot-col a{display:block;color:var(--cinza);text-decoration:none;font-size:.88rem;margin-bottom:11px;transition:.3s}
.foot-col a:hover{color:var(--branco);padding-left:8px}
.foot-bottom{display:flex;align-items:center;justify-content:space-between;gap:20px;flex-wrap:wrap;padding:20px 24px;border-top:1px solid rgba(255,255,255,.06);font-size:.78rem;color:var(--cinza)}
.foot-bottom .disc{display:flex;align-items:center;gap:8px}
.foot-bottom .disc img{width:18px;height:18px;opacity:.6}

/* ===================== TOASTS / TOPO ===================== */
#toasts{position:fixed;left:20px;bottom:20px;z-index:1300;display:flex;flex-direction:column;gap:10px}
.toast{background:var(--preto-3);border:1px solid var(--borda);border-left:3px solid var(--roxo);padding:14px 18px;font-size:.86rem;max-width:330px;box-shadow:0 16px 40px rgba(0,0,0,.5);animation:tIn .45s var(--ease)}
.toast.out{animation:tOut .35s forwards}
@keyframes tIn{from{opacity:0;transform:translateX(-36px);filter:blur(8px)}to{opacity:1;transform:none;filter:blur(0)}}
@keyframes tOut{to{opacity:0;transform:translateX(-36px)}}
#topo{position:fixed;right:22px;bottom:22px;width:46px;height:46px;z-index:950;cursor:pointer;background:var(--roxo);color:#0a0a10;border:0;font-size:1.15rem;font-weight:700;opacity:0;transform:translateY(18px);pointer-events:none;transition:.4s var(--ease);clip-path:polygon(0 0,100% 0,100% calc(100% - 10px),calc(100% - 10px) 100%,0 100%)}
#topo.show{opacity:1;transform:none;pointer-events:auto}
#topo:hover{background:#fff}

/* ===================== RESPONSIVO ===================== */
@media(max-width:1024px){
  .hero-in{grid-template-columns:1fr;padding-top:60px}
  .hero-stage{order:-1;margin-bottom:10px}
  .server-card{left:0;top:-4%}
  .drop-in{grid-template-columns:1fr;padding:80px 24px}
  .foot-grid{grid-template-columns:1fr 1fr}
  .bento{grid-template-columns:1fr 1fr}
  .b-big{grid-column:span 2}
}
@media(max-width:900px){
  .links{display:none}.hamburger{display:flex}.mobile-menu{display:flex}
  .cats{grid-template-columns:1fr 1fr}
}
@media(max-width:640px){
  .hero-stats{flex-wrap:wrap;gap:16px}.stat{padding:0 16px}.stat:first-child{padding-left:0}
  .bento{grid-template-columns:1fr}.b-big{grid-column:auto}.b-tall{grid-row:auto}
  .cats{grid-template-columns:1fr}
  .cd{min-width:68px}.cd strong{font-size:1.5rem}
  .chip-2,.chip-3{display:none}
  .server-card{display:none}
  .foot-grid{grid-template-columns:1fr;gap:32px}
  .sec{padding:76px 0}
  .banner-frame img{aspect-ratio:16/10}
}
</style>
</head>
<body>

<!-- PRELOADER -->
<div id="preloader">
  <img class="pre-icon" src="https://cdn.discordapp.com/attachments/1517004676745265172/1531244925398810695/Assets_Lab_Icon.png?ex=6a6dc877&is=6a6c76f7&hm=62c8d219d61f261f0397fa36627c82d7b05e75b1668437ed94ad40285792a742&" alt="Assets Lab" onerror="this.style.display='none'">
  <div class="pre-logo">ASSETS <span>LAB</span></div>
  <div class="pre-bar"><i></i></div>
</div>

<div id="progress"></div>

<!-- TICKER -->
<div class="ticker" aria-hidden="true">
  <div class="ticker-track" data-clone>
    <span>◆ NOVOS PACKS TODA SEMANA</span><span>◆ 100% GRATUITO</span><span>◆ +5.000 MEMBROS</span><span>◆ EVENTOS &amp; SORTEIOS</span><span>◆ FEITO PELA COMUNIDADE</span><span>◆ ENTRE AGORA</span>
  </div>
</div>

<!-- NAV -->
<header id="nav">
  <div class="nav-in">
    <a class="logo" href="#inicio">
      <img src="https://cdn.discordapp.com/attachments/1517004676745265172/1531244925398810695/Assets_Lab_Icon.png?ex=6a6dc877&is=6a6c76f7&hm=62c8d219d61f261f0397fa36627c82d7b05e75b1668437ed94ad40285792a742&" alt="Ícone Assets Lab" onerror="this.style.display='none'">
      <b>ASSETS <span>LAB</span></b>
    </a>
    <nav class="links">
      <a href="#features">Por que entrar</a>
      <a href="#categorias">Categorias</a>
      <a href="#assets">Assets</a>
      <a href="#comunidade">Comunidade</a>
    </nav>
    <div class="nav-acts">
      <a class="btn-discord" href="https://discord.gg/assetslab" target="_blank" rel="noopener">
        <img src="https://cdn-icons-png.flaticon.com/512/5968/5968756.png" alt="Discord"> Entrar
      </a>
      <button class="hamburger" id="menuBtn" aria-label="Menu"><span></span><span></span><span></span></button>
    </div>
  </div>
  <nav class="mobile-menu" id="mobileMenu">
    <a href="#features">Por que entrar</a>
    <a href="#categorias">Categorias</a>
    <a href="#assets">Assets</a>
    <a href="#comunidade">Comunidade</a>
    <a href="https://discord.gg/assetslab" target="_blank" rel="noopener" style="color:var(--roxo-neon)">💜 Entrar no Discord</a>
  </nav>
</header>

<main>
<!-- ============ HERO ============ -->
<section class="hero" id="inicio">
  <div class="hero-bg">
    <div class="hero-grid"></div>
    <span class="orb o1"></span><span class="orb o2"></span><span class="orb o3"></span>
  </div>
  <div class="hero-in">
    <div class="hero-copy">
      <p class="eyebrow"><i></i> SERVIDOR ABERTO — 342 ONLINE AGORA</p>
      <h1>
        <span class="line"><span class="line-in l1">ASSETS</span></span>
        <span class="line"><span class="line-in l2 stroke">LAB.</span></span>
      </h1>
      <p class="lead">A maior comunidade de assets gratuitos do Discord. UI kits, ícones, templates, overlays e muito mais — feitos pela comunidade, para a comunidade.</p>
      <div class="hero-cta">
        <a href="https://discord.gg/assetslab" target="_blank" rel="noopener" class="btn-discord" style="font-size:.78rem;padding:1.1rem 1.8rem">
          <img src="https://cdn-icons-png.flaticon.com/512/5968/5968756.png" alt="Discord"> Entrar no servidor
        </a>
        <a href="#assets" class="btn btn-ghost">Ver assets</a>
      </div>
      <div class="hero-stats">
        <div class="stat"><strong class="count" data-target="5200" data-suffix="+">0</strong><span>membros</span></div>
        <div class="stat"><strong class="count" data-target="840" data-suffix="+">0</strong><span>assets grátis</span></div>
        <div class="stat"><strong class="count" data-target="120" data-suffix="+">0</strong><span>packs lançados</span></div>
      </div>
    </div>
    <div class="hero-stage" id="stage">
      <div class="ring r2"></div><div class="ring r1"></div>
      <div class="glow"></div>
      <div class="swoosh"></div><div class="swoosh sw2"></div>
      <div class="banner-wrap" data-depth="22">
        <div class="banner-frame">
          <div class="banner-bar"><i></i><i></i><i></i><span>assets-lab.png</span></div>
          <img src="https://cdn.discordapp.com/attachments/1517004676745265172/1531244574834692126/ChatGPT_Image_27_de_jul._de_2026_07_18_14.png?ex=6a6dc823&is=6a6c76a3&hm=aadf93a3358b770240c81bd82c0495c8953fc4d7d750ca356fd618f28e70562a&" alt="Banner Assets Lab" onerror="this.classList.add('img-fallback');this.removeAttribute('src')">
        </div>
      </div>
      <div class="server-card" data-depth="44">
        <img src="https://cdn.discordapp.com/attachments/1517004676745265172/1531244925398810695/Assets_Lab_Icon.png?ex=6a6dc877&is=6a6c76f7&hm=62c8d219d61f261f0397fa36627c82d7b05e75b1668437ed94ad40285792a742&" alt="" onerror="this.style.display='none'">
        <div>
          <div class="sc-name">Assets Lab</div>
          <div class="sc-members"><i></i> 342 online · 5.2k membros</div>
        </div>
      </div>
      <div class="chip chip-1" data-depth="50"><span class="green">●</span> <strong>342</strong> online agora</div>
      <div class="chip chip-2" data-depth="60"><span class="roxo">840+</span> assets gratuitos</div>
      <div class="chip chip-3" data-depth="38">100% GRÁTIS ⚡</div>
    </div>
  </div>
  <a class="scroll-hint" href="#features"><span></span>role para explorar</a>
</section>

<!-- FAIXA -->
<div class="strip" aria-hidden="true">
  <div class="strip-track" data-clone>
    <div class="strip-group">
      <span class="s-solid">Assets Lab</span><i>✦</i><span class="s-outline">UI Kits</span><i>✦</i><span class="s-solid">Ícones</span><i>✦</i><span class="s-outline">Templates</span><i>✦</i><span class="s-solid">Overlays</span><i>✦</i><span class="s-outline">100% Grátis</span><i>✦</i>
    </div>
  </div>
</div>

<!-- ============ FEATURES ============ -->
<section id="features" class="sec">
  <div class="wrap">
    <div class="rv">
      <p class="kicker"><b>01</b> / Por que entrar</p>
      <div class="sec-row"><h2>Mais que um servidor,<br>um <span class="out">laboratório</span></h2></div>
    </div>
    <div class="bento">
      <div class="bento-item b-big rv">
        <span class="bento-icon">📦</span>
        <h3>Packs exclusivos toda semana</h3>
        <p>Toda semana a equipe e a comunidade lançam packs novos de assets: UI kits, icon packs, templates, overlays para stream, mockups e muito mais. Tudo organizado por categoria e sempre atualizado.</p>
        <span class="bento-tag">+120 packs lançados</span>
      </div>
      <div class="bento-item b-tall rv">
        <div>
          <span class="bento-icon">🎨</span>
          <h3>100% gratuito</h3>
          <p>Sem paywall, sem pegadinha, sem "link quebrado". Todo asset postado no servidor é gratuito para sempre. Acreditamos que design bom deve ser acessível.</p>
        </div>
        <span class="bento-tag">Zero custo, zero spam</span>
      </div>
      <div class="bento-item rv">
        <span class="bento-icon">🤝</span>
        <h3>Comunidade ativa</h3>
        <p>Milhares de designers, devs e criadores trocando ideia, dando feedback e colaborando em projetos todos os dias.</p>
      </div>
      <div class="bento-item rv">
        <span class="bento-icon">🏆</span>
        <h3>Eventos & sorteios</h3>
        <p>Game jams, desafios de design, workshops ao vivo e sorteios de assets premium e licenças de ferramentas.</p>
      </div>
      <div class="bento-item rv">
        <span class="bento-icon">📚</span>
        <h3>Tutoriais & guias</h3>
        <p>Canais dedicados com tutoriais de Figma, Photoshop, Blender e mais — escritos pela própria comunidade.</p>
      </div>
      <div class="bento-item rv">
        <span class="bento-icon">🔔</span>
        <h3>Acesso antecipado</h3>
        <p>Membros com cargo de Contributor recebem os packs 24h antes de todo mundo e podem votar nos próximos temas.</p>
      </div>
    </div>
  </div>
</section>

<!-- ============ CATEGORIAS ============ -->
<section id="categorias" class="sec">
  <div class="wrap">
    <div class="rv">
      <p class="kicker"><b>02</b> / Categorias</p>
      <div class="sec-row">
        <h2>O que tem no <span class="out">lab</span></h2>
        <a class="btn btn-ghost" style="padding:.7rem 1.3rem;font-size:.68rem" href="https://discord.gg/assetslab" target="_blank" rel="noopener">ver tudo no servidor →</a>
      </div>
    </div>
    <div class="cats">
      <a class="cat rv" href="https://discord.gg/assetslab" target="_blank" rel="noopener">
        <img src="https://images.unsplash.com/photo-1545235617-9465d2a55698?auto=format&fit=crop&w=800&q=80" alt="UI Kits" loading="lazy">
        <div class="cat-info"><div><span class="cat-count">186 assets</span><h3>UI Kits</h3></div><span class="cat-arrow">→</span></div>
      </a>
      <a class="cat rv" href="https://discord.gg/assetslab" target="_blank" rel="noopener">
        <img src="https://images.unsplash.com/photo-1558655146-9f40138edfeb?auto=format&fit=crop&w=800&q=80" alt="Ícones" loading="lazy">
        <div class="cat-info"><div><span class="cat-count">214 assets</span><h3>Ícones</h3></div><span class="cat-arrow">→</span></div>
      </a>
      <a class="cat rv" href="https://discord.gg/assetslab" target="_blank" rel="noopener">
        <img src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?auto=format&fit=crop&w=800&q=80" alt="3D" loading="lazy">
        <div class="cat-info"><div><span class="cat-count">97 assets</span><h3>3D & Renders</h3></div><span class="cat-arrow">→</span></div>
      </a>
      <a class="cat rv" href="https://discord.gg/assetslab" target="_blank" rel="noopener">
        <img src="https://images.unsplash.com/photo-1561070791-2526d30994b5?auto=format&fit=crop&w=800&q=80" alt="Templates" loading="lazy">
        <div class="cat-info"><div><span class="cat-count">143 assets</span><h3>Templates</h3></div><span class="cat-arrow">→</span></div>
      </a>
      <a class="cat rv" href="https://discord.gg/assetslab" target="_blank" rel="noopener">
        <img src="https://images.unsplash.com/photo-1620641788421-7a1c342ea42e?auto=format&fit=crop&w=800&q=80" alt="Overlays" loading="lazy">
        <div class="cat-info"><div><span class="cat-count">78 assets</span><h3>Overlays</h3></div><span class="cat-arrow">→</span></div>
      </a>
      <a class="cat rv" href="https://discord.gg/assetslab" target="_blank" rel="noopener">
        <img src="https://images.unsplash.com/photo-1524661135-423995f22d0b?auto=format&fit=crop&w=800&q=80" alt="Fontes" loading="lazy">
        <div class="cat-info"><div><span class="cat-count">122 assets</span><h3>Fontes</h3></div><span class="cat-arrow">→</span></div>
      </a>
    </div>
  </div>
</section>

<!-- ============ ASSETS EM DESTAQUE ============ -->
<section id="assets" class="sec">
  <div class="wrap">
    <div class="rv">
      <p class="kicker"><b>03</b> / Destaques</p>
      <div class="sec-row">
        <h2>Assets em <span class="out">destaque</span></h2>
        <div class="tabs" id="tabs">
          <button class="tab active" data-cat="todos">Todos</button>
          <button class="tab" data-cat="ui">UI Kits</button>
          <button class="tab" data-cat="icones">Ícones</button>
          <button class="tab" data-cat="3d">3D</button>
          <button class="tab" data-cat="templates">Templates</button>
          <button class="tab" data-cat="overlays">Overlays</button>
        </div>
      </div>
    </div>
    <div class="grid" id="grid"></div>
  </div>
</section>

<!-- ============ PRÓXIMO PACK ============ -->
<section id="drop" class="drop">
  <div class="drop-in wrap">
    <div class="drop-copy rv">
      <p class="kicker"><b>04</b> / Próximo pack</p>
      <h2 class="drop-title">Neon<span>UI</span> Vol.3</h2>
      <p>O pack mais pedido da história do servidor está chegando: 60+ componentes em estilo neon cyberpunk, dark e light mode, prontos para Figma. Contributors recebem 24h antes.</p>
      <a href="https://discord.gg/assetslab" target="_blank" rel="noopener" class="btn btn-black">Quero acesso antecipado →</a>
    </div>
    <div class="drop-right rv">
      <div class="drop-visual">
        <span class="sw3"></span>
        <img src="https://images.unsplash.com/photo-1614850715649-1d0106293bd1?auto=format&fit=crop&w=800&q=80" alt="Preview NeonUI Vol.3">
      </div>
      <div class="count" id="countdown">
        <div class="cd"><strong id="cd-d">00</strong><span>dias</span></div>
        <div class="cd"><strong id="cd-h">00</strong><span>horas</span></div>
        <div class="cd"><strong id="cd-m">00</strong><span>min</span></div>
        <div class="cd"><strong id="cd-s">00</strong><span>seg</span></div>
      </div>
    </div>
  </div>
  <div class="drop-tape" aria-hidden="true">
    <div class="tape-track" data-clone>
      <span>NEONUI VOL.3 <i>✦</i> 60+ COMPONENTES <i>✦</i> FIGMA READY <i>✦</i> DARK &amp; LIGHT <i>✦</i> 100% GRÁTIS <i>✦</i></span>
    </div>
  </div>
</section>

<!-- ============ COMUNIDADE / REVIEWS ============ -->
<section id="comunidade" class="sec">
  <div class="wrap rv">
    <p class="kicker"><b>05</b> / Comunidade</p>
    <div class="sec-row">
      <h2>Quem entra, <span class="out">fica</span></h2>
      <span style="color:var(--cinza);font-size:.88rem">+5.200 membros · 4.9★ de satisfação</span>
    </div>
  </div>
  <div class="rev-marquee rv">
    <div class="rev-track" data-clone>
      <div class="rev"><span class="stars">★★★★★</span><p>"Melhor servidor de assets que já entrei. Os packs de ícones são melhores que muito site pago por aí."</p><div class="rev-foot"><span class="avatar">KZ</span><div><strong>kauezin</strong><span>membro há 8 meses</span></div></div></div>
      <div class="rev"><span class="stars">★★★★★</span><p>"Consegui meu primeiro freela de UI usando os templates do Lab. A comunidade é absurdamente prestativa."</p><div class="rev-foot"><span class="avatar">LU</span><div><strong>luna.dev</strong><span>membro há 1 ano</span></div></div></div>
      <div class="rev"><span class="stars">★★★★★</span><p>"Os eventos de design são incríveis. Ganhei uma licença do Figma Pro no último sorteio!"</p><div class="rev-foot"><span class="avatar">TH</span><div><strong>thiago_art</strong><span>membro há 6 meses</span></div></div></div>
      <div class="rev"><span class="stars">★★★★★</span><p>"Entrei pelos overlays de stream e fiquei pela comunidade. O pessoal é muito gente boa."</p><div class="rev-foot"><span class="avatar">MI</span><div><strong>mika_streams</strong><span>membro há 4 meses</span></div></div></div>
      <div class="rev"><span class="stars">★★★★☆</span><p>"Os packs 3D são insanos. Só queria que tivessem mais modelos em Blender, mas o que tem já é top."</p><div class="rev-foot"><span class="avatar">RX</span><div><strong>renderx</strong><span>membro há 3 meses</span></div></div></div>
      <div class="rev"><span class="stars">★★★★★</span><p>"Virei Contributor e agora ajudo a criar os packs. A sensação de contribuir é outra coisa. 💜"</p><div class="rev-foot"><span class="avatar">AN</span><div><strong>ana_ui</strong><span>Contributor</span></div></div></div>
    </div>
  </div>
</section>

<!-- ============ CTA FINAL ============ -->
<section class="cta">
  <div class="wrap rv">
    <img class="cta-icon" src="https://cdn.discordapp.com/attachments/1517004676745265172/1531244925398810695/Assets_Lab_Icon.png?ex=6a6dc877&is=6a6c76f7&hm=62c8d219d61f261f0397fa36627c82d7b05e75b1668437ed94ad40285792a742&" alt="Assets Lab" onerror="this.style.display='none'">
    <h2>Bora entrar no <span class="out">Lab</span>?</h2>
    <p>São mais de 5 mil criadores te esperando. Assets grátis, eventos, tutoriais e uma comunidade que realmente ajuda. Leva 10 segundos.</p>
    <a href="https://discord.gg/assetslab" target="_blank" rel="noopener" class="btn-discord">
      <img src="https://cdn-icons-png.flaticon.com/512/5968/5968756.png" alt="Discord"> Entrar no Discord agora
    </a>
    <span class="cta-note">Grátis para sempre · Sem spam · Saia quando quiser</span>
  </div>
</section>
</main>

<!-- ============ FOOTER ============ -->
<footer>
  <div class="wrap foot-grid">
    <div class="foot-brand">
      <a class="logo" href="#inicio">
        <img src="https://cdn.discordapp.com/attachments/1517004676745265172/1531244925398810695/Assets_Lab_Icon.png?ex=6a6dc877&is=6a6c76f7&hm=62c8d219d61f261f0397fa36627c82d7b05e75b1668437ed94ad40285792a742&" alt="" style="width:36px;height:36px;border-radius:10px" onerror="this.style.display='none'">
        <b>ASSETS <span>LAB</span></b>
      </a>
      <p>Comunidade de assets gratuitos para designers, devs e criadores. Feito com 💜 no Discord.</p>
      <div class="socials">
        <a class="soc" href="https://discord.gg/assetslab" target="_blank" rel="noopener" aria-label="Discord">DC</a>
        <a class="soc" href="#" aria-label="Instagram">IG</a>
        <a class="soc" href="#" aria-label="Twitter/X">X</a>
        <a class="soc" href="#" aria-label="YouTube">YT</a>
      </div>
    </div>
    <div class="foot-col">
      <h4>Servidor</h4>
      <a href="#features">Por que entrar</a>
      <a href="#categorias">Categorias</a>
      <a href="#assets">Assets em destaque</a>
      <a href="#drop">Próximo pack</a>
    </div>
    <div class="foot-col">
      <h4>Comunidade</h4>
      <a href="#">Regras do servidor</a>
      <a href="#">Seja Contributor</a>
      <a href="#">Eventos</a>
      <a href="#">Parcerias</a>
    </div>
    <div class="foot-col">
      <h4>Contato</h4>
      <a href="https://discord.gg/assetslab" target="_blank" rel="noopener">discord.gg/assetslab</a>
      <a href="mailto:contato@assetslab.gg">contato@assetslab.gg</a>
      <a href="#">Abra um ticket no servidor</a>
    </div>
  </div>
  <div class="wrap foot-bottom">
    <span>© 2026 Assets Lab — Feito pela comunidade, para a comunidade.</span>
    <span class="disc"><img src="https://cdn-icons-png.flaticon.com/512/5968/5968756.png" alt="Discord"> Powered by Discord</span>
  </div>
</footer>

<div id="toasts"></div>
<button id="topo" aria-label="Voltar ao topo">↑</button>

<script>
/* ===================== DADOS ===================== */
const CATS = {ui:'UI Kit',icones:'Ícones','3d':'3D',templates:'Templates',overlays:'Overlays',fontes:'Fontes'};
const ASSETS = [
  {id:1,nome:'Neon UI Kit Vol.2',cat:'ui',img:'photo-1545235617-9465d2a55698',badge:'HOT',dls:2412,files:48},
  {id:2,nome:'Vortex Icon Pack',cat:'icones',img:'photo-1558655146-9f40138edfeb',badge:'NOVO',dls:1834,files:320},
  {id:3,nome:'Abstract 3D Vol.2',cat:'3d',img:'photo-1618005182384-a83a8bd57fbe',badge:null,dls:3107,files:24},
  {id:4,nome:'Stream Overlay X',cat:'overlays',img:'photo-1614850715649-1d0106293bd1',badge:'NOVO',dls:1245,files:12},
  {id:5,nome:'Dashboard Template',cat:'templates',img:'photo-1551650975-87deedd944c3',badge:null,dls:2731,files:8},
  {id:6,nome:'Glassmorphism Kit',cat:'ui',img:'photo-1620641788421-7a1c342ea42e',badge:'HOT',dls:1988,files:36},
  {id:7,nome:'Dark Mockup Scene',cat:'templates',img:'photo-1586717791821-3f44a563fa4c',badge:null,dls:987,files:15},
  {id:8,nome:'Cyber Icon Set',cat:'icones',img:'photo-1550745165-9bc0b252726f',badge:'NOVO',dls:1567,files:200},
  {id:9,nome:'Gradient 3D Pack',cat:'3d',img:'photo-1633167606207-d840b5070fc2',badge:null,dls:2203,files:18},
  {id:10,nome:'Twitch Overlay Pro',cat:'overlays',img:'photo-1558591710-4b4a1ae0f04d',badge:null,dls:1432,files:20},
];
const url = img => `https://images.unsplash.com/${img}?auto=format&fit=crop&w=800&q=80`;
const $ = s => document.querySelector(s);
const $$ = s => document.querySelectorAll(s);
let filtro = 'todos';

/* ===================== MARQUEES ===================== */
$$('[data-clone]').forEach(el => el.innerHTML += el.innerHTML);

/* ===================== SHOWCASE =====================
function badgeCls(b){return b==='HOT'?'b-hot':b==='NOVO'?'b-novo':'b-free'}
function renderAssets(){
  const grid=$('#grid');
  const lista=ASSETS.filter(a=>filtro==='todos'||a.cat===filtro);
  if(!lista.length){grid.innerHTML='<div class="vazio">Nenhum asset nessa categoria ainda 🔜</div>';return}
  grid.innerHTML=lista.map((a,i)=>`
    <article class="card" style="--d:${i*70}ms">
      <div class="card-media">
        ${a.badge?`<span class="flag ${badgeCls(a.badge)}">${a.badge}</span>`:'<span class="flag b-free">GRÁTIS</span>'}
        <img src="${url(a.img)}" alt="${a.nome}" loading="lazy">
        <button class="dl-btn" data-dl="${a.id}">⬇ Baixar no servidor</button>
      </div>
      <div class="card-info">
        <span class="card-cat">${CATS[a.cat]}</span>
        <h3>${a.nome}</h3>
        <div class="card-meta">
          <span>⬇ ${a.dls.toLocaleString('pt-BR')}</span>
          <span>📁 ${a.files} arquivos</span>
        </div>
      </div>
    </article>`).join('');
}
renderAssets();

$('#tabs').addEventListener('click',e=>{
  const t=e.target.closest('.tab');if(!t)return;
  $$('.tab').forEach(x=>x.classList.remove('active'));
  t.classList.add('active');filtro=t.dataset.cat;renderAssets();
});
$('#grid').addEventListener('click',e=>{
  const b=e.target.closest('[data-dl]');if(!b)return;
  const a=ASSETS.find(x=>x.id===+b.dataset.dl);
  toast(`⬇ <strong>${a?a.nome:'Asset'}</strong> — baixe no canal <strong>#packs</strong> do servidor!`);
});

/* ===================== TOASTS ===================== */
function toast(msg){
  const t=document.createElement('div');t.className='toast';t.innerHTML=msg;
  $('#toasts').appendChild(t);
  setTimeout(()=>{t.classList.add('out');setTimeout(()=>t.remove(),350)},3200);
}

/* ===================== COUNTDOWN ===================== */
const alvo=(()=>{const d=new Date();d.setHours(20,0,0,0);let add=(5-d.getDay()+7)%7;if(add===0&&Date.now()>=d.getTime())add=7;d.setDate(d.getDate()+add);return d})();
function tick(){
  let ms=Math.max(0,alvo-Date.now());const p=v=>String(v).padStart(2,'0');
  $('#cd-d').textContent=p(Math.floor(ms/864e5));
  $('#cd-h').textContent=p(Math.floor(ms/36e5)%24);
  $('#cd-m').textContent=p(Math.floor(ms/6e4)%60);
  $('#cd-s').textContent=p(Math.floor(ms/1e3)%60);
}
tick();setInterval(tick,1000);

/* ===================== REVEALS + CONTADORES ===================== */
function initReveals(){
  const io=new IntersectionObserver(es=>{es.forEach(en=>{if(en.isIntersecting){en.target.classList.add('in');io.unobserve(en.target)}})},{threshold:.15});
  $$('.rv').forEach(el=>io.observe(el));
  const ioC=new IntersectionObserver(es=>{es.forEach(en=>{
    if(!en.isIntersecting)return;
    const el=en.target,alvo=parseFloat(el.dataset.target),suf=el.dataset.suffix||'',t0=performance.now();
    (function passo(t){const k=Math.min(1,(t-t0)/1500),e=1-Math.pow(1-k,3);
      el.textContent=Math.round(alvo*e).toLocaleString('pt-BR')+suf;if(k<1)requestAnimationFrame(passo)})(t0);
    ioC.unobserve(el);
  })},{threshold:.5});
  $$('.count').forEach(el=>ioC.observe(el));
}
setTimeout(initReveals,1300);

/* ===================== PARALLAX ===================== */
const stage=$('#stage');
if(stage&&matchMedia('(pointer:fine)').matches){
  document.querySelector('.hero').addEventListener('mousemove',e=>{
    const r=stage.getBoundingClientRect();
    const x=(e.clientX-r.left)/r.width-.5,y=(e.clientY-r.top)/r.height-.5;
    $$('[data-depth]').forEach(el=>{const d=+el.dataset.depth;el.style.transform=`translate(${x*d}px,${y*d}px)`});
  });
}

/* ===================== NAV / SCROLL ===================== */
const nav=$('#nav'),topo=$('#topo'),prog=$('#progress');
addEventListener('scroll',()=>{
  const y=scrollY;
  nav.classList.toggle('scrolled',y>40);
  topo.classList.toggle('show',y>600);
  const h=document.documentElement.scrollHeight-innerHeight;
  prog.style.width=(h>0?y/h*100:0)+'%';
},{passive:true});
topo.addEventListener('click',()=>scrollTo({top:0,behavior:'smooth'}));

/* menu mobile */
const menuBtn=$('#menuBtn'),mm=$('#mobileMenu');
menuBtn.addEventListener('click',()=>{menuBtn.classList.toggle('open');mm.classList.toggle('open')});
mm.addEventListener('click',e=>{if(e.target.tagName==='A'){menuBtn.classList.remove('open');mm.classList.remove('open')}});

/* ===================== RASTRO MOTION BLUR ===================== */
if(matchMedia('(pointer:fine)').matches){
  let last=0;
  addEventListener('mousemove',e=>{
    const n=performance.now();if(n-last<45)return;last=n;
    const t=document.createElement('span');t.className='trail';
    t.style.left=e.clientX+'px';t.style.top=e.clientY+'px';
    document.body.appendChild(t);setTimeout(()=>t.remove(),620);
  });
}

/* ===================== PRELOADER ===================== */
setTimeout(()=>$('#preloader').classList.add('done'),1500);
</script>
</body>
</html>
