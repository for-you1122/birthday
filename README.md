<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Birthday Universe ✨</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>

<style>

/* =========================================================
   GLOBAL
========================================================= */

*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{

    overflow:hidden;
    font-family:'Poppins',sans-serif;
    color:white;

    background:
    linear-gradient(
        135deg,
        #1a0f1f,
        #2a1021,
        #4a1d3d,
        #24122d
    );

}

/* =========================================================
   DREAM LIGHTS
========================================================= */

body::before,
body::after{

    content:'';

    position:fixed;

    width:500px;
    height:500px;

    border-radius:50%;

    filter:blur(120px);

    z-index:-5;

}

body::before{

    background:#ff4d88;

    top:-150px;
    left:-100px;

    opacity:0.25;

}

body::after{

    background:#ffd166;

    bottom:-180px;
    right:-120px;

    opacity:0.15;

}

/* =========================================================
   FLOATING PARTICLES
========================================================= */

.particle{

    position:fixed;

    width:6px;
    height:6px;

    border-radius:50%;

    background:white;

    opacity:0.22;

    z-index:-2;

    animation:float linear infinite;

}

@keyframes float{

    from{
        transform:translateY(100vh);
    }

    to{
        transform:translateY(-20vh);
    }

}

/* =========================================================
   SCENES
========================================================= */

.scene{

    position:absolute;

    inset:0;

    display:none;

    justify-content:center;
    align-items:center;
    flex-direction:column;

    text-align:center;

    padding:40px;

    opacity:0;

}

.scene.active{

    display:flex;

    opacity:1;

    z-index:10;

}

/* =========================================================
   TEXT
========================================================= */

.label{

    letter-spacing:8px;

    opacity:0.7;

    margin-bottom:25px;

    font-size:13px;

}

.title{

    font-size:7rem;

    line-height:0.9;

    font-weight:700;

    background:
    linear-gradient(
        90deg,
        #fffaf2,
        #ffd166,
        #ff9ac2
    );

    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;

}

.text{

    max-width:760px;

    margin-top:35px;

    line-height:2;

    opacity:0.85;

    font-size:18px;

}

/* =========================================================
   BUTTON
========================================================= */

.btn{

    margin-top:55px;

    padding:20px 54px;

    border:none;

    border-radius:100px;

    background:rgba(255,255,255,0.08);

    color:white;

    letter-spacing:4px;

    cursor:pointer;

    backdrop-filter:blur(20px);

    transition:0.4s;

}

.btn:hover{

    transform:
    translateY(-5px)
    scale(1.03);

    background:rgba(255,255,255,0.15);

}

/* =========================================================
   MEMORIES
========================================================= */

.memory-wrap{

    display:flex;

    gap:30px;

    flex-wrap:wrap;

    justify-content:center;

    margin-top:60px;

}

.memory{

    width:280px;
    height:380px;

    border-radius:30px;

    overflow:hidden;

    position:relative;

    transition:0.5s;

    cursor:pointer;

    box-shadow:
    0 20px 60px rgba(0,0,0,0.35);

}

.memory:hover{

    transform:
    translateY(-12px)
    scale(1.03);

}

.memory img{

    width:100%;
    height:100%;

    object-fit:cover;

}

.memory-overlay{

    position:absolute;

    inset:0;

    background:
    linear-gradient(
        to top,
        rgba(0,0,0,0.95),
        rgba(0,0,0,0.1)
    );

    display:flex;

    align-items:flex-end;

    padding:30px;

}

.memory-overlay h3{

    font-size:22px;

}

/* =========================================================
   LETTER
========================================================= */

.letter-box{

    width:90%;
    max-width:950px;

    background:rgba(255,255,255,0.05);

    border:1px solid rgba(255,255,255,0.08);

    border-radius:40px;

    padding:70px;

    backdrop-filter:blur(25px);

}

#letter{

    white-space:pre-line;

    line-height:2.3;

    font-size:18px;

}

/* =========================================================
   FLOWER GIFTS
========================================================= */

.gift-wrap{

    display:flex;

    gap:35px;

    flex-wrap:wrap;

    justify-content:center;

    margin-top:60px;

}

.gift{

    width:220px;
    height:300px;

    border-radius:35px;

    overflow:hidden;

    cursor:pointer;

    position:relative;

    transition:0.5s;

    background:rgba(255,255,255,0.06);

    border:1px solid rgba(255,255,255,0.08);

}

