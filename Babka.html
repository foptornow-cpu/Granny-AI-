# Granny-AI-
AI granny
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Granny Mobile & PC Edition</title>
    <style>
        * { box-sizing: border-box; -webkit-tap-highlight-color: transparent; }
        body {
            margin: 0; background-color: #000; color: #eee;
            font-family: 'Courier New', Courier, monospace;
            overflow: hidden; touch-action: none;
            display: flex; align-items: center; justify-content: center;
            height: 100vh; width: 100vw;
        }

        #game-container {
            position: relative;
            width: 100%;
            height: 100%;
            max-width: 800px;
            max-height: 600px;
            background: #000;
        }

        canvas {
            width: 100%;
            height: 100%;
            background-color: #000;
            display: block;
        }

        /* Мобильное управление */
        #mobile-controls {
            position: absolute; bottom: 20px; left: 0; width: 100%;
            display: flex; justify-content: space-between; padding: 0 30px;
            pointer-events: none; z-index: 30;
        }

        .joystick-area {
            width: 120px; height: 120px; background: rgba(255,255,255,0.1);
            border-radius: 50%; position: relative; pointer-events: auto;
        }
        #joystick-stick {
            width: 50px; height: 50px; background: rgba(255,255,255,0.3);
            border-radius: 50%; position: absolute; top: 35px; left: 35px;
        }

        .action-btn {
            width: 80px; height: 80px; background: rgba(139, 0, 0, 0.5);
            border: 3px solid #8b0000; border-radius: 50%;
            color: white; display: flex; align-items: center; justify-content: center;
            font-weight: bold; pointer-events: auto; user-select: none;
        }
        .action-btn:active { background: #8b0000; }

        /* Экраны */
        #ui-overlay {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9); display: flex; flex-direction: column;
            align-items: center; justify-content: center; z-index: 50; text-align: center;
        }
        .hidden { display: none !important; }
        h1 { color: #8b0000; margin: 0; font-size: 2rem; }
        button {
            padding: 15px 30px; font-size: 1.2rem; background: #440000;
            color: white; border: 2px solid #8b0000; cursor: pointer; margin-top: 20px;
        }

        #screamer {
            position: absolute; top: 0; left: 0; width: 100%; height: 100%;
            background: #000; z-index: 100; display: none;
            align-items: center; justify-content: center; font-size: 150px;
        }
        .shake { animation: shake 0.1s infinite; }
        @keyframes shake {
            0% { transform: translate(5px,5px); }
            50% { transform: translate(-5px,-5px); }
            100% { transform: translate(5px,-5px); }
        }
    </style>
</head>
<body>

    <div id="game-container">
        <canvas id="gameCanvas"></canvas>
        
        <div id="mobile-controls">
            <div class="joystick-area" id="joy-area">
                <div id="joystick-stick"></div>
            </div>
            <div class="action-btn" id="hide-btn">СПРЯТАТЬСЯ</div>
        </div>

        <div id="screamer">💀</div>

        <div id="ui-overlay">
            <div id="start-screen">
                <h1>GRANNY NIGHTMARE</h1>
                <p>Найди ключ 🔑 и выход 🚪</p>
                <p>ПК: WASD + Пробел<br>ТЕЛЕФОН: Джойстик + Кнопка</p>
                <button onclick="startGame()">ИГРАТЬ</button>
            </div>
            <div id="win-screen" class="hidden">
                <h1 style="color: #4CAF50;">ТЫ ВЫБРАЛСЯ!</h1>
                <button onclick="location.reload()">ЕЩЕ РАЗ</button>
            </div>
        </div>
    </div>

<script>
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
const screamerEl = document.getElementById('screamer');

// Логическое разрешение (фиксированное для простоты расчетов)
canvas.width = 800;
canvas.height = 600;

const TILE_SIZE = 50;
let gameState = 'MENU';
let hasKey = false;
let isHidden = false;

