<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Birthday Universe</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js"></script>

<style>

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

html{
  scroll-behavior:smooth;
}

body{
  font-family:'Poppins',sans-serif;
  background:#040404;
  color:white;
  overflow-x:hidden;
}

canvas{
  position:fixed;
  inset:0;
  z-index:-10;
}

/* NAVBAR */

.navbar{
  position:fixed;
  top:0;
  width:100%;
  display:flex;
  justify-content:space-between;
  align-items:center;
  padding:24px 60px;
  z-index:999;
  backdrop-filter:blur(12px);
}

.logo{
  font-size:18px;
  letter-spacing:4px;
  color:#d6b36a;
}

.nav-links{
  display:flex;
  gap:28px;
}

.nav-links a{
  color:white;
  text-decoration:none;
  opacity:0.8;
  transition:0.3s;
}

.nav-links a:hover{
  opacity:1;
}

/* HERO */

.hero{
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  position:relative;
  text-align:center;
  padding:40px;
}

.hero::before{
  content:'';
  position:absolute;
  inset:0;
  background:radial-gradient(circle at center,
  rgba(255,255,255,0.06),
  rgba(0,0,0,0.92));
}

.hero-content{
  position:relative;
  z-index:2;
  max-width:1100px;
}

.hero-label{
  letter-spacing:10px;
  text-transform:uppercase;
  opacity:0.65;
  margin-bottom:28px;
}

