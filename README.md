<!DOCTYPE html>
<html lang="ms">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Tindakan Antibodi Interaktif</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #e6f2ff;
      color: #003366;
      margin: 0;
      padding: 20px;
    }
    header {
      background-color: #003366;
      color: white;
      padding: 20px;
      text-align: center;
    }
    .container {
      max-width: 800px;
      margin: auto;
    }
    .card {
      background: white;
      padding: 20px;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0,0,0,0.1);
      margin-bottom: 20px;
    }
    button {
      background-color: #0077cc;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    .quiz-result {
      font-weight: bold;
    }
  </style>
</head>
<body>
  <header>
    <h1>Permainan Interaktif: Tindakan Antibodi</h1>
    <p>Kenali lima jenis tindakan antibodi melalui pembelajaran digital!</p>
  </header>
  <div class="container">
    <div class="card">
      <h2>Simulasi Ringkas</h2>
      <p><strong>Situasi:</strong> Antigen menyebabkan penggumpalan sel.
        Apakah tindakan antibodi yang terlibat?</p>
      <button onclick="checkAnswer('pengaglutinatan')">Pengaglutinatan</button>
      <button onclick="checkAnswer('lisis')">Lisis</button>
      <button onclick="checkAnswer('opsonisasi')">Opsonisasi</button>
      <p id="quiz-feedback" class="quiz-result"></p>
    </div>

    <div class="card">
      <h2>Info Tambahan</h2>
      <ul>
        <li><strong>Pengaglutinatan:</strong> Menggumpalkan patogen.</li>
        <li><strong>Pengendapan:</strong> Mendak keluar antigen terlarut.</li>
        <li><strong>Lisis:</strong> Memecahkan membran sel patogen.</li>
        <li><strong>Neutralisasi:</strong> Melemahkan toksin patogen.</li>
        <li><strong>Opsonisasi:</strong> Menandakan patogen untuk fagositosis.</li>
      </ul>
    </div>
  </div>
  <script>
    function checkAnswer(answer) {
      const feedback = document.getElementById('quiz-feedback');
      if (answer === 'pengaglutinatan') {
        feedback.textContent = 'Betul! Ini ialah tindakan pengaglutinatan.';
        feedback.style.color = 'green';
      } else {
        feedback.textContent = 'Salah. Cuba lagi.';
        feedback.style.color = 'red';
      }
    }
  </script>
</body>
</html>
