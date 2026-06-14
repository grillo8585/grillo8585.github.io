<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>Aventura de Plataformas</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html, body {
    width: 100%;
    min-height: 100vh;
    min-height: 100dvh;
    background: #1a1a2e;
    font-family: 'Trebuchet MS', 'Segoe UI', system-ui, sans-serif;
    color: #fff;
    -webkit-tap-highlight-color: transparent;
  }
  body {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 12px;
  }
  #wrap {
    position: relative;
    width: 100%;
    max-width: 900px;
    box-shadow: 0 20px 60px rgba(0,0,0,0.6);
    border-radius: 12px;
    overflow: hidden;
  }
  /* Mantiene la relación 16:9 en TODOS los navegadores, incluido Safari/iOS */
  #wrap::before {
    content: "";
    display: block;
    padding-bottom: 56.25%; /* 9 / 16 */
  }
  canvas {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    image-rendering: -webkit-optimize-contrast; /* Safari */
    image-rendering: pixelated;
  }
  /* HUD */
  #hud {
    position: absolute;
    top: 0; left: 0; right: 0;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 12px 18px;
    font-weight: bold;
    font-size: clamp(14px, 2.4vw, 20px);
    text-shadow: 2px 2px 0 rgba(0,0,0,0.45);
    pointer-events: none;
    letter-spacing: 1px;
  }
  .hud-item { display: flex; align-items: center; gap: 6px; }
  .coin-dot {
    width: 16px; height: 16px; border-radius: 50%;
    background: radial-gradient(circle at 35% 30%, #ffe680, #f5a623);
    box-shadow: inset -2px -2px 0 rgba(0,0,0,0.2);
  }
  .heart { color: #ff5577; font-size: 1.1em; }

  /* Overlays */
  .overlay {
    position: absolute; inset: 0;
    display: flex; flex-direction: column;
    align-items: center; justify-content: center;
    text-align: center;
    background: rgba(15, 15, 35, 0.82);
    -webkit-backdrop-filter: blur(3px);
    backdrop-filter: blur(3px);
    padding: 20px;
    z-index: 10;
  }
  .overlay.hidden { display: none; }
  .overlay h1 {
    font-size: clamp(28px, 6vw, 52px);
    margin-bottom: 8px;
    letter-spacing: 2px;
  }
  .overlay p { font-size: clamp(14px, 2.6vw, 19px); opacity: 0.85; margin-bottom: 22px; max-width: 520px; line-height: 1.5; }
  .keys { display: flex; gap: 18px; margin-bottom: 26px; flex-wrap: wrap; justify-content: center; }
  .keycap {
    display: flex; flex-direction: column; align-items: center; gap: 6px;
    font-size: clamp(11px, 2vw, 14px); opacity: 0.9;
  }
  .keycap b {
    display: inline-flex; align-items: center; justify-content: center;
    min-width: 44px; height: 44px; padding: 0 12px;
    background: #2b2b50; border-radius: 8px;
    border-bottom: 4px solid #16162e;
    font-size: clamp(14px, 2.4vw, 18px);
  }
  button {
    font-family: inherit; font-weight: bold;
    font-size: clamp(15px, 2.6vw, 19px);
    color: #1a1a2e;
    background: linear-gradient(#ffd24d, #f5a623);
    border: none; border-radius: 10px;
    padding: 14px 34px; cursor: pointer;
    border-bottom: 5px solid #c97e0e;
    transition: transform .06s, filter .15s;
    letter-spacing: 1px;
  }
  button:hover { filter: brightness(1.06); }
  button:active { transform: translateY(3px); border-bottom-width: 2px; }

  /* Mobile touch controls */
  #touch {
    position: absolute; bottom: 0; left: 0; right: 0;
    display: none; justify-content: space-between;
    padding: 14px; pointer-events: none; z-index: 5;
  }
  .pad { display: flex; gap: 14px; pointer-events: auto; }
  .tbtn {
    width: 72px; height: 72px; border-radius: 50%;
    background: rgba(255,255,255,0.22);
    border: 2px solid rgba(255,255,255,0.45);
    color: #fff; font-size: 30px; font-weight: bold;
    display: flex; align-items: center; justify-content: center;
    user-select: none; backdrop-filter: blur(4px);
    -webkit-user-select: none; -webkit-backdrop-filter: blur(4px);
    touch-action: none;
    -webkit-touch-callout: none;
  }
  .tbtn:active { background: rgba(255,255,255,0.4); transform: scale(0.94); }
  /* Mostrar en cualquier dispositivo táctil (media query + clase por JS) */
  @media (hover: none) and (pointer: coarse) { #touch { display: flex; } }
  body.touch #touch { display: flex; }
</style>
</head>
<body>
<div id="wrap">
  <canvas id="game" width="640" height="360"></canvas>

  <div id="hud">
    <div class="hud-item"><span class="coin-dot"></span><span id="coins">0</span></div>
    <div class="hud-item" id="lives"></div>
  </div>

  <div class="overlay" id="startScreen">
    <h1>⛰️ Aventura</h1>
    <p>Recoge monedas, salta sobre los enemigos y llega a la bandera. ¡No caigas al vacío!</p>
    <div class="keys">
      <div class="keycap"><b>A</b>Izquierda</div>
      <div class="keycap"><b>D</b>Derecha</div>
      <div class="keycap"><b>espacio</b>Saltar</div>
    </div>
    <button id="startBtn">Jugar</button>
  </div>

  <div class="overlay hidden" id="endScreen">
    <h1 id="endTitle">¡Ganaste!</h1>
    <p id="endMsg"></p>
    <button id="restartBtn">Jugar de nuevo</button>
  </div>

  <div id="touch">
    <div class="pad">
      <div class="tbtn" data-key="left">◀</div>
      <div class="tbtn" data-key="right">▶</div>
    </div>
    <div class="pad">
      <div class="tbtn" data-key="jump">▲</div>
    </div>
  </div>
</div>

<script>
const canvas = document.getElementById('game');
const ctx = canvas.getContext('2d');
const W = canvas.width, H = canvas.height;

// ---------- Diseño / paleta ----------
const COLORS = {
  skyTop: '#6ec6ff',
  skyBot: '#bfeaff',
  hillFar: '#9fd98c',
  hillNear: '#7cc265',
  ground: '#6b4a2b',
  groundTop: '#3fa34d',
  brick: '#c8743a',
  brickDark: '#9c5728',
  coin: '#f5a623',
  player: '#e8533f',
  playerDark: '#c23d2c',
  enemy: '#8d5fc0',
  enemyDark: '#6a44a0',
  flag: '#ff4d6d'
};

// ---------- Mundo / nivel ----------
const TILE = 32;
const GRAVITY = 0.6;
const LEVEL_END = 3400;

// Plataformas: {x, y, w, h}
const platforms = [
  // suelo principal con un par de huecos
  {x:0,    y:328, w:640,  h:32},
  {x:704,  y:328, w:560,  h:32},
  {x:1360, y:328, w:720,  h:32},
  {x:2160, y:328, w:480,  h:32},
  {x:2740, y:328, w:760,  h:32},
  // plataformas flotantes
  {x:320,  y:248, w:96,  h:24},
  {x:520,  y:190, w:96,  h:24},
  {x:860,  y:230, w:128, h:24},
  {x:1080, y:180, w:96,  h:24},
  {x:1500, y:240, w:128, h:24},
  {x:1700, y:180, w:96,  h:24},
  {x:1900, y:240, w:96,  h:24},
  {x:2280, y:230, w:128, h:24},
  {x:2900, y:240, w:96,  h:24},
  {x:3080, y:190, w:96,  h:24},
];

// Monedas
const coinDefs = [
  [340,210],[360,210],[540,150],[880,195],[910,195],[1100,145],
  [1180,290],[1220,290],[1520,205],[1720,145],[1920,205],
  [2300,195],[2380,195],[2500,290],[2920,205],[3100,150],[3260,290]
];

// Enemigos {x, y, minX, maxX, dir}
const enemyDefs = [
  {x:760,  minX:710, maxX:1240, },
  {x:1450, minX:1370,maxX:1820, },
  {x:2250, minX:2170,maxX:2620, },
  {x:2820, minX:2750,maxX:3200, },
];

let coins, enemies, player, camX, coinsCollected, lives, state, particles;
let flagRaise = 0;

function reset(full) {
  player = {
    x: 60, y: 250, w: 26, h: 30,
    vx: 0, vy: 0,
    onGround: false, face: 1, walk: 0, dead: false, deadTimer: 0
  };
  camX = 0;
  particles = [];
  flagRaise = 0;
  if (full) { coinsCollected = 0; lives = 3; }
  coins = coinDefs.map(c => ({x:c[0], y:c[1], r:9, got:false, bob:Math.random()*Math.PI*2}));
  enemies = enemyDefs.map(e => ({
    x:e.x, y:296, w:28, h:24, dir:-1,
    minX:e.minX, maxX:e.maxX, dead:false, squish:0
  }));
}

// ---------- Input ----------
const keys = { left:false, right:false, jump:false };
let jumpHeld = false;

window.addEventListener('keydown', e => {
  const k = e.key.toLowerCase();
  if (k === 'a' || k === 'arrowleft') keys.left = true;
  if (k === 'd' || k === 'arrowright') keys.right = true;
  if (k === ' ' || k === 'spacebar' || k === 'arrowup' || k === 'w') {
    keys.jump = true; e.preventDefault();
  }
});
window.addEventListener('keyup', e => {
  const k = e.key.toLowerCase();
  if (k === 'a' || k === 'arrowleft') keys.left = false;
  if (k === 'd' || k === 'arrowright') keys.right = false;
  if (k === ' ' || k === 'spacebar' || k === 'arrowup' || k === 'w') {
    keys.jump = false; jumpHeld = false;
  }
});

// Controles táctiles
// Detecta pantalla táctil (iPhone/iPad incluidos) y muestra los botones
if ('ontouchstart' in window || (navigator.maxTouchPoints || 0) > 0) {
  document.body.classList.add('touch');
}
document.querySelectorAll('.tbtn').forEach(btn => {
  const key = btn.dataset.key;
  const set = v => {
    if (key === 'left') keys.left = v;
    if (key === 'right') keys.right = v;
    if (key === 'jump') { keys.jump = v; if (!v) jumpHeld = false; }
  };
  btn.addEventListener('touchstart', e => { e.preventDefault(); set(true); }, {passive:false});
  btn.addEventListener('touchend',   e => { e.preventDefault(); set(false); }, {passive:false});
  btn.addEventListener('touchcancel',e => { e.preventDefault(); set(false); }, {passive:false});
  btn.addEventListener('mousedown',  () => set(true));
  btn.addEventListener('mouseup',    () => set(false));
  btn.addEventListener('mouseleave', () => set(false));
});

// ---------- Física / lógica ----------
function rectsOverlap(a, b) {
  return a.x < b.x + b.w && a.x + a.w > b.x && a.y < b.y + b.h && a.y + a.h > b.y;
}

function update() {
  if (state !== 'play') return;
  const p = player;

  if (p.dead) {
    p.deadTimer++;
    p.vy += GRAVITY;
    p.y += p.vy;
    if (p.deadTimer > 70) loseLife();
    return;
  }

  // Movimiento horizontal con aceleración y fricción
  const accel = 0.7, maxSpeed = 4.2, friction = 0.8;
  if (keys.left)  { p.vx -= accel; p.face = -1; }
  if (keys.right) { p.vx += accel; p.face = 1; }
  if (!keys.left && !keys.right) p.vx *= friction;
  p.vx = Math.max(-maxSpeed, Math.min(maxSpeed, p.vx));
  if (Math.abs(p.vx) < 0.05) p.vx = 0;

  // Salto (con salto variable según cuánto se mantenga)
  if (keys.jump && p.onGround && !jumpHeld) {
    p.vy = -11.5;
    p.onGround = false;
    jumpHeld = true;
  }
  if (!keys.jump && p.vy < -4) p.vy = -4; // recorta el salto al soltar

  p.vy += GRAVITY;
  if (p.vy > 14) p.vy = 14;

  // Mover en X y resolver colisiones
  p.x += p.vx;
  for (const plat of platforms) {
    if (rectsOverlap(p, plat)) {
      if (p.vx > 0) p.x = plat.x - p.w;
      else if (p.vx < 0) p.x = plat.x + plat.w;
      p.vx = 0;
    }
  }
  if (p.x < 0) { p.x = 0; p.vx = 0; }

  // Mover en Y y resolver colisiones
  p.y += p.vy;
  p.onGround = false;
  for (const plat of platforms) {
    if (rectsOverlap(p, plat)) {
      if (p.vy > 0) { p.y = plat.y - p.h; p.onGround = true; }
      else if (p.vy < 0) p.y = plat.y + plat.h;
      p.vy = 0;
    }
  }

  // Animación de caminar
  if (p.onGround && Math.abs(p.vx) > 0.5) p.walk += 0.25;
  else p.walk = 0;

  // Cámara sigue al jugador
  camX = p.x - W * 0.4;
  camX = Math.max(0, Math.min(camX, LEVEL_END - W + 120));

  // Caída al vacío
  if (p.y > H + 40) { p.dead = true; p.deadTimer = 60; }

  // Monedas
  for (const c of coins) {
    if (!c.got) {
      c.bob += 0.1;
      if (Math.hypot((p.x+p.w/2)-c.x, (p.y+p.h/2)-c.y) < c.r + 16) {
        c.got = true;
        coinsCollected++;
        spawnParticles(c.x, c.y, COLORS.coin, 8);
      }
    }
  }

  // Enemigos
  for (const e of enemies) {
    if (e.dead) { e.squish = Math.max(0, e.squish - 0.06); continue; }
    e.x += e.dir * 1.0;
    if (e.x < e.minX) { e.x = e.minX; e.dir = 1; }
    if (e.x + e.w > e.maxX) { e.x = e.maxX - e.w; e.dir = -1; }

    if (rectsOverlap(p, e)) {
      const stomping = p.vy > 0 && (p.y + p.h) - e.y < 18;
      if (stomping) {
        e.dead = true; e.squish = 1;
        p.vy = -8; // rebote
        coinsCollected++;
        spawnParticles(e.x + e.w/2, e.y, COLORS.enemy, 10);
      } else {
        p.dead = true; p.deadTimer = 0; p.vy = -8;
      }
    }
  }

  // Meta / bandera
  if (p.x + p.w > LEVEL_END + 20) {
    state = 'win';
    win();
  }

  // Partículas
  for (const pt of particles) {
    pt.x += pt.vx; pt.y += pt.vy; pt.vy += 0.25; pt.life--;
  }
  particles = particles.filter(pt => pt.life > 0);

  updateHUD();
}

function spawnParticles(x, y, color, n) {
  for (let i = 0; i < n; i++) {
    particles.push({
      x, y, color,
      vx: (Math.random()-0.5)*4,
      vy: -Math.random()*4 - 1,
      life: 25 + Math.random()*15,
      size: 2 + Math.random()*3
    });
  }
}

function loseLife() {
  lives--;
  if (lives <= 0) { state = 'gameover'; gameOver(); }
  else { reset(false); }
}

// ---------- Dibujo ----------
function drawBackground() {
  const g = ctx.createLinearGradient(0, 0, 0, H);
  g.addColorStop(0, COLORS.skyTop);
  g.addColorStop(1, COLORS.skyBot);
  ctx.fillStyle = g;
  ctx.fillRect(0, 0, W, H);

  // Nubes (parallax suave)
  ctx.fillStyle = 'rgba(255,255,255,0.85)';
  const clouds = [[200,60],[600,90],[1000,50],[1500,80],[2100,60],[2700,90],[3200,55]];
  for (const [cx, cy] of clouds) {
    const x = cx - camX * 0.3;
    cloud(x, cy);
  }

  // Colinas lejanas (parallax)
  ctx.fillStyle = COLORS.hillFar;
  for (let i = -1; i < 8; i++) {
    const x = i*520 - (camX*0.4 % 520);
    hill(x, 300, 260, 120);
  }
  ctx.fillStyle = COLORS.hillNear;
  for (let i = -1; i < 10; i++) {
    const x = i*420 - (camX*0.6 % 420);
    hill(x, 330, 200, 90);
  }
}
function cloud(x, y) {
  ctx.beginPath();
  ctx.arc(x, y, 18, 0, 7); ctx.arc(x+22, y+4, 22, 0, 7);
  ctx.arc(x+48, y, 16, 0, 7); ctx.rect(x-2, y, 52, 18);
  ctx.fill();
}
function hill(x, baseY, w, h) {
  ctx.beginPath();
  ctx.moveTo(x, baseY);
  ctx.quadraticCurveTo(x + w/2, baseY - h, x + w, baseY);
  ctx.fill();
}

function drawPlatforms() {
  for (const plat of platforms) {
    const x = plat.x - camX;
    if (x + plat.w < -20 || x > W + 20) continue;
    if (plat.h >= 32) {
      // suelo: tierra + césped
      ctx.fillStyle = COLORS.ground;
      ctx.fillRect(x, plat.y, plat.w, plat.h + 40);
      ctx.fillStyle = COLORS.groundTop;
      ctx.fillRect(x, plat.y, plat.w, 10);
      // textura puntitos
      ctx.fillStyle = 'rgba(0,0,0,0.08)';
      for (let i = 6; i < plat.w; i += 24)
        ctx.fillRect(x + i, plat.y + 18, 4, 4);
    } else {
      // ladrillo flotante
      ctx.fillStyle = COLORS.brickDark;
      ctx.fillRect(x, plat.y, plat.w, plat.h);
      ctx.fillStyle = COLORS.brick;
      ctx.fillRect(x, plat.y, plat.w, plat.h - 5);
      ctx.fillStyle = 'rgba(0,0,0,0.18)';
      for (let i = 0; i < plat.w; i += 16) ctx.fillRect(x+i, plat.y, 2, plat.h);
      ctx.fillRect(x, plat.y + plat.h/2, plat.w, 2);
    }
  }
}

function drawCoins() {
  for (const c of coins) {
    if (c.got) continue;
    const x = c.x - camX;
    if (x < -20 || x > W + 20) continue;
    const wobble = Math.abs(Math.cos(c.bob)) * c.r + 2;
    const y = c.y;
    ctx.fillStyle = COLORS.coin;
    ctx.beginPath();
    ctx.ellipse(x, y, wobble, c.r, 0, 0, 7);
    ctx.fill();
    ctx.fillStyle = '#ffe680';
    ctx.beginPath();
    ctx.ellipse(x - wobble*0.25, y - 2, wobble*0.35, c.r*0.5, 0, 0, 7);
    ctx.fill();
  }
}

function drawEnemies() {
  for (const e of enemies) {
    const x = e.x - camX;
    if (x < -40 || x > W + 40) continue;
    if (e.dead && e.squish <= 0) continue;
    const sq = e.dead ? e.squish : 1;
    const h = e.h * sq;
    const y = e.y + (e.h - h);
    // cuerpo
    ctx.fillStyle = COLORS.enemyDark;
    ctx.fillRect(x, y+3, e.w, h-3);
    ctx.fillStyle = COLORS.enemy;
    ctx.fillRect(x, y, e.w, h-4);
    if (!e.dead) {
      // ojos
      ctx.fillStyle = '#fff';
      ctx.fillRect(x+5, y+6, 6, 6);
      ctx.fillRect(x+e.w-11, y+6, 6, 6);
      ctx.fillStyle = '#222';
      const look = e.dir < 0 ? 0 : 3;
      ctx.fillRect(x+6+look, y+8, 3, 3);
      ctx.fillRect(x+e.w-10+look, y+8, 3, 3);
      // pies
      ctx.fillStyle = COLORS.enemyDark;
      const f = Math.sin(Date.now()/120) > 0 ? 0 : 4;
      ctx.fillRect(x+2, e.y+e.h-3, 8, 4);
      ctx.fillRect(x+e.w-10, e.y+e.h-3, 8, 4);
    }
  }
}

// ---------- Sprite del personaje (bebé digitalizada) ----------
const babyCv = document.createElement('canvas');
babyCv.width = 48; babyCv.height = 56;
const bx = babyCv.getContext('2d');
const BC = {
  hair:'#241712', hair2:'#3a2419', skin:'#e0a878', skin2:'#ca915f',
  blush:'#ef9aa0', eye:'#241008', white:'#ffffff', mouth:'#9c3b3b',
  tongue:'#e07a86', dress:'#f49ac2', dress2:'#e279ab', ruffle:'#ffc6de',
  gold:'#f5c542', xeye:'#7a3a3a'
};
function bpx(x, y, w, h, color) { bx.fillStyle = color; bx.fillRect(x, y, w, h); }

function drawBabySprite(bob, blink, pose, walkPhase) {
  bx.clearRect(0, 0, 48, 56);
  const cx = 24;
  const y0 = 4 + bob;

  // Pelo
  bpx(cx-12, y0+2, 24, 9, BC.hair);
  bpx(cx-13, y0+5, 26, 7, BC.hair);
  bpx(cx-11, y0+1, 22, 3, BC.hair2);

  // Cabeza
  bpx(cx-11, y0+6, 22, 18, BC.skin);
  bpx(cx-12, y0+9, 24, 12, BC.skin);
  bpx(cx-10, y0+22, 20, 3, BC.skin2);

  // Flequillo
  bpx(cx-12, y0+5, 4, 7, BC.hair);
  bpx(cx+8,  y0+5, 4, 7, BC.hair);
  bpx(cx-9,  y0+5, 18, 3, BC.hair);
  bpx(cx-7,  y0+7, 14, 2, BC.hair2);

  // Ojos
  if (pose === 'dead') {
    bpx(cx-7, y0+12, 4, 4, BC.xeye);
    bpx(cx+3, y0+12, 4, 4, BC.xeye);
    bpx(cx-7, y0+12, 1, 4, BC.eye); bpx(cx-4, y0+12, 1, 4, BC.eye);
    bpx(cx+3, y0+12, 1, 4, BC.eye); bpx(cx+6, y0+12, 1, 4, BC.eye);
  } else if (!blink) {
    bpx(cx-7, y0+12, 4, 5, BC.eye);
    bpx(cx+3, y0+12, 4, 5, BC.eye);
    bpx(cx-6, y0+12, 1, 1, BC.white);
    bpx(cx+4, y0+12, 1, 1, BC.white);
  } else {
    bpx(cx-7, y0+15, 4, 1, BC.eye);
    bpx(cx+3, y0+15, 4, 1, BC.eye);
  }

  // Cejas
  bpx(cx-7, y0+10, 4, 1, BC.hair);
  bpx(cx+3, y0+10, 4, 1, BC.hair);

  // Cachetes
  bpx(cx-10, y0+16, 3, 2, BC.blush);
  bpx(cx+7,  y0+16, 3, 2, BC.blush);

  // Boca / sonrisa
  if (pose === 'dead') {
    bpx(cx-3, y0+20, 6, 2, BC.mouth);
  } else {
    bpx(cx-5, y0+19, 10, 1, BC.mouth);
    bpx(cx-6, y0+19, 1, 2, BC.mouth);
    bpx(cx+5, y0+19, 1, 2, BC.mouth);
    bpx(cx-5, y0+20, 10, 3, BC.mouth);
    bpx(cx-3, y0+21, 6, 2, BC.tongue);
    bpx(cx-4, y0+20, 8, 1, BC.white);
  }

  // Aretes
  bpx(cx-12, y0+17, 1, 1, BC.gold);
  bpx(cx+11, y0+17, 1, 1, BC.gold);

  // Cuello
  bpx(cx-4, y0+24, 8, 3, BC.skin2);

  // Vestido
  const by = y0 + 27;
  bpx(cx-9, by, 18, 4, BC.dress);
  bpx(cx-12, by+1, 3, 8, BC.skin);
  bpx(cx+9,  by+1, 3, 8, BC.skin);
  bpx(cx-12, by+9, 3, 3, BC.skin);
  bpx(cx+9,  by+9, 3, 3, BC.skin);
  bpx(cx-9, by+3, 18, 9, BC.dress);
  bpx(cx-10, by+9, 20, 6, BC.dress);
  bpx(cx-9, by+6, 18, 1, BC.dress2);
  bpx(cx-2, by+4, 4, 7, BC.dress2);
  bpx(cx-11, by+14, 22, 3, BC.ruffle);
  bpx(cx-11, by+16, 22, 2, BC.dress2);
  for (let i = -11; i < 11; i += 4) bpx(cx+i, by+17, 2, 1, BC.ruffle);

  // Piernas
  const ly = by + 18;
  let lL = 0, lR = 0;
  if (pose === 'walk') { lL = Math.round(Math.sin(walkPhase) * 1.5); lR = -lL; }
  else if (pose === 'jump') { lL = -1; lR = -1; }
  bpx(cx-7, ly + Math.max(0,lL), 5, 5, BC.skin);
  bpx(cx+2, ly + Math.max(0,lR), 5, 5, BC.skin);
  bpx(cx-8, ly+4 + Math.max(0,lL), 6, 2, BC.skin2);
  bpx(cx+2, ly+4 + Math.max(0,lR), 6, 2, BC.skin2);
}

let babyTick = 0;

function drawPlayer() {
  const p = player;
  const x = Math.round(p.x - camX);
  babyTick++;

  // sombra
  if (!p.dead) {
    ctx.fillStyle = 'rgba(0,0,0,0.15)';
    ctx.beginPath();
    ctx.ellipse(x + p.w/2, p.y + p.h + 4, p.w/2, 4, 0, 0, 7);
    ctx.fill();
  }

  // Elegir pose y animación
  let pose = 'idle', bob = 0, blink = false;
  if (p.dead) {
    pose = 'dead';
  } else if (!p.onGround) {
    pose = 'jump'; bob = -2;
  } else if (Math.abs(p.vx) > 0.5) {
    pose = 'walk'; bob = Math.abs(Math.sin(p.walk));
  } else {
    pose = 'idle';
    bob = Math.sin(babyTick * 0.06);
    blink = (babyTick % 160) < 8;
  }

  drawBabySprite(Math.round(bob), blink, pose, p.walk);

  // Dibujar el sprite escalado, pies alineados al suelo, volteado según dirección
  const dw = 40, dh = 46;
  const dx = Math.round(x + p.w/2 - dw/2);
  const dy = Math.round(p.y + p.h - 45);

  ctx.save();
  ctx.imageSmoothingEnabled = false;
  ctx.webkitImageSmoothingEnabled = false;
  if (p.face < 0) {
    ctx.translate(dx + dw, dy);
    ctx.scale(-1, 1);
    ctx.drawImage(babyCv, 0, 0, 48, 56, 0, 0, dw, dh);
  } else {
    ctx.drawImage(babyCv, 0, 0, 48, 56, dx, dy, dw, dh);
  }
  ctx.restore();
}

function drawFlag() {
  const x = LEVEL_END - camX;
  if (x < -40 || x > W + 60) return;
  const baseY = 328;
  const top = 120 - flagRaise*60;
  // poste
  ctx.fillStyle = '#cfd8dc';
  ctx.fillRect(x, top, 6, baseY - top);
  ctx.fillStyle = '#ffd24d';
  ctx.beginPath(); ctx.arc(x+3, top, 7, 0, 7); ctx.fill();
  // bandera
  ctx.fillStyle = COLORS.flag;
  const fy = top + 6 + (1-flagRaise)*60;
  ctx.beginPath();
  ctx.moveTo(x+6, fy);
  ctx.lineTo(x+6, fy+34);
  ctx.lineTo(x-30, fy+17);
  ctx.fill();
}

function drawParticles() {
  for (const pt of particles) {
    ctx.globalAlpha = Math.min(1, pt.life/20);
    ctx.fillStyle = pt.color;
    ctx.fillRect(pt.x - camX, pt.y, pt.size, pt.size);
  }
  ctx.globalAlpha = 1;
}

function render() {
  drawBackground();
  drawFlag();
  drawPlatforms();
  drawCoins();
  drawEnemies();
  drawParticles();
  drawPlayer();

  if (state === 'win' && flagRaise < 1) flagRaise = Math.min(1, flagRaise + 0.02);
}

// ---------- HUD / pantallas ----------
const coinsEl = document.getElementById('coins');
const livesEl = document.getElementById('lives');
function updateHUD() {
  coinsEl.textContent = coinsCollected;
  let h = '';
  for (let i = 0; i < lives; i++) h += '<span class="heart">❤</span>';
  livesEl.innerHTML = h;
}

const startScreen = document.getElementById('startScreen');
const endScreen = document.getElementById('endScreen');
const endTitle = document.getElementById('endTitle');
const endMsg = document.getElementById('endMsg');

function startGame() {
  reset(true);
  updateHUD();
  state = 'play';
  startScreen.classList.add('hidden');
  endScreen.classList.add('hidden');
}
function win() {
  setTimeout(() => {
    endTitle.textContent = '🏁 ¡Ganaste!';
    endMsg.textContent = `Llegaste a la meta con ${coinsCollected} monedas. ¡Bien jugado!`;
    endScreen.classList.remove('hidden');
  }, 900);
}
function gameOver() {
  setTimeout(() => {
    endTitle.textContent = '💀 Game Over';
    endMsg.textContent = `Conseguiste ${coinsCollected} monedas. ¿Otra vuelta?`;
    endScreen.classList.remove('hidden');
  }, 600);
}

document.getElementById('startBtn').addEventListener('click', startGame);
document.getElementById('restartBtn').addEventListener('click', startGame);

// ---------- Bucle principal ----------
reset(true);
updateHUD();
state = 'menu';

function loop() {
  update();
  render();
  requestAnimationFrame(loop);
}
loop();
</script>
</body>
</html>
