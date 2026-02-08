<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>For Jenika 💖</title>

<style>
body{
margin:0;
background:maroon;
color:#000;
font-family:Arial;
overflow:hidden;
text-align:center;
}

/* Screens */
.screen{
position:absolute;
width:100%;
height:100%;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
z-index:3;
}

.hidden{display:none;}

button{
background:pink;
border:none;
padding:12px 25px;
margin:10px;
border-radius:8px;
font-size:18px;
cursor:pointer;
}

#name{
font-size:32px;
font-weight:bold;
animation:pulse 1.5s infinite;
}

/* pulse name */
@keyframes pulse{
0%{transform:scale(1);}
50%{transform:scale(1.15);}
100%{transform:scale(1);}
}

/* rose ring */
.ring{
position:fixed;
top:50%;
left:50%;
width:320px;
height:320px;
border-radius:50%;
transform:translate(-50%,-50%);
pointer-events:none;
z-index:1;
}

.ring span{
position:absolute;
font-size:22px;
}

/* floating */
.float{
position:absolute;
animation:up 4s linear;
font-size:24px;
}

.ringemoji{
position:absolute;
font-size:60px;
z-index:10;
}

/* permanent roses */
.bg{
position:fixed;
font-size:26px;
opacity:.3;
z-index:0;
}

@keyframes up{
from{transform:translateY(0);opacity:1;}
to{transform:translateY(-120vh);opacity:0;}
}
</style>
</head>

<body>

<audio id="music" loop>
<source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3">
</audio>

<script>
// background roses
for(let i=0;i<35;i++){
let b=document.createElement("div");
b.className="bg";
b.innerText=Math.random()>0.5?"🌹":"💐";
b.style.left=Math.random()*100+"vw";
b.style.top=Math.random()*100+"vh";
document.body.appendChild(b);
}
</script>

<div class="ring" id="ring"></div>

<div id="s1" class="screen">
<h1 id="type"></h1>
<h2 id="name">Jenika 💖</h2>
<button onclick="start()">YES</button>
</div>

<div id="s2" class="screen hidden">
<h1>Will you be mine forever? ❤️</h1>
<button id="yes" onclick="yes()">YES</button>
<button onclick="no()">NO</button>
<p id="msg"></p>
</div>

<div id="s3" class="screen hidden">
<h1>I knew you would choose me 🥹❤️</h1>
<h2>My forever Jenika 💖</h2>
</div>

<script>
// typing effect
const text="Happy Propose Day My Love";
let i=0;
setInterval(()=>{
if(i<text.length){
document.getElementById("type").innerHTML+=text[i];
i++;
}
},100);

// rose ring
const ring=document.getElementById("ring");
const emojis=["🌹","💐","❤️"];
for(let i=0;i<36;i++){
let s=document.createElement("span");
s.innerText=emojis[i%3];
ring.appendChild(s);
}

function arrange(){
for(let i=0;i<ring.children.length;i++){
let a=(i/ring.children.length)*Math.PI*2;
ring.children[i].style.left=160+Math.cos(a)*140+"px";
ring.children[i].style.top=160+Math.sin(a)*140+"px";
}
}
arrange();

let deg=0;
setInterval(()=>{
deg++;
ring.style.transform=`translate(-50%,-50%) rotate(${deg}deg)`;
},40);

const music=document.getElementById("music");
const s1=document.getElementById("s1");
const s2=document.getElementById("s2");
const s3=document.getElementById("s3");
const msg=document.getElementById("msg");
const yesBtn=document.getElementById("yes");

function start(){
music.play();
s1.classList.add("hidden");
s2.classList.remove("hidden");
}

// YES click -> show ring emoji + fireworks
function yes(){
fireworks();
showRing();
s2.classList.add("hidden");
s3.classList.remove("hidden");
}

// NO button
function no(){
msg.innerText="Please say YES 🥺";
yesBtn.style.transform=`translate(${Math.random()*400-200}px,${Math.random()*400-200}px)`;
}

// floating hearts
function heart(){
let h=document.createElement("div");
h.className="float";
h.innerText="❤️";
h.style.left=Math.random()*100+"vw";
h.style.top="100vh";
document.body.appendChild(h);
setTimeout(()=>h.remove(),4000);
}
setInterval(heart,600);

// floating ring emoji
function ringFloat(){
let r=document.createElement("div");
r.className="ringemoji";
r.innerText="💍";
r.style.left=Math.random()*100+"vw";
r.style.top="100vh";
document.body.appendChild(r);
setTimeout(()=>r.remove(),5000);
}
setInterval(ringFloat,1800);

// pop-up ring in center
function showRing(){
let r=document.createElement("div");
r.className="ringemoji";
r.innerText="💍";
r.style.top="30%"; // above text
r.style.left="50%";
document.body.appendChild(r);
setTimeout(()=>r.remove(),2500);
}

// sparkles
setInterval(()=>{
let s=document.createElement("div");
s.className="sparkle";
s.innerText="✨";
s.style.left=Math.random()*100+"vw";
s.style.top=Math.random()*100+"vh";
document.body.appendChild(s);
setTimeout(()=>s.remove(),2000);
},500);

// fireworks
function fireworks(){
for(let i=0;i<20;i++){
let f=document.createElement("div");
f.className="fire";
f.innerText="🎆";
f.style.left=Math.random()*100+"vw";
f.style.top=Math.random()*100+"vh";
document.body.appendChild(f);
setTimeout(()=>f.remove(),1500);
}
}
</script>

</body>
</html>
