<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Her Birthday Universe ✨</title>

<!-- GOOGLE FONT -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">

<!-- THREE.JS -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    overflow:hidden;
    font-family:'Poppins',sans-serif;
    background:black;
    color:white;
}

/* 3D BACKGROUND */
#bg{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    z-index:-10;
}

/* UI LAYER */
.overlay{
    position:absolute;
    inset:0;
    background:linear-gradient(
        to bottom,
        rgba(0,0,0,0.3),
        rgba(0,0,0,0.7)
    );
    z-index:-1;
}

/* SCREENS */
.screen{
    position:absolute;
    width:100%;
    height:100%;
    display:none;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    text-align:center;
    padding:20px;
}

.active{
    display:flex;
}

/* TITLES */
.main-title{
    font-size:5rem;
    font-weight:700;
    letter-spacing:3px;
    background:linear-gradient(90deg,#ff4d6d,#ffd166,#ffffff);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
    animation:glow 4s infinite alternate;
}

@keyframes glow{
    from{
        filter:drop-shadow(0 0 10px #ff4d6d);
    }
    to{
        filter:drop-shadow(0 0 30px #ffd166);
    }
}

/* SUBTEXT */
.sub{
    max-width:700px;
    margin-top:20px;
    line-height:1.7;
    opacity:0.9;
}

/* BUTTON */
.btn{
    margin-top:40px;
    padding:16px 40px;
    border:none;
    border-radius:50px;
    background:linear-gradient(90deg,#ff4d6d,#ff758f);
    color:white;
    font-size:18px;
    cursor:pointer;
    transition:0.3s;
}

.btn:hover{
    transform:scale(1.08);
}

/* NAV */
.nav{
    position:fixed;
    top:20px;
    left:50%;
    transform:translateX(-50%);
    display:flex;
    gap:15px;
    z-index:999;
}

.nav button{
    background:rgba(255,255,255,0.1);
    border:none;
    color:white;
    padding:10px 20px;
    border-radius:30px;
    backdrop-filter:blur(10px);
    cursor:pointer;
}

/* MEMORY GRID */
.memory-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:25px;
    width:90%;
    max-width:1200px;
    margin-top:40px;
}

.memory-card{
    height:280px;
    background:rgba(255,255,255,0.08);
    border:1px solid rgba(255,255,255,0.15);
    border-radius:25px;
    backdrop-filter:blur(15px);
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:22px;
    transition:0.4s;
    cursor:pointer;
}

.memory-card:hover{
    transform:translateY(-15px) scale(1.03);
    background:rgba(255,255,255,0.12);
}

/* GIFT */
.gift-wrap{
    display:flex;
    gap:40px;
    flex-wrap:wrap;
    justify-content:center;
    margin-top:40px;
}

.gift{
    width:170px;
    height:170px;
    background:linear-gradient(135deg,#ff4d6d,#6a5acd);
    border-radius:30px;
    display:flex;
    justify-content:center;
    align-items:center;
    font-size:70px;
    cursor:pointer;
    transition:0.4s;
    box-shadow:0 0 40px rgba(255,77,109,0.4);
}

.gift:hover{
    transform:rotate(8deg) scale(1.08);
}

/* LETTER */
#letterText{
    max-width:900px;
    line-height:2;
    font-size:1.3rem;
    margin-top:40px;
    white-space:pre-line;
}

/* CAKE */
.cake{
    font-size:180px;
    cursor:pointer;
    transition:0.3s;
}

.cake:hover{
    transform:scale(1.05);
}

/* FINAL */
.final-title{
    font-size:6rem;
    background:linear-gradient(90deg,#fff,#ffd166,#ff4d6d);
    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;
}

/* MUSIC BUTTON */
.music{
    position:fixed;
    right:20px;
    bottom:20px;
    z-index:999;
    width:60px;
    height:60px;
    border-radius:50%;
    border:none;
    background:#ff4d6d;
    color:white;
    cursor:pointer;
    font-size:22px;
}

/* MOBILE */
@media(max-width:768px){

.main-title{
    font-size:3rem;
}

.final-title{
    font-size:3rem;
}

.cake{
    font-size:120px;
}

}
</style>
</head>

<body>

<canvas id="bg"></canvas>
<div class="overlay"></div>

<!-- NAV -->
<div class="nav">
    <button onclick="showScreen('home')">Home</button>
    <button onclick="showScreen('memories')">Memories</button>
    <button onclick="showScreen('gifts')">Gifts</button>
    <button onclick="showScreen('cakeScreen')">Cake</button>
    <button onclick="showScreen('letter')">Letter</button>
</div>

<!-- MUSIC -->
<button class="music" onclick="toggleMusic()">🎵</button>

<audio id="music" loop>
<source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8c8e0b4f6.mp3?filename=romantic-background-11254.mp3">
</audio>

<!-- HOME -->
<section id="home" class="screen active">
    <h1 class="main-title">Birthday Universe</h1>

    <p class="sub">
        This is not just a website.<br>
        It is a complete universe built from memories, emotions,
        moments, and wishes made only for one special person.
    </p>

    <button class="btn" onclick="enterUniverse()">
        Enter The Universe ✨
    </button>
</section>

<!-- MEMORIES -->
<section id="memories" class="screen">

    <h1 class="main-title">Memory Galaxy 💖</h1>

    <div class="memory-grid">

        <div class="memory-card">
            First Conversation 💬
        </div>

        <div class="memory-card">
            Endless Laughs 😂
        </div>

        <div class="memory-card">
            Late Night Talks 🌙
        </div>

        <div class="memory-card">
            Beautiful Moments ✨
        </div>

    </div>

</section>

<!-- GIFTS -->
<section id="gifts" class="screen">

    <h1 class="main-title">Unlock Gifts 🎁</h1>

    <div class="gift-wrap">

        <div class="gift" onclick="openGift(this)">🎁</div>
        <div class="gift" onclick="openGift(this)">🎁</div>
        <div class="gift" onclick="openGift(this)">🎁</div>

    </div>

</section>

<!-- CAKE -->
<section id="cakeScreen" class="screen">

    <h1 class="main-title">Make A Wish 🎂</h1>

    <div class="cake" onclick="blowCandles()">
        🕯️🕯️🕯️🎂
    </div>

    <p class="sub">
        Click the cake to blow candles and start fireworks ✨
    </p>

</section>

<!-- LETTER -->
<section id="letter" class="screen">

    <h1 class="main-title">A Letter 💌</h1>

    <div id="letterText"></div>

    <button class="btn" onclick="showScreen('final')">
        Final Surprise ✨
    </button>

</section>

<!-- FINAL -->
<section id="final" class="screen">

    <h1 class="final-title">HAPPY BIRTHDAY ❤️</h1>

    <p class="sub">
        You deserve happiness, peace, success, memories,
        laughter, adventures, and every beautiful thing life can offer.
        <br><br>
        Stay smiling always ✨
    </p>

</section>

<script>

/* =========================================================
   THREE.JS GALAXY BACKGROUND
========================================================= */

const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera(
    75,
    window.innerWidth/window.innerHeight,
    0.1,
    1000
);

const renderer = new THREE.WebGLRenderer({
    canvas:document.getElementById('bg'),
    antialias:true
});

renderer.setSize(window.innerWidth,window.innerHeight);

camera.position.z = 5;

/* STARS */

const starGeometry = new THREE.BufferGeometry();
const starCount = 12000;

const positions = new Float32Array(starCount * 3);

for(let i=0;i<starCount*3;i++){
    positions[i] = (Math.random()-0.5)*2000;
}

starGeometry.setAttribute(
    'position',
    new THREE.BufferAttribute(positions,3)
);

const starMaterial = new THREE.PointsMaterial({
    color:0xffffff,
    size:0.7
});

const stars = new THREE.Points(starGeometry,starMaterial);

scene.add(stars);

/* ANIMATE */

function animate(){

    requestAnimationFrame(animate);

    stars.rotation.y += 0.0005;
    stars.rotation.x += 0.0002;

    renderer.render(scene,camera);
}

animate();

/* RESIZE */

window.addEventListener('resize',()=>{

    camera.aspect = window.innerWidth/window.innerHeight;

    camera.updateProjectionMatrix();

    renderer.setSize(window.innerWidth,window.innerHeight);

});

/* =========================================================
   SCREEN SYSTEM
========================================================= */

function showScreen(id){

    document.querySelectorAll('.screen')
    .forEach(s=>s.classList.remove('active'));

    document.getElementById(id)
    .classList.add('active');

}

/* =========================================================
   ENTER
========================================================= */

function enterUniverse(){

    showScreen('memories');

    document.getElementById('music').play();

    typeLetter();

}

/* =========================================================
   GIFTS
========================================================= */

function openGift(el){

    el.innerHTML = "💖";

    el.style.background = "linear-gradient(135deg,#00ff95,#00c9ff)";

    explode();

}

/* =========================================================
   FIREWORK EFFECT
========================================================= */

function explode(){

    for(let i=0;i<120;i++){

        let spark = document.createElement('div');

        spark.innerHTML = "✨";

        spark.style.position='fixed';
        spark.style.left=Math.random()*100+'vw';
        spark.style.top=Math.random()*100+'vh';
        spark.style.fontSize='20px';

        document.body.appendChild(spark);

        setTimeout(()=>{
            spark.remove();
        },1500);

    }

}

/* =========================================================
   CAKE
========================================================= */

function blowCandles(){

    document.querySelector('.cake').innerHTML="🎂✨";

    explode();

    setTimeout(()=>{
        showScreen('letter');
    },2000);

}

/* =========================================================
   LETTER
========================================================= */

function typeLetter(){

const text =

`Happy Birthday ❤️

This website is not just code.

It is a universe built from emotions,
memories, moments, and wishes.

You deserve happiness,
beautiful memories,
peace,
success,
and every good thing life can offer.

May your smile always stay bright ✨`;

let i = 0;

const el = document.getElementById('letterText');

el.innerHTML = "";

const interval = setInterval(()=>{

    el.innerHTML += text[i];

    i++;

    if(i >= text.length){

        clearInterval(interval);

    }

},35);

}

/* =========================================================
   MUSIC
========================================================= */

function toggleMusic(){

    const m = document.getElementById('music');

    if(m.paused){

        m.play();

    }else{

        m.pause();

    }

}

</script>

</body>
</html>
