<!DOCTYPE html>
<html lang="ms">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Antibody Action v2.0</title>
<style>
  body { font-family: Arial, sans-serif; margin: 20px; background: #f9f9f9; }
  h1 { color: #2a7f62; text-align: center; }
  .section { margin-bottom: 40px; padding: 20px; background: #fff; border-radius: 10px; box-shadow: 0 0 10px #ccc; }
  #simulation { display: flex; gap: 20px; flex-wrap: wrap; justify-content: center; align-items: center; }
  .antigen, .antibody { width: 100px; height: 100px; border-radius: 50%; display: flex; justify-content: center; align-items: center; color: #fff; font-weight: bold; cursor: pointer; }
  .antigen { background: #e74c3c; }
  .antibody { background: #3498db; }
  .quiz-question { margin-bottom: 10px; }
  .quiz-option { margin: 5px 0; }
  button { padding: 10px 20px; background: #2a7f62; color: #fff; border: none; border-radius: 5px; cursor: pointer; }
  #qr-code { display: flex; justify-content: center; margin-top: 20px; }
</style>
</head>
<body>

<h1>Antibody Action v2.0</h1>

<div class="section">
  <h2>Pengenalan</h2>
  <p>Antibodi adalah protein yang dihasilkan oleh sistem imun untuk mengenal dan meneutralkan antigen seperti bakteria dan virus.</p>
</div>

<div class="section">
  <h2>Simulasi Antibodi</h2>
  <p>Seret antibodi ke antigen untuk melihat tindakan pengikatan.</p>
  <div id="simulation">
    <div class="antigen" id="antigen1">Antigen A</div>
    <div class="antigen" id="antigen2">Antigen B</div>
    <div class="antibody" id="antibody1" draggable="true">Antibodi 1</div>
    <div class="antibody" id="antibody2" draggable="true">Antibodi 2</div>
  </div>
  <p id="sim-result"></p>
</div>

<div class="section">
  <h2>Kuiz Antibodi</h2>
  <div class="quiz-question">
    <p>1. Apa fungsi utama antibodi?</p>
    <div class="quiz-option"><input type="radio" name="q1" value="wrong"> Membekalkan tenaga kepada sel</div>
    <div class="quiz-option"><input type="radio" name="q1" value="correct"> Mengenal dan meneutralkan antigen</div>
    <div class="quiz-option"><input type="radio" name="q1" value="wrong"> Menghantar oksigen ke sel</div>
  </div>
  <div class="quiz-question">
    <p>2. Antibodi tergolong dalam jenis protein?</p>
    <div class="quiz-option"><input type="radio" name="q2" value="correct"> Globulin</div>
    <div class="quiz-option"><input type="radio" name="q2" value="wrong"> Kolagen</div>
    <div class="quiz-option"><input type="radio" name="q2" value="wrong"> Keratin</div>
  </div>
  <button onclick="checkQuiz()">Semak Jawapan</button>
  <p id="quiz-result"></p>
</div>

<div class="section" id="qr-code">
  <div id="qrcode"></div>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/qrious/4.0.2/qrious.min.js"></script>
<script>
// Simulasi drag & drop
const antibodies = document.querySelectorAll('.antibody');
const antigens = document.querySelectorAll('.antigen');
const result = document.getElementById('sim-result');

antibodies.forEach(antibody => {
  antibody.addEventListener('dragstart', e => {
    e.dataTransfer.setData('text/plain', antibody.id);
  });
});

antigens.forEach(antigen => {
  antigen.addEventListener('dragover', e => e.preventDefault());
  antigen.addEventListener('drop', e => {
    e.preventDefault();
    const data = e.dataTransfer.getData('text');
    const antibody = document.getElementById(data);
    if(antibody) {
      result.textContent = antibody.textContent + " berjaya mengikat " + antigen.textContent + "! Neutralisasi berlaku.";
      antigen.style.background = '#2ecc71';
    }
  });
});

// Kuiz
function checkQuiz() {
  let score = 0;
  const q1 = document.querySelector('input[name="q1"]:checked');
  const q2 = document.querySelector('input[name="q2"]:checked');
  if(!q1 || !q2) { document.getElementById('quiz-result').textContent = "Sila jawab semua soalan."; return; }
  if(q1.value === 'correct') score++;
  if(q2.value === 'correct') score++;
  document.getElementById('quiz-result').textContent = "Skor anda: " + score + "/2";
}

// QR Code
const qr = new QRious({
  element: document.getElementById('qrcode'),
  value: window.location.href,
  size: 150,
  background: '#ffffff',
  foreground: '#2a7f62'
});
</script>

</body>
</html>