.gift img{

    width:100%;
    height:100%;

    object-fit:cover;

    transition:0.5s;

}

.gift:hover{

    transform:
    translateY(-12px)
    scale(1.03);

}

.gift:hover img{

    transform:scale(1.08);

}

.gift-text{

    position:absolute;

    bottom:0;

    width:100%;

    padding:20px;

    background:
    linear-gradient(
        to top,
        rgba(0,0,0,0.9),
        transparent
    );

}

/* =========================================================
   FINAL
========================================================= */

.final-title{

    font-size:8rem;

    line-height:0.9;

    background:
    linear-gradient(
        90deg,
        #fffaf2,
        #ffd166,
        #ff9ac2
    );

    -webkit-background-clip:text;
    -webkit-text-fill-color:transparent;

}

.final-text{

    max-width:760px;

    margin-top:40px;

    line-height:2;

    opacity:0.88;

}

/* =========================================================
   MUSIC
========================================================= */

.music{

    position:fixed;

    right:30px;
    bottom:30px;

    width:70px;
    height:70px;

    border-radius:50%;

    border:none;

    background:rgba(255,255,255,0.08);

    color:white;

    font-size:20px;

    cursor:pointer;

    z-index:999;

}

/* =========================================================
   MOBILE
========================================================= */

@media(max-width:900px){

.title{
    font-size:4rem;
}

.final-title{
    font-size:4rem;
}

.memory{
    width:90%;
}

.gift{
    width:90%;
}

.letter-box{
    padding:35px;
}

}

</style>
</head>

<body>

<!-- ======================================================
     PARTICLES
======================================================= -->

<script>

for(let i=0;i<50;i++){

const particle =
document.createElement('div');

particle.classList.add('particle');

particle.style.left =
Math.random()*100 + 'vw';

particle.style.animationDuration =
5 + Math.random()*10 + 's';

particle.style.opacity =
Math.random()*0.5;

document.body.appendChild(particle);

}

</script>

<!-- ======================================================
     SCENE 1
======================================================= -->

<section class="scene active" id="scene1">

<p class="label">
FOR SOMEONE SPECIAL
</p>

<h1 class="title">
HAPPY<br>
BIRTHDAY
</h1>

<p class="text">

Happy Birthday ❤️

Today is all about celebrating you,
your smile,
your happiness,
and the beautiful person you are ✨

</p>

<button class="btn"
onclick="nextScene('scene1','scene2')">

ENTER THE EXPERIENCE

</button>

</section>

<!-- ======================================================
     SCENE 2 MEMORIES
======================================================= -->

<section class="scene" id="scene2">

<p class="label">
MEMORIES
</p>

<h1 class="title">
OUR<br>
MEMORIES
</h1>

<div class="memory-wrap">

<div class="memory"
onclick="showMessage('Your smile in this memory was unforgettable ❤️')">

<img src="assets/photos/photo1.jpg">

<div class="memory-overlay">
<h3>Beautiful Moments</h3>
</div>

</div>

<div class="memory"
onclick="showMessage('Some conversations stay forever ✨')">

<img src="assets/photos/photo2.jpg">

<div class="memory-overlay">
<h3>Late Night Talks</h3>
</div>

</div>

<div class="memory"
onclick="showMessage('One of my favorite memories 🌸')">

<img src="assets/photos/photo3.jpg">

<div class="memory-overlay">
<h3>Unforgettable Smiles</h3>
</div>

</div>

</div>

<button class="btn"
onclick="nextScene('scene2','scene3')">

CONTINUE

</button>

</section>

<!-- ======================================================
     SCENE 3 LETTER
======================================================= -->

<section class="scene" id="scene3">

<p class="label">
A LETTER
</p>

<div class="letter-box">

<div id="letter"></div>

</div>

<button class="btn"
onclick="nextScene('scene3','scene4')">

OPEN FLOWERS

</button>

</section>

<!-- ======================================================
     SCENE 4 FLOWERS
======================================================= -->

<section class="scene" id="scene4">

<p class="label">
FLOWERS FOR YOU
</p>

<h1 class="title">
LITTLE<br>
SURPRISES
</h1>

<div class="gift-wrap">

<div class="gift"
onclick="openGift(this)">

<img src="assets/gifts/rose.jpg">

<div class="gift-text">
Roses For You 🌹
</div>

