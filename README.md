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

font-family:'Poppins',sans-serif;

overflow-x:hidden;

background:
linear-gradient(
135deg,
#1a0f1f,
#2a1021,
#4a1d3d,
#24122d
);

color:white;

}

/* =========================================================
LIGHTS
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
left:-120px;

opacity:0.25;

}

body::after{

background:#ffd166;

bottom:-180px;
right:-100px;

opacity:0.15;

}

/* =========================================================
PARTICLES
========================================================= */

.particle{

position:fixed;

width:6px;
height:6px;

border-radius:50%;

background:white;

opacity:0.2;

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
SCENE
========================================================= */

.scene{

min-height:100vh;

display:none;

justify-content:center;
align-items:center;
flex-direction:column;

padding:80px 25px;

text-align:center;

}

.scene.active{

display:flex;

animation:sceneFade 1s ease forwards;

}

@keyframes sceneFade{

from{
opacity:0;
transform:translateY(40px);
}

to{
opacity:1;
transform:translateY(0);
}

}

/* =========================================================
TEXT
========================================================= */

.label{

letter-spacing:8px;

opacity:0.7;

margin-bottom:25px;

font-size:12px;

}

.title{

font-size:5rem;

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

max-width:700px;

margin-top:35px;

line-height:2;

opacity:0.88;

font-size:17px;

}

/* =========================================================
BUTTON
========================================================= */

.btn{

margin-top:50px;

padding:18px 50px;

border:none;

border-radius:100px;

background:rgba(255,255,255,0.08);

color:white;

letter-spacing:4px;

cursor:pointer;

font-size:13px;

backdrop-filter:blur(20px);

transition:0.4s;

}

.btn:hover{

transform:
translateY(-5px)
scale(1.03);

background:rgba(255,255,255,0.14);

}

/* =========================================================
MEMORIES
========================================================= */

.memory-wrap{

display:flex;

flex-direction:column;

gap:25px;

margin-top:50px;

width:100%;

align-items:center;

}

.memory{

width:100%;
max-width:350px;

height:450px;

border-radius:30px;

overflow:hidden;

position:relative;

cursor:pointer;

transition:0.5s;

box-shadow:
0 20px 60px rgba(0,0,0,0.35);

}

.memory:hover{

transform:
translateY(-10px)
scale(1.02);

}

.memory img{

width:100%;
height:100%;

object-fit:cover;

transition:0.5s;

}

.memory:hover img{

transform:scale(1.08);

}

.memory-overlay{

position:absolute;

inset:0;

background:
linear-gradient(
to top,
rgba(0,0,0,0.95),
rgba(0,0,0,0.15)
);

display:flex;

align-items:flex-end;

padding:30px;

}

.memory-overlay h3{

font-size:24px;

}

/* =========================================================
LETTER
========================================================= */

.letter-box{

width:100%;
max-width:850px;

max-height:75vh;

overflow-y:auto;

background:rgba(255,255,255,0.05);

border:1px solid rgba(255,255,255,0.08);

border-radius:35px;

padding:35px;

backdrop-filter:blur(20px);

}

#letter{

white-space:pre-line;

line-height:2.2;

font-size:17px;

text-align:left;

}

/* =========================================================
GIFTS
========================================================= */

.gift-wrap{

display:flex;

flex-direction:column;

gap:25px;

margin-top:50px;

align-items:center;

width:100%;

}

.gift{

width:100%;
max-width:350px;

height:420px;

border-radius:35px;

overflow:hidden;

position:relative;

cursor:pointer;

transition:0.5s;

background:rgba(255,255,255,0.05);

}

.gift img{

width:100%;
height:100%;

object-fit:cover;

transition:0.5s;

}

.gift:hover{

transform:
translateY(-10px)
scale(1.02);

}

.gift:hover img{

transform:scale(1.08);

}

.gift-text{

position:absolute;

bottom:0;

width:100%;

padding:25px;

background:
linear-gradient(
to top,
rgba(0,0,0,0.95),
transparent
);

font-size:20px;

}

/* =========================================================
FINAL
========================================================= */

.final-title{

font-size:5rem;

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

max-width:700px;

margin-top:35px;

line-height:2;

font-size:17px;

opacity:0.88;

}

/* =========================================================
POPUP
========================================================= */

.popup{

position:fixed;

inset:0;

background:rgba(0,0,0,0.7);

backdrop-filter:blur(10px);

display:none;

justify-content:center;
align-items:center;

padding:20px;

z-index:99999;

}

.popup-box{

width:100%;
max-width:420px;

background:
linear-gradient(
135deg,
rgba(255,255,255,0.08),
rgba(255,255,255,0.03)
);

border:1px solid rgba(255,255,255,0.1);

border-radius:35px;

padding:35px;

position:relative;

overflow:hidden;

}

.popup-box h2{

font-size:30px;

margin-bottom:20px;

background:
linear-gradient(
90deg,
#ffd166,
#ff9ac2
);

-webkit-background-clip:text;
-webkit-text-fill-color:transparent;

}

.popup-box p{

line-height:2;

font-size:16px;

opacity:0.9;

}

