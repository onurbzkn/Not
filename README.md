<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0,viewport-fit=cover">
<title>Not</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.1/chart.umd.min.js"></script>
<style>
:root{--a1:#5b8cff;--a2:#b06aff;--gl:rgba(255,255,255,.55);--gb:rgba(255,255,255,.75);--gs:rgba(0,0,0,.08);--tx:#1a1a2e;--tx2:#5a5a7a;--grn:#30c98e;--yel:#f5a623;--red:#ff4d6a;--r:20px;--rs:14px;}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
body{font-family:'Nunito',sans-serif;background:linear-gradient(160deg,#e8f0fe 0%,#f0e8fe 50%,#fce8f3 100%);min-height:100vh;color:var(--tx);overflow-x:hidden;padding-bottom:110px;transition:background .4s;}
.blob{position:fixed;border-radius:50%;filter:blur(60px);opacity:.4;pointer-events:none;z-index:0;animation:bF 12s ease-in-out infinite alternate;}
.b1{width:380px;height:380px;background:radial-gradient(#a8c8ff,#d0aaff);top:-100px;left:-100px;}
.b2{width:300px;height:300px;background:radial-gradient(#ffb3c8,#ffd0a8);bottom:80px;right:-80px;animation-delay:-5s;}
.b3{width:220px;height:220px;background:radial-gradient(#b3e8ff,#c8f0d8);top:40%;left:15%;animation-delay:-9s;}
@keyframes bF{0%{transform:translate(0,0) scale(1)}100%{transform:translate(25px,35px) scale(1.1)}}
.w{position:relative;z-index:1;max-width:520px;margin:0 auto;padding:0 16px;}
/* HEADER */
.hdr{padding:56px 0 20px;}
.chip{display:inline-flex;align-items:center;background:var(--gl);border:1px solid var(--gb);backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);border-radius:99px;padding:5px 14px;font-size:11px;font-weight:800;color:var(--a2);margin-bottom:12px;}
.hdr h1{font-size:2rem;font-weight:900;letter-spacing:-1px;}
.hdr h1 span{background:linear-gradient(135deg,var(--a1),var(--a2));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;}
.hdr-sub{font-size:11px;color:var(--tx2);margin-top:5px;font-weight:600;}
/* CARD */
.card{background:var(--gl);border:1px solid var(--gb);backdrop-filter:blur(24px);-webkit-backdrop-filter:blur(24px);border-radius:var(--r);padding:20px;margin-bottom:14px;box-shadow:0 4px 24px var(--gs);}
.sl{font-size:10px;font-weight:800;letter-spacing:2px;text-transform:uppercase;color:var(--tx2);margin-bottom:14px;}
/* INPUTS */
.r2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px;}
.r3{display:grid;grid-template-columns:2fr 1fr 1fr;gap:10px;margin-bottom:10px;}
.r1{margin-bottom:10px;}
.f label{display:block;font-size:10px;font-weight:800;color:var(--tx2);margin-bottom:5px;}
.f input,.f select{width:100%;background:rgba(255,255,255,.65);border:1.5px solid rgba(255,255,255,.85);border-radius:var(--rs);padding:11px 13px;font-family:'Nunito',sans-serif;font-size:14px;font-weight:700;color:var(--tx);outline:none;transition:all .2s;-webkit-appearance:none;}
.f input:focus,.f select:focus{border-color:var(--a1);background:rgba(255,255,255,.9);box-shadow:0 0 0 3px rgba(91,140,255,.12);}
/* WARN */
.warn{background:rgba(255,77,106,.1);border:1.5px solid rgba(255,77,106,.3);border-radius:var(--rs);padding:9px 13px;font-size:11px;font-weight:700;color:var(--red);display:none;align-items:center;gap:7px;margin-bottom:10px;}
.warn.show{display:flex;animation:shk .3s ease;}
@keyframes shk{0%,100%{transform:translateX(0)}25%{transform:translateX(-4px)}75%{transform:translateX(4px)}}
/* RESULT */
.rb{background:linear-gradient(135deg,rgba(255,255,255,.72),rgba(255,255,255,.42));border:1.5px solid var(--gb);border-radius:var(--r);padding:20px;text-align:center;margin-top:12px;transition:all .3s;}
.rb.on{box-shadow:0 8px 32px rgba(91,140,255,.18);border-color:rgba(91,140,255,.35);}
.rl{font-size:10px;font-weight:800;letter-spacing:2px;text-transform:uppercase;color:var(--tx2);margin-bottom:5px;}
.rn{font-size:3rem;font-weight:900;line-height:1;transition:color .3s;}
.rd{font-size:12px;color:var(--tx2);margin-top:7px;font-weight:600;}
/* BUTTONS */
.btnf{width:100%;padding:13px;border:none;background:linear-gradient(135deg,var(--a1),var(--a2));color:white;border-radius:var(--rs);font-family:'Nunito',sans-serif;font-size:14px;font-weight:800;cursor:pointer;transition:all .2s;box-shadow:0 4px 14px rgba(91,140,255,.28);}
.btnf:active{transform:scale(.98);}
.btnd{background:rgba(255,255,255,.55);border:1.5px dashed rgba(91,140,255,.4);border-radius:var(--rs);padding:13px;width:100%;color:var(--a1);font-family:'Nunito',sans-serif;font-size:13px;font-weight:800;cursor:pointer;margin-bottom:12px;}
.btndel{background:rgba(255,77,106,.1);border:none;color:var(--red);border-radius:8px;padding:5px 9px;font-size:13px;cursor:pointer;}
.empty{text-align:center;color:var(--tx2);font-size:12px;padding:22px;font-weight:600;}
/* STATS */
.sr{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:12px;}
.sb{background:rgba(255,255,255,.6);border:1px solid var(--gb);border-radius:var(--rs);padding:12px 8px;text-align:center;}
.sbl{font-size:9px;font-weight:800;letter-spacing:1px;text-transform:uppercase;color:var(--tx2);margin-bottom:3px;}
.sbv{font-size:1.4rem;font-weight:900;}
/* LIST ITEMS */
.dl{display:flex;flex-direction:column;gap:7px;}
.di{display:grid;grid-template-columns:1fr auto auto auto;gap:8px;align-items:center;background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:11px 13px;animation:sI .22s ease both;}
@keyframes sI{from{opacity:0;transform:translateX(-6px)}to{opacity:1;transform:translateX(0)}}
.dn{font-weight:800;font-size:13px;}
.dm{font-size:11px;color:var(--tx2);font-weight:600;}
.dhb{padding:2px 9px;border-radius:7px;font-size:11px;font-weight:800;}
/* DIVIDER */
.dv{height:1px;background:rgba(255,255,255,.6);margin:16px 0;}
/* INLINE TOGGLE */
.itr{display:flex;align-items:center;gap:8px;cursor:pointer;user-select:none;}
.itp{width:36px;height:20px;border-radius:99px;background:rgba(0,0,0,.12);position:relative;transition:.3s;flex-shrink:0;}
.itp:before{content:'';position:absolute;width:14px;height:14px;left:3px;top:3px;background:white;border-radius:50%;transition:.3s;}
.iton .itp{background:linear-gradient(135deg,var(--a1),var(--a2));}
.iton .itp:before{transform:translateX(16px);}
.itext{font-size:12px;font-weight:800;color:var(--tx2);}
.ip{background:rgba(255,255,255,.35);border:1px solid rgba(255,255,255,.6);border-radius:var(--rs);padding:14px;margin-top:12px;display:none;}
.ip.show{display:block;}
/* MOTIV */
.motiv{background:linear-gradient(135deg,rgba(91,140,255,.12),rgba(176,106,255,.12));border:1.5px solid rgba(91,140,255,.2);border-radius:var(--rs);padding:12px 15px;margin-top:12px;display:none;align-items:center;gap:10px;}
.motiv.show{display:flex;}
/* TOGGLE SWITCH */
.tog{position:relative;width:48px;height:26px;flex-shrink:0;}
.tog input{opacity:0;width:0;height:0;position:absolute;}
.tsl{position:absolute;inset:0;background:rgba(0,0,0,.14);border-radius:99px;cursor:pointer;transition:.3s;}
.tsl:before{content:'';position:absolute;width:20px;height:20px;left:3px;top:3px;background:white;border-radius:50%;transition:.3s;}
.tog input:checked+.tsl{background:linear-gradient(135deg,var(--a1),var(--a2));}
.tog input:checked+.tsl:before{transform:translateX(22px);}
.tr{display:flex;align-items:center;justify-content:space-between;padding:12px 0;}
.trl .tt{font-size:13px;font-weight:800;}
.trl .ts{font-size:11px;color:var(--tx2);font-weight:600;margin-top:1px;}
/* KOMİTE */
.ki{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:15px;margin-bottom:9px;}
.kh{display:flex;justify-content:space-between;align-items:center;margin-bottom:10px;}
.kn{font-weight:800;font-size:13px;}
.kbd{font-size:10px;font-weight:800;padding:2px 9px;border-radius:99px;}
.kins{display:grid;gap:8px;}
.kins.p2{grid-template-columns:1fr 1fr;}
.kins.p4{grid-template-columns:1fr 1fr;}
.kw label{display:block;font-size:9px;font-weight:800;color:var(--tx2);margin-bottom:3px;}
.kw input{width:100%;background:rgba(255,255,255,.72);border:1.5px solid rgba(255,255,255,.9);border-radius:9px;padding:7px 10px;font-family:'Nunito',sans-serif;font-size:13px;font-weight:700;color:var(--tx);outline:none;-webkit-appearance:none;transition:border-color .2s;}
.kw input:focus{border-color:var(--a1);}
.ksum{background:linear-gradient(135deg,rgba(91,140,255,.1),rgba(176,106,255,.1));border:1.5px solid rgba(91,140,255,.25);border-radius:var(--r);padding:16px;text-align:center;display:none;margin-top:12px;}
.ksum.show{display:block;}
.ksg{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:12px;}
.ksb{background:rgba(255,255,255,.5);border-radius:12px;padding:10px 6px;text-align:center;}
.ksbl{font-size:9px;font-weight:800;color:var(--tx2);letter-spacing:1px;text-transform:uppercase;margin-bottom:2px;}
.ksbv{font-size:1.2rem;font-weight:900;}
/* DONEM */
.di2{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:12px 14px;margin-bottom:8px;}
.d2h{display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;}
.d2n{font-weight:800;font-size:13px;}
.d2g{font-size:1.1rem;font-weight:900;}
.d2bar{height:5px;background:rgba(0,0,0,.08);border-radius:99px;overflow:hidden;margin-top:8px;}
.d2bf{height:100%;border-radius:99px;transition:width .6s cubic-bezier(.34,1.56,.64,1);}
.chart-w{position:relative;height:180px;margin-top:12px;}
/* SINAV */
.si2{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:12px 14px;margin-bottom:7px;display:grid;grid-template-columns:1fr auto;align-items:center;gap:8px;}
.s2u{border-color:rgba(255,77,106,.4);background:rgba(255,77,106,.06);}
/* TUS */
.tg2{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:10px;}
.tb2{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:14px;text-align:center;}
.tb2l{font-size:9px;font-weight:800;color:var(--tx2);letter-spacing:1px;text-transform:uppercase;margin-bottom:4px;}
.tb2v{font-size:1.4rem;font-weight:900;}
.tbr{display:flex;justify-content:space-between;align-items:center;padding:10px 14px;background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);margin-bottom:6px;}
.tbn{font-size:12px;font-weight:800;}
.tbp{font-size:11px;color:var(--tx2);font-weight:600;}
.tbs{font-size:11px;font-weight:800;padding:2px 8px;border-radius:6px;}
/* AYARLAR */
.av-r{display:flex;align-items:center;gap:14px;margin-bottom:18px;}
.avc{width:64px;height:64px;border-radius:50%;background:linear-gradient(135deg,var(--a1),var(--a2));display:flex;align-items:center;justify-content:center;font-size:1.8rem;flex-shrink:0;box-shadow:0 4px 14px rgba(91,140,255,.28);cursor:pointer;overflow:hidden;}
.avc img{width:100%;height:100%;object-fit:cover;border-radius:50%;}
.avi h2{font-size:1rem;font-weight:800;}
.avi p{font-size:11px;color:var(--tx2);font-weight:600;margin-top:1px;}
.sgl{font-size:9px;font-weight:800;letter-spacing:2px;text-transform:uppercase;color:var(--tx2);margin-bottom:7px;padding:0 3px;}
.sitem{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:12px 14px;margin-bottom:5px;display:flex;align-items:center;justify-content:space-between;cursor:pointer;}
.sil{display:flex;align-items:center;gap:10px;}
.sic{width:34px;height:34px;border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:15px;flex-shrink:0;}
.sit .ti{font-size:13px;font-weight:800;}
.sit .su{font-size:10px;color:var(--tx2);font-weight:600;margin-top:1px;}
.sarr{color:var(--tx2);font-size:13px;}
.sval{font-size:11px;color:var(--tx2);font-weight:700;margin-right:4px;}
.copts{display:flex;gap:9px;flex-wrap:wrap;padding:4px 14px 12px;}
.cdot{width:30px;height:30px;border-radius:50%;cursor:pointer;transition:all .2s;border:3px solid transparent;}
.cdot.on{border-color:white;box-shadow:0 0 0 2px var(--a1);transform:scale(1.12);}
/* ROZETLER */
.roz-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;}
.roz-box{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:14px 10px;text-align:center;position:relative;}
.roz-box.locked{opacity:.3;filter:grayscale(1);}
.roz-box.unlocked{border-color:rgba(255,210,0,.5);background:rgba(255,210,0,.08);}
.roz-emoji{font-size:1.8rem;line-height:1;margin-bottom:6px;}
.roz-isim{font-size:9px;font-weight:800;color:var(--tx2);line-height:1.3;}
.roz-new{position:absolute;top:-5px;right:-5px;background:linear-gradient(135deg,var(--a1),var(--a2));color:white;font-size:8px;font-weight:800;padding:2px 6px;border-radius:99px;}
/* BACKUP */
.bk-row{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:8px;}
.bk-btn{padding:12px;border:none;border-radius:var(--rs);font-family:'Nunito',sans-serif;font-size:12px;font-weight:800;cursor:pointer;}
.bk-btn.exp{background:linear-gradient(135deg,var(--grn),#0ead69);color:white;}
.bk-btn.imp{background:rgba(255,255,255,.6);border:1.5px solid var(--gb);color:var(--tx);}
/* POMODORO */
.pom-wrap{text-align:center;padding:8px 0;}
.pom-ring{position:relative;width:190px;height:190px;margin:0 auto 16px;}
.pom-svg{width:190px;height:190px;transform:rotate(-90deg);}
.pom-track{fill:none;stroke:rgba(255,255,255,.3);stroke-width:10;}
.pom-prog{fill:none;stroke-width:10;stroke-linecap:round;transition:stroke-dashoffset .5s ease,stroke .5s ease;}
.pom-time{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);text-align:center;}
.pom-time-num{font-size:2.6rem;font-weight:900;letter-spacing:-2px;line-height:1;}
.pom-time-lbl{font-size:10px;font-weight:800;color:var(--tx2);letter-spacing:2px;text-transform:uppercase;margin-top:3px;}
.pom-btns{display:flex;gap:10px;justify-content:center;margin-bottom:16px;}
.pom-btn{width:50px;height:50px;border-radius:50%;border:none;font-size:1.2rem;cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;}
.pom-btn.main{background:linear-gradient(135deg,var(--a1),var(--a2));box-shadow:0 4px 16px rgba(91,140,255,.35);width:58px;height:58px;font-size:1.4rem;}
.pom-btn.sec{background:rgba(255,255,255,.6);border:1px solid var(--gb);}
.pom-modes{display:flex;gap:6px;justify-content:center;margin-bottom:14px;}
.pom-mode{padding:7px 14px;border-radius:99px;border:none;font-family:'Nunito',sans-serif;font-size:11px;font-weight:800;cursor:pointer;background:rgba(255,255,255,.4);color:var(--tx2);transition:all .2s;}
.pom-mode.on{background:linear-gradient(135deg,var(--a1),var(--a2));color:white;}
.pom-stats{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:12px;}
.pom-stat{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:12px 8px;text-align:center;}
.pom-stat-l{font-size:9px;font-weight:800;color:var(--tx2);letter-spacing:1px;text-transform:uppercase;margin-bottom:3px;}
.pom-stat-v{font-size:1.3rem;font-weight:900;}
.pom-log-item{background:rgba(255,255,255,.55);border:1px solid var(--gb);border-radius:var(--rs);padding:10px 14px;display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;}
.pom-notif{background:linear-gradient(135deg,rgba(48,201,142,.15),rgba(91,140,255,.15));border:1.5px solid rgba(48,201,142,.3);border-radius:var(--rs);padding:12px 16px;text-align:center;display:none;margin-top:12px;}
.pom-notif.show{display:block;}
/* SKELETON */
.skel{background:linear-gradient(90deg,rgba(255,255,255,.35) 25%,rgba(255,255,255,.65) 50%,rgba(255,255,255,.35) 75%);background-size:200% 100%;animation:shim 1.4s infinite;border-radius:10px;}
@keyframes shim{0%{background-position:200% 0}100%{background-position:-200% 0}}
.skel-l{height:13px;margin-bottom:9px;border-radius:7px;}
.skel-box{height:54px;width:100%;border-radius:var(--rs);margin-bottom:9px;}
/* KONFETİ */
#cw{position:fixed;inset:0;pointer-events:none;z-index:500;overflow:hidden;}
.cf{position:absolute;top:-20px;width:9px;height:9px;border-radius:2px;animation:cfF linear both;}
@keyframes cfF{0%{transform:translateY(0) rotate(0);opacity:1}100%{transform:translateY(110vh) rotate(720deg);opacity:0}}
/* PAYLAŞIM */
#sh-ov{position:fixed;inset:0;background:rgba(0,0,0,.5);backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);z-index:300;display:none;align-items:center;justify-content:center;padding:20px;}
#sh-ov.show{display:flex;}
#sh-cw{width:100%;max-width:400px;}
#sh-canvas{width:100%;border-radius:20px;box-shadow:0 20px 60px rgba(0,0,0,.3);display:block;}
.sh-acts{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:12px;}
.sh-abtn{padding:13px;border:none;border-radius:var(--rs);font-family:'Nunito',sans-serif;font-size:13px;font-weight:800;cursor:pointer;}
.sh-abtn.dl{background:linear-gradient(135deg,var(--a1),var(--a2));color:white;}
.sh-abtn.cl{background:rgba(255,255,255,.85);color:var(--tx);}
/* MODAL */
.overlay{position:fixed;inset:0;background:rgba(0,0,0,.28);backdrop-filter:blur(8px);-webkit-backdrop-filter:blur(8px);z-index:200;display:flex;align-items:flex-end;justify-content:center;padding:16px;}
.sheet{background:rgba(255,255,255,.94);border:1px solid var(--gb);border-radius:28px 28px 20px 20px;padding:26px 22px 22px;width:100%;max-width:520px;}
.shp{width:34px;height:4px;background:rgba(0,0,0,.13);border-radius:99px;margin:0 auto 18px;}
.sht{font-size:1.15rem;font-weight:900;text-align:center;margin-bottom:6px;}
.shs{font-size:12px;color:var(--tx2);text-align:center;font-weight:600;margin-bottom:20px;line-height:1.5;}
.shb{display:grid;grid-template-columns:1fr 1fr;gap:10px;}
.shbtn{padding:14px;border:none;border-radius:var(--rs);font-family:'Nunito',sans-serif;font-size:14px;font-weight:800;cursor:pointer;}
.shbtn.yes{background:linear-gradient(135deg,var(--a1),var(--a2));color:white;}
.shbtn.no{background:rgba(0,0,0,.05);color:var(--tx);}
/* TAB BAR */
.tbar{position:fixed;bottom:0;left:0;right:0;z-index:100;display:flex;justify-content:center;padding:0 12px;padding-bottom:max(14px,env(safe-area-inset-bottom));}
.tbi{display:flex;background:rgba(255,255,255,.75);border:1px solid rgba(255,255,255,.92);backdrop-filter:blur(30px) saturate(180%);-webkit-backdrop-filter:blur(30px) saturate(180%);border-radius:99px;padding:5px;gap:3px;box-shadow:0 8px 28px rgba(0,0,0,.11);width:100%;max-width:520px;}
.tb{flex:1;display:flex;flex-direction:column;align-items:center;gap:2px;padding:7px 5px;border:none;background:transparent;border-radius:90px;cursor:pointer;transition:all .25s cubic-bezier(.34,1.56,.64,1);color:var(--tx2);}
.tb.on{background:linear-gradient(135deg,var(--a1),var(--a2));color:white;box-shadow:0 4px 14px rgba(91,140,255,.32);transform:scale(1.06);}
.tbi2{font-size:17px;line-height:1;}
.tbl{font-size:8px;font-weight:800;white-space:nowrap;}
/* PANEL */
.panel{display:none;}
.panel.on{display:block;animation:pI .28s cubic-bezier(.34,1.2,.64,1) both;}
@keyframes pI{from{opacity:0;transform:translateY(9px) scale(.98)}to{opacity:1;transform:translateY(0) scale(1)}}
/* DARK */
body.dark{background:linear-gradient(160deg,#0d1117 0%,#10121a 50%,#12101a 100%);}
body.dark .f input,body.dark .f select,body.dark .kw input{background:rgba(255,255,255,.08);border-color:rgba(255,255,255,.12);color:#e8e8f8;}
body.dark .card{background:rgba(255,255,255,.06);}
body.dark .sitem{background:rgba(255,255,255,.07);}
body.dark .sheet{background:rgba(22,22,40,.96);}
body.dark .shbtn.no{background:rgba(255,255,255,.1);color:#e8e8f8;}
body.dark .tbi{background:rgba(18,18,36,.88);border-color:rgba(255,255,255,.1);}
</style>
</head>
<body>

<!-- KONFETİ -->
<div id="cw"></div>

<!-- PAYLAŞIM -->
<div id="sh-ov" onclick="if(event.target===this)this.classList.remove('show')">
  <div id="sh-cw">
    <canvas id="sh-canvas"></canvas>
    <div class="sh-acts">
      <button class="sh-abtn dl" onclick="downloadShare()">📥 Kaydet</button>
      <button class="sh-abtn cl" onclick="document.getElementById('sh-ov').classList.remove('show')">✕ Kapat</button>
    </div>
  </div>
</div>

<!-- PRATIK MODAL -->
<div class="overlay" id="modal">
  <div class="sheet">
    <div class="shp"></div>
    <div class="sht">🏥 Pratik Sınav Var Mı?</div>
    <div class="shs">Komite sınavlarında ayrı bir <b>pratik sınav</b> yapılıyor mu?</div>
    <div class="shb">
      <button class="shbtn no" onclick="pratikC(false)">Hayır, sadece teorik</button>
      <button class="shbtn yes" onclick="pratikC(true)">Evet, pratik de var ✓</button>
    </div>
  </div>
</div>

<div class="w">
  <!-- HEADER -->
  <div class="hdr">
    <div style="display:flex;justify-content:space-between;align-items:flex-start">
      <div>
        <div class="chip">✦ NotHesap</div>
        <h1><span>Not</span></h1>
        <p class="hdr-sub" id="hsub">Tıp · GNO · Pomodoro</p>
      </div>
      <div id="hdr-av" onclick="goProfile()" style="width:44px;height:44px;border-radius:50%;background:linear-gradient(135deg,var(--a1),var(--a2));display:flex;align-items:center;justify-content:center;font-size:1.3rem;flex-shrink:0;margin-top:54px;cursor:pointer;overflow:hidden;border:2.5px solid rgba(255,255,255,.8);box-shadow:0 4px 14px rgba(91,140,255,.28);">
        <span id="hdr-av-inner">🎓</span>
      </div>
    </div>
  </div>

  <!-- ===================== TIP FAKÜLTESİ ===================== -->
  <div id="p-tip" class="panel on">
    <!-- Komite -->
    <div class="card" id="komite-main-card">
      <div class="sl">Komite Sistemi — Katsayılı</div>
      <div style="background:rgba(91,140,255,.07);border:1px solid rgba(91,140,255,.2);border-radius:10px;padding:12px;margin-bottom:12px">
        <div style="font-size:10px;font-weight:800;color:var(--a1);letter-spacing:1px;text-transform:uppercase;margin-bottom:8px">Final Sınavı</div>
        <div class="r2">
          <div class="f"><label>Final Puanı (0–100)</label><input type="number" id="kfn" placeholder="Finalden aldığın puan" min="0" max="100" oninput="renderKG()"></div>
          <div class="f"><label>Final Katsayısı (100'den)</label><input type="number" id="kfk" placeholder="40" value="40" min="0" max="100" oninput="renderKomiteler();renderKG()"></div>
        </div>
      </div>
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
        <div class="sl" style="margin-bottom:0">Komiteler</div>
        <div style="font-size:10px;font-weight:700;color:var(--tx2)" id="kattop">Katsayı: 0</div>
      </div>
      <button class="btnd" onclick="komiteEkle()">+ Komite Ekle</button>
      <div id="klist"><div class="empty">Henüz komite eklenmedi 🏥</div></div>
      <div class="ksum" id="ksum">
        <div class="rl">Dönem Sonu Ortalaması</div>
        <div class="rn" id="ksv" style="color:var(--a1)">—</div>
        <div class="rd" id="ksd">—</div>
        <div class="ksg">
          <div class="ksb"><div class="ksbl">Komite Ort.</div><div class="ksbv" id="ks1">—</div></div>
          <div class="ksb"><div class="ksbl">Final</div><div class="ksbv" id="ks2">—</div></div>
          <div class="ksb"><div class="ksbl">Durum</div><div class="ksbv" id="ks3" style="font-size:.85rem">—</div></div>
        </div>
      </div>
    </div>
    <!-- Sınav Takvimi EN ALTA taşınacak, şimdilik buradan kaldır -->

    <!-- Staj — sadece 4-5-6. sınıflar için -->
    <div class="card" id="staj-card" style="display:none">
      <div class="sl">🩺 Staj Notu Takibi</div>
      <div class="r2">
        <div class="f"><label>Staj Adı</label><input type="text" id="sst" placeholder="Dahiliye"></div>
        <div class="f"><label>Not (0–100)</label><input type="number" id="ssn" placeholder="80" min="0" max="100"></div>
      </div>
      <div class="r1" style="margin-bottom:10px">
        <div class="f"><label>Kredi</label><input type="number" id="ssk" placeholder="4" value="4" min="1"></div>
      </div>
      <button class="btnf" onclick="stajEkle()">+ Staj Ekle</button>
      <div style="margin-top:12px"><div class="dl" id="stajlist"><div class="empty">Henüz staj eklenmedi 🏥</div></div></div>
      <div id="stajres" style="display:none">
        <div class="sr">
          <div class="sb"><div class="sbl">Staj Ort.</div><div class="sbv" id="ss1">—</div></div>
          <div class="sb"><div class="sbl">GNO (4)</div><div class="sbv" id="ss2">—</div></div>
          <div class="sb"><div class="sbl">Kredi</div><div class="sbv" id="ss3">—</div></div>
        </div>
      </div>
    </div>

    <!-- Sınav Takvimi — HER ZAMAN EN ALTTA -->
    <div class="card">
      <div class="sl">📅 Sınav Takvimi</div>
      <div class="r2">
        <div class="f"><label>Sınav Adı</label><input type="text" id="stisim" placeholder="Anatomi Komite 1"></div>
        <div class="f"><label>Tarih</label><input type="date" id="sttarih"></div>
      </div>
      <button class="btnf" onclick="sinavEkle()">+ Sınav Ekle</button>
      <div style="margin-top:12px" id="slist"><div class="empty">Sınav eklenmedi 📅</div></div>
    </div>
  </div>

  <!-- ===================== DİĞER BÖLÜMLER ===================== -->
  <div id="p-diger" class="panel">

    <!-- 1. DERSLER & ORTALAMA (en üstte) -->
    <div class="card">
      <div class="sl">📚 Dersler</div>
      <div class="r3">
        <div class="f"><label>Ders Adı</label><input type="text" id="di" placeholder="Matematik"></div>
        <div class="f"><label>Not (0–100)</label><input type="number" id="dn2" placeholder="85" min="0" max="100"></div>
        <div class="f"><label>Kredi</label><input type="number" id="dk" placeholder="3" value="3" min="1" max="10"></div>
      </div>
      <button class="btnf" onclick="dersEkle()">+ Ders Ekle</button>
      <div style="margin-top:12px"><div class="dl" id="derslist"><div class="empty">Henüz ders eklenmedi 📚</div></div></div>
      <div id="gnores" style="display:none">
        <div class="sr">
          <div class="sb"><div class="sbl">GNO (4'lük)</div><div class="sbv" id="sg4">—</div></div>
          <div class="sb"><div class="sbl">Ort (100)</div><div class="sbv" id="sg100">—</div></div>
          <div class="sb"><div class="sbl">Kredi</div><div class="sbv" id="skr">—</div></div>
        </div>
      </div>
    </div>

    <!-- 3. BÜTÜNLEME -->
    <div class="card">
      <div class="sl">🔄 Bütünleme Hesaplayıcı</div>
      <div class="r2">
        <div class="f"><label>Dönem Sonu Ortalamanız</label><input type="number" id="bt-ort" placeholder="örn: 45" min="0" max="100" oninput="hBut()"></div>
        <div class="f"><label>Bütünleme Ağırlığı (%)</label><input type="number" id="bt-agir" value="100" min="0" max="100" oninput="hBut()"></div>
      </div>
      <div class="r2">
        <div class="f"><label>Dönem Ağırlığı (%)</label><input type="number" id="bt-dagir" value="0" min="0" max="100" oninput="hBut()"></div>
        <div class="f"><label>Geçme Notu</label><select id="bt-gec" onchange="hBut()"><option value="60">60</option><option value="50">50</option><option value="45">45</option></select></div>
      </div>
      <div class="rb" id="rb2"><div class="rl">Bütünlemeden Alman Gereken</div><div class="rn" style="color:var(--tx2)">—</div><div class="rd">dönem ortalamanı gir</div></div>
    </div>

    <!-- 4. DÖNEM GEÇMİŞİ & GRAFİK -->
    <div class="card">
      <div class="sl">📅 Dönem Geçmişi & Grafik</div>
      <div id="dlist"><div class="empty">Henüz dönem eklenmedi 📅</div></div>
      <div class="chart-w" id="cwrap" style="display:none"><canvas id="gnoCh"></canvas></div>
      <div class="dv"></div>
      <div class="r2">
        <div class="f"><label>Dönem Adı</label><input type="text" id="ddad" placeholder="2024-Güz"></div>
        <div class="f"><label>Ort. (100'lük)</label><input type="number" id="ddgno" placeholder="75" min="0" max="100"></div>
      </div>
      <button class="btnf" onclick="donemEkle()">+ Dönem Ekle</button>
    </div>

    <!-- 5. HEDEF GNO -->
    <div class="card">
      <div class="sl">🎯 Hedef GNO</div>
      <div class="r2">
        <div class="f"><label>Hedef Ort. (100)</label><input type="number" id="hgno" placeholder="80" min="0" max="100" oninput="hHedef()"></div>
        <div class="f"><label>Kalan Ders Sayısı</label><input type="number" id="hkal" placeholder="5" min="1" oninput="hHedef()"></div>
      </div>
      <div id="hres" style="display:none">
        <div class="rb on" style="margin-top:10px">
          <div class="rl">Her Dersten Alman Gereken</div>
          <div class="rn" id="hnum" style="color:var(--a1)">—</div>
          <div class="rd" id="hdet">—</div>
        </div>
      </div>
    </div>

    <!-- 6. ROZETLER -->
    <div class="card">
      <div class="sl">🏅 Başarım Rozetleri</div>
      <div id="rozet-grid" style="display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-top:4px"></div>
    </div>

  </div>

  <!-- ===================== POMODORO ===================== -->
  <div id="p-pomodoro" class="panel">
    <div class="card">
      <div class="sl">🍅 Odaklanma Sayacı</div>
      <div class="pom-modes">
        <button class="pom-mode on" onclick="pomMode('focus',this)">🎯 Odak</button>
        <button class="pom-mode" onclick="pomMode('short',this)">☕ Kısa Mola</button>
        <button class="pom-mode" onclick="pomMode('long',this)">🛋️ Uzun Mola</button>
      </div>
      <div class="pom-wrap">
        <div class="pom-ring">
          <svg class="pom-svg" viewBox="0 0 190 190">
            <circle class="pom-track" cx="95" cy="95" r="80"/>
            <circle class="pom-prog" id="pom-circle" cx="95" cy="95" r="80"/>
          </svg>
          <div class="pom-time">
            <div class="pom-time-num" id="pom-display">25:00</div>
            <div class="pom-time-lbl" id="pom-lbl">ODAK</div>
          </div>
        </div>
        <div class="pom-btns">
          <button class="pom-btn sec" onclick="pomReset()">↺</button>
          <button class="pom-btn main" id="pom-playbtn" onclick="pomToggle()">▶</button>
          <button class="pom-btn sec" onclick="pomSkip()">⏭</button>
        </div>
      </div>
      <div class="pom-notif" id="pom-notif">
        <div style="font-size:1.5rem;margin-bottom:4px" id="pom-notif-icon">✅</div>
        <div style="font-size:14px;font-weight:800" id="pom-notif-txt">Süre bitti!</div>
      </div>
    </div>
    <div class="card">
      <div class="sl">Ne çalışıyorsun?</div>
      <div class="r2" style="margin-bottom:8px">
        <div class="f"><label>Konu / Ders</label><input type="text" id="pom-konu" placeholder="Anatomi — Sinir Sistemi"></div>
        <div class="f"><label>Hedef Pomodoro</label><input type="number" id="pom-hedef" placeholder="4" min="1" max="20" value="4"></div>
      </div>
      <div class="pom-stats">
        <div class="pom-stat"><div class="pom-stat-l">Bugün</div><div class="pom-stat-v" id="ps-bugun">0 🍅</div></div>
        <div class="pom-stat"><div class="pom-stat-l">Toplam</div><div class="pom-stat-v" id="ps-toplam">0 🍅</div></div>
        <div class="pom-stat"><div class="pom-stat-l">Süre</div><div class="pom-stat-v" id="ps-sure">0 dk</div></div>
      </div>
    </div>
    <div class="card">
      <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:12px">
        <div class="sl" style="margin-bottom:0">📋 Çalışma Geçmişi</div>
        <button class="btndel" onclick="pomLogTemizle()">Temizle</button>
      </div>
      <div id="pom-log"><div class="empty">Henüz çalışma kaydı yok 📖</div></div>
    </div>
    <div class="card">
      <div class="sl">⚙️ Süre Ayarları</div>
      <div class="r3">
        <div class="f"><label>Odak (dk)</label><input type="number" id="pom-set-focus" value="25" min="1" max="90" onchange="pomSureGun()"></div>
        <div class="f"><label>Kısa Mola (dk)</label><input type="number" id="pom-set-short" value="5" min="1" max="30" onchange="pomSureGun()"></div>
        <div class="f"><label>Uzun Mola (dk)</label><input type="number" id="pom-set-long" value="15" min="5" max="60" onchange="pomSureGun()"></div>
      </div>
    </div>
  </div>

  <!-- ===================== AYARLAR ===================== -->
  <div id="p-ayarlar" class="panel">
    <div class="card">
      <div class="av-r">
        <div class="avc" id="avc" onclick="document.getElementById('avinp').click()">
          <span id="avemo">🎓</span>
          <input type="file" id="avinp" accept="image/*" style="display:none" onchange="avDeg(this)">
        </div>
        <div class="avi"><h2 id="avisim">Tıp Öğrencisi</h2><p id="avuni">Üniversite seçilmedi</p></div>
      </div>
      <div class="r2">
        <div class="f"><label>Adın</label><input type="text" id="pisim" placeholder="Ad Soyad" oninput="pGun()"></div>
        <div class="f"><label>Sınıf</label><select id="psinif" onchange="pGun()"><option value="">Seç</option><option>1. Sınıf</option><option>2. Sınıf</option><option>3. Sınıf</option><option>4. Sınıf</option><option>5. Sınıf</option><option>6. Sınıf</option></select></div>
      </div>
      <div class="r1"><div class="f"><label>Üniversite</label><input type="text" id="puni" placeholder="Hacettepe Üniversitesi" oninput="pGun()"></div></div>
    </div>
    <div style="margin-bottom:7px"><div class="sgl">Görünüm</div></div>
    <div class="card" style="padding:8px 12px">
      <div class="tr"><div class="trl"><div class="tt">🌙 Karanlık Mod</div><div class="ts">Gece kullanımı</div></div><label class="tog"><input type="checkbox" id="darkt" onchange="tDark()"><div class="tsl"></div></label></div>
      <div class="dv" style="margin:8px 0"></div>
      <div class="tr" style="cursor:pointer" onclick="toggleCol()"><div class="trl"><div class="tt">🎨 Tema Rengi</div><div class="ts" id="rsub">Mavi</div></div><span class="sarr">›</span></div>
      <div class="copts" id="copts" style="display:none">
        <div class="cdot on" style="background:linear-gradient(135deg,#5b8cff,#b06aff)" onclick="rSec('Mavi',this,'#5b8cff','#b06aff')"></div>
        <div class="cdot" style="background:linear-gradient(135deg,#ff6b6b,#feca57)" onclick="rSec('Turuncu',this,'#ff6b6b','#feca57')"></div>
        <div class="cdot" style="background:linear-gradient(135deg,#48c774,#0ead69)" onclick="rSec('Yeşil',this,'#48c774','#0ead69')"></div>
        <div class="cdot" style="background:linear-gradient(135deg,#ff6b9d,#c44dff)" onclick="rSec('Pembe',this,'#ff6b9d','#c44dff')"></div>
        <div class="cdot" style="background:linear-gradient(135deg,#f7971e,#ffd200)" onclick="rSec('Altın',this,'#f7971e','#ffd200')"></div>
      </div>
      <div class="dv" style="margin:8px 0"></div>
      <div class="tr"><div class="trl"><div class="tt">🔤 Büyük Yazı</div><div class="ts">Yazı boyutunu artırır</div></div><label class="tog"><input type="checkbox" id="bytt" onchange="tByt()"><div class="tsl"></div></label></div>
      <div class="dv" style="margin:8px 0"></div>
      <div class="tr"><div class="trl"><div class="tt">🌓 Otomatik Karanlık Mod</div><div class="ts">22:00–07:00 arası otomatik</div></div><label class="tog"><input type="checkbox" id="autod" onchange="saveS()"><div class="tsl"></div></label></div>
    </div>
    <div style="margin:12px 0 7px"><div class="sgl">Not Sistemi</div></div>
    <div class="card" style="padding:8px 12px">
      <div class="tr"><div class="trl"><div class="tt">🏥 Pratik Sınav</div><div class="ts" id="psub">Komitede pratik var mı?</div></div><label class="tog"><input type="checkbox" id="pratt" onchange="pratikT()"><div class="tsl"></div></label></div>
      <div class="dv" style="margin:8px 0"></div>
      <div class="tr"><div class="trl"><div class="tt">💬 Motivasyon Mesajları</div><div class="ts">Not girince kutlama göster</div></div><label class="tog"><input type="checkbox" id="motivt" checked onchange="saveS()"><div class="tsl"></div></label></div>
    </div>
    <div style="margin:12px 0 7px"><div class="sgl">Veri & Paylaşım</div></div>
    <div class="card" style="padding:8px 12px">
      <div class="tr" style="cursor:default"><div class="trl"><div class="tt">💾 Yedekleme</div><div class="ts">Verilerini kaybet, içe aktar</div></div></div>
      <div class="bk-row">
        <button class="bk-btn exp" onclick="exportData()">📤 Dışa Aktar</button>
        <button class="bk-btn imp" onclick="document.getElementById('imp-inp').click()">📥 İçe Aktar</button>
      </div>
      <input type="file" id="imp-inp" accept=".json" style="display:none" onchange="importData(this)">
      <div class="dv" style="margin:12px 0 8px"></div>
      <div class="tr" style="cursor:default"><div class="trl"><div class="tt">🎨 Dönem Özet Kartı</div><div class="ts">Sosyal medyada paylaş</div></div></div>
      <button class="btnf" style="margin-top:8px" onclick="generateShareCard()">✨ Paylaşım Kartı Oluştur</button>
    </div>
    <div style="margin:12px 0 7px"><div class="sgl">Diğer</div></div>
    <div class="card" style="padding:8px 12px">
      <div class="sitem" onclick="reset()">
        <div class="sil"><div class="sic" style="background:linear-gradient(135deg,#ff6b6b,#ee0979)">🗑️</div><div class="sit"><div class="ti">Verileri Sıfırla</div><div class="su">Tüm veriler silinir</div></div></div>
        <span class="sarr" style="color:var(--red)">›</span>
      </div>
      <div class="sitem" style="cursor:default">
        <div class="sil"><div class="sic" style="background:linear-gradient(135deg,#a18cd1,#fbc2eb)">ℹ️</div><div class="sit"><div class="ti">NotHesap</div><div class="su">v2.0 — Tıp öğrencileri için</div></div></div>
        <span class="sval">v2.0</span>
      </div>
    </div>
  </div>
</div>

<!-- TAB BAR -->
<div class="tbar">
  <div class="tbi">
    <button class="tb on"  id="tb-tip"      onclick="sw('tip',this)">     <span class="tbi2">🏥</span><span class="tbl">Tıp Fakültesi</span></button>
    <button class="tb"     id="tb-diger"    onclick="sw('diger',this)">   <span class="tbi2">📐</span><span class="tbl">Diğer</span></button>
    <button class="tb"     id="tb-pomodoro" onclick="sw('pomodoro',this)"><span class="tbi2">🍅</span><span class="tbl">Pomodoro</span></button>
    <button class="tb"     id="tb-ayarlar"  onclick="sw('ayarlar',this)"> <span class="tbi2">⚙️</span><span class="tbl">Ayarlar</span></button>
  </div>
</div>

<script>
// ====== STATE ======
let pratikVar=false,dersler=[],donemler=[],komiteler=[],sinavlar=[],stajlar=[],gnoCh=null;
let kazanilanRozetler=[];
const MVi=['🔥 Harika gidiyorsun!','🎯 Tam hedefte!','⭐ Süpersin!','💪 Devam et!','🚀 Uçuyorsun!'];
const MVo=['👍 İyi iş!','📚 Biraz daha çalış!','💡 Gelişiyorsun!'];
const MVk=['😮 Dikkat et!','📖 Daha çok çalışman gerek','💪 Pes etme!'];

// ====== INIT ======
window.onload=()=>{
  try{
    const sv=localStorage.getItem('pratikVar');
    if(sv!==null){
      pratikVar=sv==='true';
      const modal=document.getElementById('modal');
      const pratt=document.getElementById('pratt');
      if(modal)modal.style.display='none';
      if(pratt)pratt.checked=pratikVar;
      upPratik();
    }
    loadAll();
    checkAD();
    setInterval(checkAD,60000);
    pomYukle();
    pomGuncelle();
  }catch(e){console.warn('Init hatası:',e);}
};

// ====== TAB ======
function sw(id,btn){
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('on'));
  document.querySelectorAll('.tb').forEach(b=>b.classList.remove('on'));
  document.getElementById('p-'+id).classList.add('on');
  btn.classList.add('on');
}
function goProfile(){
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('on'));
  document.querySelectorAll('.tb').forEach(b=>b.classList.remove('on'));
  document.getElementById('p-ayarlar').classList.add('on');
  document.getElementById('tb-ayarlar').classList.add('on');
  window.scrollTo({top:0,behavior:'smooth'});
}

// ====== HELPERS ======
function harf(n){
  if(n>=90)return{h:'AA',p:4.0,c:'#30c98e'};if(n>=85)return{h:'BA',p:3.5,c:'#5ec98e'};
  if(n>=80)return{h:'BB',p:3.0,c:'#8ec930'};if(n>=75)return{h:'CB',p:2.5,c:'#c9b030'};
  if(n>=70)return{h:'CC',p:2.0,c:'#f5a623'};if(n>=65)return{h:'DC',p:1.5,c:'#f57823'};
  if(n>=60)return{h:'DD',p:1.0,c:'#f55023'};return{h:'FF',p:0.0,c:'#ff4d6a'};
}
function nc(n){return n>=75?'var(--grn)':n>=60?'var(--yel)':'var(--red)';}
function kA(a,b,w){
  const va=parseFloat(document.getElementById(a).value)||0;
  const el=document.getElementById(b);
  if(va+(parseFloat(el.value)||0)>100){el.value=100-va;const ew=document.getElementById(w);ew.classList.add('show');clearTimeout(ew._t);ew._t=setTimeout(()=>ew.classList.remove('show'),3000);}
}

// ====== SES & HAPTİK ======
let audioCtx=null;
function playTick(){try{if(!audioCtx)audioCtx=new(window.AudioContext||window.webkitAudioContext)();const o=audioCtx.createOscillator();const g=audioCtx.createGain();o.connect(g);g.connect(audioCtx.destination);o.frequency.value=880;o.type='sine';g.gain.setValueAtTime(.15,audioCtx.currentTime);g.gain.exponentialRampToValueAtTime(.001,audioCtx.currentTime+.08);o.start(audioCtx.currentTime);o.stop(audioCtx.currentTime+.08);}catch(e){}if(navigator.vibrate)navigator.vibrate(8);}
function playSuccess(){try{if(!audioCtx)audioCtx=new(window.AudioContext||window.webkitAudioContext)();[523,659,784].forEach((f,i)=>{const o=audioCtx.createOscillator();const g=audioCtx.createGain();o.connect(g);g.connect(audioCtx.destination);o.frequency.value=f;o.type='sine';const t=audioCtx.currentTime+i*.1;g.gain.setValueAtTime(.12,t);g.gain.exponentialRampToValueAtTime(.001,t+.15);o.start(t);o.stop(t+.15);});}catch(e){}if(navigator.vibrate)navigator.vibrate([10,50,10]);}

// ====== KONFETİ ======
function konfeti(){
  const wrap=document.getElementById('cw');
  const cols=['#5b8cff','#b06aff','#ff6b9d','#30c98e','#f5a623','#ff4d6a','#ffd200'];
  for(let i=0;i<60;i++){const el=document.createElement('div');el.className='cf';el.style.cssText=`left:${Math.random()*100}%;background:${cols[Math.floor(Math.random()*cols.length)]};width:${6+Math.random()*8}px;height:${6+Math.random()*8}px;animation-duration:${2+Math.random()*2}s;animation-delay:${Math.random()*.5}s;border-radius:${Math.random()>.5?'50%':'2px'}`;wrap.appendChild(el);setTimeout(()=>el.remove(),(4+Math.random()*2)*1000);}
  playSuccess();
}

// ====== MOTİVASYON ======
function showMot(n){
  if(!document.getElementById('motivt').checked)return;
  const el=document.getElementById('motiv');const pool=n>=80?MVi:n>=60?MVo:MVk;
  document.getElementById('mtext').textContent=pool[Math.floor(Math.random()*pool.length)];
  el.classList.add('show');clearTimeout(el._t);el._t=setTimeout(()=>el.classList.remove('show'),3000);
  if(n>=80){playSuccess();konfeti();}else if(n>=60)playTick();
}

// ====== PRATİK MODAL ======
function pratikC(v){pratikVar=v;localStorage.setItem('pratikVar',v);document.getElementById('modal').style.display='none';document.getElementById('pratt').checked=v;upPratik();renderKomiteler();}
function pratikT(){pratikVar=document.getElementById('pratt').checked;localStorage.setItem('pratikVar',pratikVar);upPratik();renderKomiteler();}
function upPratik(){const el=document.getElementById('psub');if(el)el.textContent=pratikVar?'Pratik sınav aktif ✓':'Sadece teorik sınav';}

// ====== VİZE/FİNAL ======
function hvize(){
  // Artık sadece hgec'i tetikle, rv yok
  hgec();
}
let iOn=false;
function toggleI(){} // artık kullanılmıyor
function hgec(){
  const v=parseFloat(document.getElementById('vize').value);
  const va=parseFloat(document.getElementById('va').value)/100;
  const fa=parseFloat(document.getElementById('fa').value)/100;
  const gec=parseFloat(document.getElementById('gss').value)||60;
  const box=document.getElementById('rg');
  if(isNaN(v)||fa===0)return;
  const g=(gec-v*va)/fa;
  box.classList.add('on');
  if(g<=0){box.querySelector('.rn').textContent='✓';box.querySelector('.rn').style.color='var(--grn)';box.querySelector('.rd').textContent='Vize notunla zaten geçiyorsun!';}
  else if(g>100){box.querySelector('.rn').textContent='✗';box.querySelector('.rn').style.color='var(--red)';box.querySelector('.rd').textContent='100\'den fazla gerekiyor!';}
  else{const hr=harf(g);box.querySelector('.rn').textContent=g.toFixed(1);box.querySelector('.rn').style.color=nc(g);box.querySelector('.rd').innerHTML=`Bu notu alırsan: <b style="color:${hr.c}">${hr.h}</b>`;}
}
let butOn=false;
function toggleBut(){} // artık kullanılmıyor
function hBut(){
  const ort=parseFloat(document.getElementById('bt-ort').value);const ba=parseFloat(document.getElementById('bt-agir').value)/100;const da=parseFloat(document.getElementById('bt-dagir').value)/100;const gec=parseFloat(document.getElementById('bt-gec').value);
  if(isNaN(ort))return;const ger=(gec-ort*da)/ba;const box=document.getElementById('rb2');box.classList.add('on');
  if(ger<=0){box.querySelector('.rn').textContent='✓';box.querySelector('.rn').style.color='var(--grn)';box.querySelector('.rd').textContent='Dönem notunla zaten geçiyorsun!';}
  else if(ger>100){box.querySelector('.rn').textContent='✗';box.querySelector('.rn').style.color='var(--red)';box.querySelector('.rd').textContent='Bütünlemeden geçmen mümkün değil 😔';}
  else{box.querySelector('.rn').textContent=ger.toFixed(1);box.querySelector('.rn').style.color=nc(ger);const hr=harf(ger);box.querySelector('.rd').innerHTML=`Bütünlemeden <b style="color:${hr.c}">${ger.toFixed(1)}</b> alman gerekiyor`;}
}

// ====== DÖNEM & GNO ======
function donemEkle(){const isim=document.getElementById('ddad').value.trim();const gno=parseFloat(document.getElementById('ddgno').value);if(!isim||isNaN(gno)){alert('Dönem adı ve not gir!');return;}donemler.push({isim,gno});document.getElementById('ddad').value='';document.getElementById('ddgno').value='';saveAll();renderDonemler();}
function donemSil(i){donemler.splice(i,1);saveAll();renderDonemler();}
function renderDonemler(){
  const list=document.getElementById('dlist');const cw=document.getElementById('cwrap');
  if(!donemler.length){list.innerHTML='<div class="empty">Henüz dönem eklenmedi 📅</div>';cw.style.display='none';return;}
  list.innerHTML=donemler.map((d,i)=>{const col=d.gno>=75?'#30c98e':d.gno>=60?'#f5a623':'#ff4d6a';return `<div class="di2"><div class="d2h"><div class="d2n">${d.isim}</div><div style="display:flex;align-items:center;gap:8px"><div class="d2g" style="color:${col}">${d.gno.toFixed(1)}</div><button class="btndel" onclick="donemSil(${i})">✕</button></div></div><div class="d2bar"><div class="d2bf" style="width:${d.gno}%;background:${col}"></div></div></div>`;}).join('');
  cw.style.display='block';renderGC();
}
function renderGC(){
  if(gnoCh)gnoCh.destroy();const ctx=document.getElementById('gnoCh').getContext('2d');const dk=document.body.classList.contains('dark');
  gnoCh=new Chart(ctx,{type:'line',data:{labels:donemler.map(d=>d.isim),datasets:[{label:'GNO',data:donemler.map(d=>d.gno),borderColor:'#5b8cff',backgroundColor:'rgba(91,140,255,.1)',borderWidth:2.5,pointBackgroundColor:'#5b8cff',pointRadius:5,tension:.4,fill:true}]},options:{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:{grid:{color:dk?'rgba(255,255,255,.07)':'rgba(0,0,0,.06)'},ticks:{color:dk?'#7a7a9a':'#5a5a7a',font:{size:10,weight:'700'}}},y:{min:0,max:100,grid:{color:dk?'rgba(255,255,255,.07)':'rgba(0,0,0,.06)'},ticks:{color:dk?'#7a7a9a':'#5a5a7a',font:{size:10,weight:'700'}}}}}});
}
function dersEkle(){const isim=document.getElementById('di').value.trim();const n=parseFloat(document.getElementById('dn2').value);const k=parseFloat(document.getElementById('dk').value);if(!isim||isNaN(n)||isNaN(k)){alert('Tüm alanları doldur!');return;}dersler.push({isim,n,k});document.getElementById('di').value='';document.getElementById('dn2').value='';document.getElementById('dk').value='3';playTick();saveAll();renderDersler();kontrolRozetler();}
function dersSil(i){dersler.splice(i,1);saveAll();renderDersler();}
function renderDersler(){
  const list=document.getElementById('derslist');
  if(!dersler.length){list.innerHTML='<div class="empty">Henüz ders eklenmedi 📚</div>';document.getElementById('gnores').style.display='none';return;}
  list.innerHTML=dersler.map((d,i)=>{const hr=harf(d.n);return `<div class="di"><div><div class="dn">${d.isim}</div><div class="dm">${d.n}/100 · ${d.k} kredi</div></div><div class="dhb" style="background:${hr.c}22;color:${hr.c}">${hr.h}</div><div style="font-size:11px;color:var(--tx2);font-weight:700">${hr.p}</div><button class="btndel" onclick="dersSil(${i})">✕</button></div>`;}).join('');
  let tp=0,tk=0,tn=0;dersler.forEach(d=>{const hr=harf(d.n);tp+=hr.p*d.k;tk+=d.k;tn+=d.n*d.k;});
  const g4=(tp/tk).toFixed(2);const g100=(tn/tk).toFixed(1);
  document.getElementById('sg4').textContent=g4;document.getElementById('sg4').style.color=g4>=3?'var(--grn)':g4>=2?'var(--yel)':'var(--red)';
  document.getElementById('sg100').textContent=g100;document.getElementById('sg100').style.color=nc(parseFloat(g100));
  document.getElementById('skr').textContent=tk;document.getElementById('gnores').style.display='block';
}
function hHedef(){
  const h=parseFloat(document.getElementById('hgno').value);const k=parseFloat(document.getElementById('hkal').value);if(isNaN(h)||isNaN(k))return;
  let mt=0,mk=0;dersler.forEach(d=>{mt+=d.n*d.k;mk+=d.k;});const g=(h*(mk+k)-mt)/k;document.getElementById('hres').style.display='block';
  const num=document.getElementById('hnum');const det=document.getElementById('hdet');
  if(g<=0){num.textContent='✓';num.style.color='var(--grn)';det.textContent='Hedefini zaten geçiyorsun!';}
  else if(g>100){num.textContent='✗';num.style.color='var(--red)';det.textContent='Bu hedef ulaşılamaz.';}
  else{num.textContent=g.toFixed(1);num.style.color=nc(g);const hr=harf(g);det.innerHTML=`Kalan ${k} dersten ortalama <b style="color:${hr.c}">${hr.h}</b> alman gerekiyor`;}
}

// ====== KOMİTE ======
function komiteEkle(){komiteler.push({id:Date.now(),isim:`Komite ${komiteler.length+1}`,teorik:NaN,pratik:NaN,teorikA:pratikVar?60:100,pratikA:40,katsayi:7});playTick();saveAll();renderKomiteler();kontrolRozetler();}
function komiteSil(id){komiteler=komiteler.filter(k=>k.id!==id);saveAll();renderKomiteler();}
function komiteG(id,alan,val){
  const k=komiteler.find(k=>k.id===id);if(!k)return;
  if(alan==='teorikA'||alan==='pratikA'||alan==='katsayi')k[alan]=parseFloat(val)||0;else k[alan]=parseFloat(val);
  if(alan==='teorikA'&&pratikVar&&k.teorikA+k.pratikA>100){k.pratikA=100-k.teorikA;const e=document.getElementById(`pA${id}`);if(e)e.value=k.pratikA;}
  if(alan==='pratikA'&&pratikVar&&k.teorikA+k.pratikA>100){k.teorikA=100-k.pratikA;const e=document.getElementById(`tA${id}`);if(e)e.value=k.teorikA;}
  saveAll();renderKO(id);renderKG();
}
function kNotu(k){if(pratikVar){if(isNaN(k.teorik)||isNaN(k.pratik))return NaN;return k.teorik*(k.teorikA/100)+k.pratik*(k.pratikA/100);}return isNaN(k.teorik)?NaN:k.teorik;}
function renderKO(id){
  const k=komiteler.find(k=>k.id===id);const b=document.getElementById(`kbd${id}`);if(!b)return;
  const ort=kNotu(k);if(isNaN(ort)){b.textContent='—';b.style.background='rgba(90,90,122,.1)';b.style.color='var(--tx2)';return;}
  const hr=harf(ort);b.textContent=ort.toFixed(1);b.style.background=hr.c+'22';b.style.color=hr.c;
}
function renderKG(){
  const fk=parseFloat(document.getElementById('kfk').value)||40;const fn=parseFloat(document.getElementById('kfn').value);
  const topKat=komiteler.reduce((s,k)=>s+k.katsayi,0);
  document.getElementById('kattop').innerHTML=`Komite katsayı: <b>${topKat}</b>/${100-fk}`;
  const dolular=komiteler.filter(k=>!isNaN(kNotu(k)));const ksum=document.getElementById('ksum');
  if(!dolular.length&&isNaN(fn)){ksum.classList.remove('show');renderKA();return;}
  let ktp=0,kta=0;dolular.forEach(k=>{ktp+=kNotu(k)*k.katsayi;kta+=k.katsayi;});
  const kort=kta>0?ktp/kta:NaN;let dOrt=NaN;
  if(!isNaN(kort)&&!isNaN(fn)){dOrt=kort*((100-fk)/100)+fn*(fk/100);}else if(!isNaN(kort))dOrt=kort;
  if(isNaN(dOrt)){ksum.classList.remove('show');renderKA();return;}
  const hr=harf(dOrt);
  document.getElementById('ksv').textContent=dOrt.toFixed(2);document.getElementById('ksv').style.color=nc(dOrt);
  document.getElementById('ksd').innerHTML=`Harf: <b style="color:${hr.c}">${hr.h}</b>`;
  document.getElementById('ks1').textContent=isNaN(kort)?'—':kort.toFixed(1);document.getElementById('ks1').style.color=isNaN(kort)?'var(--tx2)':nc(kort);
  document.getElementById('ks2').textContent=isNaN(fn)?'—':fn.toFixed(1);document.getElementById('ks2').style.color=isNaN(fn)?'var(--tx2)':nc(fn);
  document.getElementById('ks3').textContent=dOrt>=60?'✅ Geçer':'❌ Kalır';
  ksum.classList.add('show');renderKA();
}
function renderKA(){
  const t=komiteler.length;const d=komiteler.filter(k=>!isNaN(kNotu(k)));
  document.getElementById('ka1').textContent=t;document.getElementById('ka2').textContent=d.filter(k=>kNotu(k)>=60).length;document.getElementById('ka3').textContent=d.filter(k=>kNotu(k)<60).length;
}
function renderKomiteler(){
  const list=document.getElementById('klist');
  if(!komiteler.length){list.innerHTML='<div class="empty">Henüz komite eklenmedi 🏥</div>';document.getElementById('ksum').classList.remove('show');renderKA();return;}
  const fk=parseFloat(document.getElementById('kfk').value)||40;
  list.innerHTML=komiteler.map(k=>{
    const pi=pratikVar?`<div class="kw"><label>Pratik Not</label><input type="number" placeholder="0–100" min="0" max="100" value="${isNaN(k.pratik)?'':k.pratik}" oninput="komiteG(${k.id},'pratik',this.value)"></div><div class="kw"><label>Pratik Ağırlık (%)</label><input type="number" id="pA${k.id}" value="${k.pratikA}" min="0" max="100" oninput="komiteG(${k.id},'pratikA',this.value)"></div>`:'';
    const ta=pratikVar?`<div class="kw"><label>Teorik Ağırlık (%)</label><input type="number" id="tA${k.id}" value="${k.teorikA}" min="0" max="100" oninput="komiteG(${k.id},'teorikA',this.value)"></div>`:'';
    return `<div class="ki"><div class="kh"><div class="kn">🏥 ${k.isim}</div><div style="display:flex;align-items:center;gap:7px"><div class="kbd" id="kbd${k.id}">—</div><button class="btndel" onclick="komiteSil(${k.id})">✕</button></div></div>
    <div class="kins ${pratikVar?'p4':'p2'}">
      <div class="kw"><label>${pratikVar?'Teorik Not':'Not'}</label><input type="number" placeholder="0–100" min="0" max="100" value="${isNaN(k.teorik)?'':k.teorik}" oninput="komiteG(${k.id},'teorik',this.value)"></div>
      ${ta}${pi}
      <div class="kw" style="grid-column:1/-1"><label>Katsayı (${100-fk} üzerinden)</label><input type="number" placeholder="7" min="0" max="${100-fk}" value="${k.katsayi}" oninput="komiteG(${k.id},'katsayi',this.value)"></div>
    </div></div>`;
  }).join('');
  komiteler.forEach(k=>renderKO(k.id));renderKG();
}

// ====== SINAV TAKVİMİ ======
function sinavEkle(){
  const isim=document.getElementById('stisim').value.trim();
  const tarih=document.getElementById('sttarih').value;
  if(!isim||!tarih){alert('Sınav adı ve tarih gir!');return;}
  sinavlar.push({isim,tarih});
  sinavlar.sort((a,b)=>new Date(a.tarih)-new Date(b.tarih));
  document.getElementById('stisim').value='';document.getElementById('sttarih').value='';
  playTick();saveAll();renderS();kontrolRozetler();
}
function sinavSil(i){sinavlar.splice(i,1);saveAll();renderS();}
function renderS(){
  const list=document.getElementById('slist');if(!sinavlar.length){list.innerHTML='<div class="empty">Sınav eklenmedi 📅</div>';return;}
  const bug=new Date();bug.setHours(0,0,0,0);
  list.innerHTML=sinavlar.map((s,i)=>{
    const t=new Date(s.tarih);t.setHours(0,0,0,0);const f=Math.round((t-bug)/(1000*60*60*24));
    const gc=f<0;const urg=f>=0&&f<=3;const gs=gc?'Geçti':(f===0?'Bugün!':`${f} gün`);const gr=gc?'var(--tx2)':f===0?'var(--red)':f<=3?'var(--yel)':'var(--grn)';
    return `<div class="si2${urg?' s2u':''}"><div><div style="font-weight:800;font-size:13px">${s.isim}</div><div style="font-size:11px;color:var(--tx2);font-weight:600;margin-top:2px">${t.toLocaleDateString('tr-TR',{day:'numeric',month:'long',year:'numeric'})}</div></div><div style="text-align:right"><div style="font-size:1.2rem;font-weight:900;color:${gr}">${gs}</div><button class="btndel" onclick="sinavSil(${i})">✕</button></div></div>`;
  }).join('');
}

// ====== TUS ======
const tusB=[{isim:'Kardiyoloji',min:88},{isim:'Radyoloji',min:87},{isim:'Dermatoloji',min:86},{isim:'Göz Hast.',min:85},{isim:'Nöroloji',min:84},{isim:'Anestezi',min:80},{isim:'Gen. Cerrahi',min:79},{isim:'Ortopedi',min:79},{isim:'İç Hast.',min:77},{isim:'Psikiyatri',min:76},{isim:'Çocuk Sağ.',min:75},{isim:'Aile Hek.',min:65}];
function hTUS(){
  const tb=parseFloat(document.getElementById('ttb').value);const kb=parseFloat(document.getElementById('tkb').value);if(isNaN(tb)||isNaN(kb))return;
  const p=(tb*.45+kb*.55).toFixed(1);const d=p>=90?'İlk %5':p>=85?'İlk %15':p>=80?'İlk %25':p>=75?'İlk %40':p>=70?'İlk %60':'%60 altı';
  document.getElementById('tpuan').textContent=p;document.getElementById('tdil').textContent=d;document.getElementById('tdil').style.color=nc(parseFloat(p));
  const gir=tusB.filter(b=>parseFloat(p)>=b.min);const gir2=tusB.filter(b=>parseFloat(p)<b.min).slice(0,4);
  document.getElementById('tbrans').innerHTML=[...gir.map(b=>`<div class="tbr"><div class="tbn">${b.isim}</div><div class="tbp">Min: ${b.min}</div><div class="tbs" style="background:#30c98e22;color:#30c98e">✓</div></div>`),...gir2.map(b=>`<div class="tbr"><div class="tbn">${b.isim}</div><div class="tbp">Min: ${b.min}</div><div class="tbs" style="background:#ff4d6a22;color:#ff4d6a">${(b.min-p).toFixed(1)} eksik</div></div>`)].join('');
  document.getElementById('tresult').style.display='block';
}

// ====== STAJ ======
function stajEkle(){const isim=document.getElementById('sst').value.trim();const n=parseFloat(document.getElementById('ssn').value);const k=parseFloat(document.getElementById('ssk').value);if(!isim||isNaN(n)||isNaN(k)){alert('Tüm alanları doldur!');return;}stajlar.push({isim,n,k});document.getElementById('sst').value='';document.getElementById('ssn').value='';document.getElementById('ssk').value='4';playTick();saveAll();renderStaj();kontrolRozetler();}
function stajSil(i){stajlar.splice(i,1);saveAll();renderStaj();}
function renderStaj(){
  const list=document.getElementById('stajlist');if(!stajlar.length){list.innerHTML='<div class="empty">Henüz staj eklenmedi 🏥</div>';document.getElementById('stajres').style.display='none';return;}
  list.innerHTML=stajlar.map((s,i)=>{const hr=harf(s.n);return `<div class="di"><div><div class="dn">${s.isim}</div><div class="dm">${s.n}/100 · ${s.k} kredi</div></div><div class="dhb" style="background:${hr.c}22;color:${hr.c}">${hr.h}</div><div style="font-size:11px;color:var(--tx2);font-weight:700">${hr.p}</div><button class="btndel" onclick="stajSil(${i})">✕</button></div>`;}).join('');
  let tp=0,tk=0,tn=0;stajlar.forEach(s=>{const hr=harf(s.n);tp+=hr.p*s.k;tk+=s.k;tn+=s.n*s.k;});
  document.getElementById('ss1').textContent=(tn/tk).toFixed(1);document.getElementById('ss1').style.color=nc(tn/tk);
  document.getElementById('ss2').textContent=(tp/tk).toFixed(2);document.getElementById('ss2').style.color=(tp/tk)>=3?'var(--grn)':(tp/tk)>=2?'var(--yel)':'var(--red)';
  document.getElementById('ss3').textContent=tk;document.getElementById('stajres').style.display='block';
}

// ====== POMODORO ======
const POM={focus:25,short:5,long:15};
let pom={mod:'focus',kalan:25*60,toplam:25*60,calisiyor:false,iv:null,tamamlanan:0,bugun:0,toplamDk:0,log:[]};
function pomSureGun(){POM.focus=parseInt(document.getElementById('pom-set-focus').value)||25;POM.short=parseInt(document.getElementById('pom-set-short').value)||5;POM.long=parseInt(document.getElementById('pom-set-long').value)||15;if(!pom.calisiyor){pom.toplam=POM[pom.mod]*60;pom.kalan=pom.toplam;pomGuncelle();}}
function pomMode(mod,btn){if(pom.calisiyor)pomDurdur();pom.mod=mod;pom.toplam=POM[mod]*60;pom.kalan=pom.toplam;document.querySelectorAll('.pom-mode').forEach(b=>b.classList.remove('on'));btn.classList.add('on');const lbl={focus:'ODAK',short:'KISA MOLA',long:'UZUN MOLA'};document.getElementById('pom-lbl').textContent=lbl[mod];pomGuncelle();document.getElementById('pom-notif').classList.remove('show');}
function pomToggle(){if(pom.calisiyor)pomDurdur();else pomBasla();}
function pomBasla(){if(pom.kalan<=0)pomReset();pom.calisiyor=true;document.getElementById('pom-playbtn').textContent='⏸';pom.iv=setInterval(()=>{pom.kalan--;pomGuncelle();if(pom.kalan<=0)pomBitti();},1000);}
function pomDurdur(){pom.calisiyor=false;clearInterval(pom.iv);document.getElementById('pom-playbtn').textContent='▶';}
function pomReset(){pomDurdur();pom.kalan=pom.toplam;pomGuncelle();document.getElementById('pom-notif').classList.remove('show');}
function pomSkip(){pomDurdur();pomBitti();}
function pomBitti(){
  clearInterval(pom.iv);pom.calisiyor=false;document.getElementById('pom-playbtn').textContent='▶';
  if(pom.mod==='focus'){
    pom.tamamlanan++;pom.bugun++;pom.toplamDk+=POM.focus;
    const konu=document.getElementById('pom-konu').value||'Genel çalışma';const hedef=parseInt(document.getElementById('pom-hedef').value)||4;
    pom.log.unshift({konu,sure:POM.focus,zaman:new Date().toLocaleTimeString('tr-TR',{hour:'2-digit',minute:'2-digit'}),tarih:new Date().toLocaleDateString('tr-TR')});
    if(pom.log.length>50)pom.log.pop();
    pomNotif('🎉',`Pomodoro tamamlandı! (${pom.bugun}/${hedef})`);
    if(pom.bugun>=hedef)konfeti();else playSuccess();
    if(navigator.vibrate)navigator.vibrate([100,50,100,50,200]);
    const yeni=pom.tamamlanan%4===0?'long':'short';
    setTimeout(()=>{const btns=document.querySelectorAll('.pom-mode');pomMode(yeni,btns[yeni==='short'?1:2]);},2000);
  }else{pomNotif('☕','Mola bitti! Çalışmaya hazır mısın?');playTick();setTimeout(()=>{pomMode('focus',document.querySelectorAll('.pom-mode')[0]);},2000);}
  pomStat();pomLogRender();localStorage.setItem('pomData',JSON.stringify({tamamlanan:pom.tamamlanan,toplamDk:pom.toplamDk,log:pom.log,bugunTarih:new Date().toLocaleDateString('tr-TR'),bugun:pom.bugun}));
}
function pomGuncelle(){
  const dk=Math.floor(pom.kalan/60).toString().padStart(2,'0');const sn=(pom.kalan%60).toString().padStart(2,'0');
  document.getElementById('pom-display').textContent=`${dk}:${sn}`;
  const c=document.getElementById('pom-circle');const r=80;const cevre=2*Math.PI*r;
  const renk=pom.mod==='focus'?'#5b8cff':pom.mod==='short'?'#30c98e':'#b06aff';
  c.style.stroke=renk;c.style.strokeDasharray=cevre;c.style.strokeDashoffset=cevre*(1-pom.kalan/pom.toplam);
  document.getElementById('pom-display').style.color=renk;
  document.title=pom.calisiyor?`${dk}:${sn} — Not`:'Not';
}
function pomNotif(icon,txt){const n=document.getElementById('pom-notif');document.getElementById('pom-notif-icon').textContent=icon;document.getElementById('pom-notif-txt').textContent=txt;n.classList.add('show');clearTimeout(n._t);n._t=setTimeout(()=>n.classList.remove('show'),4000);}
function pomStat(){document.getElementById('ps-bugun').textContent=`${pom.bugun} 🍅`;document.getElementById('ps-toplam').textContent=`${pom.tamamlanan} 🍅`;document.getElementById('ps-sure').textContent=`${pom.toplamDk} dk`;}
function pomLogRender(){const list=document.getElementById('pom-log');if(!pom.log.length){list.innerHTML='<div class="empty">Henüz çalışma kaydı yok 📖</div>';return;}list.innerHTML=pom.log.map(l=>`<div class="pom-log-item"><div><div style="font-size:13px;font-weight:700">📚 ${l.konu}</div><div style="font-size:11px;color:var(--tx2);font-weight:600">${l.tarih} ${l.zaman}</div></div><div style="font-size:12px;font-weight:800;color:var(--a1)">${l.sure} dk</div></div>`).join('');}
function pomLogTemizle(){if(confirm('Çalışma geçmişi silinsin mi?')){pom.log=[];pom.bugun=0;pomStat();pomLogRender();localStorage.removeItem('pomData');}}
function pomYukle(){const d=localStorage.getItem('pomData');if(!d)return;const o=JSON.parse(d);pom.tamamlanan=o.tamamlanan||0;pom.toplamDk=o.toplamDk||0;pom.log=o.log||[];const bugun=new Date().toLocaleDateString('tr-TR');pom.bugun=o.bugunTarih===bugun?o.bugun:0;pomStat();pomLogRender();}

// ====== ROZETLER ======
const ROZETLER=[
  {id:'ilk_ders',emoji:'📝',isim:'İlk Ders',kontrol:()=>dersler.length>=1},
  {id:'bes_ders',emoji:'📚',isim:'5 Ders',kontrol:()=>dersler.length>=5},
  {id:'on_ders',emoji:'🎒',isim:'10 Ders',kontrol:()=>dersler.length>=10},
  {id:'ilk_komite',emoji:'🏥',isim:'İlk Komite',kontrol:()=>komiteler.length>=1},
  {id:'komite_5',emoji:'💉',isim:'5 Komite',kontrol:()=>komiteler.length>=5},
  {id:'gec_60',emoji:'✅',isim:'Geçer Not',kontrol:()=>dersler.some(d=>d.n>=60)},
  {id:'gec_80',emoji:'⭐',isim:'Yıldız Öğr.',kontrol:()=>dersler.some(d=>d.n>=80)},
  {id:'gec_90',emoji:'🏆',isim:'Şampiyon',kontrol:()=>dersler.some(d=>d.n>=90)},
  {id:'gno_3',emoji:'🎓',isim:'3.0 GNO',kontrol:()=>{if(!dersler.length)return false;let tp=0,tk=0;dersler.forEach(d=>{const hr=harf(d.n);tp+=hr.p*d.k;tk+=d.k;});return(tp/tk)>=3.0;}},
  {id:'gno_35',emoji:'🌟',isim:'3.5 GNO',kontrol:()=>{if(!dersler.length)return false;let tp=0,tk=0;dersler.forEach(d=>{const hr=harf(d.n);tp+=hr.p*d.k;tk+=d.k;});return(tp/tk)>=3.5;}},
  {id:'donem_2',emoji:'📅',isim:'2. Dönem',kontrol:()=>donemler.length>=2},
  {id:'sinav_5',emoji:'🗓️',isim:'Planlayıcı',kontrol:()=>sinavlar.length>=5},
  {id:'staj_ilk',emoji:'🩺',isim:'Stajyer',kontrol:()=>stajlar.length>=1},
  {id:'komite_gec_5',emoji:'💪',isim:'Komite Savaşçısı',kontrol:()=>komiteler.filter(k=>{const n=kNotu(k);return !isNaN(n)&&n>=60;}).length>=5},
  {id:'pom_10',emoji:'🍅',isim:'Odak Ustası',kontrol:()=>pom.tamamlanan>=10},
];
function kontrolRozetler(){
  const yeni=[];ROZETLER.forEach(r=>{if(r.kontrol()&&!kazanilanRozetler.includes(r.id)){kazanilanRozetler.push(r.id);yeni.push(r);}});
  if(yeni.length){yeni.forEach((r,i)=>setTimeout(()=>rozToast(r),i*800));}
  localStorage.setItem('rozetler',JSON.stringify(kazanilanRozetler));renderRozetler();
}
function rozToast(roz){
  const t=document.createElement('div');
  t.style.cssText='position:fixed;top:24px;left:50%;transform:translateX(-50%) translateY(-80px);background:linear-gradient(135deg,rgba(255,210,0,.95),rgba(255,160,0,.95));border-radius:99px;padding:12px 20px;display:flex;align-items:center;gap:10px;z-index:600;box-shadow:0 8px 32px rgba(0,0,0,.2);transition:transform .4s cubic-bezier(.34,1.56,.64,1);max-width:90vw;';
  t.innerHTML=`<span style="font-size:1.5rem">${roz.emoji}</span><div><div style="font-size:13px;font-weight:800;color:#fff">Yeni Rozet! ${roz.isim}</div></div>`;
  document.body.appendChild(t);setTimeout(()=>t.style.transform='translateX(-50%) translateY(0)',50);
  playSuccess();konfeti();setTimeout(()=>{t.style.transform='translateX(-50%) translateY(-80px)';setTimeout(()=>t.remove(),500);},3000);
}
function renderRozetler(){
  const grid=document.getElementById('rozet-grid');
  if(!grid)return;
  grid.style.display='grid';
  grid.style.gridTemplateColumns='repeat(3,1fr)';
  grid.style.gap='10px';
  grid.innerHTML=ROZETLER.map(r=>{
    const u=kazanilanRozetler.includes(r.id);
    const bg=u?'rgba(255,255,255,.6)':'rgba(255,255,255,.1)';
    const border=u?'rgba(255,210,0,.6)':'rgba(255,255,255,.15)';
    const emojiOp=u?'1':'.3';
    const textColor=u?'#5a5a7a':'rgba(255,255,255,.35)';
    return `<div onclick="rozAciklama('${r.id}')" style="background:${bg};border:1.5px solid ${border};border-radius:14px;padding:14px 8px;text-align:center;position:relative;cursor:pointer;">
      <div style="font-size:1.8rem;line-height:1;margin-bottom:6px;opacity:${emojiOp}">${r.emoji}</div>
      <div style="font-size:9px;font-weight:800;color:${textColor};letter-spacing:.3px;line-height:1.3">${r.isim}</div>
      ${u?'<div style="position:absolute;top:-5px;right:-5px;background:linear-gradient(135deg,#f5a623,#ffd200);color:white;font-size:8px;font-weight:800;padding:2px 6px;border-radius:99px">✓</div>':''}
    </div>`;
  }).join('');
}

function rozAciklama(id){
  const r=ROZETLER.find(r=>r.id===id);if(!r)return;
  const u=kazanilanRozetler.includes(id);
  const eski=document.getElementById('roz-popup');if(eski)eski.remove();
  const popup=document.createElement('div');
  popup.id='roz-popup';
  popup.style.cssText='position:fixed;inset:0;background:rgba(0,0,0,.5);backdrop-filter:blur(8px);z-index:400;display:flex;align-items:center;justify-content:center;padding:20px;';
  popup.innerHTML=`<div style="background:rgba(255,255,255,.96);border-radius:24px;padding:28px 24px;max-width:300px;width:100%;text-align:center;animation:fU .25s ease both;box-shadow:0 20px 60px rgba(0,0,0,.2)">
    <div style="font-size:3.5rem;margin-bottom:10px;${u?'':'filter:grayscale(1);opacity:.4'}">${r.emoji}</div>
    <div style="font-size:1rem;font-weight:900;margin-bottom:8px;color:var(--tx)">${r.isim}</div>
    <div style="font-size:12px;color:var(--tx2);font-weight:600;margin-bottom:16px;line-height:1.6;background:rgba(0,0,0,.04);border-radius:12px;padding:10px 14px">${r.aciklama}</div>
    <div style="font-size:12px;font-weight:800;padding:8px 16px;border-radius:99px;display:inline-block;margin-bottom:14px;${u?'background:rgba(48,201,142,.15);color:#30c98e':'background:rgba(91,140,255,.1);color:var(--a1)'}">
      ${u?'✅ Kazanıldı!':'🔒 Henüz kazanılmadı'}
    </div><br>
    <button onclick="document.getElementById('roz-popup').remove()" style="border:none;background:rgba(0,0,0,.07);border-radius:99px;padding:8px 22px;font-family:'Nunito',sans-serif;font-size:13px;font-weight:800;cursor:pointer;color:var(--tx)">Kapat</button>
  </div>`;
  popup.addEventListener('click',e=>{if(e.target===popup)popup.remove();});
  document.body.appendChild(popup);
}

// ====== PAYLAŞIM KARTI ======
function generateShareCard(){
  const canvas=document.getElementById('sh-canvas');const ctx=canvas.getContext('2d');const W=800,H=420;canvas.width=W;canvas.height=H;
  const bg=ctx.createLinearGradient(0,0,W,H);bg.addColorStop(0,'#1a1a3e');bg.addColorStop(.5,'#2d1b4e');bg.addColorStop(1,'#1a2a4e');ctx.fillStyle=bg;ctx.fillRect(0,0,W,H);
  ctx.save();ctx.globalAlpha=.12;ctx.fillStyle='#5b8cff';ctx.beginPath();ctx.arc(W-80,80,120,0,Math.PI*2);ctx.fill();ctx.fillStyle='#b06aff';ctx.beginPath();ctx.arc(80,H-60,100,0,Math.PI*2);ctx.fill();ctx.restore();
  ctx.fillStyle='rgba(255,255,255,.15)';ctx.beginPath();rRect(ctx,30,30,100,34,17);ctx.fill();ctx.fillStyle='#b06aff';ctx.font='bold 12px Arial';ctx.textAlign='left';ctx.fillText('✦ NotHesap',46,52);
  const isim=localStorage.getItem('profil')?JSON.parse(localStorage.getItem('profil')).isim||'Tıp Öğrencisi':'Tıp Öğrencisi';
  ctx.fillStyle='rgba(255,255,255,.6)';ctx.font='600 15px Arial';ctx.fillText(isim,30,108);
  ctx.fillStyle='white';ctx.font='bold 36px Arial';ctx.fillText('Bu dönemi kapattım! 🎓',30,152);
  let g4='—',g100='—';if(dersler.length){let tp=0,tk=0,tn=0;dersler.forEach(d=>{const hr=harf(d.n);tp+=hr.p*d.k;tk+=d.k;tn+=d.n*d.k;});g4=(tp/tk).toFixed(2);g100=(tn/tk).toFixed(1);}
  [{l:'GNO (4)',v:g4,c:'#5b8cff'},{l:'Ortalama',v:g100,c:'#b06aff'},{l:'Ders',v:String(dersler.length),c:'#30c98e'},{l:'Komite',v:String(komiteler.length),c:'#f5a623'}].forEach((s,i)=>{
    const x=30+i*185,y=192;ctx.fillStyle='rgba(255,255,255,.08)';ctx.beginPath();rRect(ctx,x,y,170,90,14);ctx.fill();ctx.fillStyle=s.c;ctx.font='bold 26px Arial';ctx.textAlign='left';ctx.fillText(s.v,x+14,y+44);ctx.fillStyle='rgba(255,255,255,.5)';ctx.font='500 11px Arial';ctx.fillText(s.l,x+14,y+65);
  });
  const grad=ctx.createLinearGradient(30,H-50,W-30,H-50);grad.addColorStop(0,'#5b8cff');grad.addColorStop(1,'#b06aff');ctx.strokeStyle=grad;ctx.lineWidth=2;ctx.beginPath();ctx.moveTo(30,H-50);ctx.lineTo(W-30,H-50);ctx.stroke();
  ctx.fillStyle='rgba(255,255,255,.4)';ctx.font='500 12px Arial';ctx.textAlign='right';ctx.fillText(new Date().toLocaleDateString('tr-TR',{day:'numeric',month:'long',year:'numeric'}),W-30,H-25);
  document.getElementById('sh-ov').classList.add('show');
}
function rRect(ctx,x,y,w,h,r){ctx.moveTo(x+r,y);ctx.lineTo(x+w-r,y);ctx.quadraticCurveTo(x+w,y,x+w,y+r);ctx.lineTo(x+w,y+h-r);ctx.quadraticCurveTo(x+w,y+h,x+w-r,y+h);ctx.lineTo(x+r,y+h);ctx.quadraticCurveTo(x,y+h,x,y+h-r);ctx.lineTo(x,y+r);ctx.quadraticCurveTo(x,y,x+r,y);ctx.closePath();}
function downloadShare(){const a=document.createElement('a');a.download='not-donem-karti.png';a.href=document.getElementById('sh-canvas').toDataURL();a.click();playTick();}

// ====== YEDEK ======
function exportData(){
  const data={dersler,donemler,komiteler,sinavlar,stajlar,profil:localStorage.getItem('profil'),pratikVar,exportDate:new Date().toISOString()};
  const a=document.createElement('a');a.download=`not-yedek-${new Date().toLocaleDateString('tr-TR').replace(/\./g,'-')}.json`;a.href=URL.createObjectURL(new Blob([JSON.stringify(data,null,2)],{type:'application/json'}));a.click();playTick();alert('✅ Veriler dışa aktarıldı!');
}
function importData(input){
  const file=input.files[0];if(!file)return;const r=new FileReader();
  r.onload=e=>{try{const data=JSON.parse(e.target.result);if(confirm(`📥 "${file.name}" yüklensin mi? Mevcut veriler silinecek.`)){dersler=data.dersler||[];donemler=data.donemler||[];komiteler=data.komiteler||[];sinavlar=data.sinavlar||[];stajlar=data.stajlar||[];if(data.profil)localStorage.setItem('profil',data.profil);if(data.pratikVar!==undefined){pratikVar=data.pratikVar;localStorage.setItem('pratikVar',pratikVar);document.getElementById('pratt').checked=pratikVar;upPratik();}saveAll();renderDersler();renderDonemler();renderKomiteler();renderS();renderStaj();konfeti();alert('✅ Veriler içe aktarıldı!');}}catch(err){alert('❌ Geçersiz dosya!');}};
  r.readAsText(file);input.value='';
}

// ====== AYARLAR ======
function tDark(){document.body.classList.toggle('dark',document.getElementById('darkt').checked);if(gnoCh)renderGC();saveS();}
function toggleCol(){const p=document.getElementById('copts');p.style.display=p.style.display==='none'?'flex':'none';}
function rSec(isim,el,c1,c2){document.querySelectorAll('.cdot').forEach(d=>d.classList.remove('on'));el.classList.add('on');document.documentElement.style.setProperty('--a1',c1);document.documentElement.style.setProperty('--a2',c2);document.getElementById('rsub').textContent=isim;localStorage.setItem('renk',JSON.stringify({isim,c1,c2}));}
function tByt(){document.body.style.fontSize=document.getElementById('bytt').checked?'17px':'';saveS();}
function pGun(){
  const isim=document.getElementById('pisim').value||'Tıp Öğrencisi';
  const uni=document.getElementById('puni').value||'Üniversite seçilmedi';
  const sinif=document.getElementById('psinif').value;
  document.getElementById('avisim').textContent=isim+(sinif?' · '+sinif:'');
  document.getElementById('avuni').textContent=uni;
  document.getElementById('hsub').textContent=sinif?`${sinif} · Tıp · GNO · Pomodoro`:'Tıp · GNO · Pomodoro';
  const ustSinif=['4. Sınıf','5. Sınıf','6. Sınıf'].includes(sinif);
  const stajCard=document.getElementById('staj-card');
  const komiteMainCard=document.getElementById('komite-main-card');
  if(stajCard) stajCard.style.display=ustSinif?'block':'none';
  if(komiteMainCard) komiteMainCard.style.display=ustSinif?'none':'block';
  localStorage.setItem('profil',JSON.stringify({isim,uni,sinif}));
}
function avDeg(input){const file=input.files[0];if(!file)return;const r=new FileReader();r.onload=e=>{const c=document.getElementById('avc');c.innerHTML=`<img src="${e.target.result}" alt="av"><input type="file" id="avinp" accept="image/*" style="display:none" onchange="avDeg(this)">`;document.getElementById('hdr-av').innerHTML=`<img src="${e.target.result}" alt="av" style="width:100%;height:100%;object-fit:cover;border-radius:50%">`;localStorage.setItem('avatar',e.target.result);};r.readAsDataURL(file);}
function goProfile(){
  document.querySelectorAll('.panel').forEach(p=>p.classList.remove('on'));
  document.querySelectorAll('.tb').forEach(b=>b.classList.remove('on'));
  const ayarlarPanel=document.getElementById('p-ayarlar');
  if(ayarlarPanel) ayarlarPanel.classList.add('on');
  // Tab bar'daki son butonu seç
  const tabs=document.querySelectorAll('.tb');
  if(tabs.length) tabs[tabs.length-1].classList.add('on');
  window.scrollTo({top:0,behavior:'smooth'});
}
function checkAD(){
  const el=document.getElementById('autod');
  if(!el||!el.checked)return;
  const h=new Date().getHours();const sd=h>=22||h<7;
  document.body.classList.toggle('dark',sd);
  const darkt=document.getElementById('darkt');if(darkt)darkt.checked=sd;
}
function saveS(){
  const darkt=document.getElementById('darkt');
  const bytt=document.getElementById('bytt');
  const autod=document.getElementById('autod');
  const motivt=document.getElementById('motivt');
  localStorage.setItem('settings',JSON.stringify({dark:darkt?.checked,byt:bytt?.checked,autoDark:autod?.checked,motiv:motivt?.checked}));
}
function saveAll(){localStorage.setItem('data',JSON.stringify({dersler,donemler,komiteler,sinavlar,stajlar}));}
function reset(){if(confirm('Tüm veriler silinecek!')){dersler=[];donemler=[];komiteler=[];sinavlar=[];stajlar=[];kazanilanRozetler=[];saveAll();renderDersler();renderDonemler();renderKomiteler();renderS();renderStaj();renderRozetler();}}
function loadAll(){
  try{
    const d=localStorage.getItem('data');
    if(d){const o=JSON.parse(d);dersler=o.dersler||[];donemler=o.donemler||[];komiteler=o.komiteler||[];sinavlar=o.sinavlar||[];stajlar=o.stajlar||[];}
    const p=localStorage.getItem('profil');
    if(p){
      const o=JSON.parse(p);
      const pisim=document.getElementById('pisim');
      const puni=document.getElementById('puni');
      const psinif=document.getElementById('psinif');
      if(pisim&&o.isim)pisim.value=o.isim;
      if(puni&&o.uni)puni.value=o.uni;
      if(psinif&&o.sinif)psinif.value=o.sinif;
      pGun();
    }
    const av=localStorage.getItem('avatar');
    if(av){
      const avc=document.getElementById('avc');
      const hav=document.getElementById('hdr-av');
      if(avc)avc.innerHTML=`<img src="${av}" alt="av"><input type="file" id="avinp" accept="image/*" style="display:none" onchange="avDeg(this)">`;
      if(hav)hav.innerHTML=`<img src="${av}" alt="av" style="width:100%;height:100%;object-fit:cover;border-radius:50%">`;
    }
    const s=localStorage.getItem('settings');
    if(s){
      const o=JSON.parse(s);
      const darkt=document.getElementById('darkt');
      const bytt=document.getElementById('bytt');
      const autod=document.getElementById('autod');
      const motivt=document.getElementById('motivt');
      if(o.dark&&darkt){darkt.checked=true;document.body.classList.add('dark');}
      if(o.byt&&bytt){bytt.checked=true;document.body.style.fontSize='17px';}
      if(o.autoDark&&autod)autod.checked=true;
      if(o.motiv===false&&motivt)motivt.checked=false;
    }
    const r=localStorage.getItem('renk');
    if(r){
      const o=JSON.parse(r);
      document.documentElement.style.setProperty('--a1',o.c1);
      document.documentElement.style.setProperty('--a2',o.c2);
      const rsub=document.getElementById('rsub');
      if(rsub)rsub.textContent=o.isim;
    }
    const roz=localStorage.getItem('rozetler');
    if(roz)kazanilanRozetler=JSON.parse(roz);
    renderDersler();renderDonemler();renderKomiteler();renderS();renderStaj();renderRozetler();
  }catch(e){console.warn('loadAll hatası:',e);}
}
</script>
</body>
</html>