</div>

<div class="gift"
onclick="openGift(this)">

<img src="assets/gifts/bouquet.jpg">

<div class="gift-text">
A Bouquet Of Happiness 💐
</div>

</div>

<div class="gift"
onclick="openGift(this)">

<img src="assets/gifts/tulips.jpg">

<div class="gift-text">
Beautiful Like You ✨
</div>

</div>

</div>

<button class="btn"
onclick="nextScene('scene4','scene5')">

FINAL WISH

</button>

</section>

<!-- ======================================================
     SCENE 5 FINAL
======================================================= -->

<section class="scene" id="scene5">

<h1 class="final-title">
HAPPY<br>
BIRTHDAY ❤️
</h1>

<p class="final-text">

May life always protect your smile.

May your heart always find peace.

May your dreams become reality.

And may you always be surrounded
by beautiful moments and people
who truly deserve you ✨

Forever one of the most beautiful
parts of my memories ❤️

</p>

</section>

<!-- ======================================================
     MUSIC
======================================================= -->

<button class="music"
onclick="toggleMusic()">

🎵

</button>

<audio id="music" loop>

<source src="assets/music/song.mp3">

</audio>

<!-- ======================================================
     JAVASCRIPT
======================================================= -->

<script>

/* =========================================================
   OPENING ANIMATION
========================================================= */

gsap.from('.title',{

y:80,
opacity:0,
duration:1.8,
ease:'power3.out'

});

gsap.from('.text',{

y:40,
opacity:0,
delay:0.5,
duration:1.8

});

gsap.from('.btn',{

y:30,
opacity:0,
delay:1,
duration:1.5

});

/* =========================================================
   WORKING SCENE TRANSITION
========================================================= */

function nextScene(currentId,nextId){

const current =
document.getElementById(currentId);

const next =
document.getElementById(nextId);

/* PREPARE NEXT */

next.style.display='flex';

next.style.opacity='0';

next.style.transform='translateY(40px) scale(0.98)';

next.style.zIndex='20';

/* CURRENT OUT */

gsap.to(current,{

opacity:0,
scale:1.05,
duration:0.8,

onComplete:()=>{

current.classList.remove('active');

current.style.display='none';

/* SHOW NEXT */

next.classList.add('active');

gsap.to(next,{

opacity:1,
y:0,
scale:1,
duration:1

});

}

});

/* MUSIC */

document.getElementById('music').play();

/* LETTER */

if(nextId === 'scene3'){

setTimeout(()=>{

typeLetter();

},800);

}

}

/* =========================================================
   LETTER TYPING
========================================================= */

const text = `

Happy Birthday ❤️

Some people become memories.

Some become feelings.

And somehow...
you became both.

The kind of person whose smile
stays in someone's mind.

The kind of person whose presence
feels comforting.

I genuinely hope life gives you:

peace in your heart,
warmth in your soul,
success in your dreams,
and beautiful memories that never fade ✨

Celebrate yourself today.

Because the world became softer
the day you were born ❤️

`;

let i = 0;

function type(){

if(i < text.length){

document.getElementById('letter')
.innerHTML += text.charAt(i);

i++;

setTimeout(type,38);

}

}

function typeLetter(){

document.getElementById('letter').innerHTML='';

i=0;

type();

}

/* =========================================================
   MEMORY MESSAGE
========================================================= */

function showMessage(text){

alert(text);

}

/* =========================================================
   FLOWER EFFECT
========================================================= */

function openGift(el){

explode();

el.style.transform =
'scale(1.06)';

}

/* =========================================================
   PARTICLE EXPLOSION
========================================================= */

function explode(){

for(let i=0;i<70;i++){

let spark =
document.createElement('div');

spark.innerHTML='✨';

spark.style.position='fixed';

spark.style.left=
Math.random()*100+'vw';

spark.style.top=
Math.random()*100+'vh';

spark.style.fontSize='20px';

spark.style.pointerEvents='none';

spark.style.zIndex='9999';

document.body.appendChild(spark);

gsap.to(spark,{

y:-120,
opacity:0,
duration:1.5,

onComplete:()=>{

spark.remove();

}

});

}

}

/* =========================================================
   MUSIC
========================================================= */

function toggleMusic(){

const m =
document.getElementById('music');

if(m.paused){

m.play();

}else{

m.pause();

}

}

</script>

</body>
</html>
