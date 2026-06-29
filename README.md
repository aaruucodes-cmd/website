<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Singh Electronics | Premium Experience</title>

<!-- =========================
     GOOGLE FONT
========================== -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">

<!-- =========================
THREE JS
========================== -->

<script src="https://cdn.jsdelivr.net/npm/three@0.164/build/three.min.js"></script>

<!-- GSAP -->

<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/gsap.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/gsap@3/dist/ScrollTrigger.min.js"></script>

<!-- LENIS -->

<script src="https://cdn.jsdelivr.net/npm/@studio-freight/lenis@1/bundled/lenis.min.js"></script>

<style>

:root{

--bg:#050505;
--card:#111111;
--glass:rgba(255,255,255,.07);
--glass2:rgba(255,255,255,.04);
--line:rgba(255,255,255,.09);
--blue:#00BFFF;
--silver:#C0C0C0;
--white:#fff;

}

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Inter,sans-serif;
}

html{
scroll-behavior:smooth;
}

body{

background:var(--bg);
overflow-x:hidden;
color:white;

}

/* background */

body::before{

content:'';

position:fixed;

inset:0;

background:

radial-gradient(circle at 20% 20%,rgba(0,191,255,.15),transparent 30%),

radial-gradient(circle at 80% 40%,rgba(0,191,255,.12),transparent 25%),

radial-gradient(circle at 50% 90%,rgba(255,255,255,.05),transparent 40%),

#050505;

z-index:-5;

}

/* Noise */

body::after{

content:"";

position:fixed;

inset:0;

background-image:url("https://www.transparenttextures.com/patterns/asfalt-light.png");

opacity:.04;

pointer-events:none;

z-index:-4;

}

a{

color:inherit;
text-decoration:none;

}

canvas{

display:block;

}

/* =====================
CUSTOM CURSOR
===================== */

.cursor{

width:20px;
height:20px;

border:2px solid var(--blue);

border-radius:50%;

position:fixed;

pointer-events:none;

z-index:99999;

transform:translate(-50%,-50%);

transition:.08s;

backdrop-filter:blur(10px);

}

.cursor2{

position:fixed;

width:6px;

height:6px;

background:var(--blue);

border-radius:50%;

pointer-events:none;

z-index:99999;

transform:translate(-50%,-50%);

}

/* =======================
NAVBAR
======================= */

nav{

position:fixed;

top:20px;

left:50%;

transform:translateX(-50%);

width:min(1300px,95%);

height:80px;

border:1px solid rgba(255,255,255,.09);

backdrop-filter:blur(25px);

background:rgba(17,17,17,.55);

display:flex;

align-items:center;

justify-content:space-between;

padding:0 40px;

border-radius:100px;

z-index:9999;

}

