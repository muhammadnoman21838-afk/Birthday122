<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Khushi 💖 Final Boss</title>

<style>
body{
margin:0;
font-family:sans-serif;
background:black;
overflow:hidden;
color:white;
text-align:center;
}

/* SPLASH */
#splash{
position:fixed;
width:100%;
height:100%;
background:linear-gradient(135deg,#ff4b5c,#ff9a9e);
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
z-index:10;
animation:fadeOut 2.5s forwards;
animation-delay:2s;
}

@keyframes fadeOut{
to{opacity:0; visibility:hidden;}
}

/* LOGIN */
#login{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
padding:20px;
background:rgba(255,255,255,0.1);
backdrop-filter:blur(10px);
border-radius:15px;
}

input{
padding:10px;
border:none;
border-radius:10px;
margin-top:10px;
}

button{
padding:10px 20px;
margin-top:10px;
border:none;
border-radius:10px;
background:#ff4b5c;
color:white;
cursor:pointer;
}

/* MAIN */
.container{
padding:20px;
opacity:0;
animation:show 1s forwards;
animation-delay:3s;
}

@keyframes show{
to{opacity:1;}
}

/* glow title */
h1{
text-shadow:0 0 15px pink;
}

/* image */
img{
width:90%;
max-width:280px;
border-radius:15px;
margin-top:10px;
transition:0.5s;
}

/* hearts */
.heart{
position:absolute;
color:pink;
animation:floatUp 5s linear infinite;
}

@keyframes floatUp{
0%{transform:translateY(100vh);}
100%{transform:translateY(-10vh); opacity:0;}
}

/* stars */
.star{
position:absolute;
width:2px;
height:2px;
background:white;
animation:twinkle 2s infinite;
}

@keyframes twinkle{
0%{opacity:0;}
50%{opacity:1;}
100%{opacity:0;}
}

/* FINAL SCREEN */
#end{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
display:none;
}

</style>
</head>

<body>

<!-- SPLASH -->
<div id="splash">
<h1>💖 Loading Surprise...</h1>
<p>For Khushi 🎂</p>
</div>

<!-- LOGIN -->
<div id="login">
<h2>Enter Password 💖</h2>
<input type="password" id="pass">
<br>
<button onclick="check()">Unlock</button>
</div>

<!-- MAIN -->
<div class="container hidden" id="main">
<h1>🎂 Happy Birthday Khushi 💖</h1>

<div id="text"></div>

<img id="img" src="https://images.unsplash.com/photo-1524504388940-b1c1722653e1">

<br>
<button onclick="final()">Open Surprise 🎁</button>
</div>

<!-- END -->
<div id="end">
<h2>💖 Final Message 💖</h2>
<p>
Tu meri bestie hai... aur hamesha special rahegi 🫶<br><br>
Teri smile meri duniya hai 😊<br><br>
Har moment priceless hai 💖<br><br>
I’m lucky to have you Khushi 🎂<br><br>
— Noman ❤️
</p>
</div>

<script>

/* password */
function check(){
if(pass.value==="Shonaaaa"){
login.style.display="none";
document.getElementById("main").classList.remove("hidden");
type();
slider();
hearts();
stars();
}else{
alert("Wrong Password 😜");
}
}

/* typing */
let msg="Tu meri bestie hai... aur tu hamesha special rahegi 💖";
let i=0;

function type(){
if(i<msg.length){
text.innerHTML+=msg[i];
i++;
setTimeout(type,40);
}
}

/* slider */
let pics=[
"https://images.unsplash.com/photo-1524504388940-b1c1722653e1",
"https://images.unsplash.com/photo-1506863530036-1efeddceb993",
"https://images.unsplash.com/photo-1511988617509-a57c8a288659",
"https://images.unsplash.com/photo-1529626455594-4ff0802cfb7e"
];

let j=0;
setInterval(()=>{
j=(j+1)%pics.length;
img.src=pics[j];
},2000);

/* hearts */
setInterval(()=>{
let h=document.createElement("div");
h.className="heart";
h.innerHTML="❤️";
h.style.left=Math.random()*100+"%";
document.body.appendChild(h);
setTimeout(()=>h.remove(),5000);
},300);

/* stars */
function stars(){
for(let i=0;i<80;i++){
let s=document.createElement("div");
s.className="star";
s.style.left=Math.random()*100+"%";
s.style.top=Math.random()*100+"%";
document.body.appendChild(s);
}
}
stars();

/* final */
function final(){
document.getElementById("main").style.display="none";
document.getElementById("end").style.display="block";

/* controlled fireworks */
let count=0;
let fire=setInterval(()=>{
let f=document.createElement("div");
f.innerHTML="🎆";
f.style.position="absolute";
f.style.left=Math.random()*100+"%";
f.style.top=Math.random()*100+"%";
f.style.fontSize="25px";
document.body.appendChild(f);

setTimeout(()=>f.remove(),2000);

count++;
if(count>25) clearInterval(fire);

},120);
}

</script>

</body>
</html>
