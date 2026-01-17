<!DOCTYPE html>
<html lang="ro">
<head>
<meta charset="UTF-8">
<title>Triangle Shooter</title>
<style>
html, body {
    margin: 0;
    width: 100%;
    height: 100%;
    background: black;
    overflow: hidden;
    font-family: Arial, sans-serif;
    color: white;
}

#startScreen, #gameOverScreen {
    position: absolute;
    width: 100%;
    height: 100%;
    background: radial-gradient(#222, #000);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    z-index: 5;
}

#gameOverScreen { display: none; }

input, button { padding: 10px; margin: 5px; font-size: 16px; }

#leaderboard {
    margin-top: 20px;
    background: rgba(255,255,255,0.1);
    padding: 10px;
    width: 260px;
    text-align: center;
}

canvas { display: none; touch-action: none; }

#pauseBtn {
    position: fixed;
    top: 10px;
    left: 10px;
    z-index: 10;
    display: none;
}

/* Mobile Controls */
#mobileControls {
    position: fixed;
    bottom: 20px;
    width: 100%;
    display: flex;
    justify-content: space-around;
    z-index: 10;
    display: none;
}

#mobileControls button {
    width: 60px;
    height: 60px;
    font-size: 24px;
    border-radius: 50%;
    opacity: 0.6;
}
</style>
</head>
<body>

<div id="startScreen">
    <h1>🔺 Triangle Shooter</h1>
    <input id="username" placeholder="Insert your username">
    <button onclick="startGame()">START</button>
    <div id="leaderboard">
        <h3>LEADERBOARD</h3>
        <ul id="scores"></ul>
    </div>
</div>

<div id="gameOverScreen">
    <h1 style="color:red;">💥 GAME OVER 💥</h1>
    <p id="finalScore"></p>
    <button onclick="location.reload()">RESTART</button>
</div>

<button id="pauseBtn" onclick="togglePause()">PAUSE</button>
<canvas id="game"></canvas>

<div id="mobileControls">
    <button id="leftBtn">⬅️</button>
    <button id="shootBtn">🔫</button>
    <button id="rightBtn">➡️</button>
</div>

<audio id="bgMusic" loop>
    <source src="music.mp3" type="audio/mpeg">
</audio>

<script>
const canvas = document.getElementById("game");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let bullets = [];
let enemies = [];
let score = 0;
let paused = false;
let gameOver = false;
let username = localStorage.getItem("username") || "";
let lives = 3;
let enemySpeed = 3;

const keys = {};
const player = { x: canvas.width / 2, y: canvas.height - 80, size: 40, speed: 7 };

window.addEventListener("keydown", e => keys[e.key] = true);
window.addEventListener("keyup", e => keys[e.key] = false);

// MOBILE BUTTONS
const leftBtn = document.getElementById("leftBtn");
const rightBtn = document.getElementById("rightBtn");
const shootBtn = document.getElementById("shootBtn");

leftBtn.addEventListener("touchstart", ()=> keys["ArrowLeft"]=true);
leftBtn.addEventListener("touchend", ()=> keys["ArrowLeft"]=false);
rightBtn.addEventListener("touchstart", ()=> keys["ArrowRight"]=true);
rightBtn.addEventListener("touchend", ()=> keys["ArrowRight"]=false);
shootBtn.addEventListener("touchstart", shoot);

function shoot(){ if(!gameOver) bullets.push({ x: player.x, y: player.y - 20 }); }

// START GAME
function startGame() {
    const inputName = document.getElementById("username").value;
    if(inputName) { 
        username = inputName; 
        localStorage.setItem("username", username);
    }
    document.getElementById("startScreen").style.display = "none";
    canvas.style.display = "block";
    document.getElementById("pauseBtn").style.display = "block";

    if(window.innerWidth < 768) document.getElementById("mobileControls").style.display = "flex";

    const music = document.getElementById("bgMusic");
    music.volume = 0.2;
    music.play();

    setInterval(spawnEnemy, 1000);
    requestAnimationFrame(gameLoop);
}

