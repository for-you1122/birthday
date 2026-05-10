<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Birthday Universe Pro Max ✨</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
body {
    margin:0;
    font-family: 'Segoe UI', sans-serif;
    background:black;
    overflow:hidden;
    color:white;
}

/* CANVAS BACKGROUND */
#bg {
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    z-index:-2;
}

/* OVERLAY GRADIENT */
.overlay {
    position:fixed;
    width:100%;
    height:100%;
    background: radial-gradient(circle, rgba(0,0,0,0.3), black);
    z-index:-1;
}

/* SCENES */
.scene {
    display:none;
    height:100vh;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    text-align:center;
    padding:20px;
}

.active {
    display:flex;
}

/* TITLE */
h1 {
    font-size:3.5em;
    color:#ff4d6d;
    animation: glow 2s infinite alternate;
}

@keyframes glow {
    from { text-shadow:0 0 10px #ff4d6d; }
    to { text-shadow:0 0 40px #ffcc00; }
}

/* BUTTON */
.btn {
    padding:15px 30px;
    border:none;
    border-radius:30px;
    background:#ff4d6d;
    color:white;
    cursor:pointer;
    margin-top:20px;
    font-size:16px;
}

/* GIFT SYSTEM */
.gifts {
    display:flex;
    gap:15px;
}

.gift {
    width:100px;
    height:100px;
    background:linear-gradient(45deg,#ff4d6d,#6a5acd);
    border-radius:20px;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:40px;
    cursor:pointer;
}

/* MEMORY */
.memory {
    display:flex;
    gap:15px;
    flex-wrap:wrap;
    justify-content:center;
}

.card {
    width:200px;
    height:250px;
    background:rgba(255,255,255,0.1);
    border-radius:20px;
    display:flex;
    justify-content:center;
    align-items:center;
    backdrop-filter: blur(10px);
    cursor:pointer;
}

/* CAKE */
.cake {
    font-size:120px;
    cursor:pointer;
}

/* LETTER */
#letter {
    max-width:600px;
    font-size:20px;
    white-space:pre-line;
}

/* MODAL */
#modal {
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:rgba(0,0,0,0.8);
    display:none;
    justify-content:center;
    align-items:center;
}

#modalBox {
    background:#111;
    padding:30px;
    border-radius:20px;
    max-width:400px;
}
</style>
</head>

<body>

<canvas id="bg"></canvas>
<div class="overlay"></div>

<!-- MUSIC -->
<audio id="music" loop>
<source src="https://www.bensound.com/bensound-music/bensound-sweet.mp3">
</audio>

<!-- SCENE 1 -->
<div id="s1" class="scene active">
    <h1>🎂 Birthday Universe</h1>
    <p>A cinematic experience created only for you 💖</p>
    <button class="btn" onclick="start()">Enter Universe</button>
</div>

<!-- SCENE 2 MEMORIES -->
<div id="s2" class="scene">
    <h2>💖 Memory Universe</h2>
    <div class="memory">
        <div class="card" onclick="openModal('First Talk 💬')">Talk</div>
        <div class="card" onclick="openModal('Late Nights 🌙')">Nights</div>
        <div class="card" onclick="openModal('Laughs 😂')">Laughs</div>
        <div class="card" onclick="openModal('Moments ✨')">Moments</div>
    </div>
    <button class="btn" onclick="next(3)">Next</button>
</div>

<!-- SCENE 3 GIFTS -->
<div id="s3" class="scene">
    <h2>🎁 Gift Unlock System</h2>
    <div class="gifts">
        <div class="gift" onclick="gift(this)">🎁</div>
        <div class="gift" onclick="gift(this)">🎁</div>
        <div class="gift" onclick="gift(this)">🎁</div>
    </div>
    <button class="btn" onclick="next(4)">Next</button>
</div>

<!-- SCENE 4 CAKE -->
<div id="s4" class="scene">
    <h2>🎂 Make a Wish</h2>
    <div class="cake" onclick="cake()">🕯️🕯️🕯️🎂</div>
</div>

<!-- SCENE 5 LETTER -->
<div id="s5" class="scene">
    <h2>💌 Letter</h2>
    <div id="letter"></div>
    <button class="btn" onclick="final()">Final Surprise</button>
</div>

<!-- FINAL -->
<div id="s6" class="scene">
    <h1>🎆 SURPRISE 🎆</h1>
    <p>You just entered a universe made of memories & emotions 💖</p>
</div>

<!-- MODAL -->
<div id="modal">
    <div id="modalBox"></div>
</div>

<script>

/* ===== CANVAS BACKGROUND ===== */
const canvas = document.getElementById("bg");
const ctx = canvas.getContext("2d");

canvas.width = innerWidth;
canvas.height = innerHeight;

let stars = [];

for(let i=0;i<200;i++){
    stars.push({
        x:Math.random()*canvas.width,
        y:Math.random()*canvas.height,
        r:Math.random()*2,
        d:Math.random()*1
    });
}

function drawStars(){
    ctx.clearRect(0,0,canvas.width,canvas.height);
    ctx.fillStyle="white";

    stars.forEach(s=>{
        ctx.beginPath();
        ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
        ctx.fill();

        s.y += s.d;
        if(s.y>canvas.height) s.y=0;
    });

    requestAnimationFrame(drawStars);
}
drawStars();

/* ===== NAV ===== */
function show(n){
    document.querySelectorAll(".scene").forEach(s=>s.classList.remove("active"));
    document.getElementById("s"+n).classList.add("active");
}

function start(){
    document.getElementById("music").play();
    show(2);
    typeLetter();
}

function next(n){ show(n); }

/* ===== GIFTS ===== */
function gift(el){
    el.innerHTML="💖";
    el.style.background="green";
    explode();
}

/* ===== CAKE FIREWORK ===== */
function cake(){
    explode();
    document.querySelector(".cake").innerHTML="🎂✨";
}

/* ===== EXPLOSION ===== */
function explode(){
    for(let i=0;i<80;i++){
        let e=document.createElement("div");
        e.innerHTML="✨";
        e.style.position="fixed";
        e.style.left=Math.random()*100+"vw";
        e.style.top="50vh";
        document.body.appendChild(e);

        setTimeout(()=>e.remove(),1500);
    }
}

/* ===== LETTER ===== */
function typeLetter(){
    let text =
`Happy Birthday ❤️

This is not just a website...
It is a universe built for your memories.

You deserve happiness, peace, and everything beautiful.

Stay smiling always ✨`;

    let i=0;
    let el=document.getElementById("letter");

    let t=setInterval(()=>{
        el.innerHTML+=text[i];
        i++;
        if(i>=text.length) clearInterval(t);
    },40);
}

/* ===== FINAL ===== */
function final(){
    show(6);
    explode();
}

/* ===== MODAL ===== */
function openModal(text){
    document.getElementById("modal").style.display="flex";
    document.getElementById("modalBox").innerHTML=text;
}

document.getElementById("modal").onclick=()=> {
    document.getElementById("modal").style.display="none";
};

</script>

</body>
</html>