.close{

position:absolute;

top:15px;
right:20px;

font-size:35px;

cursor:pointer;

}

/* =========================================================
ROSES
========================================================= */

.rose{

position:fixed;

top:-50px;

font-size:25px;

pointer-events:none;

z-index:999999;

animation:roseFall linear forwards;

}

@keyframes roseFall{

to{

transform:
translateY(110vh)
rotate(360deg);

opacity:0;

}

}

/* =========================================================
MUSIC BUTTON
========================================================= */

.music{

position:fixed;

right:20px;
bottom:20px;

width:65px;
height:65px;

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

@media(max-width:768px){

.title{
font-size:3.5rem;
}

.final-title{
font-size:3.5rem;
}

.text{
font-size:15px;
}

}

</style>
</head>

<body>

<!-- ======================================================
POPUP
======================================================= -->

<div id="popup" class="popup">

<div class="popup-box">

<span class="close" onclick="closePopup()">×</span>

<h2 id="popupTitle"></h2>

<p id="popupText"></p>

</div>

</div>

<!-- ======================================================
PARTICLES
======================================================= -->

<script>

for(let i=0;i<45;i++){

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

Happy Birthday Ginni ❤️

Today is all about you,
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
onclick="memoryPopup(
'Beautiful Moments ❤️',
'Your smile is honestly unforgettable. The kind of smile that stays in someone’s mind long after the moment passes. Every time you smiled in this memory, everything around felt lighter and happier ✨'
)">

<img src="photo1.jpeg">

<div class="memory-overlay">
<h3>Beautiful Moments ❤️</h3>
</div>

</div>

<div class="memory"
onclick="memoryPopup(
'Beautiful Energy ✨',
'There is something about your energy that feels peaceful and beautiful. The way you talk, laugh, and exist naturally makes moments feel special. Some people simply carry warmth within them — and you are one of them ❤️'
)">

<img src="photo2.jpeg">

<div class="memory-overlay">
<h3>Beautiful Energy ✨</h3>
</div>

</div>

<div class="memory"
onclick="memoryPopup(
'Forever Memories 🌸',
'Your smile, your personality, your caring nature, your laughter — all of it creates memories that never really fade. Some people are remembered because of moments. But some are remembered because of how they make people feel ❤️'
)">

<img src="photo3.jpeg">

<div class="memory-overlay">
<h3>Forever Memories 🌸</h3>
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
onclick="roseRain()">

<img src="assets/gifts/rose.jpg">

<div class="gift-text">
Roses For You 🌹
</div>

</div>

<div class="gift"
onclick="memoryPopup(
'A Bouquet Of Happiness 💐',
'I genuinely hope your life is always filled with happiness, peace, beautiful memories, success, and people who truly value your heart ❤️'
)">

<img src="photo5.jpg">

<div class="gift-text">
A Bouquet Of Happiness 💐
</div>

</div>

<div class="gift"
onclick="memoryPopup(
'Beautiful Like You ✨',
'No flower, no sunset, and no beautiful thing in this world could ever truly compare to your beauty — not just outside, but the beauty of your heart, smile, and soul ❤️'
)">

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
BIRTHDAY GINNI❤️
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
SCENE CHANGE
========================================================= */

function nextScene(currentId,nextId){

document.getElementById(currentId)
.classList.remove('active');

document.getElementById(nextId)
.classList.add('active');

window.scrollTo({
top:0,
behavior:'smooth'
});

document.getElementById('music').play();

if(nextId === 'scene3'){

setTimeout(()=>{

typeLetter();

},400);

}

}

/* =========================================================
LETTER
========================================================= */

const text = `

Happy Birthday GINNI❤️

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

Because its your day 
and i hope you will get all the happiness you deserve ❤️

`;

let i = 0;

function type(){

if(i < text.length){

document.getElementById('letter')
.innerHTML += text.charAt(i);

i++;

setTimeout(type,35);

}

}

function typeLetter(){

document.getElementById('letter').innerHTML='';

i=0;

type();

}

/* =========================================================
POPUP
========================================================= */

function memoryPopup(title,text){

document.getElementById('popup')
.style.display='flex';

document.getElementById('popupTitle')
.innerHTML = title;

document.getElementById('popupText')
.innerHTML = text;

gsap.from('.popup-box',{

y:80,
opacity:0,
duration:0.8,
ease:'power3.out'

});

}

/* =========================================================
CLOSE POPUP
========================================================= */

function closePopup(){

document.getElementById('popup')
.style.display='none';

}

/* =========================================================
ROSE RAIN
========================================================= */

function roseRain(){

memoryPopup(
'Roses For You 🌹',
'These roses are for your beautiful smile, your beautiful heart, and the happiness you bring into people’s lives ❤️'
);

for(let i=0;i<50;i++){

let rose =
document.createElement('div');

rose.classList.add('rose');

rose.innerHTML='🌹';

rose.style.left =
Math.random()*100 + 'vw';

rose.style.animationDuration =
3 + Math.random()*5 + 's';

document.body.appendChild(rose);

setTimeout(()=>{

rose.remove();

},7000);

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
