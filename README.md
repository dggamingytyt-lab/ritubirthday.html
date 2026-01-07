# ritubirthday.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday Ritu 🌸</title>
<style>
/* Body and gradient background */
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
  height: 100vh;
  overflow: hidden;
  background: linear-gradient(to top, #ffe6f0, #ffd6e8);
  display: flex;
  justify-content: center;
  align-items: center;
}

/* Floating petals */
.petal {
  position: absolute;
  font-size: 24px;
  opacity: 0.9;
  animation: fall linear infinite;
}
@keyframes fall {
  0% { transform: translateY(-10vh) rotate(0deg); }
  100% { transform: translateY(110vh) rotate(360deg); }
}

/* Start button screen */
#startScreen {
  text-align: center;
}
#startBtn {
  padding: 18px 36px;
  font-size: 20px;
  border-radius: 30px;
  border: none;
  background: linear-gradient(45deg,#ff7eb3,#ffb6c1);
  color: white;
  cursor: pointer;
  animation: pulse 1.5s infinite;
}
@keyframes pulse {50%{transform:scale(1.1);}}

/* Birthday card */
.card {
  display: none;
  background: rgba(255,255,255,0.95);
  padding: 25px;
  border-radius: 20px;
  text-align: center;
  max-width: 420px;
  width: 90%;
  box-shadow: 0 10px 40px rgba(255,182,193,0.6);
  animation: zoomIn 1.5s ease;
}
@keyframes zoomIn { from{transform:scale(0);opacity:0;} to{transform:scale(1);opacity:1;} }

h1 { color:#ff69b4; animation:bounce 2s infinite; }
@keyframes bounce {50%{transform:translateY(-10px);} }

h2 { color:#ff4081; }
p { color:#444; font-size:17px; }

/* Balloons */
.balloon {
  position: absolute;
  bottom: -100px;
  width: 40px;
  height: 55px;
  border-radius: 50%;
  animation: fly linear infinite;
}
.balloon::after {
  content:"";
  position:absolute;
  top:55px; left:50%;
  width:2px; height:40px;
  background:white;
}
@keyframes fly { to{transform:translateY(-120vh);} }

/* Fireworks */
.spark {
  position:absolute;
  width:6px; height:6px;
  border-radius:50%;
  animation:spark 1s ease-out forwards;
}
@keyframes spark { to{transform:scale(3); opacity:0;} }

/* Share button */
.share {
  margin-top: 15px;
  padding: 10px 22px;
  border-radius: 25px;
  border: none;
  background: linear-gradient(45deg,#ffb6c1,#ff69b4);
  color:white;
  font-size:16px;
  cursor:pointer;
}
</style>
</head>
<body>

<!-- Start screen -->
<div id="startScreen">
  <button id="startBtn">🎁 Tap Here</button>
</div>

<!-- Birthday Card -->
<div class="card" id="card">
  <h1>🎂 Happy Birthday 🎉</h1>
  <h2>Ritu Magar 💖</h2>
  <p><b>November 7th</b></p>
  <p>
    Sorry for the late wish 😅<br>
    But my wishes are full of love 💫<br>
    May your life bloom like cherry blossoms 🌸<br>
    With happiness, smiles, and joy ✨
  </p>
  <p>Stay cute and amazing always 💕</p>
  <p><b>Best of luck for your exam results! 🍀📚</b></p>
  <button class="share" onclick="sharePage()">📤 Share</button>
</div>

<script>
// Floating petals
for(let i=0;i<30;i++){
  let p=document.createElement("div");
  p.className="petal";
  p.innerHTML="🌸";
  p.style.left=Math.random()*100+"vw";
  p.style.animationDuration=4+Math.random()*6+"s";
  document.body.appendChild(p);
}

// Click to start
const startBtn=document.getElementById("startBtn");
const startScreen=document.getElementById("startScreen");
const card=document.getElementById("card");

startBtn.onclick=()=>{
  startScreen.style.display="none";
  card.style.display="block";

  // Balloons
  const colors=["#ff7eb3","#ffd6e8","#ffb6c1","#ffc0cb","#ff69b4"];
  for(let i=0;i<15;i++){
    let b=document.createElement("div");
    b.className="balloon";
    b.style.left=Math.random()*100+"vw";
    b.style.background=colors[Math.floor(Math.random()*colors.length)];
    b.style.animationDuration=5+Math.random()*5+"s";
    document.body.appendChild(b);
  }

  // Fireworks
  setInterval(()=>firework(Math.random()*window.innerWidth,Math.random()*window.innerHeight),700);
};

// Fireworks function
function firework(x,y){
  const colors=["#ff7eb3","#ffd6e8","#ffb6c1","#ffc0cb","#ff69b4"];
  for(let i=0;i<20;i++){
    let s=document.createElement("div");
    s.className="spark";
    s.style.left=x+"px";
    s.style.top=y+"px";
    s.style.background=colors[Math.floor(Math.random()*colors.length)];
    s.style.transform=`translate(${Math.random()*80-40}px,${Math.random()*80-40}px)`;
    document.body.appendChild(s);
    setTimeout(()=>s.remove(),1000);
  }
}

// Click/touch fireworks
document.addEventListener("click",e=>firework(e.clientX,e.clientY));
document.addEventListener("touchstart",e=>{
  let t=e.touches[0];
  firework(t.clientX,t.clientY);
});

// Share function
function sharePage(){
  if(navigator.share){
    navigator.share({
      title:"Happy Birthday 🌸",
      text:"A cute cherry blossom birthday wish for Ritu Magar 💖",
      url:location.href
    });
  } else {
    navigator.clipboard.writeText(location.href);
    alert("Link copied 💌");
  }
}
</script>

</body>
</html>
