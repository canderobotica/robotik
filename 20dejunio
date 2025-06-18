<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Coloreá por la Patria 🇦🇷</title>
  <style>
    body { text-align: center; font-family: sans-serif; background: #e3f2fd; }
    canvas { border: 2px solid #555; margin-top: 10px; cursor: crosshair; background: white; }
    .color-btn, .image-btn {
      width: 30px; height: 30px; border: none; margin: 4px; cursor: pointer;
    }
    .image-btn {
      width: 100px; height: auto;
    }
    #gallery img {
      width: 80px; margin: 5px; cursor: pointer;
      border: 2px solid transparent;
    }
    #gallery img:hover {
      border-color: #1976d2;
    }
  </style>
</head>
<body>
  <h1>🎨 Coloreá por la Patria 🇦🇷</h1>
  <p>Elegí un dibujo y pintalo para homenajear el 20 de junio</p>

  <div id="gallery">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Flag_of_Argentina.svg/320px-Flag_of_Argentina.svg.png" onclick="loadImage(this.src)">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/Manuel_Belgrano_por_Carib.jpg/320px-Manuel_Belgrano_por_Carib.jpg" onclick="loadImage(this.src)">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f9/Escarapela_argentina_%28con_cinta%29.svg/320px-Escarapela_argentina_%28con_cinta%29.svg.png" onclick="loadImage(this.src)">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/f/f8/Remedios_del_Valle.jpg/320px-Remedios_del_Valle.jpg" onclick="loadImage(this.src)">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Izamiento_de_la_bandera_en_Misiones.jpg/320px-Izamiento_de_la_bandera_en_Misiones.jpg" onclick="loadImage(this.src)">
  </div>

  <p>🎨 Elegí un color:</p>
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
  <button onclick="saveImage()">💾 Guardar dibujo</button>

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
      baseImage.onload = () => ctx.drawImage(baseImage, 0, 0, canvas.width, canvas.height);
    }

    function saveImage() {
      const link = document.createElement('a');
      link.download = 'mi-dibujo-patria.png';
      link.href = canvas.toDataURL();
      link.click();
    }

    // Cargar imagen por defecto
    window.onload = () => {
      loadImage("https://upload.wikimedia.org/wikipedia/commons/thumb/1/1a/Flag_of_Argentina.svg/320px-Flag_of_Argentina.svg.png");
    };
  </script>
</body>
</html>