function movePlayer() {
    if(keys["a"] || keys["ArrowLeft"]) player.x -= player.speed;
    if(keys["d"] || keys["ArrowRight"]) player.x += player.speed;
    player.x = Math.max(player.size, Math.min(canvas.width - player.size, player.x));
}

function drawPlayer() {
    ctx.fillStyle = "red";
    ctx.beginPath();
    ctx.moveTo(player.x, player.y - player.size);
    ctx.lineTo(player.x - player.size, player.y + player.size);
    ctx.lineTo(player.x + player.size, player.y + player.size);
    ctx.closePath();
    ctx.fill();
}

canvas.addEventListener("click", shoot);

// ENEMY
function spawnEnemy() {
    if(!gameOver) {
        enemies.push({ x: Math.random()*(canvas.width-50), y: -60, size: 50 });
    }
}

function explosion(x,y){
    ctx.fillStyle="orange";
    ctx.beginPath();
    ctx.arc(x,y,60,0,Math.PI*2);
    ctx.fill();
}

function endGame() {
    gameOver = true;
    explosion(player.x, player.y);
    saveLeaderboard();
    document.getElementById("finalScore").innerText = "Score: "+score;
    setTimeout(()=>document.getElementById("gameOverScreen").style.display="flex",600);
}

// LEADERBOARD
function saveLeaderboard() {
    let data = JSON.parse(localStorage.getItem("scores")||"[]");
    data.push({name:username,score:score});
    data.sort((a,b)=>b.score-a.score);
    data = data.slice(0,5);
    localStorage.setItem("scores",JSON.stringify(data));
    loadLeaderboard();
}
function loadLeaderboard() {
    let data = JSON.parse(localStorage.getItem("scores")||"[]");
    const ul=document.getElementById("scores");
    ul.innerHTML="";
    data.forEach(s=>{
        let li=document.createElement("li");
        li.textContent=s.name+" - "+s.score;
        ul.appendChild(li);
    });
}
loadLeaderboard();

// DRAW LIVES
function drawLives() {
    for(let i=0;i<lives;i++){
        ctx.fillStyle="red";
        ctx.beginPath();
        ctx.arc(20+i*30, canvas.height-20,10,0,Math.PI*2);
        ctx.fill();
    }
}

// GAME LOOP
function gameLoop() {
    if(!paused && !gameOver){
        ctx.clearRect(0,0,canvas.width,canvas.height);
        movePlayer();
        drawPlayer();

        // BULLETS
        bullets.forEach((b,i)=>{
            b.y-=10;
            ctx.fillStyle="yellow";
            ctx.fillRect(b.x-3,b.y,6,12);
            if(b.y<0) bullets.splice(i,1);
        });

        // ENEMIES
        enemies.forEach((e,ei)=>{
            e.y += enemySpeed;
            ctx.fillStyle="purple";
            ctx.fillRect(e.x,e.y,e.size,e.size);

            // HIT BULLET
            bullets.forEach((b,bi)=>{
                if(b.x>e.x && b.x<e.x+e.size && b.y>e.y && b.y<e.y+e.size){
                    enemies.splice(ei,1);
                    bullets.splice(bi,1);
                    score++;
                    enemySpeed = 3 + Math.floor(score/5);
                }
            });

            // REMOVE ENEMY IF PASSES BOTTOM
            if(e.y>canvas.height) enemies.splice(ei,1);

            // HIT PLAYER
            if(
                e.x < player.x + player.size &&
                e.x + e.size > player.x - player.size &&
                e.y + e.size > player.y - player.size
            ) endGame();
        });

        // SCORE RIGHT TOP
        ctx.fillStyle="white";
        ctx.font="20px Arial";
        ctx.fillText("SCORE: "+score, canvas.width-120,30);

        // DRAW LIVES LEFT BOTTOM (NON COLIDABLE)
        drawLives();
    }
    requestAnimationFrame(gameLoop);
}

function togglePause(){ paused=!paused; }
</script>
</body>
</html>
