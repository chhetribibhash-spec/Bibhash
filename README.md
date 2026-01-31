# Bibhash
My resume from complete web developer course
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Physics Simulator – Projectile Motion</title>
<style>
  body {
    font-family: Arial, sans-serif;
    text-align: center;
    background: #eef2f3;
  }
  canvas {
    background: white;
    border: 2px solid black;
    margin-top: 10px;
  }
  .controls {
    margin-top: 10px;
  }
  input {
    width: 60px;
  }
</style>
</head>

<body>

<h1>⚙️ Physics Simulator</h1>
<h3>Projectile Motion</h3>

<div class="controls">
  Velocity (m/s):
  <input type="number" id="velocity" value="30">
  Angle (°):
  <input type="number" id="angle" value="45">
  <button onclick="start()">Launch</button>
</div>

<canvas id="canvas" width="700" height="400"></canvas>

<p>
Formula used: <br>
Range = (u² sin2θ) / g <br>
Height = (u² sin²θ) / 2g
</p>

<script>
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

let t = 0;
let animation;

function start() {
  cancelAnimationFrame(animation);
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  t = 0;
  animate();
}

function animate() {
  const u = Number(document.getElementById("velocity").value);
  const angle = Number(document.getElementById("angle").value);
  const g = 9.8;

  const theta = angle * Math.PI / 180;

  const x = u * Math.cos(theta) * t;
  const y = u * Math.sin(theta) * t - 0.5 * g * t * t;

  ctx.fillStyle = "red";
  ctx.beginPath();
  ctx.arc(x * 5, canvas.height - y * 5, 5, 0, Math.PI * 2);
  ctx.fill();

  t += 0.1;

  if (y >= 0) {
    animation = requestAnimationFrame(animate);
  }
}
</script>

</body>
</html>
