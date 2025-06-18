<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Coloreando por la Patria 🇦🇷</title>
  <style>
    body {
      text-align: center;
      font-family: sans-serif;
      background: #f0f8ff;
      margin: 0;
      padding: 20px;
    }

    canvas {
      border: 2px solid #555;
      margin-top: 10px;
      cursor: crosshair;
      background: white;
    }

    .color-btn {
      width: 30px;
      height: 30px;
      border: none;
      margin: 5px;
      cursor: pointer;
    }

    #gallery img {
      width: 100px;
      margin: 5px;
      cursor: pointer;
      border: 2px solid transparent;
    }

    #gallery img:hover {
      border-color: #1976d2;
    }
  </style>
</head>
<body>

  <h1>🎨 Coloreando por la Patria 🇦🇷</h1>
  <p>Elegí una imagen y pintala con los colores que más te gusten</p>

  <div id="gallery">
    <!-- Bandera Argentina en blanco y negro -->
    <img src="https://i.imgur.com/b1dR2fN.png" onclick="loadImage(this.src)" alt="Bandera">
    <!-- Escarapela en blanco y negro -->
    <img src="https://i.imgur.com/pku6mny.png" onclick="loadImage(this.src)" alt="Escarapela">
    <!-- Escuela para colorear -->
    <img src="https://i.imgur.com/vqJS8Bb.png" onclick="loadImage(this.src)" alt="Escuela">
    <!-- Mapa de Argentina en contorno -->
    <img src="https://i.imgur.com/9TGy0Gu.png" onclick="loadImage(this.src)" alt="Mapa">
    <!-- María Remedios del Valle en estilo dibujo -->
    <img src="https://i.imgur.com/FfIC1wW.png" onclick="loadImage(this.src)" alt="Remedios del Valle">
  </div>

  <p>🖌️ Elegí un color:</p>
  <div id="colors">
    <button class="color-btn" style="background: white;" onclick="setColor('white')"></button>
    <button class="color-btn" style="background: #75AADB;" onclick="setColor('#75AADB')"></button>
    <button class="color-btn" style="background: gold;" onclick="setColor('gold')"></button>
    <button class="color-btn" style="background: black;" onclick="setColor('black')"></button>
    <button class="color-btn" style="background: brown;" onclick="setColor('brown')"></button>
    <button class="color-btn" style="background: green;" onclick="setColor('green')"></button>
    <button class="color-btn" style="background: red;" onclick="setColor('red')"></button>
    <button class="color-btn" style="background: pink;" onclick="setColor('pink')"></button>
    <button class="color-btn" style="background: purple;" onclick="setColor('purple')"></button>
  </div>

  <canvas id="canvas" width="500" height="350"></canvas><br>
  <button onclick="saveImage()">💾 Guardar mi dibujo</button>

  <script>
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
    let painting = false;
    let currentColor = '#75AADB';
    let baseImage = new Image();

    function setColor(color) {
      currentColor = color;
    }

    canvas.addEventListener('mousedown', () => painting = true);
    canvas.addEventListener('mouseup', () => painting = false);
    canvas.addEventListener('mouseout', () => painting = false);
    canvas.addEventListener('mousemove', draw);

    function draw(e) {
      if (!painting) return;
      const rect = canvas.getBoundingClientRect();
      ctx.fillStyle = currentColor;
      ctx.beginPath();
      ctx.arc(e.clientX - rect.left, e.clientY - rect.top, 8, 0, 2 * Math.PI);
      ctx.fill();
    }

    function loadImage(src) {
      baseImage = new Image();
      baseImage.crossOrigin = "anonymous";
      baseImage.src = src;
      baseImage.onload = () => {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        ctx.drawImage(baseImage, 0, 0, canvas.width, canvas.height);
      };
    }

    function saveImage() {
      const link = document.createElement('a');
      link.download = 'mi-dibujo-patria.png';
      link.href = canvas.toDataURL();
      link.click();
    }

    // Imagen por defecto
    window.onload = () => {
      loadImage("https://i.imgur.com/b1dR2fN.png");
    };
  </script>
</body>
</html>
