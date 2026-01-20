<html lang="en">
<head>
<meta charset="UTF-8">
<title>Emad Elite Pixels</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;600&family=Inter:wght@300;400;500&display=swap" rel="stylesheet">

<style>
:root{
  --bg:#f6f4ef;
  --primary:#3f4f3c;
  --accent:#c2a35f;
  --dark:#1e1e1e;
}
body{
  margin:0;
  background:var(--bg);
  font-family:'Inter', sans-serif;
  color:var(--dark);
}
.container{
  max-width:1100px;
  margin:50px auto;
  background:#fff;
  padding:45px;
  border-radius:20px;
  box-shadow:0 35px 70px rgba(0,0,0,0.12);
}
header{
  text-align:center;
  margin-bottom:35px;
}
header h1{
  font-family:'Playfair Display', serif;
  font-size:44px;
  margin:0;
}
header span{ color:var(--accent); }
header p{
  margin-top:10px;
  color:#555;
}

.upload{
  text-align:center;
  margin:30px 0;
}
input[type=file]{
  padding:14px;
  border-radius:12px;
  border:1px solid #ccc;
}

.preview{
  position:relative;
  border-radius:16px;
  overflow:hidden;
  display:none;
  max-height:520px;
}
.preview img{
  width:100%;
  display:block;
}
.after{
  position:absolute;
  top:0;
  left:0;
  width:50%;
  overflow:hidden;
}

.slider{
  width:100%;
  margin:25px 0;
  display:none;
}

.buttons{
  text-align:center;
  margin-top:35px;
}
button{
  background:var(--primary);
  color:#fff;
  border:none;
  padding:16px 34px;
  border-radius:40px;
  font-size:16px;
  cursor:pointer;
  margin:10px;
}
button:hover{
  background:#2f3e2c;
}

footer{
  text-align:center;
  margin-top:45px;
  font-size:13px;
  color:#777;
}

canvas{display:none;}
</style>
</head>

<body>

<div class="container">
<header>
<h1>Emad <span>Elite Pixels</span></h1>
<p>One-click luxury AI product photo enhancement</p>
</header>

<div class="upload">
<input type="file" id="upload" accept="image/*">
</div>

<div class="preview" id="preview">
<img id="before">
<div class="after" id="afterBox">
<img id="after">
</div>
</div>

<input type="range" min="1" max="100" value="50" id="slider" class="slider">

<div class="buttons">
<button onclick="autoEnhance()">Enhance Image</button>
<button onclick="download()">Download</button>
</div>

<footer>
� 2026 Emad Elite Pixels � Studio quality in one click
</footer>

<canvas id="canvas"></canvas>
</div>

<script>
const upload = document.getElementById("upload");
const before = document.getElementById("before");
const after = document.getElementById("after");
const preview = document.getElementById("preview");
const slider = document.getElementById("slider");
const afterBox = document.getElementById("afterBox");
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");

upload.onchange = e =>{
  const reader = new FileReader();
  reader.onload = ()=>{
    before.src = reader.result;
    after.src = reader.result;
    preview.style.display="block";
    slider.style.display="block";
  }
  reader.readAsDataURL(e.target.files[0]);
}

slider.oninput = ()=> afterBox.style.width = slider.value+"%";

function autoEnhance(){
  canvas.width = before.naturalWidth;
  canvas.height = before.naturalHeight;

  /* =========================
     YOUR FINAL TUNED SETTINGS
     Exposure: 0
     Brilliance: 0
     Highlights: -18
     Shadows: -28
     Contrast: +19
  ==========================*/

  // Base draw (NO over-brightening)
  ctx.globalCompositeOperation = "source-over";
  ctx.filter = "brightness(1) contrast(1)";
  ctx.drawImage(before, 0, 0);

  // Highlights control (-18)
  ctx.globalCompositeOperation = "multiply";
  ctx.fillStyle = "rgba(245,245,245,0.12)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  // Shadows deepen (-28)
  ctx.globalCompositeOperation = "overlay";
  ctx.fillStyle = "rgba(0,0,0,0.18)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  // Contrast +19 (clean product look)
  ctx.globalCompositeOperation = "source-over";
  ctx.filter = "contrast(1.19) saturate(1.05)";
  ctx.drawImage(canvas, 0, 0);

  // Very subtle studio warmth
  ctx.fillStyle = "rgba(255,220,180,0.04)";
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  // Soft vignette (premium depth)
  const grd = ctx.createRadialGradient(
    canvas.width/2, canvas.height/2, canvas.width/3,
    canvas.width/2, canvas.height/2, canvas.width/1.1
  );
  grd.addColorStop(0, "rgba(0,0,0,0)");
  grd.addColorStop(1, "rgba(0,0,0,0.25)");
  ctx.fillStyle = grd;
  ctx.fillRect(0, 0, canvas.width, canvas.height);

  after.src = canvas.toDataURL("image/png");
}

function download(){
  const a = document.createElement("a");
  a.href = after.src;
  a.download = "emad-elite-enhanced.png";
  a.click();
}
</script>

</body>
</html>