.logo{

font-size:28px;

font-weight:800;

letter-spacing:2px;

background:linear-gradient(90deg,#fff,#00BFFF);

-webkit-background-clip:text;

-webkit-text-fill-color:transparent;

}

nav ul{

display:flex;

gap:35px;

list-style:none;

}

nav li{

position:relative;

cursor:pointer;

font-size:15px;

}

nav li::after{

content:'';

position:absolute;

left:0;

bottom:-8px;

height:2px;

width:0;

background:var(--blue);

transition:.4s;

}

nav li:hover::after{

width:100%;

}

.nav-btn{

padding:14px 28px;

border-radius:100px;

background:linear-gradient(135deg,#00BFFF,#1d6fff);

font-weight:700;

box-shadow:0 0 40px rgba(0,191,255,.4);

}

/* ===================
HERO
=================== */

.hero{

position:relative;

height:100vh;

display:flex;

align-items:center;

padding:0 8%;

overflow:hidden;

}

#scene{

position:absolute;

inset:0;

z-index:0;

}

.hero-content{

position:relative;

z-index:5;

max-width:720px;

}

.tag{

display:inline-flex;

padding:12px 25px;

border-radius:50px;

background:var(--glass);

border:1px solid rgba(255,255,255,.08);

backdrop-filter:blur(30px);

margin-bottom:30px;

font-size:14px;

color:#ddd;

}

.hero h1{

font-size:clamp(50px,7vw,100px);

line-height:.95;

font-weight:900;

margin-bottom:25px;

}

.hero h1 span{

background:linear-gradient(90deg,#00BFFF,#ffffff);

-webkit-background-clip:text;

-webkit-text-fill-color:transparent;

}

.hero p{

font-size:20px;

line-height:1.8;

color:#bbb;

margin-bottom:40px;

}

.btns{

display:flex;

gap:20px;

}

.btn{

padding:18px 36px;

border-radius:100px;

background:var(--glass);

backdrop-filter:blur(25px);

border:1px solid rgba(255,255,255,.08);

transition:.45s;

cursor:pointer;

font-weight:700;

}

.primary{

background:linear-gradient(135deg,#00BFFF,#005dff);

box-shadow:0 0 45px rgba(0,191,255,.5);

}

.btn:hover{

transform:translateY(-6px) scale(1.03);

}

.glass-card{

position:absolute;

width:240px;

height:150px;

background:rgba(255,255,255,.05);

backdrop-filter:blur(30px);

border:1px solid rgba(255,255,255,.08);

border-radius:30px;

box-shadow:0 0 40px rgba(0,191,255,.1);

}

.card1{

right:9%;

top:18%;

}

.card2{

right:18%;

bottom:14%;

}

.card3{

right:36%;

bottom:22%;

width:180px;

height:180px;

}

/* sections */

section{

padding:120px 8%;

position:relative;

}

.title{

font-size:58px;

font-weight:900;

margin-bottom:20px;

}

.subtitle{

max-width:700px;

color:#b8b8b8;

line-height:1.8;

margin-bottom:70px;

}

.grid{

display:grid;

grid-template-columns:repeat(auto-fit,minmax(250px,1fr));

gap:35px;

}

.category{

position:relative;

padding:35px;

border-radius:28px;

background:var(--glass);

border:1px solid rgba(255,255,255,.08);

overflow:hidden;

transition:.5s;

transform-style:preserve-3d;

}

.category::before{

content:'';

position:absolute;

width:180px;

height:180px;

background:radial-gradient(var(--blue),transparent);

filter:blur(80px);

top:-80px;

right:-80px;

opacity:.3;

}

.category:hover{

transform:rotateX(8deg) rotateY(-8deg) translateY(-10px);

box-shadow:0 30px 80px rgba(0,191,255,.18);

}

.icon{

font-size:60px;

margin-bottom:25px;

}

.category h3{

margin-bottom:15px;

font-size:25px;

}

.category p{

line-height:1.8;

color:#bdbdbd;

}

/* product */

.products{

display:grid;

grid-template-columns:repeat(auto-fit,minmax(290px,1fr));

gap:35px;

}

.product{

background:rgba(255,255,255,.05);

border-radius:30px;

padding:25px;

border:1px solid rgba(255,255,255,.08);

transition:.45s;

overflow:hidden;

position:relative;

}

.product:hover{

transform:translateY(-10px);

box-shadow:0 30px 80px rgba(0,191,255,.2);

}

.product img{

width:100%;

height:240px;

object-fit:contain;

transition:.5s;

}

.product:hover img{

transform:scale(1.08) rotate(-2deg);

}

.badge{

display:inline-block;

padding:8px 16px;

border-radius:100px;

background:#00BFFF;

font-size:12px;

font-weight:700;

margin-bottom:20px;

}

.price{

font-size:30px;

font-weight:800;

margin:18px 0;

}

.buy{

width:100%;

padding:15px;

border:none;

border-radius:100px;

background:linear-gradient(135deg,#00BFFF,#0057ff);

color:white;

font-weight:800;

cursor:pointer;

}

#threeCanvas{

position:absolute;
inset:0;

}

</style>
</head>

<body>

<div class="cursor"></div>
<div class="cursor2"></div>

<nav>

<div class="logo">
SINGH ELECTRONICS
</div>

<ul>

<li>Home</li>
<li>Products</li>
<li>Brands</li>
<li>Services</li>
<li>Gallery</li>
<li>Contact</li>

</ul>

<a class="nav-btn">
Visit Store
</a>

</nav>

<header class="hero">

<div id="scene"></div>

<div class="hero-content">

<div class="tag">

⚡ Premium Electronics Destination

</div>

<h1>

Future Of

<span>Technology</span>

Starts Here.

</h1>

<p>

Experience India's most premium digital electronics showroom with luxury products, immersive technology, cinematic shopping experience and trusted after-sales support.

</p>

<div class="btns">

<div class="btn primary">
Explore Collection
</div>

<div class="btn">
Book Demo
</div>

</div>

</div>

<div class="glass-card card1"></div>

<div class="glass-card card2"></div>

<div class="glass-card card3"></div>

</header>

<section>

<h2 class="title">

Shop By Category

</h2>

<p class="subtitle">

Explore premium gadgets curated from the world's biggest technology brands.

</p>

<div class="grid">

<div class="category">

<div class="icon">📱</div>

<h3>Smartphones</h3>

<p>Latest flagship phones from Apple Samsung Xiaomi and OnePlus.</p>

</div>

<div class="category">

<div class="icon">💻</div>

<h3>Laptops</h3>

<p>Powerful laptops for gaming creators business and students.</p>

</div>

<div class="category">

<div class="icon">📺</div>

<h3>Televisions</h3>

<p>4K OLED QLED Mini LED premium smart televisions.</p>

</div>

<div class="category">

<div class="icon">🎧</div>

<h3>Headphones</h3>

<p>Immersive wireless audio with premium sound quality.</p>

</div>

</div>

</section>

<script>

const cursor=document.querySelector(".cursor");
const cursor2=document.querySelector(".cursor2");

window.addEventListener("mousemove",(e)=>{

cursor.style.left=e.clientX+"px";
cursor.style.top=e.clientY+"px";

cursor2.style.left=e.clientX+"px";
cursor2.style.top=e.clientY+"px";

});

const lenis=new Lenis();

function raf(t){

lenis.raf(t);

requestAnimationFrame(raf);

}

requestAnimationFrame(raf);

gsap.registerPlugin(ScrollTrigger);

gsap.from(".hero h1",{

y:120,
opacity:0,
duration:1.3

});

gsap.from(".hero p",{

y:80,
opacity:0,
delay:.5

});

gsap.from(".btn",{

scale:.8,
opacity:0,
duration:1,
stagger:.15,
delay:.8

});

/* THREE JS */

const scene=new THREE.Scene();

scene.fog=new THREE.Fog(0x050505,12,40);

const camera=new THREE.PerspectiveCamera(
60,
window.innerWidth/window.innerHeight,
0.1,
1000
);

camera.position.set(0,1,8);

const renderer=new THREE.WebGLRenderer({
alpha:true,
antialias:true
});

renderer.setPixelRatio(window.devicePixelRatio);

renderer.setSize(window.innerWidth,window.innerHeight);

document.getElementById("scene").appendChild(renderer.domElement);

const ambient=new THREE.AmbientLight(0x00bfff,2);

scene.add(ambient);

const light=new THREE.PointLight(0xffffff,3);

light.position.set(3,5,5);

scene.add(light);

/* Phone */

const phone=new THREE.Mesh(

new THREE.BoxGeometry(1.1,2.2,.12),

new THREE.MeshPhysicalMaterial({

color:0x111111,

metalness:1,

roughness:.15,

clearcoat:1

})

);

scene.add(phone);

phone.position.x=-2.5;

phone.rotation.y=.4;

/* Laptop */

const laptop=new THREE.Group();

const base=new THREE.Mesh(

new THREE.BoxGeometry(2.4,.1,1.6),

new THREE.MeshStandardMaterial({

color:0x333333,
metalness:1

})

);

const screen=new THREE.Mesh(

new THREE.BoxGeometry(2.3,1.5,.05),

new THREE.MeshStandardMaterial({

color:0x00bfff,

emissive:0x00bfff,

emissiveIntensity:.4

})

);

screen.position.y=.8;
screen.position.z=-.75;
screen.rotation.x=-.5;

laptop.add(base);

laptop.add(screen);

scene.add(laptop);

laptop.position.x=2;

const ring=new THREE.Mesh(

new THREE.TorusGeometry(3,.02,30,120),

new THREE.MeshBasicMaterial({

color:0x00bfff

})

);

scene.add(ring);

function animate(){

requestAnimationFrame(animate);

phone.rotation.y+=.01;

laptop.rotation.y-=.006;

ring.rotation.x+=.003;

ring.rotation.y+=.004;

renderer.render(scene,camera);

}

animate();

window.addEventListener("resize",()=>{

camera.aspect=window.innerWidth/window.innerHeight;

camera.updateProjectionMatrix();

renderer.setSize(window.innerWidth,window.innerHeight);

});

</script>

</body>
</html>