.hero-title{
  font-size:9rem;
  line-height:0.9;
  font-weight:700;

  background:linear-gradient(
  90deg,
  #ffffff,
  #d6b36a,
  #ffffff);

  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

.hero-text{
  max-width:750px;
  margin:40px auto 0;
  line-height:2;
  opacity:0.82;
  font-size:18px;
}

.enter-btn{
  margin-top:50px;
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

.enter-btn:hover{
  transform:translateY(-6px);
  background:rgba(255,255,255,0.12);
}

/* SECTION */

.section{
  min-height:100vh;
  padding:140px 10%;
  position:relative;
}

.section-small{
  letter-spacing:6px;
  opacity:0.6;
  margin-bottom:20px;
}

.section-title{
  font-size:5rem;
  margin-bottom:30px;
}

.section-text{
  max-width:750px;
  line-height:2;
  opacity:0.82;
}

/* MEMORY GRID */

.memory-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
  gap:30px;
  margin-top:70px;
}

.memory-card{
  height:380px;
  border-radius:28px;
  overflow:hidden;
  position:relative;
  background:#111;
  cursor:pointer;
  transition:0.4s;
}

.memory-card:hover{
  transform:translateY(-10px) scale(1.02);
}

.memory-card img{
  width:100%;
  height:100%;
  object-fit:cover;
}

.memory-overlay{
  position:absolute;
  inset:0;
  background:linear-gradient(to top,
  rgba(0,0,0,0.9),
  rgba(0,0,0,0.1));

  display:flex;
  align-items:flex-end;
  padding:30px;
}

.memory-overlay h3{
  font-size:24px;
}

/* LETTER */

.letter-box{
  margin-top:60px;
  background:rgba(255,255,255,0.04);
  border:1px solid rgba(255,255,255,0.08);
  border-radius:40px;
  padding:70px;
  backdrop-filter:blur(20px);
}

.letter-text{
  line-height:2.4;
  font-size:18px;
  opacity:0.9;
  white-space:pre-line;
}

/* GIFT */

.gift-grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:30px;
  margin-top:70px;
}

.gift-card{
  height:260px;
  border-radius:30px;
  background:rgba(255,255,255,0.04);
  border:1px solid rgba(255,255,255,0.08);
  display:flex;
  justify-content:center;
  align-items:center;
  font-size:70px;
  cursor:pointer;
  transition:0.4s;
}

.gift-card:hover{
  transform:translateY(-8px);
}

/* CAKE */

.cake-wrap{
  display:flex;
  justify-content:center;
  margin-top:80px;
}

.cake{
  font-size:200px;
  cursor:pointer;
  transition:0.4s;
}

.cake:hover{
  transform:scale(1.05);
}

/* FINAL */

.final{
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  position:relative;
}

.final h1{
  font-size:8rem;

  background:linear-gradient(
  90deg,
  #ffffff,
  #d6b36a,
  #ffffff);

  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

.final p{
  max-width:700px;
  margin:40px auto 0;
  line-height:2;
  opacity:0.82;
}

/* MUSIC */

.music-btn{
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
  backdrop-filter:blur(20px);
  z-index:999;
}

/* MOBILE */

@media(max-width:900px){

.navbar{
  padding:20px;
}

.hero-title{
  font-size:4.5rem;
}

.section-title{
  font-size:3rem;
}

.final h1{
  font-size:4rem;
}

.letter-box{
  padding:35px;
}

.cake{
  font-size:120px;
}

}

</style>
</head>
<body>

<canvas id="bg"></canvas>

<!-- NAVBAR -->

<div class="navbar">
  <div class="logo">BIRTHDAY UNIVERSE</div>

  <div class="nav-links">
    <a href="#story">Story</a>
    <a href="#memories">Memories</a>
    <a href="#letter">Letter</a>
    <a href="#gifts">Gifts</a>
  </div>
</div>

<!-- HERO -->

<section class="hero">

<div class="hero-content">

<p class="hero-label">
FOR SOMEONE SPECIAL
</p>

<h1 class="hero-title">
HAPPY<br>
BIRTHDAY
</h1>

<p class="hero-text">
This is not just a birthday website.
It is an immersive cinematic experience inspired by emotions,
memories, luxury storytelling, and timeless moments.

Some people become memories.
Some become feelings.
And some quietly become part of your life in a way words can never fully explain.
</p>

<button class="enter-btn" onclick="scrollToSection()">
ENTER THE EXPERIENCE
</button>

</div>

</section>

<!-- STORY -->

<section class="section" id="story">

<p class="section-small">
THE STORY
</p>

<h2 class="section-title">
A Beautiful Presence
</h2>

<p class="section-text">
Some birthdays are celebrated with candles.
Some with gifts.
Some with parties.

But some people deserve something deeper.

A memory.
A feeling.
An experience.

Today is not just about celebrating another year.
It is about celebrating your existence.

The kindness you carry.
The energy you bring.
The smile that unknowingly changes someone's mood.
The memories you leave behind in small ordinary moments.

The world became softer the day you were born.
</p>

</section>

<!-- MEMORIES -->

<section class="section" id="memories">

<p class="section-small">
MEMORIES
</p>

<h2 class="section-title">
Moments That Stay
</h2>

<div class="memory-grid">

<div class="memory-card">
<img src="https://images.unsplash.com/photo-1517841905240-472988babdf9?q=80&w=1200&auto=format&fit=crop" />
<div class="memory-overlay">
<h3>Beautiful Conversations</h3>
</div>
</div>

<div class="memory-card">
<img src="https://images.unsplash.com/photo-1524504388940-b1c1722653e1?q=80&w=1200&auto=format&fit=crop" />
<div class="memory-overlay">
<h3>Late Night Talks</h3>
</div>
</div>

<div class="memory-card">
<img src="https://images.unsplash.com/photo-1511988617509-a57c8a288659?q=80&w=1200&auto=format&fit=crop" />
<div class="memory-overlay">
<h3>Unforgettable Laughs</h3>
</div>
</div>

</div>

</section>

<!-- LETTER -->

<section class="section" id="letter">

<p class="section-small">
A LETTER
</p>

<h2 class="section-title">
To Someone Truly Rare
</h2>

<div class="letter-box">

<div class="letter-text">
Happy Birthday ❤️

There are some people who enter life quietly...
but somehow leave an impact deeper than loud moments ever could.

You are one of those people.

The kind of person whose presence feels calming.
The kind of person whose smile stays in someone's mind longer than expected.
The kind of person who unknowingly becomes important.

I genuinely hope life gives you everything beautiful.
Not just success.
Not just achievements.

But peace.
Warmth.
Safety.
Real happiness.
People who understand you.
Moments that heal you.
Dreams that finally come true.

I hope one day you look back at your life and realize:

how loved you were,
how valued you were,
and how much light you brought into the lives around you.

Because honestly...
this world became a little more beautiful the day you were born.

So today,
celebrate yourself.
Celebrate your existence.
Celebrate the person you are becoming.

✨ Happy Birthday ✨

</div>

</div>

</section>

<!-- GIFTS -->

<section class="section" id="gifts">

<p class="section-small">
SURPRISES
</p>

<h2 class="section-title">
Little Moments
</h2>

<div class="gift-grid">

<div class="gift-card" onclick="openGift(this)">
🎁
</div>

<div class="gift-card" onclick="openGift(this)">
🎁
</div>

<div class="gift-card" onclick="openGift(this)">
🎁
</div>

<div class="gift-card" onclick="openGift(this)">
🎁
</div>

</div>

</section>

<!-- CAKE -->

<section class="section">

<p class="section-small">
MAKE A WISH
</p>

<h2 class="section-title">
A Moment To Celebrate
</h2>

<div class="cake-wrap">
<div class="cake" onclick="blowCandle()">
🕯️🕯️🕯️🎂
</div>
</div>

</section>

<!-- FINAL -->

<section class="final">

<div>
<h1>
HAPPY BIRTHDAY
</h1>

<p>
May life always protect your smile,
bring peace to your heart,
and surround you with people and moments that truly deserve you.

You deserve beautiful things.
Always.
</p>
</div>

</section>

<!-- MUSIC -->

<button class="music-btn" onclick="toggleMusic()">
🎵
</button>

<audio id="music" loop>
<source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8c8e0b4f6.mp3?filename=romantic-background-11254.mp3">
</audio>

<script>

/* THREE JS */

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

const geometry = new THREE.BufferGeometry();

const count = 15000;

const positions = new Float32Array(count*3);

for(let i=0;i<count*3;i++){
positions[i] = (Math.random()-0.5)*2000;
}

geometry.setAttribute(
'position',
new THREE.BufferAttribute(positions,3)
);

const material = new THREE.PointsMaterial({
color:0xffffff,
size:0.7
});

const stars = new THREE.Points(geometry,material);

scene.add(stars);

function animate(){
requestAnimationFrame(animate);

stars.rotation.y += 0.00015;
stars.rotation.x += 0.00005;

renderer.render(scene,camera);
}

animate();

window.addEventListener('resize',()=>{

camera.aspect = window.innerWidth/window.innerHeight;

camera.updateProjectionMatrix();

renderer.setSize(window.innerWidth,window.innerHeight);

});

/* BUTTON */

function scrollToSection(){

document.getElementById('story').scrollIntoView({
behavior:'smooth'
});

const m = document.getElementById('music');

m.play();

}

/* GIFT */

function openGift(el){

el.innerHTML = '💖';

el.style.background = 'rgba(255,255,255,0.1)';

explode();

}

/* CAKE */

function blowCandle(){

document.querySelector('.cake').innerHTML = '🎂✨';

explode();

}

/* EXPLOSION */

function explode(){

for(let i=0;i<80;i++){

let spark = document.createElement('div');

spark.innerHTML = '✨';

spark.style.position='fixed';
spark.style.left=Math.random()*100+'vw';
spark.style.top=Math.random()*100+'vh';
spark.style.fontSize='20px';

spark.style.pointerEvents='none';

spark.style.zIndex='9999';

spark.style.transition='1.5s';

spark.style.opacity='1';



document.body.appendChild(spark);

setTimeout(()=>{

spark.style.opacity='0';

spark.style.transform='translateY(-100px)';

},100);

setTimeout(()=>{

spark.remove();

},1600);

}

}

/* MUSIC */

function toggleMusic(){

const m = document.getElementById('music');

if(m.paused){
m.play();
}else{
m.pause();
}

}

/* GSAP */

gsap.from('.hero-title',{
y:80,
opacity:0,
duration:1.5
});

gsap.from('.hero-text',{
y:50,
opacity:0,
delay:0.4,
duration:1.5
});

gsap.from('.enter-btn',{
y:40,
opacity:0,
delay:0.7,
duration:1.5
});

</script>

</body>
</html
