i dont know i only make that https://github.com/alejandrokcorea-ux/Stick-fighters.git<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="mobile-web-app-capable" content="yes">
<title>Stick Fight PRO</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;-webkit-user-select:none;user-select:none;touch-action:none;}
html,body{width:100%;height:100%;background:#020208;overflow:hidden;font-family:-apple-system,sans-serif;}

/* ── PORTRAIT ── */
#ph{display:none;position:fixed;inset:0;background:#020208;z-index:9999;align-items:center;justify-content:center;flex-direction:column;}
#ph .ph-icon{font-size:64px;animation:phRot 2s ease-in-out infinite;}
@keyframes phRot{0%,100%{transform:rotate(0)}50%{transform:rotate(90deg)}}
#ph p{color:#444;font-size:14px;margin-top:16px;text-align:center;line-height:1.8;}
@media(orientation:portrait){#ph{display:flex;}}

/* ── MENU ── */
#menu{position:fixed;inset:0;z-index:100;display:flex;flex-direction:column;align-items:center;justify-content:center;overflow:hidden;}
#menu-bg{position:absolute;inset:0;}
.menu-content{position:relative;z-index:2;display:flex;flex-direction:column;align-items:center;}
.logo-wrap{text-align:center;margin-bottom:28px;}
.logo-main{font-size:56px;font-weight:900;line-height:1;letter-spacing:.04em;
  background:linear-gradient(160deg,#ff6600 0%,#ff2244 35%,#cc00ff 70%,#0088ff 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;
  filter:drop-shadow(0 0 30px rgba(255,80,0,.4));}
.logo-sub{font-size:13px;letter-spacing:.5em;color:#444;margin-top:4px;text-transform:uppercase;}
.logo-ver{font-size:9px;color:#2a2a3a;letter-spacing:.2em;margin-top:2px;}
.menu-btns{display:flex;flex-direction:column;gap:8px;width:220px;}
.mbtn{position:relative;padding:13px 0;border:none;border-radius:12px;font-size:13px;font-weight:700;letter-spacing:.12em;cursor:pointer;-webkit-tap-highlight-color:transparent;overflow:hidden;transition:transform .1s;}
.mbtn:active{transform:scale(.96);}
.mbtn::after{content:'';position:absolute;inset:0;background:rgba(255,255,255,.06);opacity:0;transition:.1s;}
.mbtn:active::after{opacity:1;}
.mbtn-p{background:linear-gradient(135deg,#2d0a5e,#6a2ccc);color:#fff;box-shadow:0 4px 24px rgba(106,44,204,.4);}
.mbtn-s{background:rgba(255,255,255,.05);color:#888;border:1px solid rgba(255,255,255,.08);}
.mbtn-g{background:linear-gradient(135deg,#0a3d1a,#1a8a3a);color:#fff;}

/* ── SUBMENUS ── */
.sub{position:fixed;inset:0;background:rgba(2,2,8,.96);z-index:101;display:none;flex-direction:column;align-items:center;justify-content:center;gap:10px;padding:20px;overflow-y:auto;}
.sub.act{display:flex;}
.sub h2{font-size:18px;font-weight:800;color:#fff;letter-spacing:.15em;margin-bottom:4px;}
.sub-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;width:300px;}
.mcard{background:rgba(255,255,255,.04);border:1.5px solid rgba(255,255,255,.08);border-radius:12px;padding:12px;cursor:pointer;text-align:center;-webkit-tap-highlight-color:transparent;transition:.12s;}
.mcard:active,.mcard.sel{border-color:#7a3fff;background:rgba(122,63,255,.12);}
.mcard-icon{font-size:24px;margin-bottom:3px;}
.mcard-name{font-size:11px;font-weight:700;color:#ccc;}
.mcard-desc{font-size:9px;color:#444;margin-top:1px;}
.opt-row{display:flex;justify-content:space-between;align-items:center;width:290px;padding:8px 0;border-bottom:1px solid rgba(255,255,255,.05);}
.opt-label{font-size:11px;color:#888;}
.opt-btns{display:flex;gap:4px;}
.tog{padding:5px 12px;border:none;border-radius:6px;font-size:10px;font-weight:700;cursor:pointer;-webkit-tap-highlight-color:transparent;transition:.1s;}
.ton{background:#2d0a5e;color:#bf8fff;}
.toff{background:rgba(255,255,255,.07);color:#444;}
.back-btn{padding:9px 24px;background:rgba(255,255,255,.05);border:1px solid rgba(255,255,255,.1);color:#666;border-radius:8px;font-size:12px;font-weight:600;cursor:pointer;-webkit-tap-highlight-color:transparent;margin-top:4px;}
.mode-card{background:rgba(255,255,255,.04);border:1.5px solid rgba(255,255,255,.08);border-radius:12px;padding:13px;cursor:pointer;width:290px;-webkit-tap-highlight-color:transparent;transition:.12s;}
.mode-card.sel{border-color:#ffaa00;background:rgba(255,170,0,.07);}
.mode-title{font-size:13px;font-weight:800;color:#fff;margin-bottom:2px;}
.mode-desc{font-size:10px;color:#555;}

/* ── GAME ── */
#app{display:none;flex-direction:column;width:100vw;height:100dvh;}
#game-area{flex:1;display:flex;align-items:center;justify-content:center;background:#020208;min-height:0;position:relative;}
#cw{position:relative;}
#gc{display:block;outline:none;}

/* ── HUD ── */
#hud{position:absolute;top:0;left:0;right:0;padding:6px 10px;display:flex;justify-content:space-between;align-items:flex-start;pointer-events:none;z-index:3;}
.hw{display:flex;flex-direction:column;align-items:center;gap:2px;min-width:110px;}
.hn{font-size:8px;font-weight:700;color:rgba(255,255,255,.35);letter-spacing:.1em;}
.hb-wrap{width:110px;height:7px;background:rgba(0,0,0,.7);border-radius:4px;overflow:hidden;border:1px solid rgba(255,255,255,.06);}
.hf{height:100%;border-radius:3px;transition:width .05s;}
.hwep{font-size:13px;height:15px;margin-top:1px;text-align:center;}
/* Combo bar */
.combo-bar-wrap{width:110px;height:3px;background:rgba(255,255,255,.06);border-radius:2px;margin-top:1px;}
.combo-bar{height:100%;border-radius:2px;background:linear-gradient(90deg,#ff6600,#ffdd00);transition:width .1s;}
.combo-count{font-size:16px;font-weight:900;color:#ffdd00;line-height:1;text-shadow:0 0 10px rgba(255,200,0,.5);}

#mid-hud{display:flex;flex-direction:column;align-items:center;gap:1px;}
#rnd-lbl{font-size:7px;color:rgba(255,255,255,.2);letter-spacing:.1em;}
#score-wrap{display:flex;gap:12px;align-items:center;}
.sc-num{font-size:18px;font-weight:900;line-height:1;}
#timer-d{font-size:9px;font-weight:700;color:#ffaa44;display:none;}

/* ── ANNOUNCE ── */
#ann{position:absolute;top:42%;left:50%;transform:translate(-50%,-50%);z-index:10;pointer-events:none;text-align:center;opacity:0;transition:opacity .15s;}
#ann.show{opacity:1;}
#ann-text{font-size:26px;font-weight:900;color:#fff;letter-spacing:.08em;text-shadow:0 0 24px rgba(255,150,50,.6);}
#ann-sub{font-size:11px;color:#666;margin-top:2px;}

/* ── COMBO ANNOUNCE ── */
#combo-ann{position:absolute;top:38%;left:50%;transform:translate(-50%,-50%);z-index:11;pointer-events:none;text-align:center;opacity:0;transition:opacity .12s;}
#combo-ann.show{opacity:1;}
#combo-ann-text{font-size:20px;font-weight:900;letter-spacing:.06em;}

/* ── KILL FEED ── */
#kf{position:absolute;top:36px;right:8px;pointer-events:none;z-index:4;}
.kfe{font-size:9px;color:#ffdd44;text-align:right;margin-bottom:2px;animation:kfA 2.5s forwards;}
@keyframes kfA{0%{opacity:1;transform:translateY(0)}80%{opacity:.8}100%{opacity:0;transform:translateY(-12px)}}

/* ── OVERLAY ── */
#ov{position:absolute;inset:0;display:none;flex-direction:column;align-items:center;justify-content:center;background:rgba(2,2,8,.92);z-index:5;}
.ov-scores{display:flex;gap:28px;margin-bottom:10px;}
.ov-score{text-align:center;}
.ov-sname{font-size:8px;color:#444;letter-spacing:.1em;}
.ov-snum{font-size:36px;font-weight:900;line-height:1;}
#ov-title{font-size:22px;font-weight:800;color:#fff;letter-spacing:.1em;margin-bottom:4px;}
#ov-sub{font-size:10px;color:#555;margin-bottom:18px;}
.ov-btns{display:flex;gap:10px;}
.ov-btn{padding:10px 22px;border:none;border-radius:10px;font-size:12px;font-weight:700;cursor:pointer;-webkit-tap-highlight-color:transparent;color:#fff;}
.ov-p{background:#2d0a5e;}
.ov-s{background:rgba(255,255,255,.07);border:1px solid rgba(255,255,255,.1);}

/* ── CONTROLS ── */
#controls{height:120px;background:linear-gradient(0deg,#020208,#06060f);border-top:1px solid rgba(122,63,255,.15);display:flex;justify-content:space-between;align-items:center;padding:0 24px 8px;flex-shrink:0;position:relative;}

/* ── JOYSTICK ── */
#joystick-wrap{position:relative;width:108px;height:108px;}
#joystick-base{position:absolute;inset:0;border-radius:50%;background:radial-gradient(circle at 35% 35%,rgba(122,63,255,.18),rgba(0,0,0,.7));border:2px solid rgba(122,63,255,.3);box-shadow:0 0 20px rgba(122,63,255,.1),inset 0 0 20px rgba(0,0,0,.5);}
/* tick marks */
#joystick-base::before{content:'';position:absolute;inset:8px;border-radius:50%;border:1px solid rgba(122,63,255,.12);}
#joystick-base::after{content:'';position:absolute;inset:18px;border-radius:50%;border:1px dashed rgba(122,63,255,.08);}
#joystick-knob{position:absolute;width:44px;height:44px;border-radius:50%;background:radial-gradient(circle at 35% 30%,rgba(180,120,255,.9),rgba(80,30,150,.95));border:2px solid rgba(200,160,255,.4);box-shadow:0 4px 16px rgba(122,63,255,.5),0 0 8px rgba(200,100,255,.3),inset 0 2px 4px rgba(255,255,255,.2);top:50%;left:50%;transform:translate(-50%,-50%);transition:none;cursor:pointer;}
#joystick-dir{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);font-size:9px;color:rgba(255,255,255,.3);letter-spacing:.15em;text-align:center;pointer-events:none;line-height:1.8;}

/* ── ATTACK BUTTON ── */
#attack-zone{display:flex;flex-direction:column;align-items:center;gap:6px;}
#atk-btn{width:80px;height:80px;border-radius:50%;border:none;cursor:pointer;-webkit-tap-highlight-color:transparent;position:relative;overflow:hidden;
  background:radial-gradient(circle at 40% 30%,#ff4466,#cc1133);
  box-shadow:0 6px 28px rgba(255,30,60,.5),0 0 0 0 rgba(255,60,80,.4),inset 0 2px 4px rgba(255,255,255,.25);
  transition:transform .06s,box-shadow .06s;}
#atk-btn:active{transform:scale(.9);box-shadow:0 2px 12px rgba(255,30,60,.4),inset 0 2px 8px rgba(0,0,0,.3);}
#atk-btn-inner{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center;}
#atk-icon{font-size:26px;line-height:1;}
#atk-label{font-size:7px;font-weight:800;color:rgba(255,255,255,.7);letter-spacing:.1em;margin-top:1px;}
/* Combo ring */
#combo-ring{position:absolute;inset:-4px;border-radius:50%;border:3px solid transparent;transition:border-color .12s;}
#combo-ring.c1{border-color:rgba(255,200,0,.5);}
#combo-ring.c2{border-color:rgba(255,100,0,.8);box-shadow:0 0 12px rgba(255,100,0,.4);}
#combo-ring.c3{border-color:#ff3300;box-shadow:0 0 20px rgba(255,50,0,.7);animation:ringPulse .3s ease-out;}
@keyframes ringPulse{0%{transform:scale(1.1)}100%{transform:scale(1)}}
/* Cooldown overlay */
#cd-overlay{position:absolute;inset:0;border-radius:50%;pointer-events:none;}
#cd-label{font-size:10px;color:#ffaa44;font-weight:700;text-align:center;height:12px;}

/* ── JUMP BUTTON ── */
#jump-btn{width:52px;height:52px;border-radius:50%;border:none;cursor:pointer;-webkit-tap-highlight-color:transparent;
  background:radial-gradient(circle at 40% 30%,rgba(80,180,255,.9),rgba(30,80,200,.95));
  box-shadow:0 4px 16px rgba(50,120,255,.4),inset 0 2px 4px rgba(255,255,255,.2);
  font-size:20px;transition:transform .06s;}
#jump-btn:active{transform:scale(.88);}

/* ── WEAPON PICKUP HINT ── */
#wep-hint{position:absolute;bottom:130px;left:50%;transform:translateX(-50%);font-size:9px;color:#ffaa44;font-weight:700;letter-spacing:.1em;pointer-events:none;opacity:0;transition:opacity .3s;}
#wep-hint.show{opacity:1;}
</style>
</head>
<body>

<!-- PORTRAIT -->
<div id="ph">
  <div class="ph-icon">📱</div>
  <p>Gira el dispositivo<br>para jugar</p>
</div>

<!-- ════ MENU ════ -->
<div id="menu">
  <canvas id="menu-bg"></canvas>
  <div class="menu-content">
    <div class="logo-wrap">
      <div class="logo-main">STICK FIGHT</div>
      <div class="logo-sub">The Game · Pro</div>
      <div class="logo-ver">V3.0 ULTRA</div>
    </div>
    <div class="menu-btns">
      <button class="mbtn mbtn-p" id="btn-create">⚔️&nbsp; CREAR PARTIDA</button>
      <button class="mbtn mbtn-s" id="btn-modes">🎮&nbsp; MODOS</button>
      <button class="mbtn mbtn-s" id="btn-maps">🗺️&nbsp; MAPAS</button>
      <button class="mbtn mbtn-s" id="btn-opts">⚙️&nbsp; OPCIONES</button>
    </div>
  </div>
</div>

<!-- CREAR PARTIDA -->
<div id="sub-create" class="sub">
  <h2>CREAR PARTIDA</h2>
  <div class="opt-row"><span class="opt-label">Jugadores</span>
    <div class="opt-btns"><button class="tog ton" id="op1">1 vs CPU</button><button class="tog toff" id="op2">2P LOCAL</button></div></div>
  <div class="opt-row"><span class="opt-label">Rondas</span>
    <div class="opt-btns"><button class="tog toff" id="or1">1</button><button class="tog ton" id="or3">3</button><button class="tog toff" id="or5">5</button></div></div>
  <div class="opt-row"><span class="opt-label">Armas</span>
    <div class="opt-btns"><button class="tog ton" id="owep">ON</button></div></div>
  <div class="opt-row"><span class="opt-label">Mapa</span>
    <div class="opt-btns"><button class="tog ton" id="omapmode">ALEATORIO</button></div></div>
  <button class="mbtn mbtn-g" id="btn-fight" style="width:290px;margin-top:8px;">▶&nbsp; ¡A PELEAR!</button>
  <button class="back-btn" id="bb-create">← VOLVER</button>
</div>

<!-- MODOS -->
<div id="sub-modes" class="sub">
  <h2>MODOS</h2>
  <div class="mode-card sel" id="md-normal"><div class="mode-title">⚔️ PELEA NORMAL</div><div class="mode-desc">Sistema de combos. Rondas al mejor de X.</div></div>
  <div class="mode-card" id="md-sudden"><div class="mode-title">⚡ MUERTE SÚBITA</div><div class="mode-desc">Un combo completo = muerte instantánea.</div></div>
  <div class="mode-card" id="md-timed"><div class="mode-title">⏱️ CONTRARRELOJ</div><div class="mode-desc">60 segundos. Más vida al final gana.</div></div>
  <button class="back-btn" id="bb-modes">← VOLVER</button>
</div>

<!-- MAPAS -->
<div id="sub-maps" class="sub">
  <h2>MAPAS</h2>
  <div class="sub-grid">
    <div class="mcard" id="mc0"><div class="mcard-icon">🌃</div><div class="mcard-name">CIUDAD</div><div class="mcard-desc">El clásico</div></div>
    <div class="mcard" id="mc1"><div class="mcard-icon">🌋</div><div class="mcard-name">VOLCÁN</div><div class="mcard-desc">Lava que daña</div></div>
    <div class="mcard" id="mc2"><div class="mcard-icon">❄️</div><div class="mcard-name">HIELO</div><div class="mcard-desc">Resbaladizo</div></div>
    <div class="mcard" id="mc3"><div class="mcard-icon">🌿</div><div class="mcard-name">JUNGLA</div><div class="mcard-desc">Plataformas móviles</div></div>
    <div class="mcard" id="mc4"><div class="mcard-icon">🏙️</div><div class="mcard-name">TEJADOS</div><div class="mcard-desc">Alturas</div></div>
    <div class="mcard" id="mc5"><div class="mcard-icon">⚙️</div><div class="mcard-name">FÁBRICA</div><div class="mcard-desc">Trampas</div></div>
    <div class="mcard sel" id="mc-1" style="grid-column:span 2"><div class="mcard-icon">🎲</div><div class="mcard-name">ALEATORIO</div><div class="mcard-desc">Sorpresa cada ronda</div></div>
  </div>
  <button class="back-btn" id="bb-maps">← VOLVER</button>
</div>

<!-- OPCIONES -->
<div id="sub-opts" class="sub">
  <h2>OPCIONES</h2>
  <div class="opt-row"><span class="opt-label">Sonido FX</span><div class="opt-btns"><button class="tog ton" id="o-sfx">ON</button></div></div>
  <div class="opt-row"><span class="opt-label">Música</span><div class="opt-btns"><button class="tog ton" id="o-mus">ON</button></div></div>
  <div class="opt-row"><span class="opt-label">Partículas</span><div class="opt-btns"><button class="tog ton" id="o-part">ON</button></div></div>
  <div class="opt-row"><span class="opt-label">Dificultad CPU</span>
    <div class="opt-btns"><button class="tog toff" id="od1">FÁCIL</button><button class="tog ton" id="od2">NORMAL</button><button class="tog toff" id="od3">DIFÍCIL</button></div></div>
  <button class="back-btn" id="bb-opts">← VOLVER</button>
</div>

<!-- ════ GAME ════ -->
<div id="app">
  <div id="game-area">
    <div id="cw">
      <canvas id="gc" width="680" height="400"></canvas>
      <!-- HUD -->
      <div id="hud">
        <div class="hw">
          <span class="hn" id="p1n">P1</span>
          <div class="hb-wrap"><div class="hf" id="h1" style="width:100%;background:linear-gradient(90deg,#ff2244,#ff6622);"></div></div>
          <div class="hwep" id="w1i"></div>
          <div class="combo-bar-wrap"><div class="combo-bar" id="cb1" style="width:0%"></div></div>
          <div class="combo-count" id="cc1"></div>
        </div>
        <div id="mid-hud">
          <div id="rnd-lbl">RONDA 1</div>
          <div id="score-wrap">
            <span class="sc-num" id="sc1" style="color:#ff4466;">0</span>
            <span style="color:#222;font-size:12px;">–</span>
            <span class="sc-num" id="sc2" style="color:#33aaff;">0</span>
          </div>
          <div id="timer-d"></div>
        </div>
        <div class="hw" style="align-items:flex-end;">
          <span class="hn" id="p2n">CPU</span>
          <div class="hb-wrap"><div class="hf" id="h2" style="width:100%;background:linear-gradient(90deg,#33aaff,#0055ff);"></div></div>
          <div class="hwep" id="w2i" style="text-align:right;"></div>
          <div class="combo-bar-wrap"><div class="combo-bar" id="cb2" style="width:0%"></div></div>
          <div class="combo-count" id="cc2" style="text-align:right;"></div>
        </div>
      </div>
      <!-- Announce -->
      <div id="ann"><div id="ann-text"></div><div id="ann-sub"></div></div>
      <!-- Combo announce -->
      <div id="combo-ann"><div id="combo-ann-text"></div></div>
      <!-- Kill feed -->
      <div id="kf"></div>
      <!-- Weapon hint -->
      <div id="wep-hint">⬇ ARMA CERCA · TOCA ATAQUE</div>
      <!-- Game Over -->
      <div id="ov">
        <div class="ov-scores">
          <div class="ov-score"><div class="ov-sname">P1</div><div class="ov-snum" id="fs1" style="color:#ff4466;">0</div></div>
          <div class="ov-score"><div class="ov-sname">P2/CPU</div><div class="ov-snum" id="fs2" style="color:#33aaff;">0</div></div>
        </div>
        <div id="ov-title">¡GANASTE!</div>
        <div id="ov-sub"></div>
        <div class="ov-btns">
          <button class="ov-btn ov-p" id="btn-retry">REVANCHA</button>
          <button class="ov-btn ov-s" id="btn-menu">MENÚ</button>
        </div>
      </div>
    </div>
  </div>

  <!-- ── CONTROLS ── -->
  <div id="controls">
    <!-- JOYSTICK -->
    <div id="joystick-wrap">
      <div id="joystick-base">
        <div id="joystick-dir">MOVE</div>
      </div>
      <div id="joystick-knob"></div>
    </div>

    <!-- ATTACK + JUMP -->
    <div id="attack-zone">
      <button id="atk-btn">
        <div id="combo-ring"></div>
        <div id="atk-btn-inner">
          <div id="atk-icon">👊</div>
          <div id="atk-label">ATACAR</div>
        </div>
        <canvas id="cd-overlay"></canvas>
      </button>
      <div id="cd-label"></div>
    </div>

    <button id="jump-btn">↑</button>
  </div>
</div>

<script>
(function(){
'use strict';

// ════════════════════════════════════════════
// CONFIG
// ════════════════════════════════════════════
var CFG={players:1,rounds:3,weapons:true,mapMode:'random',selMap:-1,gameMode:'normal',sfx:true,music:true,particles:true,diff:2};
var scores=[0,0],curRound=1;

// ════════════════════════════════════════════
// WEB AUDIO - EPIC SOUND ENGINE
// ════════════════════════════════════════════
var AC=null,musTimer=null;
function getAC(){
  if(!AC){try{AC=new(window.AudioContext||window.webkitAudioContext)();}catch(e){}}
  return AC;
}
function masterGain(){
  var ac=getAC();if(!ac)return null;
  var g=ac.createGain();g.gain.value=.7;g.connect(ac.destination);return g;
}
function tone(freq,type,dur,vol,del,bend){
  var ac=getAC();if(!ac||!CFG.sfx)return;
  try{
    var o=ac.createOscillator(),g=ac.createGain(),mg=masterGain();
    o.type=type||'sine';o.frequency.value=freq;
    if(bend)o.frequency.exponentialRampToValueAtTime(bend,ac.currentTime+(del||0)+dur*.6);
    g.gain.setValueAtTime((vol||.3)*.4,ac.currentTime+(del||0));
    g.gain.exponentialRampToValueAtTime(.001,ac.currentTime+(del||0)+dur);
    o.connect(g);g.connect(mg||ac.destination);
    o.start(ac.currentTime+(del||0));o.stop(ac.currentTime+(del||0)+dur);
  }catch(e){}
}
function noise(dur,vol,del){
  var ac=getAC();if(!ac||!CFG.sfx)return;
  try{
    var sz=Math.floor(ac.sampleRate*dur);
    var buf=ac.createBuffer(1,sz,ac.sampleRate);
    var d=buf.getChannelData(0);for(var i=0;i<sz;i++)d[i]=Math.random()*2-1;
    var src=ac.createBufferSource(),g=ac.createGain(),mg=masterGain();
    var lp=ac.createBiquadFilter();lp.type='lowpass';lp.frequency.value=2000;
    src.buffer=buf;
    g.gain.setValueAtTime((vol||.4)*.5,ac.currentTime+(del||0));
    g.gain.exponentialRampToValueAtTime(.001,ac.currentTime+(del||0)+dur);
    src.connect(lp);lp.connect(g);g.connect(mg||ac.destination);src.start(ac.currentTime+(del||0));
  }catch(e){}
}
// Rich SFX
var SFX={
  punch1:function(){noise(.05,.6);tone(200,'sine',.08,.5);tone(400,'square',.04,.2,.03);},
  punch2:function(){noise(.07,.8);tone(150,'sine',.1,.6);tone(300,'sawtooth',.05,.3,.04);tone(500,'sine',.04,.2,.06);},
  punch3:function(){noise(.12,1);tone(100,'sawtooth',.15,.8);tone(200,'square',.08,.4,.05);tone(600,'sine',.05,.3,.1);},
  kick:function(){noise(.1,.9);tone(80,'sawtooth',.12,.7);tone(160,'sine',.08,.4,.04);},
  headkick:function(){noise(.15,1.2);tone(60,'sawtooth',.2,.9);tone(120,'square',.1,.5,.06);tone(800,'sine',.06,.4,.12);},
  jump:function(){tone(320,'sine',.1,.3);tone(480,'triangle',.07,.2,.06);},
  djump:function(){tone(450,'sine',.08,.4);tone(680,'triangle',.06,.3,.05);tone(900,'sine',.04,.2,.09);},
  land:function(){noise(.06,.4);tone(90,'sine',.07,.3);},
  death:function(){for(var i=0;i<6;i++)tone(350-i*40,'sawtooth',.18,.4,i*.07);noise(.3,.6);},
  win:function(){[523,659,784,1047,1318].forEach(function(f,i){tone(f,'sine',.25,.5,i*.1);tone(f*2,'triangle',.15,.2,i*.1+.05);});},
  pickup:function(){tone(660,'sine',.07,.5);tone(880,'triangle',.07,.4,.08);tone(1100,'sine',.05,.3,.15);},
  gun:function(){noise(.08,1.2);tone(80,'sawtooth',.1,1);tone(200,'square',.04,.4,.03);},
  sword:function(){tone(600,'sawtooth',.12,.5);tone(300,'sawtooth',.08,.3,.05);noise(.05,.3,.02);},
  explosion:function(){noise(.4,1.5);tone(60,'sawtooth',.3,1);tone(30,'sine',.5,.8,.05);},
  roundStart:function(){[262,330,392,523].forEach(function(f,i){tone(f,'square',.15,.35,i*.12);});},
  countdown:function(){tone(440,'sine',.2,.6);},
  go:function(){tone(880,'sine',.3,.9);tone(1320,'triangle',.2,.6,.1);tone(660,'square',.15,.4,.2);},
  comboFinish:function(){[440,550,660,880].forEach(function(f,i){tone(f,'triangle',.15,.6,i*.04);});noise(.08,.5);},
  comboSpecial:function(){[330,440,550,770,1100].forEach(function(f,i){tone(f,'sine',.2,.7,i*.05);tone(f*1.5,'triangle',.1,.3,i*.05+.03);});noise(.15,.8);},
  hit:function(power){var p=power||1;noise(.04+p*.04,p*.8);tone(200-p*30,'sine',.06+p*.04,p*.5);}
};

// MUSIC ENGINE - ambient fighting music
var musStep=0,musNotes=[196,220,246,262,294,330,370,392,440];
var musBass=[98,110,131,147,164];
function startMusic(){
  if(!CFG.music)return;
  stopMusic();
  var step=0;
  function tick(){
    if(!CFG.music)return;
    var n=musNotes[step%musNotes.length];
    tone(n*(step%8<4?1:.5),'triangle',.18,.05);
    if(step%4===0)tone(musBass[Math.floor(step/4)%musBass.length],'sine',.35,.08);
    if(step%8===6)tone(n*2,'square',.06,.03);
    step++;
    musTimer=setTimeout(tick,200);
  }
  musTimer=setTimeout(tick,800);
}
function stopMusic(){if(musTimer){clearTimeout(musTimer);musTimer=null;}}

// ════════════════════════════════════════════
// MENU BG ANIMATION
// ════════════════════════════════════════════
var mbc=document.getElementById('menu-bg'),mbx=mbc.getContext('2d');
var mSticks=[],mAnimId=null;
function initMenuAnim(){
  mbc.width=window.innerWidth;mbc.height=window.innerHeight;
  mSticks=[];
  for(var i=0;i<8;i++){
    mSticks.push({x:(i+.5)*window.innerWidth/8,y:window.innerHeight*.75,
      vx:(Math.random()-.5)*2.5,vy:-4-Math.random()*3,
      col:['#ff4466','#33aaff','#ffdd00','#44ff88','#ff88ff','#ff8800','#00ffcc','#ff3300'][i],
      ph:Math.random()*Math.PI*2,scale:.8+Math.random()*.5});
  }
}
function animMenu(){
  if(document.getElementById('menu').style.display==='none'){return;}
  mbc.width=window.innerWidth;mbc.height=window.innerHeight;
  var W=mbc.width,H=mbc.height;
  mbx.fillStyle='rgba(2,2,8,.15)';mbx.fillRect(0,0,W,H);
  // Draw tiny stars
  if(Math.random()<.08){mbx.fillStyle='rgba(255,255,255,.3)';mbx.beginPath();mbx.arc(Math.random()*W,Math.random()*H*.5,Math.random()*1.5,0,Math.PI*2);mbx.fill();}
  mSticks.forEach(function(s){
    s.ph+=.05;s.x+=s.vx;s.y+=s.vy;s.vy+=.1;
    if(s.y>H*.82){s.vy=-5-Math.random()*3;s.vx=(Math.random()-.5)*3;}
    if(s.x<0||s.x>W)s.vx*=-1;
    var sc=s.scale,t=s.ph;
    mbx.save();mbx.translate(s.x,s.y);mbx.scale(sc,sc);
    mbx.strokeStyle=s.col;mbx.lineWidth=2.5;mbx.lineCap='round';mbx.globalAlpha=.4;
    mbx.beginPath();mbx.moveTo(0,0);mbx.lineTo(0,-28);mbx.stroke();
    mbx.beginPath();mbx.arc(0,-38,8,0,Math.PI*2);mbx.stroke();
    mbx.beginPath();mbx.moveTo(-14,-19+Math.sin(t)*6);mbx.lineTo(0,-22);mbx.lineTo(14,-19+Math.sin(t+Math.PI)*6);mbx.stroke();
    mbx.beginPath();mbx.moveTo(-10,14+Math.sin(t)*8);mbx.lineTo(0,0);mbx.lineTo(10,14+Math.sin(t+Math.PI)*8);mbx.stroke();
    mbx.globalAlpha=1;mbx.restore();
  });
  mAnimId=requestAnimationFrame(animMenu);
}
initMenuAnim();animMenu();
window.addEventListener('resize',function(){if(document.getElementById('menu').style.display!=='none')initMenuAnim();});

// ════════════════════════════════════════════
// MENU LOGIC
// ════════════════════════════════════════════
function showSub(id){document.querySelectorAll('.sub').forEach(function(s){s.classList.remove('act');});var e=document.getElementById(id);if(e)e.classList.add('act');}
function hideSubs(){document.querySelectorAll('.sub').forEach(function(s){s.classList.remove('act');});}

document.getElementById('btn-create').addEventListener('click',function(){getAC();showSub('sub-create');});
document.getElementById('btn-modes').addEventListener('click',function(){showSub('sub-modes');});
document.getElementById('btn-maps').addEventListener('click',function(){showSub('sub-maps');});
document.getElementById('btn-opts').addEventListener('click',function(){showSub('sub-opts');});
['bb-create','bb-modes','bb-maps','bb-opts'].forEach(function(id){document.getElementById(id).addEventListener('click',hideSubs);});

// players
function setPlayers(n){CFG.players=n;document.getElementById('op1').className='tog '+(n===1?'ton':'toff');document.getElementById('op2').className='tog '+(n===2?'ton':'toff');}
document.getElementById('op1').addEventListener('click',function(){setPlayers(1);});
document.getElementById('op2').addEventListener('click',function(){setPlayers(2);});

// rounds
function setRounds(n){CFG.rounds=n;[1,3,5].forEach(function(v){document.getElementById('or'+v).className='tog '+(n===v?'ton':'toff');});}
document.getElementById('or1').addEventListener('click',function(){setRounds(1);});
document.getElementById('or3').addEventListener('click',function(){setRounds(3);});
document.getElementById('or5').addEventListener('click',function(){setRounds(5);});

// weapons
document.getElementById('owep').addEventListener('click',function(){CFG.weapons=!CFG.weapons;this.textContent=CFG.weapons?'ON':'OFF';this.className='tog '+(CFG.weapons?'ton':'toff');});

// map mode
document.getElementById('omapmode').addEventListener('click',function(){CFG.mapMode=CFG.mapMode==='random'?'fixed':'random';this.textContent=CFG.mapMode==='random'?'ALEATORIO':'FIJO';});

// map select
[-1,0,1,2,3,4,5].forEach(function(idx){
  var id=idx===-1?'mc-1':'mc'+idx;
  var el=document.getElementById(id);if(!el)return;
  el.addEventListener('click',function(){
    CFG.selMap=idx;CFG.mapMode=idx===-1?'random':'fixed';
    document.querySelectorAll('.mcard').forEach(function(c){c.classList.remove('sel');});
    el.classList.add('sel');
    document.getElementById('omapmode').textContent=CFG.mapMode==='random'?'ALEATORIO':'FIJO';
  });
});

// game mode
['normal','sudden','timed'].forEach(function(m){
  var el=document.getElementById('md-'+m);if(!el)return;
  el.addEventListener('click',function(){CFG.gameMode=m;document.querySelectorAll('.mode-card').forEach(function(c){c.classList.remove('sel');});el.classList.add('sel');});
});

// options
document.getElementById('o-sfx').addEventListener('click',function(){CFG.sfx=!CFG.sfx;this.textContent=CFG.sfx?'ON':'OFF';this.className='tog '+(CFG.sfx?'ton':'toff');});
document.getElementById('o-mus').addEventListener('click',function(){CFG.music=!CFG.music;this.textContent=CFG.music?'ON':'OFF';this.className='tog '+(CFG.music?'ton':'toff');if(CFG.music)startMusic();else stopMusic();});
document.getElementById('o-part').addEventListener('click',function(){CFG.particles=!CFG.particles;this.textContent=CFG.particles?'ON':'OFF';this.className='tog '+(CFG.particles?'ton':'toff');});
function setDiff(d){CFG.diff=d;[1,2,3].forEach(function(v){document.getElementById('od'+v).className='tog '+(d===v?'ton':'toff');});}
document.getElementById('od1').addEventListener('click',function(){setDiff(1);});
document.getElementById('od2').addEventListener('click',function(){setDiff(2);});
document.getElementById('od3').addEventListener('click',function(){setDiff(3);});

// START
document.getElementById('btn-fight').addEventListener('click',function(){
  hideSubs();
  document.getElementById('menu').style.display='none';
  document.getElementById('app').style.display='flex';
  stopMusic();scores=[0,0];curRound=1;
  document.getElementById('p2n').textContent=CFG.players===2?'P2':'CPU';
  initRound();
});
document.getElementById('btn-retry').addEventListener('click',function(){scores=[0,0];curRound=1;initRound();});
document.getElementById('btn-menu').addEventListener('click',function(){
  document.getElementById('ov').style.display='none';
  document.getElementById('app').style.display='none';
  document.getElementById('menu').style.display='flex';
  stopMusic();scores=[0,0];curRound=1;
  if(mAnimId)cancelAnimationFrame(mAnimId);
  initMenuAnim();animMenu();startMusic();
});

// ════════════════════════════════════════════
// MAPS
// ════════════════════════════════════════════
var GW=680,GH=400;
var MAPS=[
  {name:'CIUDAD',bg:'#09091c',gc:'#0e0e2c',ge:'#534AB7',lava:false,ice:false,
   pl:[{x:0,y:348,w:680,h:52,t:'ground'},{x:190,y:272,w:148,h:10,t:'plat'},{x:52,y:298,w:108,h:10,t:'plat'},{x:430,y:285,w:118,h:10,t:'plat'},{x:270,y:210,w:100,h:10,t:'plat'},{x:0,y:0,w:12,h:400,t:'wall'},{x:668,y:0,w:12,h:400,t:'wall'}],
   mv:[],p1:{x:120,y:270},p2:{x:540,y:270},
   stars:{x:[55,105,168,222,285,338,392,448,502,558,614],y:[14,32,11,42,20,9,38,25,50,17,34]}},
  {name:'VOLCÁN',bg:'#1a0800',gc:'#3d0e00',ge:'#ff4400',lava:true,ice:false,
   pl:[{x:0,y:348,w:200,h:52,t:'ground'},{x:480,y:348,w:200,h:52,t:'ground'},{x:200,y:375,w:280,h:25,t:'lava'},{x:240,y:270,w:120,h:10,t:'plat'},{x:80,y:290,w:90,h:10,t:'plat'},{x:510,y:290,w:90,h:10,t:'plat'},{x:295,y:205,w:90,h:10,t:'plat'},{x:0,y:0,w:12,h:400,t:'wall'},{x:668,y:0,w:12,h:400,t:'wall'}],
   mv:[{x:300,y:240,w:80,h:10,t:'moving',dx:1.5,range:100,ox:300}],
   p1:{x:100,y:290},p2:{x:560,y:290},stars:{x:[],y:[]}},
  {name:'HIELO',bg:'#050e1a',gc:'#0a1e3a',ge:'#88ddff',lava:false,ice:true,
   pl:[{x:0,y:348,w:680,h:52,t:'ice-ground'},{x:150,y:280,w:140,h:10,t:'ice-plat'},{x:380,y:280,w:140,h:10,t:'ice-plat'},{x:265,y:210,w:150,h:10,t:'ice-plat'},{x:0,y:0,w:12,h:400,t:'wall'},{x:668,y:0,w:12,h:400,t:'wall'}],
   mv:[],p1:{x:120,y:290},p2:{x:540,y:290},
   stars:{x:[50,150,250,350,450,550,650],y:[10,20,15,25,12,18,22]}},
  {name:'JUNGLA',bg:'#030e03',gc:'#071a07',ge:'#33aa44',lava:false,ice:false,
   pl:[{x:0,y:348,w:680,h:52,t:'ground'},{x:60,y:300,w:100,h:10,t:'plat'},{x:520,y:300,w:100,h:10,t:'plat'},{x:295,y:230,w:90,h:10,t:'plat'},{x:0,y:0,w:12,h:400,t:'wall'},{x:668,y:0,w:12,h:400,t:'wall'}],
   mv:[{x:180,y:262,w:100,h:10,t:'moving',dx:1.5,range:120,ox:180},{x:390,y:282,w:100,h:10,t:'moving',dx:-1.5,range:100,ox:390}],
   p1:{x:80,y:300},p2:{x:580,y:300},stars:{x:[],y:[]}},
  {name:'TEJADOS',bg:'#080815',gc:'#10102a',ge:'#aaaaff',lava:false,ice:false,
   pl:[{x:0,y:360,w:120,h:40,t:'ground'},{x:560,y:360,w:120,h:40,t:'ground'},{x:120,y:320,w:140,h:10,t:'plat'},{x:420,y:320,w:140,h:10,t:'plat'},{x:265,y:260,w:150,h:10,t:'plat'},{x:195,y:200,w:90,h:10,t:'plat'},{x:395,y:200,w:90,h:10,t:'plat'},{x:0,y:0,w:12,h:400,t:'wall'},{x:668,y:0,w:12,h:400,t:'wall'}],
   mv:[],p1:{x:60,y:320},p2:{x:610,y:320},
   stars:{x:[60,160,260,360,460,560],y:[15,30,12,40,20,10]}},
  {name:'FÁBRICA',bg:'#0a0a08',gc:'#1a1a10',ge:'#aaaa44',lava:false,ice:false,
   pl:[{x:0,y:348,w:680,h:52,t:'ground'},{x:100,y:290,w:80,h:10,t:'plat'},{x:500,y:290,w:80,h:10,t:'plat'},{x:275,y:240,w:130,h:10,t:'plat'},{x:0,y:0,w:12,h:400,t:'wall'},{x:668,y:0,w:12,h:400,t:'wall'},{x:190,y:185,w:18,h:75,t:'wall'},{x:472,y:185,w:18,h:75,t:'wall'}],
   mv:[{x:265,y:312,w:90,h:10,t:'moving',dx:2,range:60,ox:265}],
   p1:{x:100,y:290},p2:{x:560,y:290},stars:{x:[],y:[]}}
];
var curMapIdx=0,curMap=null,PLATS=[],movPlats=[];
function pickMap(){
  if(CFG.mapMode==='random'||CFG.selMap===-1)curMapIdx=Math.floor(Math.random()*MAPS.length);
  else curMapIdx=Math.max(0,Math.min(MAPS.length-1,CFG.selMap));
  curMap=MAPS[curMapIdx];
  PLATS=curMap.pl.map(function(p){return{x:p.x,y:p.y,w:p.w,h:p.h,t:p.t,solid:true};});
  movPlats=(curMap.mv||[]).map(function(p){return{x:p.x,y:p.y,w:p.w,h:p.h,t:p.t,solid:true,dx:p.dx,range:p.range,ox:p.ox};});
  PLATS=PLATS.concat(movPlats);
}

// ════════════════════════════════════════════
// WEAPONS
// ════════════════════════════════════════════
var WTYPES=[
  {id:'sword',icon:'⚔️',name:'Espada',col:'#aaddff',dmg:18,reach:88,cd:20,ranged:false,exp:false},
  {id:'gun',icon:'🔫',name:'Pistola',col:'#ffaa44',dmg:12,reach:999,cd:30,ranged:true,ammo:8,exp:false},
  {id:'bat',icon:'🏏',name:'Bate',col:'#ddaa66',dmg:24,reach:78,cd:20,ranged:false,exp:false},
  {id:'bomb',icon:'💣',name:'Bomba',col:'#ff4444',dmg:28,reach:50,cd:60,ranged:false,exp:true}
];
var wDrops=[],bullets=[],exps=[];
function spawnWeapon(){
  if(!CFG.weapons)return;
  var t=WTYPES[Math.floor(Math.random()*WTYPES.length)];
  wDrops.push({x:80+Math.random()*(GW-160),y:50,t:t,vy:0,grnd:false,timer:550});
}
function updateWeapons(){
  var i;
  for(i=wDrops.length-1;i>=0;i--){
    var w=wDrops[i];
    if(!w.grnd){w.vy+=.5;w.y+=w.vy;}
    for(var j=0;j<PLATS.length;j++){var p=PLATS[j];if(p.t==='wall')continue;if(w.y>=p.y&&w.y<=p.y+16&&w.x>=p.x&&w.x<=p.x+p.w){w.y=p.y;w.vy=0;w.grnd=true;break;}}
    w.timer--;
    var fis=[{f:P,fi:0},{f:N,fi:1}];
    for(var fi=0;fi<fis.length;fi++){
      var ff=fis[fi].f,fii=fis[fi].fi;
      if(!ff||ff.dead||ff.weapon)continue;
      if(Math.abs(ff.x-w.x)<30&&Math.abs(ff.y-w.y)<40){
        ff.weapon={id:w.t.id,icon:w.t.icon,name:w.t.name,col:w.t.col,dmg:w.t.dmg,reach:w.t.reach,cd:w.t.cd,ranged:w.t.ranged,exp:w.t.exp};
        ff.wAmmo=w.t.ranged?(w.t.ammo||8):1;
        wDrops.splice(i,1);SFX.pickup();
        document.getElementById('w'+(fii+1)+'i').textContent=ff.weapon.icon;
        addKF((fii===0?'P1':'CPU')+' cogió '+ff.weapon.name+'!');break;
      }
    }
  }
  wDrops=wDrops.filter(function(w){return w.timer>0;});
  // bullets
  for(i=bullets.length-1;i>=0;i--){
    var b=bullets[i];b.x+=b.vx;b.y+=b.vy;b.vy+=.15;b.life--;
    var ts=[{f:P,fi:0},{f:N,fi:1}];
    for(var ti=0;ti<ts.length;ti++){var tf=ts[ti].f;if(!tf||tf.dead||ts[ti].fi===b.owner)continue;if(Math.abs(tf.x-b.x)<22&&Math.abs((tf.y-40)-b.y)<44){doHit(b.owner===0?P:N,tf,b.dmg,false,1);b.life=0;emit(b.x,b.y,'#ffaa44',8,5,.3,.5);break;}}
    for(var pi=0;pi<PLATS.length;pi++){var pp=PLATS[pi];if(b.y>=pp.y&&b.y<=pp.y+pp.h&&b.x>=pp.x&&b.x<=pp.x+pp.w){b.life=0;emit(b.x,b.y,'#ffaa44',5,3,.3,.4);break;}}
  }
  bullets=bullets.filter(function(b){return b.life>0;});
  // explosions
  for(i=exps.length-1;i>=0;i--){
    var ex=exps[i];ex.life--;
    if(ex.life===12){[{f:P},{f:N}].forEach(function(o){if(!o.f||o.f.dead)return;if(Math.hypot(o.f.x-ex.x,o.f.y-40-ex.y)<ex.r+30)doHit(P,o.f,30,true,3);});emit(ex.x,ex.y,'#ff6600',30,10,.3,.8);emit(ex.x,ex.y,'#ffdd44',18,7,.3,.5);applyShake(12);SFX.explosion();}
  }
  exps=exps.filter(function(e){return e.life>0;});
}
function useWeapon(f,fi){
  if(!f.weapon||f.dead||f.hStop>0)return;
  var w=f.weapon;
  if(w.ranged){SFX.gun();bullets.push({x:f.x+f.dir*18,y:f.y-42,vx:f.dir*13,vy:-1,col:w.col,owner:fi,life:65,dmg:w.dmg});f.wAmmo--;}
  else if(w.exp){SFX.gun();exps.push({x:f.x+f.dir*50,y:f.y-40,r:65,life:20});f.wAmmo=0;}
  else{SFX.sword();var vic=fi===0?N:P;if(vic&&!vic.dead&&Math.abs(f.x-vic.x)<w.reach)doHit(f,vic,w.dmg,true,2);f.pF=16;f.pCD=w.cd;f.wAmmo=0;}
  if(f.wAmmo<=0){f.weapon=null;document.getElementById('w'+(fi+1)+'i').textContent='';}
}

// ════════════════════════════════════════════
// COMBO SYSTEM
// ════════════════════════════════════════════
// comboState per fighter: {count, timer, inAir, phase}
// Combo rules:
//   3 hits = PATADA (kick) - auto triggered
//   2 hits + jump + hit = HEAD STOMP (if airborne on 3rd hit)
// Cooldown 0.2s (12 frames) after each hit group of 3
var COMBO_WINDOW=35; // frames to chain combo
var COMBO_CD_FRAMES=12; // 0.2s cooldown

function mkCombo(){return{count:0,timer:0,cd:0,jumpedMid:false,hitIcons:['','',''],lastHitAir:false};}

function triggerAttack(f,fi){
  // During cooldown: no attack
  if(f.comboCd>0)return;
  // Increment combo
  f.combo.count++;
  f.combo.timer=COMBO_WINDOW;
  var c=f.combo.count;

  // Pick which sound
  if(c===1)SFX.punch1();
  else if(c===2)SFX.punch2();
  else SFX.punch3();

  // Mark if this hit was in the air
  f.combo.lastHitAir=!f.onGnd;

  var vic=fi===0?N:P;
  var dx=Math.abs(f.x-vic.x);
  var hit=false;

  // Check HEAD STOMP combo: count==3, air, came from jump mid-combo
  if(c===3&&f.combo.lastHitAir&&f.combo.jumpedMid&&!f.onGnd){
    // HEAD STOMP
    if(vic&&!vic.dead&&dx<100){
      doHit(f,vic,32,true,3);
      SFX.headkick();
      SFX.comboSpecial();
      showComboAnn('💀 CABEZAZO!','#ff3300',fi);
      addKF((fi===0?'P1':'CPU')+' ¡CABEZAZO! -32HP');
      applyShake(10);
      hit=true;
    }
    resetCombo(f);
    f.comboCd=COMBO_CD_FRAMES;
  } else if(c===3){
    // PATADA (kick)
    if(vic&&!vic.dead&&dx<90){
      doHit(f,vic,24,true,2);
      SFX.kick();
      SFX.comboFinish();
      showComboAnn('🦵 PATADA!','#ffaa00',fi);
      addKF((fi===0?'P1':'CPU')+' ¡COMBO PATADA! -24HP');
      applyShake(7);
      hit=true;
    }
    resetCombo(f);
    f.comboCd=COMBO_CD_FRAMES;
  } else {
    // Normal punch hit
    if(vic&&!vic.dead&&dx<72&&(f.dir===1?vic.x>f.x:vic.x<f.x)){
      var dmg=c===1?8:14;
      doHit(f,vic,dmg,false,c-1);
      SFX.hit(c*.4);
      hit=true;
    }
    f.pF=14;f.pCD=14;f.atkHit=false;
  }
  // Update combo bar UI
  updateComboHUD(f,fi);
  return hit;
}

function resetCombo(f){f.combo.count=0;f.combo.timer=0;f.combo.jumpedMid=false;f.combo.lastHitAir=false;}

function updateComboHUD(f,fi){
  var c=f.combo.count;
  var pct=c/3*100;
  document.getElementById('cb'+(fi+1)).style.width=pct+'%';
  document.getElementById('cc'+(fi+1)).textContent=c>0?'×'+c:'';
  // ring color
  if(fi===0){
    var ring=document.getElementById('combo-ring');
    ring.className=c===0?'':c===1?'c1':c===2?'c2':'c3';
  }
}

var comboAnnTimer=null;
function showComboAnn(txt,col,fi){
  var el=document.getElementById('combo-ann');
  var tx=document.getElementById('combo-ann-text');
  tx.textContent=txt;tx.style.color=col;tx.style.textShadow='0 0 20px '+col;
  el.classList.add('show');
  clearTimeout(comboAnnTimer);
  comboAnnTimer=setTimeout(function(){el.classList.remove('show');},1200);
}

// ════════════════════════════════════════════
// PHYSICS
// ════════════════════════════════════════════
var GRAV=.72,VJ=-15.5,VDJ=-13,WJX=6.5,WJY=-13,RACC=2.2,RMAX=5.2,FG=.62,FA=.94,WSG=.18;
var cv=document.getElementById('gc'),cx=cv.getContext('2d');
var frame=0,running=false,over=null;
var shX=0,shY=0,shD=0;
var parts=[],keys={};
var jPressed=false,jPrev=false;
var wSpawnT=180,gameTimer=0;
var nT=0,nJT=0,nThink=0,nComboT=0;
var P=null,N=null;
var annTimeout=null;

function resize(){
  var ga=document.getElementById('game-area'),cw=document.getElementById('cw');
  var aW=ga.clientWidth,aH=ga.clientHeight;
  var sc=Math.min(aW/GW,aH/GH);
  var w=Math.floor(GW*sc),h=Math.floor(GH*sc);
  cw.style.width=w+'px';cw.style.height=h+'px';
  cv.style.width='100%';cv.style.height='100%';
}
window.addEventListener('resize',resize);

function mkF(x,col,dir){
  return{x:x,y:280,vx:0,vy:0,col:col,dir:dir,hp:100,maxHp:100,dead:false,
    onGnd:false,onWall:0,wSide:0,canDj:true,coy:0,
    pF:0,pCD:0,kF:0,kCD:0,hFlash:0,hStop:0,atkHit:false,runT:0,
    weapon:null,wAmmo:0,
    combo:mkCombo(),comboCd:0,
    rd:{sp:0,spV:0,hd:0,hdV:0,lA:0,lAV:0,rA:0,rAV:0,lL:0,lLV:0,rL:0,rLV:0},
    lvx:0,lvy:0};
}

function applyShake(m){shX=(Math.random()-.5)*m*2;shY=(Math.random()-.5)*m*2;shD=m;}

function emit(x,y,col,n,spd,g,life){
  if(!CFG.particles)return;
  for(var i=0;i<n;i++){
    var a=Math.random()*Math.PI*2,s=spd*(.3+Math.random()*.7);
    parts.push({x:x,y:y,vx:Math.cos(a)*s,vy:Math.sin(a)*s-spd*.18,life:life||.7,col:col,g:g||.3,r:1+Math.random()*2.5});
  }
}
function emitBurst(x,y,col,size){
  emit(x,y,col,size*2,size*.8,.25,.8);
  emit(x,y,'#ffffff',size,size*.5,.2,.5);
  if(size>2)emit(x,y,'rgba(255,200,100,.5)',size,size*.3,.15,.4);
}

function overlap(ax,ay,aw,ah,bx,by,bw,bh){return ax<bx+bw&&ax+aw>bx&&ay<by+bh&&ay+ah>by;}

function resolveCol(f){
  var fw=14,fh=88,fx=f.x-fw/2,fy=f.y-fh;
  f.onGnd=false;f.onWall=0;
  for(var i=0;i<PLATS.length;i++){
    var p=PLATS[i];if(!p.solid)continue;
    if(!overlap(fx,fy,fw,fh,p.x,p.y,p.w,p.h))continue;
    var oL=(fx+fw)-p.x,oR=(p.x+p.w)-fx,oT=(fy+fh)-p.y,oB=(p.y+p.h)-fy;
    if(Math.min(oT,oB)<=Math.min(oL,oR)){
      if(oT<oB&&f.vy>=0){f.y=p.y-.1;f.vy=0;f.onGnd=true;if(p.t==='lava')doHit(f,f,2,false,0);}
      else if(oT>=oB&&f.vy<0){f.y=p.y+p.h+fh+.1;f.vy=0;}
    }else if(p.t==='wall'){
      if(oL<oR){f.x=p.x-fw/2-.1;f.onWall=-1;f.wSide=-1;}
      else{f.x=p.x+p.w+fw/2+.1;f.onWall=1;f.wSide=1;}
      f.vx=0;
    }
  }
  if(f.onGnd&&curMap&&curMap.ice)f.vx*=.988;
}

function updRD(f){
  var rd=f.rd,st=f.hFlash>0?.06:.22,da=.75;
  rd.spV+=(f.vx*.06-rd.sp)*st;rd.spV*=da;rd.sp+=rd.spV;
  rd.hdV+=(f.vx*.04-rd.hd)*st;rd.hdV*=da;rd.hd+=rd.hdV;
  var imp=Math.hypot(f.vx-f.lvx,f.vy-f.lvy);
  if(imp>3&&f.hFlash>0){rd.spV+=(f.vy-f.lvy)*.08;rd.hdV+=(f.vy-f.lvy)*.1;rd.lAV+=(f.vy-f.lvy)*.12;rd.rAV+=(f.vy-f.lvy)*.12;}
  var ls=f.hFlash>0?.04:.18;
  ['lA','rA','lL','rL'].forEach(function(k){rd[k+'V']+=(0-rd[k])*ls;rd[k+'V']*=.72;rd[k]+=rd[k+'V'];rd[k]=Math.max(-.7,Math.min(.7,rd[k]));});
  f.lvx=f.vx;f.lvy=f.vy;
}

function doHit(atk,vic,dmg,isK,power){
  if(vic===atk){vic.hp=Math.max(0,vic.hp-dmg);if(vic.hp<=0)vic.dead=true;return false;}
  if(vic.hFlash>0)return false;
  if(CFG.gameMode==='sudden')dmg=999;
  vic.hp=Math.max(0,vic.hp-dmg);
  vic.vx=atk.dir*(isK?10:6)*(.8+Math.random()*.4);
  vic.vy=-(isK?8:4.5)*(.8+Math.random()*.4);
  vic.hFlash=22;
  vic.rd.spV+=atk.dir*(isK?.5:.3);
  vic.rd.hdV+=atk.dir*(isK?.6:.35);
  vic.hStop=Math.max(vic.hStop,isK?5:3);
  var pw=power||1;
  applyShake(isK?5*pw:3*pw);
  var hx=vic.x+atk.dir*22,hy=vic.y-42;
  emitBurst(hx,hy,isK?'#ffe066':'#ff8888',isK?pw*4+6:pw*2+4);
  emit(hx,hy,vic.col,8,5,.25,.5);
  if(navigator.vibrate)navigator.vibrate(isK?[40,20,40]:20);
  return true;
}

function phys(f){
  if(f.dead){f.vy+=GRAV*.5;f.x+=f.vx;f.y+=f.vy;f.vx*=.98;return;}
  if(f.hStop>0){f.hStop--;return;}
  var grav=GRAV;
  if(f.onWall!==0&&f.vy>0&&!f.onGnd)grav=WSG;
  f.vy=Math.min(f.vy+grav,22);f.x+=f.vx;f.y+=f.vy;
  f.vx*=f.onGnd?FG:FA;
  resolveCol(f);updRD(f);
  if(f.onGnd){f.canDj=true;f.coy=8;if(Math.abs(f.lvy-f.vy)>5){emit(f.x,f.y,'rgba(255,255,255,.3)',4,2,.3,.3);}}
  else if(f.coy>0)f.coy--;
  if(f.pF>0)f.pF--;if(f.pCD>0)f.pCD--;
  if(f.kF>0)f.kF--;if(f.kCD>0)f.kCD--;
  if(f.hFlash>0)f.hFlash--;
  // combo timers
  if(f.combo.timer>0){f.combo.timer--;if(f.combo.timer===0)resetCombo(f);}
  if(f.comboCd>0)f.comboCd--;
  if(Math.abs(f.vx)>.4&&f.onGnd)f.runT+=Math.abs(f.vx)*.14;
  if(f.hp<=0)f.dead=true;
  f.y=Math.min(f.y,GH+200);
}

function doJump(f){
  if(f.coy>0||f.onGnd){f.vy=VJ;f.coy=0;f.onGnd=false;emit(f.x,f.y,'#ffffff',8,3.5,.35,.4);SFX.jump();
    // track jump during combo
    if(f.combo.count>=2)f.combo.jumpedMid=true;
  }
  else if(f.onWall!==0&&!f.onGnd){f.vx=-f.wSide*WJX;f.vy=WJY;f.dir=-f.wSide;f.onWall=0;emit(f.x,f.y-20,f.col,10,4,.3,.5);SFX.jump();}
  else if(f.canDj){f.vy=VDJ;f.canDj=false;emit(f.x,f.y,f.col,12,4.5,.28,.6);applyShake(2);SFX.djump();}
}

// ── JOYSTICK STATE ──
var JS={dx:0,dy:0,active:false};

function inputFromJoystick(){
  if(!P||P.dead||P.hStop>0)return;
  if(JS.active&&Math.abs(JS.dx)>.15){
    var dir=JS.dx>0?1:-1;
    P.vx+=dir*RACC;P.vx=Math.max(-RMAX,Math.min(RMAX,P.vx));P.dir=dir;
  }
}

// ── NPC AI WITH COMBO ──
var DIFFS=[null,{ai:24,ki:40,r:.45},{ai:16,ki:28,r:.75},{ai:10,ki:18,r:.96}];
function npcAI(){
  if(CFG.players>=2||!N||N.dead||N.hStop>0)return;
  nT++;nJT--;nThink--;nComboT--;
  var dp=DIFFS[CFG.diff];
  var dx=P.x-N.x,adx=Math.abs(dx);
  N.dir=dx>0?1:-1;
  if(Math.random()<dp.r){
    if(adx>70){N.vx+=N.dir*1.8;N.vx=Math.max(-RMAX,Math.min(RMAX,N.vx));}
    else if(adx<45)N.vx-=N.dir*1.4;
  }
  // CPU uses combo system
  if(adx<80&&N.comboCd<=0&&nComboT<=0){
    triggerAttack(N,1);
    nComboT=20;
  }
  if(N.weapon&&adx<110&&nT%22===0)useWeapon(N,1);
  if(nJT<=0&&(N.onGnd||N.coy>0)&&(adx>100||P.y<N.y-60)){doJump(N);nJT=50;}
  if(N.onWall!==0&&!N.onGnd&&nThink<=0){doJump(N);nThink=20;}
  if(N.x<35&&N.onGnd)N.vx+=3;
  if(N.x>GW-35&&N.onGnd)N.vx-=3;
}

// ════════════════════════════════════════════
// IK + DRAW
// ════════════════════════════════════════════
function IK(ox,oy,tx,ty,L1,L2,col,lw,flip){
  var dd=Math.min(Math.hypot(tx-ox,ty-oy),L1+L2-.5);
  var a0=Math.atan2(ty-oy,tx-ox);
  var c2v=Math.max(-1,Math.min(1,(L1*L1+dd*dd-L2*L2)/(2*L1*dd)));
  var a2=Math.acos(c2v)*(flip===undefined?1:flip);
  var kx=ox+Math.cos(a0+a2)*L1,ky=oy+Math.sin(a0+a2)*L1;
  cx.strokeStyle=col;cx.lineWidth=lw;cx.lineCap='round';
  cx.beginPath();cx.moveTo(ox,oy);cx.lineTo(kx,ky);cx.lineTo(tx,ty);cx.stroke();
  cx.beginPath();cx.arc(kx,ky,lw*.5,0,Math.PI*2);cx.fillStyle=col;cx.fill();
}

function drawFighter(f){
  if(!f||(f.dead&&f.y>GH+100))return;
  cx.save();
  if(f.hFlash>0)cx.globalAlpha=.35+.65*Math.abs(Math.sin(frame*.55));
  var col=f.col,lw=2.8,rd=f.rd;
  var moving=Math.abs(f.vx)>.6&&f.onGnd,air=!f.onGnd,t=f.runT;
  var pF=f.pF,kF=f.kF,pPh=pF>0?pF/16:0,kPh=kF>0?kF/18:0;
  var ws=f.onWall!==0&&air&&f.vy>0;
  var rX=f.x,rY=f.y,hpX=rX,hpY=rY-36,spLen=28;
  var spA=rd.sp,hdA=rd.hd;
  var spEX=hpX+Math.sin(spA)*spLen,spEY=hpY-Math.cos(spA)*spLen;
  var nkX=spEX+Math.sin(spA+hdA)*8,nkY=spEY-Math.cos(spA+hdA)*8;
  var hR=10,hX=nkX+Math.sin(spA+hdA)*hR,hY=nkY-Math.cos(spA+hdA)*hR;
  // Glow based on combo
  if(f.combo.count>0){
    cx.save();
    var gc=f.combo.count===1?'rgba(255,200,0,.15)':f.combo.count===2?'rgba(255,100,0,.25)':'rgba(255,30,0,.4)';
    var gr=cx.createRadialGradient(f.x,f.y-44,0,f.x,f.y-44,40);
    gr.addColorStop(0,gc);gr.addColorStop(1,'rgba(0,0,0,0)');
    cx.fillStyle=gr;cx.beginPath();cx.arc(f.x,f.y-44,40,0,Math.PI*2);cx.fill();
    cx.restore();
  }
  cx.strokeStyle=col;cx.fillStyle=col;cx.lineWidth=lw;cx.lineCap='round';
  cx.beginPath();cx.moveTo(hpX,hpY);cx.lineTo(spEX,spEY);cx.stroke();
  cx.beginPath();cx.arc(hX,hY,hR,0,Math.PI*2);cx.fill();
  // eyes
  cx.fillStyle='rgba(0,0,0,.7)';
  cx.beginPath();cx.arc(hX+f.dir*4,hY-1,2,0,Math.PI*2);cx.fill();
  // weapon
  if(f.weapon){cx.font='12px serif';cx.textAlign='center';cx.globalAlpha=Math.min(1,(cx.globalAlpha||1)+.3);cx.fillStyle='#fff';cx.fillText(f.weapon.icon,hX+f.dir*15,hY-15);}
  var L1=20,L2=18;
  if(kF>0){
    var kE=Math.sin((1-kPh)*Math.PI),kd=f.dir;
    var tKX=hpX+kd*52*kE,tKY=hpY+22-kE*28;
    IK(hpX,hpY,tKX,tKY,L1,L2,col,lw,kd);IK(hpX,hpY,hpX-kd*10,rY-2,L1,L2,col,lw,-1);
    if(kE>.55){var ke2=(kE-.55)/.45;cx.save();cx.strokeStyle='rgba(255,220,50,'+ke2+')';cx.lineWidth=3.5;cx.beginPath();cx.arc(tKX,tKY,ke2*14,0,Math.PI*2);cx.stroke();cx.restore();}
  }else if(ws){IK(hpX,hpY,hpX-f.wSide*14,rY-6,L1,L2,col,lw,f.wSide);IK(hpX,hpY,hpX+f.wSide*6,rY-2,L1,L2,col,lw,-f.wSide);}
  else if(air){var yf=Math.max(-1,Math.min(1,f.vy/15));IK(hpX,hpY,hpX+f.dir*14+rd.lL*8,rY-4+yf*12,L1,L2,col,lw,1);IK(hpX,hpY,hpX-f.dir*10+rd.rL*8,rY-2+yf*8,L1,L2,col,lw,-1);}
  else if(moving){var s=Math.sin(t),c2=Math.cos(t),kA=Math.min(Math.abs(f.vx)/RMAX,1),sw=22*kA;IK(hpX,hpY,hpX+s*sw+rd.lL*6,rY-3+Math.max(0,-c2)*10,L1,L2,col,lw,1);IK(hpX,hpY,hpX-s*sw+rd.rL*6,rY-3+Math.max(0,c2)*10,L1,L2,col,lw,-1);}
  else{IK(hpX,hpY,hpX+f.dir*10,rY-2,L1,L2,col,lw,1);IK(hpX,hpY,hpX-f.dir*8,rY-2,L1,L2,col,lw,-1);}
  var AL1=17,AL2=15,sX2=spEX,sY2=spEY+5;
  if(pF>0){var pE=Math.sin((1-pPh)*Math.PI),pAX=sX2+f.dir*40*pE+rd.lA*5,pAY=sY2-10*pE+rd.lAV*3;IK(sX2,sY2,pAX,pAY,AL1,AL2,col,lw,-f.dir);IK(sX2,sY2,sX2-f.dir*12+rd.rA*5,sY2+18,AL1,AL2,col,lw,f.dir);if(pE>.5){var pe2=(pE-.5)*2;cx.save();cx.strokeStyle='rgba(255,180,60,'+pe2+')';cx.lineWidth=2.5;cx.beginPath();cx.arc(pAX,pAY,pe2*11,0,Math.PI*2);cx.stroke();cx.restore();}}
  else if(ws){IK(sX2,sY2,sX2+f.wSide*22,sY2-8,AL1,AL2,col,lw,-f.wSide);IK(sX2,sY2,sX2-f.wSide*8,sY2+14,AL1,AL2,col,lw,f.wSide);}
  else if(air){var yfa=Math.max(-1,Math.min(1,f.vy/14));IK(sX2,sY2,sX2+f.dir*16+rd.lA*8,sY2+10-yfa*14,AL1,AL2,col,lw,-1);IK(sX2,sY2,sX2-f.dir*12+rd.rA*8,sY2+14+yfa*10,AL1,AL2,col,lw,1);}
  else if(moving){var sm=Math.sin(t+Math.PI),c2m=Math.cos(t+Math.PI),kAm=Math.min(Math.abs(f.vx)/RMAX,1);IK(sX2,sY2,sX2+sm*16*kAm+rd.lA*6,sY2+18+c2m*5,AL1,AL2,col,lw,-1);IK(sX2,sY2,sX2-sm*16*kAm+rd.rA*6,sY2+18-c2m*5,AL1,AL2,col,lw,1);}
  else{IK(sX2,sY2,sX2+f.dir*18,sY2+16,AL1,AL2,col,lw,-1);IK(sX2,sY2,sX2-f.dir*14,sY2+16,AL1,AL2,col,lw,1);}
  if(ws&&frame%4===0)emit(f.x,f.y-20,f.col,3,2,.2,.3);
  if(moving&&frame%3===0)parts.push({x:f.x,y:f.y,vx:(Math.random()-.5)*.6,vy:-.4,life:.3,col:f.col+'33',g:.04,r:2});
  cx.restore();
}

function drawBG(){
  if(!curMap)return;
  var m=curMap;
  cx.save();cx.translate(shX,shY);
  cx.fillStyle=m.bg;cx.fillRect(-10,-10,GW+20,GH+20);
  // stars
  var sx=m.stars.x,sy=m.stars.y;
  for(var i=0;i<sx.length;i++){var br=.2+(i%3)*.12+.08*Math.sin(frame*.03+i);cx.fillStyle='rgba(255,255,255,'+br+')';cx.beginPath();cx.arc(sx[i],sy[i],i%4===0?1.5:1,0,Math.PI*2);cx.fill();}
  // lava
  if(m.lava&&frame%22===0)emit(80+Math.random()*(GW-160),343,'#ff4400',3,2,.15,.5);
  // ice snow
  if(m.ice&&frame%7===0&&CFG.particles)parts.push({x:Math.random()*GW,y:0,vx:(Math.random()-.5)*.5,vy:.8+Math.random()*.6,life:4,col:'rgba(200,230,255,.4)',g:.01,r:1.5});
  // platforms
  PLATS.forEach(function(p){
    if(p.t==='lava'){
      var lg=cx.createLinearGradient(0,p.y,0,p.y+p.h);lg.addColorStop(0,'#ff4400');lg.addColorStop(1,'#aa0000');
      cx.fillStyle=lg;cx.fillRect(p.x,p.y,p.w,p.h);
      cx.strokeStyle='rgba(255,180,0,'+(.6+.4*Math.sin(frame*.1))+')';cx.lineWidth=2;
      cx.beginPath();cx.moveTo(p.x,p.y);cx.lineTo(p.x+p.w,p.y);cx.stroke();
    }else if(p.t==='ground'||p.t==='ice-ground'){
      cx.fillStyle=m.gc;cx.fillRect(p.x,p.y,p.w,p.h);
      cx.strokeStyle=m.ge;cx.lineWidth=2.5;
      cx.beginPath();cx.moveTo(p.x,p.y);cx.lineTo(p.x+p.w,p.y);cx.stroke();
    }else if(p.t==='plat'||p.t==='ice-plat'||p.t==='moving'){
      cx.fillStyle=p.t==='ice-plat'?'#0a2040':p.t==='moving'?'#1a1240':'#161640';
      cx.fillRect(p.x,p.y,p.w,p.h);
      var ec=p.t==='ice-plat'?'rgba(100,200,255,.8)':p.t==='moving'?'rgba(180,120,255,.8)':'rgba(83,74,183,.7)';
      cx.strokeStyle=ec;cx.lineWidth=1.5;
      cx.beginPath();cx.moveTo(p.x,p.y);cx.lineTo(p.x+p.w,p.y);cx.stroke();
    }else if(p.t==='wall'){
      cx.fillStyle=m.gc;cx.fillRect(p.x,p.y,p.w,p.h);
    }
  });
  // weapon drops
  wDrops.forEach(function(w){
    var pulse=.85+.15*Math.sin(frame*.1);
    cx.globalAlpha=pulse;
    cx.font='17px serif';cx.textAlign='center';cx.fillText(w.t.icon,w.x,w.y+4);
    cx.globalAlpha=(.2+.1*Math.sin(frame*.1));
    cx.fillStyle=w.t.col;cx.beginPath();cx.arc(w.x,w.y-2,12,0,Math.PI*2);cx.fill();
    cx.globalAlpha=1;
  });
  // bullets
  bullets.forEach(function(b){
    cx.fillStyle=b.col;cx.beginPath();cx.arc(b.x,b.y,3,0,Math.PI*2);cx.fill();
    cx.fillStyle='rgba(255,200,50,.3)';cx.beginPath();cx.arc(b.x-b.vx*.6,b.y-b.vy*.6,2,0,Math.PI*2);cx.fill();
  });
  // explosions
  exps.forEach(function(e){
    var prog=1-e.life/20;
    cx.globalAlpha=(1-prog)*.8;
    var eg=cx.createRadialGradient(e.x,e.y,0,e.x,e.y,e.r*prog);
    eg.addColorStop(0,'#fff');eg.addColorStop(.3,'#ffaa00');eg.addColorStop(1,'rgba(255,50,0,0)');
    cx.fillStyle=eg;cx.beginPath();cx.arc(e.x,e.y,e.r*prog,0,Math.PI*2);cx.fill();
    cx.globalAlpha=1;
  });
  cx.restore();
}

function drawParts(){
  cx.save();cx.translate(shX,shY);
  parts=parts.filter(function(p){return p.life>0;});
  parts.forEach(function(p){
    cx.globalAlpha=Math.min(p.life,1)*.9;cx.fillStyle=p.col;
    cx.beginPath();cx.arc(p.x,p.y,Math.max(.1,p.r*Math.min(p.life,1)),0,Math.PI*2);cx.fill();
    p.x+=p.vx;p.y+=p.vy;p.vy+=p.g;p.life-=.035+Math.random()*.02;
  });
  cx.globalAlpha=1;cx.restore();
}

// Cooldown ring on attack button
var cdCanvas=document.getElementById('cd-overlay');
var cdCtx=cdCanvas.getContext('2d');
cdCanvas.width=80;cdCanvas.height=80;
function drawCdRing(){
  if(!P)return;
  cdCtx.clearRect(0,0,80,80);
  if(P.comboCd>0){
    var frac=1-P.comboCd/COMBO_CD_FRAMES;
    cdCtx.strokeStyle='rgba(255,255,100,.6)';
    cdCtx.lineWidth=4;
    cdCtx.beginPath();
    cdCtx.arc(40,40,36,-Math.PI/2,-Math.PI/2+frac*Math.PI*2);
    cdCtx.stroke();
    document.getElementById('cd-label').textContent=Math.ceil(P.comboCd/60*10)/10+'s';
  }else{
    document.getElementById('cd-label').textContent='';
  }
}

function drawHUD(){
  if(!P||!N)return;
  document.getElementById('h1').style.width=Math.max(0,P.hp/P.maxHp*100)+'%';
  document.getElementById('h2').style.width=Math.max(0,N.hp/N.maxHp*100)+'%';
  document.getElementById('sc1').textContent=scores[0];
  document.getElementById('sc2').textContent=scores[1];
  if(CFG.gameMode==='timed'){
    var s=Math.ceil(gameTimer/60);
    var td=document.getElementById('timer-d');
    td.textContent='⏱ '+s+'s';td.style.color=s<=10?'#ff4444':'#ffaa44';
  }
  // weapon hint
  var nearWep=false;
  wDrops.forEach(function(w){if(P&&Math.abs(P.x-w.x)<60&&Math.abs(P.y-w.y)<60)nearWep=true;});
  document.getElementById('wep-hint').className=nearWep&&!P.weapon?'show':'';
  drawCdRing();
  // attack icon based on combo
  if(P){
    var c=P.combo.count;
    document.getElementById('atk-icon').textContent=c===0?'👊':c===1?'✊':c===2?'💥':'🦵';
    document.getElementById('atk-label').textContent=c===0?'ATACAR':c===1?'×2':c===2?'×3 ó ✈️':'COMBO!';
  }
}

function announce(txt,sub,dur){
  var el=document.getElementById('ann');
  document.getElementById('ann-text').textContent=txt;
  document.getElementById('ann-sub').textContent=sub||'';
  el.classList.add('show');
  clearTimeout(annTimeout);
  annTimeout=setTimeout(function(){el.classList.remove('show');},dur||2000);
}

function addKF(msg){
  var kf=document.getElementById('kf');
  var el=document.createElement('div');el.className='kfe';el.textContent=msg;
  kf.appendChild(el);setTimeout(function(){if(el.parentNode)el.parentNode.removeChild(el);},3000);
}

// ════════════════════════════════════════════
// ROUND
// ════════════════════════════════════════════
function initRound(){
  pickMap();resize();
  var mp=curMap;
  P=mkF(mp.p1.x,'#ff4466',1);
  N=mkF(mp.p2.x,'#33aaff',-1);
  if(CFG.gameMode==='sudden'){P.maxHp=1;P.hp=1;N.maxHp=1;N.hp=1;}
  if(CFG.gameMode==='timed'){gameTimer=60*60;document.getElementById('timer-d').style.display='block';}
  else document.getElementById('timer-d').style.display='none';
  parts=[];frame=0;over=null;
  wDrops=[];bullets=[];exps=[];wSpawnT=200;
  nT=0;nJT=0;nThink=0;nComboT=0;
  jPressed=false;jPrev=false;keys={};
  running=false;
  document.getElementById('w1i').textContent='';
  document.getElementById('w2i').textContent='';
  document.getElementById('rnd-lbl').textContent=mp.name+' · R'+curRound;
  document.getElementById('ov').style.display='none';
  updateComboHUD(P,0);updateComboHUD(N,1);
  SFX.roundStart();
  var cd=3;
  announce('RONDA '+curRound,mp.name,1100);
  var itv=setInterval(function(){
    cd--;
    if(cd>0){SFX.countdown();announce(String(cd),'',900);}
    else{clearInterval(itv);announce('¡PELEA!','',700);SFX.go();running=true;}
  },1000);
}

function showEnd(msg,p1win){
  running=false;
  if(p1win===true)scores[0]++;
  else if(p1win===false)scores[1]++;
  SFX.death();
  var need=Math.ceil(CFG.rounds/2);
  var mOver=scores[0]>=need||scores[1]>=need||CFG.rounds===1;
  if(mOver){
    var winner='EMPATE';
    if(scores[0]>scores[1])winner='¡P1 GANA!';
    else if(scores[1]>scores[0])winner=CFG.players===2?'¡P2 GANA!':'¡CPU GANA!';
    SFX.win();
    setTimeout(function(){
      document.getElementById('ov-title').textContent=winner;
      document.getElementById('ov-sub').textContent='Resultado: '+scores[0]+' - '+scores[1];
      document.getElementById('fs1').textContent=scores[0];
      document.getElementById('fs2').textContent=scores[1];
      document.getElementById('ov').style.display='flex';
    },800);
  }else{
    addKF(msg);announce(msg,'',1400);curRound++;
    setTimeout(initRound,2000);
  }
}

// ════════════════════════════════════════════
// MAIN LOOP
// ════════════════════════════════════════════
function loop(){
  frame++;
  if(shD>0){shX=(Math.random()-.5)*shD*2;shY=(Math.random()-.5)*shD*2;shD=Math.max(0,shD-.7);}
  else{shX=0;shY=0;}
  cx.clearRect(0,0,GW,GH);
  drawBG();
  if(running&&P&&N){
    inputFromJoystick();
    // P2 keyboard movement
    if(CFG.players>=2){
      if(keys['ArrowLeft']){N.vx-=RACC;N.vx=Math.max(-RMAX,N.vx);N.dir=-1;}
      else if(keys['ArrowRight']){N.vx+=RACC;N.vx=Math.min(RMAX,N.vx);N.dir=1;}
    }
    // jump
    var jNow=keys['Space']||keys['KeyW'];
    if(jNow&&!jPrev)doJump(P);jPrev=jNow;
    var j2=keys['ArrowUp'];
    if(j2&&CFG.players>=2)doJump(N);
    // P2 attack
    if(keys['ShiftRight']&&CFG.players>=2)triggerAttack(N,1);
    // Moving plats
    movPlats.forEach(function(p){
      p.x+=p.dx;
      if(Math.abs(p.x-p.ox)>p.range)p.dx*=-1;
      [P,N].forEach(function(f){if(f.onGnd&&f.y<=p.y+3&&f.x>=p.x&&f.x<=p.x+p.w)f.x+=p.dx;});
    });
    npcAI();phys(P);phys(N);
    updateWeapons();
    wSpawnT--;
    if(wSpawnT<=0&&CFG.weapons){spawnWeapon();wSpawnT=260+Math.floor(Math.random()*180);}
    if(CFG.gameMode==='timed'){
      gameTimer--;
      if(gameTimer<=0){
        if(P.hp>N.hp)showEnd('¡P1 GANA RONDA!',true);
        else if(N.hp>P.hp)showEnd((CFG.players===2?'¡P2':'¡CPU')+' GANA!',false);
        else showEnd('EMPATE',null);
      }
    }
    drawHUD();
    if(!over){
      if(P.dead&&N.dead){over=1;setTimeout(function(){showEnd('EMPATE',null);},600);}
      else if(P.dead){over=1;setTimeout(function(){showEnd(CFG.players===2?'¡P2 GANA!':'¡CPU GANA!',false);},600);}
      else if(N.dead){over=1;setTimeout(function(){showEnd('¡P1 GANA!',true);},600);}
    }
  }
  drawParts();
  if(P)drawFighter(P);
  if(N)drawFighter(N);
  requestAnimationFrame(loop);
}

// ════════════════════════════════════════════
// JOYSTICK INPUT (PREMIUM)
// ════════════════════════════════════════════
var jWrap=document.getElementById('joystick-wrap');
var jKnob=document.getElementById('joystick-knob');
var jBase=document.getElementById('joystick-base');
var jActiveId=null;
var jCenter={x:0,y:0};
var JR=48; // max radius

function getJCenter(){
  var r=jBase.getBoundingClientRect();
  return{x:r.left+r.width/2,y:r.top+r.height/2};
}
function updateKnob(cx2,cy2){
  var jc=getJCenter();
  var dx2=cx2-jc.x,dy2=cy2-jc.y;
  var dist=Math.hypot(dx2,dy2);
  var capped=Math.min(dist,JR);
  var angle=Math.atan2(dy2,dx2);
  var kx=Math.cos(angle)*capped,ky=Math.sin(angle)*capped;
  jKnob.style.transform='translate(calc(-50% + '+kx+'px), calc(-50% + '+ky+'px))';
  JS.dx=dx2/Math.max(dist,1)*(Math.min(dist,JR)/JR);
  JS.dy=dy2/Math.max(dist,1)*(Math.min(dist,JR)/JR);
  // Visual feedback
  var pct=Math.min(dist/JR,1);
  jKnob.style.boxShadow='0 4px 16px rgba(122,63,255,'+(0.3+pct*.5)+'),0 0 '+(8+pct*12)+'px rgba(200,100,255,'+(0.2+pct*.4)+'),inset 0 2px 4px rgba(255,255,255,.2)';
  // Jump detection (strong upward flick)
  if(JS.dy<-0.7&&dist>JR*.6&&running&&P&&!P.dead){doJump(P);}
}
function resetKnob(){
  jKnob.style.transform='translate(-50%,-50%)';
  jKnob.style.boxShadow='0 4px 16px rgba(122,63,255,.5),0 0 8px rgba(200,100,255,.3),inset 0 2px 4px rgba(255,255,255,.2)';
  JS.dx=0;JS.dy=0;JS.active=false;jActiveId=null;
}
jWrap.addEventListener('pointerdown',function(e){
  e.preventDefault();
  if(jActiveId!==null)return;
  jActiveId=e.pointerId;JS.active=true;
  updateKnob(e.clientX,e.clientY);
});
jWrap.addEventListener('pointermove',function(e){
  e.preventDefault();
  if(e.pointerId!==jActiveId)return;
  updateKnob(e.clientX,e.clientY);
});
jWrap.addEventListener('pointerup',function(e){e.preventDefault();if(e.pointerId===jActiveId)resetKnob();});
jWrap.addEventListener('pointercancel',function(e){if(e.pointerId===jActiveId)resetKnob();});
jWrap.addEventListener('contextmenu',function(e){e.preventDefault();});

// ════════════════════════════════════════════
// ATTACK BUTTON
// ════════════════════════════════════════════
var atkBtn=document.getElementById('atk-btn');
atkBtn.addEventListener('pointerdown',function(e){
  e.preventDefault();
  if(!running||!P||P.dead)return;
  // pick up weapon if near
  var nearWep=false;
  for(var i=0;i<wDrops.length;i++){
    var w=wDrops[i];
    if(Math.abs(P.x-w.x)<36&&Math.abs(P.y-w.y)<50){nearWep=true;break;}
  }
  if(P.weapon){useWeapon(P,0);}
  else{triggerAttack(P,0);}
});
atkBtn.addEventListener('contextmenu',function(e){e.preventDefault();});

// ════════════════════════════════════════════
// JUMP BUTTON
// ════════════════════════════════════════════
var jumpBtn=document.getElementById('jump-btn');
jumpBtn.addEventListener('pointerdown',function(e){
  e.preventDefault();
  if(!running||!P||P.dead)return;
  doJump(P);
  // track for combo
  if(P.combo.count>=2)P.combo.jumpedMid=true;
  jumpBtn.classList.add('pressed');
});
jumpBtn.addEventListener('pointerup',function(){jumpBtn.classList.remove('pressed');});
jumpBtn.addEventListener('pointercancel',function(){jumpBtn.classList.remove('pressed');});
jumpBtn.addEventListener('contextmenu',function(e){e.preventDefault();});

// ════════════════════════════════════════════
// KEYBOARD FALLBACK
// ════════════════════════════════════════════
document.addEventListener('keydown',function(e){
  keys[e.code]=true;
  var mv=['KeyW','KeyA','KeyD','Space','ArrowUp','ArrowLeft','ArrowRight','ShiftRight','KeyE'];
  if(mv.indexOf(e.code)>=0)e.preventDefault();
  if(!running)return;
  if((e.code==='KeyA')&&P){P.vx-=RACC;if(P.vx<-RMAX)P.vx=-RMAX;P.dir=-1;}
  if((e.code==='KeyD')&&P){P.vx+=RACC;if(P.vx>RMAX)P.vx=RMAX;P.dir=1;}
  if(e.code==='KeyE'&&P&&!P.dead){
    if(P.weapon)useWeapon(P,0);else triggerAttack(P,0);
  }
  if(e.code==='ShiftRight'&&N&&!N.dead&&CFG.players>=2)triggerAttack(N,1);
});
document.addEventListener('keyup',function(e){keys[e.code]=false;});

// orientation
if(screen.orientation&&screen.orientation.lock){try{screen.orientation.lock('landscape');}catch(e){}}

loop();

})();
</script>
</body>
</html>
