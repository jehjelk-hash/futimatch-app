<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>FutiMatch 足球约战</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Noto+Sans+SC:wght@400;500;700;900&family=DM+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
:root{
  --g:#1a7a3c;--gl:#25a352;--gd:#0a3d1e;--gx:#06240f;
  --ac:#c8f135;--ac2:#f5e642;
  --bg:#f2f2ed;--card:#fff;--txt:#111;--mu:#888;--br:#e4e4dc;
  --red:#e53935;--orange:#f57c00;--blue:#1565c0;
}
html,body{height:100%;background:#1a1a1a;display:flex;align-items:center;justify-content:center;font-family:'DM Sans',sans-serif}

/* ── PHONE SHELL ── */
.phone{
  width:390px;height:844px;background:var(--bg);border-radius:50px;
  border:3px solid #333;overflow:hidden;position:relative;
  box-shadow:0 30px 80px rgba(0,0,0,.6),inset 0 1px 0 rgba(255,255,255,.1);
}
.notch{position:absolute;top:0;left:50%;transform:translateX(-50%);width:126px;height:34px;background:#1a1a1a;border-radius:0 0 20px 20px;z-index:999}

/* ── SCREENS ── */
.screen{position:absolute;inset:0;overflow-y:auto;overflow-x:hidden;transition:transform .35s cubic-bezier(.4,0,.2,1),opacity .35s;scrollbar-width:none}
.screen::-webkit-scrollbar{display:none}
.screen.hidden{transform:translateX(100%);opacity:0;pointer-events:none}
.screen.slide-left{transform:translateX(-40%);opacity:0;pointer-events:none}

/* ══ SPLASH ══ */
#splash{background:var(--gx);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:0}
.splash-ball{font-size:72px;animation:bounce 1.2s ease-in-out infinite alternate;margin-bottom:8px}
@keyframes bounce{from{transform:translateY(0)}to{transform:translateY(-18px)}}
.splash-logo{font-family:'Bebas Neue';font-size:56px;letter-spacing:2px;color:var(--ac);line-height:1}
.splash-cn{font-family:'Noto Sans SC';font-size:16px;color:rgba(255,255,255,.5);letter-spacing:4px;margin-bottom:48px}
.splash-loader{width:48px;height:4px;background:rgba(255,255,255,.15);border-radius:2px;overflow:hidden}
.splash-loader-bar{width:0;height:100%;background:var(--ac);border-radius:2px;animation:load 1.8s ease forwards}
@keyframes load{0%{width:0}60%{width:70%}100%{width:100%}}
.splash-tagline{font-size:13px;color:rgba(255,255,255,.35);margin-top:12px;letter-spacing:.5px}

/* ══ ONBOARD ══ */
#onboard{background:var(--gx)}
.ob-img{height:420px;background:linear-gradient(to bottom,var(--gx) 0%,#1a5c2e 60%,#2d8a4e 100%);position:relative;display:flex;align-items:flex-end;justify-content:center;overflow:hidden}
.ob-pitch{width:300px;height:180px;border:2.5px solid rgba(255,255,255,.25);border-radius:4px;position:relative;margin-bottom:30px}
.ob-pitch::before{content:'';position:absolute;left:50%;top:0;bottom:0;width:1.5px;background:rgba(255,255,255,.2)}
.ob-pitch::after{content:'';position:absolute;left:50%;top:50%;transform:translate(-50%,-50%);width:55px;height:55px;border-radius:50%;border:1.5px solid rgba(255,255,255,.25)}
.ob-goal{position:absolute;width:40px;height:20px;border:1.5px solid rgba(255,255,255,.3)}
.ob-goal.l{left:-1.5px;top:50%;transform:translateY(-50%)}
.ob-goal.r{right:-1.5px;top:50%;transform:translateY(-50%)}
.ob-players{position:absolute;inset:0;pointer-events:none}
.ob-dot{position:absolute;width:10px;height:10px;border-radius:50%;border:2px solid #fff}
.ob-content{padding:32px 28px 40px;color:#fff}
.ob-tag{display:inline-block;background:rgba(200,241,53,.15);color:var(--ac);font-size:11px;font-weight:700;letter-spacing:1px;text-transform:uppercase;padding:5px 12px;border-radius:20px;border:1px solid rgba(200,241,53,.3);margin-bottom:16px}
.ob-title{font-family:'Bebas Neue';font-size:44px;letter-spacing:1px;line-height:1;margin-bottom:12px}
.ob-title span{color:var(--ac)}
.ob-desc{font-size:14px;color:rgba(255,255,255,.6);line-height:1.7;margin-bottom:32px}
.btn-primary{width:100%;padding:16px;background:var(--ac);color:var(--gx);border:none;border-radius:16px;font-size:16px;font-weight:700;cursor:pointer;font-family:'DM Sans',sans-serif;letter-spacing:.3px;transition:.2s}
.btn-primary:hover{background:#d4f54a;transform:translateY(-1px)}
.btn-secondary{width:100%;padding:14px;background:transparent;color:rgba(255,255,255,.6);border:1.5px solid rgba(255,255,255,.2);border-radius:16px;font-size:15px;cursor:pointer;font-family:'DM Sans',sans-serif;margin-top:10px;transition:.2s}
.btn-secondary:hover{border-color:rgba(255,255,255,.4);color:#fff}

/* ══ HOME ══ */
#home{background:var(--bg)}
.sbar{height:44px;background:var(--gd);display:flex;align-items:flex-end;justify-content:space-between;padding:0 20px 8px;font-size:12px;color:#fff;font-weight:500;flex-shrink:0}
.hdr{background:var(--gd);padding:10px 20px 20px;color:#fff;flex-shrink:0}
.hdr-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
.logo-sm{font-family:'Bebas Neue';font-size:24px;color:var(--ac);letter-spacing:1px}
.logo-sm span{color:#fff}
.city-pill{display:flex;align-items:center;gap:5px;background:rgba(255,255,255,.12);border-radius:20px;padding:6px 12px;font-size:12px;cursor:pointer;border:1px solid rgba(255,255,255,.1);transition:.2s}
.city-pill:hover{background:rgba(255,255,255,.2)}
.city-dot{width:6px;height:6px;background:var(--ac);border-radius:50%;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.4}}
.srch-bar{display:flex;align-items:center;gap:8px;background:rgba(255,255,255,.1);border:1px solid rgba(255,255,255,.15);border-radius:12px;padding:10px 14px;font-size:13px;color:rgba(255,255,255,.5);backdrop-filter:blur(10px)}
.quick-row{display:flex;gap:8px;padding:14px 16px 0;overflow-x:auto}
.quick-row::-webkit-scrollbar{display:none}
.qchip{white-space:nowrap;padding:6px 13px;border-radius:20px;font-size:12px;font-weight:600;border:1.5px solid var(--br);background:#fff;cursor:pointer;color:var(--mu);transition:.2s;flex-shrink:0}
.qchip.on{background:var(--g);color:#fff;border-color:var(--g)}
.qchip:hover{border-color:var(--g);color:var(--g)}

/* MAP */
.map-box{margin:14px 16px;height:160px;background:#b8ddb8;border-radius:18px;position:relative;overflow:hidden;cursor:pointer}
.map-box:hover .map-overlay{opacity:1}
.map-grid{position:absolute;inset:0;background-image:linear-gradient(rgba(0,0,0,.06) 1px,transparent 1px),linear-gradient(90deg,rgba(0,0,0,.06) 1px,transparent 1px);background-size:24px 24px}
.mrd{position:absolute;background:rgba(255,255,255,.7)}
.mpin{position:absolute;width:22px;height:22px;background:var(--gd);border-radius:50% 50% 50% 0;transform:rotate(-45deg);border:2px solid #fff;cursor:pointer;transition:.2s;box-shadow:0 2px 6px rgba(0,0,0,.3)}
.mpin:hover{transform:rotate(-45deg) scale(1.15)}
.mpin::after{content:'';position:absolute;width:7px;height:7px;background:var(--ac);border-radius:50%;top:50%;left:50%;transform:translate(-50%,-50%)}
.myou{position:absolute;width:14px;height:14px;background:#2196F3;border-radius:50%;border:3px solid #fff;box-shadow:0 0 0 6px rgba(33,150,243,.2)}
.mlbl{position:absolute;bottom:10px;right:10px;background:#fff;border-radius:8px;padding:4px 10px;font-size:11px;font-weight:700;color:var(--gd);box-shadow:0 2px 8px rgba(0,0,0,.15)}
.map-overlay{position:absolute;inset:0;background:rgba(10,61,30,.3);display:flex;align-items:center;justify-content:center;opacity:0;transition:.2s;border-radius:18px}
.map-overlay span{background:var(--ac);color:var(--gx);font-size:12px;font-weight:700;padding:6px 14px;border-radius:20px}

.sec-hdr{display:flex;justify-content:space-between;align-items:center;padding:4px 16px 10px}
.sec-title{font-size:14px;font-weight:700;color:var(--txt)}
.sec-link{font-size:12px;color:var(--g);font-weight:600}

/* CARDS */
.card{margin:0 16px 12px;background:#fff;border-radius:18px;border:1px solid var(--br);overflow:hidden;cursor:pointer;transition:.15s;box-shadow:0 2px 8px rgba(0,0,0,.04)}
.card:hover{transform:translateY(-2px);box-shadow:0 6px 20px rgba(0,0,0,.1)}
.cimg{height:88px;position:relative;display:flex;align-items:center;justify-content:center}
.pitch-svg{width:96px;height:58px;opacity:.65}
.bdg{position:absolute;top:8px;right:8px;font-size:10px;font-weight:700;border-radius:8px;padding:3px 8px}
.bdg.spots{background:var(--ac);color:var(--gx)}
.bdg.full{background:var(--red);color:#fff}
.bdg.indoor{background:var(--orange);color:#fff}
.bdg.few{background:#fff3e0;color:var(--orange);border:1px solid var(--orange)}
.cinfo{padding:11px 14px 13px}
.cname{font-size:13px;font-weight:700;margin-bottom:4px;color:var(--txt)}
.cmeta{display:flex;gap:8px;font-size:11px;color:var(--mu);margin-bottom:9px;flex-wrap:wrap}
.prow{display:flex;align-items:center;padding-bottom:9px}
.pav{width:27px;height:27px;border-radius:50%;border:2px solid #fff;display:flex;align-items:center;justify-content:center;font-size:10px;font-weight:700;color:#fff;margin-right:-7px;flex-shrink:0}
.pneed{margin-left:15px;font-size:11px;color:var(--mu)}
.pneed strong{color:var(--gd)}
.slots{display:flex;gap:5px}
.slot{flex:1;text-align:center;padding:5px 2px;border-radius:8px;font-size:11px;font-weight:600;border:1.5px solid var(--br);color:var(--g);background:#f0faf4;cursor:pointer;transition:.15s}
.slot:hover{background:var(--g);color:#fff;border-color:var(--g)}
.slot.tk{background:#f8f8f8;color:#ccc;border-color:#eee;text-decoration:line-through;cursor:default}
.slot.tk:hover{background:#f8f8f8;color:#ccc;border-color:#eee}

.bookbtn{display:block;margin:8px 16px 16px;padding:14px;background:var(--g);color:#fff;border:none;border-radius:14px;font-size:15px;font-weight:700;text-align:center;cursor:pointer;font-family:'DM Sans',sans-serif;width:calc(100% - 32px);transition:.2s;box-shadow:0 4px 14px rgba(26,122,60,.3)}
.bookbtn:hover{background:var(--gl);transform:translateY(-1px)}

/* NAV */
.nav{background:#fff;border-top:1px solid var(--br);display:flex;padding:8px 0 18px;flex-shrink:0;position:sticky;bottom:0}
.ni{flex:1;display:flex;flex-direction:column;align-items:center;gap:3px;font-size:10px;color:var(--mu);cursor:pointer;padding:4px 0;transition:.2s;font-weight:500}
.ni.on{color:var(--g)}
.ni-ic{font-size:20px}

/* ══ PITCH DETAIL ══ */
#detail{background:var(--bg)}
.detail-hero{height:220px;position:relative;display:flex;align-items:center;justify-content:center;overflow:hidden}
.detail-back{position:absolute;top:50px;left:16px;width:36px;height:36px;background:rgba(0,0,0,.4);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:18px;cursor:pointer;color:#fff;z-index:10;border:none;backdrop-filter:blur(6px)}
.detail-fav{position:absolute;top:50px;right:16px;width:36px;height:36px;background:rgba(0,0,0,.4);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:18px;cursor:pointer;color:#fff;z-index:10;border:none;backdrop-filter:blur(6px)}
.detail-pitch-svg{width:180px;height:110px;opacity:.55}
.detail-badge{position:absolute;bottom:16px;left:16px;background:var(--ac);color:var(--gx);font-size:11px;font-weight:700;padding:4px 10px;border-radius:8px}
.detail-body{padding:20px 18px}
.detail-name{font-size:20px;font-weight:700;margin-bottom:6px}
.detail-meta{display:flex;gap:12px;font-size:13px;color:var(--mu);margin-bottom:18px;flex-wrap:wrap}
.detail-meta span{display:flex;align-items:center;gap:4px}
.divider{height:1px;background:var(--br);margin:16px 0}
.detail-section{font-size:13px;font-weight:700;color:var(--txt);margin-bottom:12px;text-transform:uppercase;letter-spacing:.5px}
.players-joined{display:flex;gap:8px;overflow-x:auto;padding-bottom:4px;margin-bottom:16px}
.players-joined::-webkit-scrollbar{display:none}
.pj-card{flex-shrink:0;display:flex;flex-direction:column;align-items:center;gap:5px;font-size:11px;color:var(--mu)}
.pj-av{width:42px;height:42px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:16px;font-weight:700;color:#fff}
.pj-empty{width:42px;height:42px;border-radius:50%;border:2px dashed var(--br);display:flex;align-items:center;justify-content:center;font-size:18px;color:var(--br)}
.slot-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:20px}
.slot-big{padding:12px;border-radius:12px;border:1.5px solid var(--br);text-align:center;cursor:pointer;transition:.2s}
.slot-big:hover{border-color:var(--g);background:#f0faf4}
.slot-big.sel{border-color:var(--g);background:var(--g);color:#fff}
.slot-big.tk{opacity:.4;cursor:default;background:#f8f8f8}
.slot-big.tk:hover{border-color:var(--br);background:#f8f8f8}
.slot-time{font-size:15px;font-weight:700}
.slot-avail{font-size:11px;opacity:.7;margin-top:2px}
.book-bar{padding:16px 18px 32px;background:#fff;border-top:1px solid var(--br)}
.book-bar-row{display:flex;justify-content:space-between;align-items:center;margin-bottom:12px}
.price-big{font-size:22px;font-weight:700;color:var(--gd)}
.price-sub{font-size:12px;color:var(--mu)}
.btn-book{flex:1;margin-left:16px;padding:14px;background:var(--g);color:#fff;border:none;border-radius:14px;font-size:15px;font-weight:700;cursor:pointer;font-family:'DM Sans',sans-serif;transition:.2s;box-shadow:0 4px 14px rgba(26,122,60,.25)}
.btn-book:hover{background:var(--gl)}

/* ══ BOOKING CONFIRM ══ */
#confirm{background:var(--bg);display:flex;flex-direction:column}
.confirm-top{background:var(--gd);padding:56px 24px 28px;color:#fff;text-align:center}
.confirm-icon{font-size:56px;margin-bottom:8px}
.confirm-title{font-family:'Bebas Neue';font-size:38px;color:var(--ac);letter-spacing:1px}
.confirm-sub{font-size:14px;color:rgba(255,255,255,.6);margin-top:6px}
.confirm-card{margin:20px 18px;background:#fff;border-radius:20px;padding:20px;border:1px solid var(--br)}
.confirm-row{display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-bottom:1px solid var(--br);font-size:14px}
.confirm-row:last-child{border:none}
.confirm-label{color:var(--mu);font-size:13px}
.confirm-val{font-weight:700;color:var(--txt)}
.qr-box{margin:0 18px 16px;background:#fff;border-radius:20px;padding:24px;border:1px solid var(--br);display:flex;flex-direction:column;align-items:center;gap:12px}
.qr-grid{display:grid;grid-template-columns:repeat(9,1fr);gap:2px;width:120px;height:120px}
.qr-cell{border-radius:1px}

/* ══ PROFILE ══ */
#profile{background:var(--bg)}
.profile-hdr{background:var(--gd);padding:56px 20px 24px;color:#fff}
.profile-av{width:70px;height:70px;border-radius:50%;background:var(--gl);border:3px solid var(--ac);display:flex;align-items:center;justify-content:center;font-size:28px;font-weight:700;color:#fff;margin-bottom:12px}
.profile-name{font-size:20px;font-weight:700;margin-bottom:2px}
.profile-loc{font-size:13px;color:rgba(255,255,255,.6)}
.profile-stats{display:flex;gap:0;margin:16px 16px 0;background:#fff;border-radius:16px;border:1px solid var(--br);overflow:hidden}
.pstat{flex:1;padding:16px;text-align:center;border-right:1px solid var(--br)}
.pstat:last-child{border:none}
.pstat-n{font-size:20px;font-weight:700;color:var(--gd)}
.pstat-l{font-size:11px;color:var(--mu);margin-top:2px}
.plist{margin:14px 16px 0;background:#fff;border-radius:16px;border:1px solid var(--br);overflow:hidden}
.plist-item{display:flex;align-items:center;gap:12px;padding:14px 16px;border-bottom:1px solid var(--br);cursor:pointer;transition:.15s;font-size:14px}
.plist-item:last-child{border:none}
.plist-item:hover{background:#f9f9f7}
.plist-ic{font-size:20px;width:28px;text-align:center}
.plist-arr{margin-left:auto;color:var(--mu);font-size:18px}

/* ══ CITY MODAL ══ */
.overlay{position:absolute;inset:0;background:rgba(0,0,0,.5);z-index:200;display:none;align-items:flex-end;backdrop-filter:blur(3px)}
.overlay.show{display:flex}
.sheet{background:#fff;border-radius:24px 24px 0 0;width:100%;padding:20px 18px 32px;animation:slideup .3s ease}
@keyframes slideup{from{transform:translateY(100%)}to{transform:translateY(0)}}
.sheet-handle{width:36px;height:4px;background:var(--br);border-radius:2px;margin:0 auto 16px}
.sheet-title{font-size:16px;font-weight:700;margin-bottom:16px;text-align:center}
.city-grid{display:grid;grid-template-columns:1fr 1fr;gap:9px;margin-bottom:14px}
.city-btn{padding:11px;border:1.5px solid var(--br);border-radius:12px;font-size:13px;font-weight:600;text-align:center;cursor:pointer;background:#fff;color:var(--txt);font-family:'DM Sans',sans-serif;transition:.2s}
.city-btn:hover{border-color:var(--g);color:var(--g)}
.city-btn.sel{background:var(--g);color:#fff;border-color:var(--g)}
.city-btn .cn{font-size:10px;opacity:.7;display:block;margin-top:2px}
.close-btn2{width:100%;padding:13px;background:var(--bg);border:none;border-radius:12px;font-size:14px;cursor:pointer;font-family:'DM Sans',sans-serif;color:var(--mu);font-weight:500;margin-top:4px}

/* ══ HOST MODAL ══ */
.host-opt{border:1.5px solid var(--br);border-radius:14px;padding:14px 16px;margin-bottom:10px;cursor:pointer;transition:.2s;display:flex;align-items:center;gap:14px}
.host-opt:hover{border-color:var(--g);background:#f0faf4}
.host-ic{font-size:28px}
.host-name{font-size:14px;font-weight:700;margin-bottom:2px}
.host-desc{font-size:12px;color:var(--mu)}

/* Scroll top padding for fixed header */
.scroll-content{padding-top:0}
</style>
</head>
<body>

<div class="phone" id="phone">
  <div class="notch"></div>

  <!-- ══ SPLASH ══ -->
  <div class="screen" id="splash">
    <div class="splash-ball">⚽</div>
    <div class="splash-logo">FutiMatch</div>
    <div class="splash-cn">足球约战</div>
    <div class="splash-loader"><div class="splash-loader-bar"></div></div>
    <div class="splash-tagline">Find your game. Play your city.</div>
  </div>

  <!-- ══ ONBOARD ══ -->
  <div class="screen hidden" id="onboard">
    <div class="ob-img">
      <div class="ob-pitch">
        <div class="ob-goal l"></div>
        <div class="ob-goal r"></div>
        <div class="ob-players">
          <div class="ob-dot" style="background:#c8f135;top:30%;left:20%"></div>
          <div class="ob-dot" style="background:#c8f135;top:65%;left:15%"></div>
          <div class="ob-dot" style="background:#c8f135;top:50%;left:35%"></div>
          <div class="ob-dot" style="background:#fff;top:30%;left:75%"></div>
          <div class="ob-dot" style="background:#fff;top:65%;left:80%"></div>
          <div class="ob-dot" style="background:#fff;top:50%;left:62%"></div>
        </div>
      </div>
    </div>
    <div class="ob-content">
      <div class="ob-tag">🇨🇳 Available Across China</div>
      <div class="ob-title">Play Football<br><span>Anywhere.</span><br>Anytime.</div>
      <div class="ob-desc">No friends? No problem. Find a nearby pitch, join a game with strangers, and play the beautiful game — across Shanghai, Beijing, Chongqing and more.</div>
      <button class="btn-primary" onclick="goTo('home')">Get Started →</button>
      <button class="btn-secondary" onclick="goTo('home')">Already have an account? Sign in</button>
    </div>
  </div>

  <!-- ══ HOME ══ -->
  <div class="screen hidden" id="home">
    <div class="sbar"><span>9:41</span><span>📶 🔋</span></div>
    <div class="hdr">
      <div class="hdr-row">
        <div class="logo-sm">FutiMatch <span style="font-family:'Noto Sans SC';font-size:12px;font-weight:400;opacity:.7">足球约战</span></div>
        <div class="city-pill" onclick="showCityModal()">
          <div class="city-dot"></div>
          <span id="city-label">Shanghai</span> ▾
        </div>
      </div>
      <div class="srch-bar">🔍 &nbsp;<span>Search pitches, games or players...</span></div>
    </div>

    <div class="quick-row">
      <div class="qchip on">All</div>
      <div class="qchip">5-a-side</div>
      <div class="qchip">7-a-side</div>
      <div class="qchip">11-a-side</div>
      <div class="qchip">Indoor</div>
      <div class="qchip">Tonight</div>
      <div class="qchip">Weekend</div>
    </div>

    <div class="map-box" onclick="">
      <div class="map-grid"></div>
      <div class="mrd" style="left:0;right:0;top:47%;height:8px"></div>
      <div class="mrd" style="top:0;bottom:0;left:37%;width:8px"></div>
      <div class="mrd" style="top:0;bottom:0;left:68%;width:5px;opacity:.5"></div>
      <div class="mrd" style="left:0;right:0;top:22%;height:4px;opacity:.4"></div>
      <div class="mpin" style="top:20%;left:28%"></div>
      <div class="mpin" style="top:52%;left:56%;background:#1565c0"></div>
      <div class="mpin" style="top:14%;left:65%"></div>
      <div class="mpin" style="top:60%;left:20%;background:#7b1fa2"></div>
      <div class="myou" style="top:42%;left:39%"></div>
      <div class="mlbl" id="map-label">4 pitches nearby</div>
      <div class="map-overlay"><span>📍 Open Full Map</span></div>
    </div>

    <div class="sec-hdr">
      <div class="sec-title">Available Games Today</div>
      <div class="sec-link">See all</div>
    </div>

    <!-- Card 1 -->
    <div class="card" onclick="goToDetail(0)">
      <div class="cimg" style="background:linear-gradient(135deg,#0f4d24 0%,#1a7a3c 50%,#3aad63 100%)">
        <svg class="pitch-svg" viewBox="0 0 96 58"><rect x="2" y="2" width="92" height="54" rx="2" fill="none" stroke="rgba(255,255,255,0.6)" stroke-width="1.5"/><line x1="48" y1="2" x2="48" y2="56" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><circle cx="48" cy="29" r="9" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="2" y="17" width="12" height="24" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="82" y="17" width="12" height="24" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/></svg>
        <div class="bdg spots">2 spots left</div>
      </div>
      <div class="cinfo">
        <div class="cname">静安体育中心 Jing'an Sports Centre · 5-a-side</div>
        <div class="cmeta"><span>📍 0.8km</span><span>⭐ 4.8 (142)</span><span>💴 ¥35/person</span><span>🌿 Outdoor</span></div>
        <div class="prow">
          <div class="pav" style="background:#1a7a3c">李</div>
          <div class="pav" style="background:#e65c00">王</div>
          <div class="pav" style="background:#7b1fa2">张</div>
          <div class="pav" style="background:#1565c0">陈</div>
          <div class="pneed">Need <strong>2 more</strong> players</div>
        </div>
        <div class="slots">
          <div class="slot" onclick="event.stopPropagation();goToDetail(0)">18:00</div>
          <div class="slot" onclick="event.stopPropagation();goToDetail(0)">19:00</div>
          <div class="slot tk">20:00</div>
          <div class="slot tk">21:00</div>
        </div>
      </div>
    </div>

    <!-- Card 2 -->
    <div class="card" onclick="goToDetail(1)">
      <div class="cimg" style="background:linear-gradient(135deg,#0d4f8a 0%,#1976D2 60%,#42a5f5 100%)">
        <svg class="pitch-svg" viewBox="0 0 96 58"><rect x="2" y="2" width="92" height="54" rx="2" fill="none" stroke="rgba(255,255,255,0.6)" stroke-width="1.5"/><line x1="48" y1="2" x2="48" y2="56" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><circle cx="48" cy="29" r="9" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="2" y="12" width="15" height="34" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="79" y="12" width="15" height="34" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/></svg>
        <div class="bdg indoor">Indoor</div>
      </div>
      <div class="cinfo">
        <div class="cname">普陀全民健身 Putuo Fitness Hub · 7-a-side</div>
        <div class="cmeta"><span>📍 1.4km</span><span>⭐ 4.6 (88)</span><span>💴 ¥28/person</span><span>🏠 Indoor</span></div>
        <div class="prow">
          <div class="pav" style="background:#c62828">刘</div>
          <div class="pav" style="background:#00838f">吴</div>
          <div class="pav" style="background:#558b2f">周</div>
          <div class="pneed">Need <strong>5 more</strong> players</div>
        </div>
        <div class="slots">
          <div class="slot tk">17:00</div>
          <div class="slot" onclick="event.stopPropagation();goToDetail(1)">19:30</div>
          <div class="slot" onclick="event.stopPropagation();goToDetail(1)">21:00</div>
          <div class="slot" onclick="event.stopPropagation();goToDetail(1)">22:30</div>
        </div>
      </div>
    </div>

    <!-- Card 3 -->
    <div class="card" onclick="goToDetail(2)">
      <div class="cimg" style="background:linear-gradient(135deg,#4a148c 0%,#7b1fa2 60%,#ab47bc 100%)">
        <svg class="pitch-svg" viewBox="0 0 96 58"><rect x="2" y="2" width="92" height="54" rx="2" fill="none" stroke="rgba(255,255,255,0.6)" stroke-width="1.5"/><line x1="48" y1="2" x2="48" y2="56" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><circle cx="48" cy="29" r="9" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="2" y="9" width="18" height="40" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="76" y="9" width="18" height="40" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/></svg>
        <div class="bdg full">Game Full</div>
      </div>
      <div class="cinfo">
        <div class="cname">浦东世纪公园 Century Park · 11-a-side</div>
        <div class="cmeta"><span>📍 3.1km</span><span>⭐ 4.9 (203)</span><span>💴 ¥20/person</span><span>🌿 Outdoor</span></div>
        <div class="prow">
          <div class="pav" style="background:#1a7a3c">赵</div>
          <div class="pav" style="background:#e65c00">孙</div>
          <div class="pav" style="background:#7b1fa2">周</div>
          <div class="pav" style="background:#c62828;font-size:9px">+8</div>
          <div class="pneed" style="color:var(--red);font-weight:700">Game is full!</div>
        </div>
        <div class="slots">
          <div class="slot tk">08:00</div><div class="slot tk">10:00</div>
          <div class="slot tk">14:00</div><div class="slot tk">16:00</div>
        </div>
      </div>
    </div>

    <!-- Card 4 -->
    <div class="card" onclick="goToDetail(3)">
      <div class="cimg" style="background:linear-gradient(135deg,#bf360c,#e64a19,#ff7043)">
        <svg class="pitch-svg" viewBox="0 0 96 58"><rect x="2" y="2" width="92" height="54" rx="2" fill="none" stroke="rgba(255,255,255,0.6)" stroke-width="1.5"/><line x1="48" y1="2" x2="48" y2="56" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><circle cx="48" cy="29" r="9" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="2" y="17" width="12" height="24" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/><rect x="82" y="17" width="12" height="24" fill="none" stroke="rgba(255,255,255,0.4)" stroke-width="1"/></svg>
        <div class="bdg few">3 spots left</div>
      </div>
      <div class="cinfo">
        <div class="cname">虹桥运动公园 Hongqiao Sports Park · 5-a-side</div>
        <div class="cmeta"><span>📍 2.2km</span><span>⭐ 4.7 (61)</span><span>💴 ¥40/person</span><span>🌿 Outdoor</span></div>
        <div class="prow">
          <div class="pav" style="background:#bf360c">何</div>
          <div class="pav" style="background:#1565c0">林</div>
          <div class="pneed">Need <strong>3 more</strong> players</div>
        </div>
        <div class="slots">
          <div class="slot" onclick="event.stopPropagation();goToDetail(3)">16:00</div>
          <div class="slot" onclick="event.stopPropagation();goToDetail(3)">18:00</div>
          <div class="slot tk">20:00</div>
          <div class="slot" onclick="event.stopPropagation();goToDetail(3)">22:00</div>
        </div>
      </div>
    </div>

    <button class="bookbtn" onclick="showHostModal()">+ Host a New Game</button>

    <div class="nav">
      <div class="ni on" onclick=""><span class="ni-ic">🏟️</span>Pitches</div>
      <div class="ni" onclick=""><span class="ni-ic">⚽</span>Games</div>
      <div class="ni" onclick=""><span class="ni-ic">👥</span>Players</div>
      <div class="ni" onclick="goTo('profile')"><span class="ni-ic">👤</span>Profile</div>
    </div>
  </div>

  <!-- ══ DETAIL ══ -->
  <div class="screen hidden" id="detail">
    <div class="detail-hero" id="detail-hero">
      <button class="detail-back" onclick="goTo('home','slide-left')">←</button>
      <button class="detail-fav">♡</button>
      <svg class="detail-pitch-svg" viewBox="0 0 180 110"><rect x="3" y="3" width="174" height="104" rx="3" fill="none" stroke="rgba(255,255,255,0.5)" stroke-width="2"/><line x1="90" y1="3" x2="90" y2="107" stroke="rgba(255,255,255,0.35)" stroke-width="1.5"/><circle cx="90" cy="55" r="16" fill="none" stroke="rgba(255,255,255,0.35)" stroke-width="1.5"/><rect x="3" y="32" width="22" height="46" fill="none" stroke="rgba(255,255,255,0.35)" stroke-width="1.5"/><rect x="155" y="32" width="22" height="46" fill="none" stroke="rgba(255,255,255,0.35)" stroke-width="1.5"/><rect x="3" y="42" width="10" height="26" fill="none" stroke="rgba(255,255,255,0.25)" stroke-width="1"/><rect x="167" y="42" width="10" height="26" fill="none" stroke="rgba(255,255,255,0.25)" stroke-width="1"/></svg>
      <div class="detail-badge" id="detail-badge">2 spots left</div>
    </div>
    <div class="detail-body">
      <div class="detail-name" id="detail-name">静安体育中心 · 5-a-side</div>
      <div class="detail-meta">
        <span>📍 <span id="detail-dist">0.8km</span></span>
        <span>⭐ <span id="detail-rating">4.8 (142)</span></span>
        <span>🌿 <span id="detail-type">Outdoor</span></span>
      </div>
      <div class="divider"></div>
      <div class="detail-section">Players Joined</div>
      <div class="players-joined" id="players-joined"></div>
      <div class="divider"></div>
      <div class="detail-section">Choose a Time Slot</div>
      <div class="slot-grid" id="slot-grid"></div>
    </div>
    <div class="book-bar">
      <div class="book-bar-row">
        <div>
          <div class="price-big" id="detail-price">¥35 <span style="font-size:14px;color:var(--mu)">/ person</span></div>
          <div class="price-sub">No booking fee</div>
        </div>
        <button class="btn-book" onclick="goTo('confirm')">Book Now →</button>
      </div>
    </div>
  </div>

  <!-- ══ CONFIRM ══ -->
  <div class="screen hidden" id="confirm">
    <div class="sbar" style="background:var(--gd)"><span>9:41</span><span>📶 🔋</span></div>
    <div class="confirm-top">
      <div class="confirm-icon">🎉</div>
      <div class="confirm-title">You're In!</div>
      <div class="confirm-sub">Your spot has been booked successfully</div>
    </div>
    <div class="confirm-card">
      <div class="confirm-row">
        <span class="confirm-label">Venue</span>
        <span class="confirm-val" id="conf-venue">静安体育中心</span>
      </div>
      <div class="confirm-row">
        <span class="confirm-label">Format</span>
        <span class="confirm-val">5-a-side · Outdoor</span>
      </div>
      <div class="confirm-row">
        <span class="confirm-label">Date</span>
        <span class="confirm-val">Today · 19:00</span>
      </div>
      <div class="confirm-row">
        <span class="confirm-label">City</span>
        <span class="confirm-val" id="conf-city">Shanghai</span>
      </div>
      <div class="confirm-row">
        <span class="confirm-label">Price Paid</span>
        <span class="confirm-val" style="color:var(--g)">¥35.00</span>
      </div>
    </div>
    <div class="qr-box">
      <div style="font-size:13px;font-weight:700;color:var(--gd)">Entry QR Code</div>
      <div style="font-size:56px">⚽</div>
      <div style="font-size:11px;color:var(--mu);text-align:center">Show this at the venue entrance</div>
      <div style="font-size:11px;font-weight:700;color:var(--gd);letter-spacing:2px">FM-2026-8842-SH</div>
    </div>
    <div style="padding:0 18px 32px;display:flex;gap:10px">
      <button class="btn-primary" style="flex:1;margin:0" onclick="goTo('home')">← Back to Home</button>
    </div>
  </div>

  <!-- ══ PROFILE ══ -->
  <div class="screen hidden" id="profile">
    <div class="sbar" style="background:var(--gd)"><span>9:41</span><span>📶 🔋</span></div>
    <div class="profile-hdr">
      <div class="profile-av">张</div>
      <div class="profile-name">Zhang Wei · 张伟</div>
      <div class="profile-loc">📍 Shanghai · Member since 2025</div>
    </div>
    <div class="profile-stats">
      <div class="pstat"><div class="pstat-n">24</div><div class="pstat-l">Games</div></div>
      <div class="pstat"><div class="pstat-n">4.9</div><div class="pstat-l">Rating</div></div>
      <div class="pstat"><div class="pstat-n">18</div><div class="pstat-l">Friends</div></div>
      <div class="pstat"><div class="pstat-n">⚽</div><div class="pstat-l">MVP x3</div></div>
    </div>
    <div class="plist" style="margin-top:16px">
      <div class="plist-item"><span class="plist-ic">🏟️</span> My Bookings <span class="plist-arr">›</span></div>
      <div class="plist-item"><span class="plist-ic">👥</span> My Friends <span class="plist-arr">›</span></div>
      <div class="plist-item"><span class="plist-ic">💴</span> Payment Methods <span class="plist-arr">›</span></div>
      <div class="plist-item"><span class="plist-ic">⚙️</span> Settings <span class="plist-arr">›</span></div>
      <div class="plist-item" onclick="goTo('onboard')"><span class="plist-ic">🚪</span> Sign Out <span class="plist-arr">›</span></div>
    </div>
    <div class="nav">
      <div class="ni" onclick="goTo('home')"><span class="ni-ic">🏟️</span>Pitches</div>
      <div class="ni"><span class="ni-ic">⚽</span>Games</div>
      <div class="ni"><span class="ni-ic">👥</span>Players</div>
      <div class="ni on"><span class="ni-ic">👤</span>Profile</div>
    </div>
  </div>

  <!-- ══ CITY MODAL ══ -->
  <div class="overlay" id="city-modal">
    <div class="sheet">
      <div class="sheet-handle"></div>
      <div class="sheet-title">Choose Your City</div>
      <div class="city-grid">
        <div class="city-btn sel" onclick="setCity('Shanghai','上海',4,this)">Shanghai<span class="cn">上海</span></div>
        <div class="city-btn" onclick="setCity('Beijing','北京',6,this)">Beijing<span class="cn">北京</span></div>
        <div class="city-btn" onclick="setCity('Chongqing','重庆',3,this)">Chongqing<span class="cn">重庆</span></div>
        <div class="city-btn" onclick="setCity('Tianjin','天津',5,this)">Tianjin<span class="cn">天津</span></div>
        <div class="city-btn" onclick="setCity('Guangzhou','广州',7,this)">Guangzhou<span class="cn">广州</span></div>
        <div class="city-btn" onclick="setCity('Shenzhen','深圳',4,this)">Shenzhen<span class="cn">深圳</span></div>
        <div class="city-btn" onclick="setCity('Wuhan','武汉',3,this)">Wuhan<span class="cn">武汉</span></div>
        <div class="city-btn" onclick="setCity('Chengdu','成都',5,this)">Chengdu<span class="cn">成都</span></div>
      </div>
      <button class="close-btn2" onclick="closeModal('city-modal')">Done ✓</button>
    </div>
  </div>

  <!-- ══ HOST MODAL ══ -->
  <div class="overlay" id="host-modal">
    <div class="sheet">
      <div class="sheet-handle"></div>
      <div class="sheet-title">Host a New Game</div>
      <div style="font-size:12px;color:var(--mu);text-align:center;margin-bottom:16px">Format depends on the pitch size — contact the venue first</div>
      <div class="host-opt" onclick="closeModal('host-modal')">
        <div class="host-ic">⚽</div>
        <div><div class="host-name">5-a-side</div><div class="host-desc">Small pitch · Fast paced · 10 players total</div></div>
      </div>
      <div class="host-opt" onclick="closeModal('host-modal')">
        <div class="host-ic">⚽</div>
        <div><div class="host-name">7-a-side</div><div class="host-desc">Medium pitch · 14 players total · Most popular in China</div></div>
      </div>
      <div class="host-opt" onclick="closeModal('host-modal')">
        <div class="host-ic">⚽</div>
        <div><div class="host-name">11-a-side</div><div class="host-desc">Full pitch · 22 players total · Full match experience</div></div>
      </div>
      <button class="close-btn2" onclick="closeModal('host-modal')">Cancel</button>
    </div>
  </div>

</div><!-- /phone -->

<script>
const pitches = [
  {name:"静安体育中心 Jing'an Sports Centre · 5-a-side",dist:"0.8km",rating:"4.8 (142)",type:"Outdoor",price:"¥35",badge:"2 spots left",badgeClass:"spots",bg:"linear-gradient(135deg,#0f4d24,#1a7a3c,#3aad63)",players:[{c:"#1a7a3c",n:"李"},{c:"#e65c00",n:"王"},{c:"#7b1fa2",n:"张"},{c:"#1565c0",n:"陈"}],total:6,slots:[{t:"18:00",tk:false},{t:"19:00",tk:false},{t:"20:00",tk:true},{t:"21:00",tk:true}]},
  {name:"普陀全民健身 Putuo Fitness Hub · 7-a-side",dist:"1.4km",rating:"4.6 (88)",type:"Indoor",price:"¥28",badge:"Indoor",badgeClass:"indoor",bg:"linear-gradient(135deg,#0d4f8a,#1976D2,#42a5f5)",players:[{c:"#c62828",n:"刘"},{c:"#00838f",n:"吴"},{c:"#558b2f",n:"周"}],total:14,slots:[{t:"17:00",tk:true},{t:"19:30",tk:false},{t:"21:00",tk:false},{t:"22:30",tk:false}]},
  {name:"浦东世纪公园 Century Park · 11-a-side",dist:"3.1km",rating:"4.9 (203)",type:"Outdoor",price:"¥20",badge:"Game Full",badgeClass:"full",bg:"linear-gradient(135deg,#4a148c,#7b1fa2,#ab47bc)",players:[{c:"#1a7a3c",n:"赵"},{c:"#e65c00",n:"孙"},{c:"#7b1fa2",n:"周"},{c:"#c62828",n:"+8"}],total:22,slots:[{t:"08:00",tk:true},{t:"10:00",tk:true},{t:"14:00",tk:true},{t:"16:00",tk:true}]},
  {name:"虹桥运动公园 Hongqiao Sports Park · 5-a-side",dist:"2.2km",rating:"4.7 (61)",type:"Outdoor",price:"¥40",badge:"3 spots left",badgeClass:"few",bg:"linear-gradient(135deg,#bf360c,#e64a19,#ff7043)",players:[{c:"#bf360c",n:"何"},{c:"#1565c0",n:"林"}],total:10,slots:[{t:"16:00",tk:false},{t:"18:00",tk:false},{t:"20:00",tk:true},{t:"22:00",tk:false}]}
];

let currentScreen = 'splash';

function goTo(id, exitClass='slide-left'){
  const cur = document.getElementById(currentScreen);
  const next = document.getElementById(id);
  cur.classList.add(exitClass);
  setTimeout(()=>cur.classList.add('hidden'),350);
  next.classList.remove('hidden','slide-left');
  // scroll to top
  next.scrollTop = 0;
  currentScreen = id;
}

function goToDetail(idx){
  const p = pitches[idx];
  document.getElementById('detail-hero').style.background = p.bg;
  document.getElementById('detail-badge').textContent = p.badge;
  document.getElementById('detail-badge').className = 'detail-badge bdg ' + p.badgeClass;
  document.getElementById('detail-name').textContent = p.name;
  document.getElementById('detail-dist').textContent = p.dist;
  document.getElementById('detail-rating').textContent = p.rating;
  document.getElementById('detail-type').textContent = p.type;
  document.getElementById('detail-price').innerHTML = p.price + ' <span style="font-size:14px;color:var(--mu)">/ person</span>';
  document.getElementById('conf-venue').textContent = p.name.split('·')[0].trim();

  // Players
  const pj = document.getElementById('players-joined');
  pj.innerHTML = '';
  p.players.forEach(pl=>{
    pj.innerHTML+=`<div class="pj-card"><div class="pj-av" style="background:${pl.c}">${pl.n}</div><span>Joined</span></div>`;
  });
  const empty = p.total - p.players.length;
  for(let i=0;i<Math.min(empty,4);i++){
    pj.innerHTML+=`<div class="pj-card"><div class="pj-empty">+</div><span>Open</span></div>`;
  }

  // Slots
  const sg = document.getElementById('slot-grid');
  sg.innerHTML = '';
  p.slots.forEach(s=>{
    const cls = s.tk ? 'slot-big tk' : 'slot-big';
    sg.innerHTML+=`<div class="${cls}" onclick="selectSlot(this)"><div class="slot-time">${s.t}</div><div class="slot-avail">${s.tk?'Unavailable':'Available'}</div></div>`;
  });

  goTo('detail');
}

function selectSlot(el){
  if(el.classList.contains('tk')) return;
  document.querySelectorAll('.slot-big').forEach(s=>s.classList.remove('sel'));
  el.classList.add('sel');
}

function showCityModal(){document.getElementById('city-modal').classList.add('show')}
function showHostModal(){document.getElementById('host-modal').classList.add('show')}
function closeModal(id){document.getElementById(id).classList.remove('show')}

function setCity(en,cn,count,el){
  document.getElementById('city-label').textContent = en;
  document.getElementById('map-label').textContent = count + ' pitches nearby';
  document.getElementById('conf-city').textContent = en;
  document.querySelectorAll('.city-btn').forEach(b=>b.classList.remove('sel'));
  el.classList.add('sel');
}

// Filter chips
document.querySelectorAll('.qchip').forEach(c=>{
  c.addEventListener('click',function(){
    document.querySelectorAll('.qchip').forEach(x=>x.classList.remove('on'));
    this.classList.add('on');
  });
});

// Splash → Onboard
setTimeout(()=>goTo('onboard','slide-left'), 2200);
</script>
</body>
</html>
