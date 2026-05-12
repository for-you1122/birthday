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

    overflow:hidden;

    color:white;

    background:
    linear-gradient(
        135deg,
        #120b14,
        #2a1021,
        #43233a,
        #1f1228
    );

}

/* =========================================================
   DREAMY BACKGROUND LIGHTS
========================================================= */

.bg-light{

    position:fixed;

    border-radius:50%;

    filter:blur(120px);

    z-index:-5;

    animation:floatLight 8s ease-in-out infinite;

}

.light1{

    width:450px;
    height:450px;

    background:#ff4d88;

    top:-120px;
    left:-120px;

    opacity:0.25;

}

.light2{

    width:500px;
    height:500px;

    background:#ffd166;

    bottom:-180px;
    right:-100px;

    opacity:0.18;

}

@keyframes floatLight{

    0%{
        transform:translateY(0px);
    }

    50%{
        transform:translateY(40px);
    }

    100%{
        transform:translateY(0px);
    }

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

    z-index:-3;

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

}

.active{
    display:flex;
}

/* =========================================================
   HERO
========================================================= */

.label{

    letter-spacing:8px;

    text-transform:uppercase;

    opacity:0.7;

    margin-bottom:25px;

    font-size:13px;

}

.hero-title{

    font-size:8rem;

    line-height:0.88;

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

    opacity:0;

    transform:translateY(80px);

}

.hero-text{

    max-width:760px;

    margin-top:40px;

    line-height:2;

    opacity:0.82;

    font-size:18px;

}

/* =========================================================
   BUTTON
========================================================= */

.btn{

    margin-top:55px;

    padding:20px 54px;

    border-radius:100px;

    border:none;

    background:rgba(255,255,255,0.08);

    color:white;

    backdrop-filter:blur(20px);

    letter-spacing:4px;

    cursor:pointer;

    transition:0.4s;

}

.btn:hover{

    transform:translateY(-5px) scale(1.03);

    background:rgba(255,255,255,0.15);

}

/* =========================================================
   MEMORY CARDS
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

    cursor:pointer;

    transition:0.5s;

    background:#111;

    box-shadow:
    0 10px 40px rgba(0,0,0,0.3);

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
        rgba(0,0,0,0.9),
        rgba(0,0,0,0.1)
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

    width:90%;
    max-width:950px;

    background:rgba(255,255,255,0.05);

    border:1px solid rgba(255,255,255,0.08);

    backdrop-filter:blur(30px);

    border-radius:40px;

    padding:70px;

}

#letter{

    line-height:2.3;

    font-size:18px;

    white-space:pre-line;

    opacity:0.9;

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

    max-width:700px;

    margin-top:40px;

    line-height:2;

    opacity:0.85;

}

/* =========================================================
   MOBILE
========================================================= */

@media(max-width:900px){

.hero-title{
    font-size:4.5rem;
}

.final-title{
    font-size:4rem;
}

.hero-text{
    font-size:15px;
}

.letter-box{
    padding:35px;
}

}

/* =========================================================
   FADE
========================================================= */

.fade-out{
    animation:fadeOut 1s forwards;
}

.fade-in{
    animation:fadeIn 1s forwards;
}

@keyframes fadeOut{

    to{
        opacity:0;
        transform:scale(1.05);
    }

}

@keyframes fadeIn{

    from{
        opacity:0;
    }

    to{
        opacity:1;
    }

}

</style>
</head>

<body>

<!-- DREAMY LIGHTS -->

<div class="bg-light light1"></div>
<div class="bg-light light2"></div>

<!-- PARTICLES -->

<script>

for(let i=0;i<40;i++){

    const particle =
    document.createElement('div');

    particle.classList.add('particle');

    particle.style.left =
    Math.random()*100 + 'vw';

    particle.style.animationDuration =
    5 + Math.random()*10 + 's';

    particle.style.opacity =
    Math.random()*0.4;

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

<h1 class="hero-title">
HAPPY<br>
BIRTHDAY
</h1>

<p class="hero-text">

Some people enter life quietly...

but somehow make everything feel softer,
warmer,
and more beautiful.

This experience was created
to celebrate not just your birthday —

but your existence ✨

</p>

<button class="btn" onclick="nextScene(1,2)">
ENTER THE EXPERIENCE
</button>

</section>

<!-- ======================================================
     SCENE 2
======================================================= -->

<section class="scene" id="scene2">

<p class="label">
MEMORIES
</p>

<h1 class="hero-title" style="font-size:6rem;">
MOMENTS<br>
THAT STAY
</h1>

<div class="memory-wrap">

<div class="memory">

<img src="assets/photos/photo1.jpg">

<div class="memory-overlay">
<h3>Beautiful Memories</h3>
</div>

</div>

<div class="memory">

<img src="assets/photos/photo2.jpg">

<div class="memory-overlay">
<h3>Late Night Talks</h3>
</div>

</div>

<div class="memory">

<img src="assets/photos/photo3.jpg">

<div class="memory-overlay">
<h3>Unforgettable Smiles</h3>
</div>

</div>

</div>

<button class="btn" onclick="nextScene(2,3)">
CONTINUE
</button>

</section>

<!-- ======================================================
     SCENE 3
======================================================= -->

<section class="scene" id="scene3">

<p class="label">
A LETTER
</p>

<div class="letter-box">

<div id="letter"></div>

</div>

<button class="btn" onclick="nextScene(3,4)">
FINAL SURPRISE
</button>

</section>

<!-- ======================================================
     SCENE 4
======================================================= -->

<section class="scene" id="scene4">

<h1 class="final-title">
HAPPY<br>
BIRTHDAY ❤️
</h1>

<p class="final-text">

May life always protect your smile.

May your heart always find peace.

May your dreams become reality.

And may you always be surrounded
by people and moments that truly deserve you.

Because honestly...

the world became a little more beautiful
the day you were born ✨

</p>

</section>

<!-- MUSIC -->

<audio id="music" loop>
<source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_c8c8e0b4f6.mp3?filename=romantic-background-11254.mp3">
</audio>

<script>

/* =========================================================
   HERO ANIMATION
========================================================= */

gsap.to('.hero-title',{

    opacity:1,
    y:0,
    duration:1.8,
    ease:'power3.out'

});

/* =========================================================
   SCENE TRANSITIONS
========================================================= */

function nextScene(current,next){

    const currentScene =
    document.getElementById(`scene${current}`);

    const nextScene =
    document.getElementById(`scene${next}`);

    currentScene.classList.add('fade-out');

    setTimeout(()=>{

        currentScene.classList.remove('active');

        nextScene.classList.add('active');

        nextScene.classList.add('fade-in');

    },900);

    document.getElementById('music').play();

    if(next === 3){

        typeLetter();

    }

}

/* =========================================================
   TYPING LETTER
========================================================= */

const text = `

Happy Birthday ❤️

There are some people
who become memories.

And then there are people
who become feelings.

You became both.

The kind of person whose presence feels comforting.

The kind of person whose smile stays in someone's mind.

The kind of person who unknowingly becomes important.

I genuinely hope life gives you:

peace in your heart,
warmth in your soul,
success in your dreams,
and beautiful memories that never fade.

You deserve happiness.
Real happiness.

Not just today —
but in every chapter ahead.

So today...

celebrate yourself.

Celebrate your existence.

Because this world became softer
the day you were born ✨

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

</script>

</body>
</html>