const map = [
    [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
    [1,0,0,0,1,0,0,0,0,0,0,4,0,0,0,1],
    [1,0,1,0,1,0,1,1,1,0,1,1,1,1,0,1],
    [1,0,1,0,0,0,0,0,1,0,0,0,0,1,0,1],
    [1,4,1,1,1,1,1,0,1,1,1,1,0,1,0,1],
    [1,0,0,0,0,0,1,0,4,0,0,0,0,1,0,1],
    [1,1,1,0,1,0,1,1,1,1,1,0,1,1,0,1],
    [1,0,0,0,1,0,0,0,0,0,1,0,0,4,0,1],
    [1,0,1,1,1,1,1,1,1,0,1,1,1,1,0,1],
    [1,0,0,3,1,0,0,0,1,0,0,0,0,0,0,1],
    [1,1,1,0,1,0,1,0,1,1,1,1,4,1,0,1],
    [1,2,0,0,0,0,1,0,0,0,0,0,0,0,0,1],
    [1,1,1,1,1,1,1,1,1,1,1,1,1,1,1,1],
];

const player = { x: 75, y: 75, angle: 0, vx: 0, vy: 0 };
const granny = {
    x: 700, y: 500, angle: 0, state: 'PATROL',
    patrolPoints: [{x:700,y:500}, {x:700,y:100}, {x:100,y:500}, {x:400,y:300}],
    patrolIndex: 0
};

// Управление
const keys = {};
let joyX = 0, joyY = 0;
let mobileHide = false;

window.addEventListener('keydown', e => keys[e.code] = true);
window.addEventListener('keyup', e => keys[e.code] = false);

// Логика джойстика
const joyArea = document.getElementById('joy-area');
const joyStick = document.getElementById('joystick-stick');
const hideBtn = document.getElementById('hide-btn');

joyArea.addEventListener('touchstart', handleTouch);
joyArea.addEventListener('touchmove', handleTouch);
joyArea.addEventListener('touchend', () => {
    joyX = 0; joyY = 0;
    joyStick.style.transform = `translate(0, 0)`;
});

function handleTouch(e) {
    const rect = joyArea.getBoundingClientRect();
    const touch = e.touches[0];
    const centerX = rect.left + rect.width / 2;
    const centerY = rect.top + rect.height / 2;
    
    let dx = touch.clientX - centerX;
    let dy = touch.clientY - centerY;
    const distance = Math.min(Math.hypot(dx, dy), 40);
    const angle = Math.atan2(dy, dx);

    joyX = Math.cos(angle) * (distance / 40);
    joyY = Math.sin(angle) * (distance / 40);

    joyStick.style.transform = `translate(${Math.cos(angle)*distance}px, ${Math.sin(angle)*distance}px)`;
    e.preventDefault();
}

hideBtn.addEventListener('touchstart', () => mobileHide = true);
hideBtn.addEventListener('touchend', () => mobileHide = false);

// Звук
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();
function playScream() {
    const osc = audioCtx.createOscillator();
    const g = audioCtx.createGain();
    osc.type = 'sawtooth';
    osc.frequency.setValueAtTime(150, audioCtx.currentTime);
    osc.frequency.exponentialRampToValueAtTime(40, audioCtx.currentTime + 1);
    g.gain.setValueAtTime(0.3, audioCtx.currentTime);
    osc.connect(g); g.connect(audioCtx.destination);
    osc.start(); osc.stop(audioCtx.currentTime + 1);
}

function startGame() {
    audioCtx.resume();
    document.getElementById('ui-overlay').classList.add('hidden');
    gameState = 'PLAYING';
    gameLoop();
}

function checkCollision(nx, ny) {
    const gx = Math.floor(nx / TILE_SIZE), gy = Math.floor(ny / TILE_SIZE);
    if (!map[gy] || map[gy][gx] === undefined) return true;
    const tile = map[gy][gx];
    if (tile === 1) return true;
    if (tile === 2) { 
        if(hasKey) { gameState = 'WON'; document.getElementById('ui-overlay').classList.remove('hidden'); document.getElementById('win-screen').classList.remove('hidden'); }
        return true; 
    }
    if (tile === 3) { hasKey = true; map[gy][gx] = 0; }
    return false;
}

function update() {
    // Движение (Клавиатура + Джойстик)
    let speed = 2.5;
    let vx = 0, vy = 0;

    if (keys['KeyW'] || keys['ArrowUp']) vy = -speed;
    if (keys['KeyS'] || keys['ArrowDown']) vy = speed;
    if (keys['KeyA'] || keys['ArrowLeft']) vx = -speed;
    if (keys['KeyD'] || keys['ArrowRight']) vx = speed;

    if (joyX !== 0 || joyY !== 0) {
        vx = joyX * speed; vy = joyY * speed;
    }

    // Прятки
    const gx = Math.floor(player.x / TILE_SIZE), gy = Math.floor(player.y / TILE_SIZE);
    let nearCloset = false;
    for(let i=-1; i<=1; i++) for(let j=-1; j<=1; j++) if(map[gy+i] && map[gy+i][gx+j] === 4) nearCloset = true;

    isHidden = (keys['Space'] || mobileHide) && nearCloset;

    if (!isHidden) {
        if (vx !== 0 || vy !== 0) {
            player.angle = Math.atan2(vy, vx);
            if (!checkCollision(player.x + vx, player.y)) player.x += vx;
            if (!checkCollision(player.x, player.y + vy)) player.y += vy;
        }
    }

    // Бабка
    const dist = Math.hypot(granny.x - player.x, granny.y - player.y);
    if (!isHidden && dist < 250) granny.state = 'CHASE';
    else if (dist > 350) granny.state = 'PATROL';

    let target = granny.state === 'CHASE' ? player : granny.patrolPoints[granny.patrolIndex];
    const gAngle = Math.atan2(target.y - granny.y, target.x - granny.x);
    granny.angle = gAngle;
    const gSpd = granny.state === 'CHASE' ? 3.4 : 1.5;
    
    const gvx = Math.cos(gAngle) * gSpd, gvy = Math.sin(gAngle) * gSpd;
    if (!checkCollision(granny.x + gvx, granny.y + gvy)) {
        granny.x += gvx; granny.y += gvy;
    }

    if (granny.state === 'PATROL' && Math.hypot(target.x - granny.x, target.y - granny.y) < 10) {
        granny.patrolIndex = (granny.patrolIndex + 1) % granny.patrolPoints.length;
    }

    if (!isHidden && dist < 30) {
        gameState = 'LOST';
        playScream();
        screamerEl.style.display = 'flex';
        screamerEl.classList.add('shake');
        setTimeout(() => location.reload(), 2000);
    }
}

function draw() {
    ctx.fillStyle = "#000";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    for (let y = 0; y < map.length; y++) {
        for (let x = 0; x < map[y].length; x++) {
            const px = x * TILE_SIZE, py = y * TILE_SIZE;
            if (map[y][x] === 1) { ctx.fillStyle = '#1a0808'; ctx.fillRect(px, py, TILE_SIZE, TILE_SIZE); }
            if (map[y][x] === 4) { ctx.font = "20px Arial"; ctx.fillText("🗄️", px+12, py+35); }
            if (map[y][x] === 3) { ctx.font = "20px Arial"; ctx.fillText("🔑", px+12, py+35); }
            if (map[y][x] === 2) { ctx.font = "20px Arial"; ctx.fillText("🚪", px+12, py+35); }
        }
    }

    if (!isHidden) {
        ctx.save(); ctx.translate(player.x, player.y); ctx.rotate(player.angle);
        ctx.font = "24px Arial"; ctx.fillText("🏃", -12, 10); ctx.restore();
    }

    ctx.save(); ctx.translate(granny.x, granny.y); ctx.rotate(granny.angle);
    ctx.font = "30px Arial"; ctx.fillText(granny.state === 'CHASE' ? "👵🔪" : "👵", -15, 12); ctx.restore();

    // Свет фонарика
    ctx.save();
    const grad = ctx.createRadialGradient(player.x, player.y, 30, player.x, player.y, isHidden ? 80 : 200);
    grad.addColorStop(0, 'rgba(0,0,0,0)');
    grad.addColorStop(1, 'rgba(0,0,0,0.98)');
    ctx.fillStyle = grad;
    ctx.globalCompositeOperation = 'multiply';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    ctx.restore();
}

function gameLoop() {
    if (gameState === 'PLAYING') {
        update();
        draw();
        requestAnimationFrame(gameLoop);
    }
}
</script>
</body>
</html>
