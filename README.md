<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<title>İyi Ki Doğdun Cemile 🎉</title>
<style>
body {
  margin: 0;
  height: 100vh;
  background: radial-gradient(circle, #ffecd2, #fcb69f);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial, sans-serif;
  overflow: hidden;
  text-align: center;
}
.box {
  background: rgba(255,255,255,0.85);
  padding: 35px;
  border-radius: 25px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}
h1 {
  font-size: 42px;
}
p {
  font-size: 20px;
}
button {
  padding: 12px 20px;
  font-size: 16px;
  border: none;
  border-radius: 20px;
  background: #ff7a18;
  color: white;
  cursor: pointer;
}
canvas {
  position: fixed;
  top: 0;
  left: 0;
}
</style>
</head>

<body>
<canvas id="fireworks"></canvas>

<div class="box">
  <h1>🎂 İyi Ki Doğdun Cemile!</h1>
  <p>🎉 Bugün senin günün!</p>
  <p>Bol kahkaha, eğlence ve güzel anılar seninle olsun ✨</p>
  <button onclick="playMusic()">🎶 Müziği Başlat</button>
</div>

<audio id="music" loop>
  <source src="https://cdn.pixabay.com/audio/2022/03/15/audio_8c98e6e7c6.mp3" type="audio/mpeg">
</audio>

<script>
function playMusic(){
  document.getElementById("music").play();
}

const canvas = document.getElementById("fireworks");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particles = [];

function createFirework(){
  const x = Math.random() * canvas.width;
  const y = Math.random() * canvas.height / 2;
  for(let i=0;i<50;i++){
    particles.push({
      x, y,
      dx: (Math.random()-0.5)*6,
      dy: (Math.random()-0.5)*6,
      life: 100
    });
  }
}

function animate(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  particles.forEach((p,i)=>{
    p.x += p.dx;
    p.y += p.dy;
    p.life--;
    ctx.fillStyle = "hsl(" + Math.random()*360 + ",100%,60%)";
    ctx.fillRect(p.x,p.y,3,3);
    if(p.life<=0) particles.splice(i,1);
  });
  requestAnimationFrame(animate);
}

setInterval(createFirework, 800);
animate();
</script>
</body>
</html>
