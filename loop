<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>loop</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@900&display=swap" rel="stylesheet">
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: #000;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    font-family: 'Cinzel', serif;
  }

  canvas {
    position: fixed;
    top: 0; left: 0;
    pointer-events: none;
    z-index: 0;
  }

  .center {
    position: relative;
    z-index: 1;
    text-align: center;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 32px;
  }

  h1 {
    font-size: clamp(64px, 15vw, 140px);
    font-weight: 900;
    color: #fff;
    letter-spacing: 0.15em;
    text-transform: lowercase;
    text-shadow:
      0 0 40px rgba(255,255,255,0.3),
      0 0 80px rgba(255,255,255,0.1);
    animation: fadeIn 1.2s ease forwards;
  }

  button {
    font-family: 'Cinzel', serif;
    font-size: 14px;
    font-weight: 700;
    letter-spacing: 0.25em;
    text-transform: uppercase;
    color: #fff;
    background: transparent;
    border: 1px solid rgba(255,255,255,0.4);
    padding: 14px 40px;
    cursor: pointer;
    transition: all 0.3s ease;
    animation: fadeIn 1.6s ease forwards;
    opacity: 0;
    animation-fill-mode: forwards;
  }

  button:hover {
    background: rgba(255,255,255,0.08);
    border-color: rgba(255,255,255,0.9);
    box-shadow: 0 0 24px rgba(255,255,255,0.15);
    transform: translateY(-2px);
  }

  button:active {
    transform: translateY(0);
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
</style>
</head>
<body>
<canvas id="snow"></canvas>

<div class="center">
  <h1>loop</h1>
  <button onclick="alert('Commands coming soon!')">Commands</button>
</div>

<script>
const canvas = document.getElementById('snow');
const ctx = canvas.getContext('2d');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

window.addEventListener('resize', () => {
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
});

const flakes = Array.from({ length: 120 }, () => ({
  x: Math.random() * canvas.width,
  y: Math.random() * canvas.height,
  r: Math.random() * 2.5 + 0.5,
  speed: Math.random() * 0.8 + 0.3,
  drift: (Math.random() - 0.5) * 0.4,
  opacity: Math.random() * 0.6 + 0.2,
}));

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  flakes.forEach(f => {
    ctx.beginPath();
    ctx.arc(f.x, f.y, f.r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(255,255,255,${f.opacity})`;
    ctx.fill();

    f.y += f.speed;
    f.x += f.drift;

    if (f.y > canvas.height + 5) {
      f.y = -5;
      f.x = Math.random() * canvas.width;
    }
    if (f.x > canvas.width + 5) f.x = -5;
    if (f.x < -5) f.x = canvas.width + 5;
  });
  requestAnimationFrame(draw);
}

draw();
</script>
</body>
</html>
