<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>❤ ECRİN İÇİN HER ŞEY ❤</title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4);
      text-align: center;
      padding: 50px;
      overflow: hidden;
      position: relative;
      height: 100vh;
    }
    h1 {
      color: #d6336c;
      font-size: 40px;
    }
    .question { margin: 20px; font-size: 24px; font-weight: bold; }
    .answers button {
      display: block; width: 250px; margin: 15px auto; padding: 15px;
      border: none; border-radius: 12px;
      background: linear-gradient(135deg, #ff758c, #ff7eb3);
      color: white; font-size: 18px; font-weight: bold; cursor: pointer;
      box-shadow: 0 4px 15px rgba(0,0,0,0.2); transition: 0.3s;
    }
    .answers button:hover { transform: scale(1.05); box-shadow: 0 6px 20px rgba(0,0,0,0.3); }
    #startBtn { padding: 15px 30px; border: none; border-radius: 30px;
      background: #ff4d6d; color: white; font-size: 18px; cursor: pointer; transition: 0.3s; }
    #startBtn:hover { background: #d6336c; transform: scale(1.1); }
    #quiz { display: none; }
    #result { display: none; font-size: 24px; color: #2f3542; margin-top: 30px; }
    .correct { background-color: #28a745 !important; color: white; }
    .wrong { background-color: #dc3545 !important; color: white; }
    .floating {
      position: absolute;
      font-weight: 900;
      animation: floatUp 5s ease-in forwards, sparkle 1.5s infinite alternate;
      opacity: 1; z-index: 1000; pointer-events: none;
      text-shadow: 0 0 5px #fff, 0 0 10px #ffb6c1;
    }
    @keyframes floatUp {
      0% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
      20% { opacity: 1; }
      100% { transform: translateY(-20vh) rotate(360deg); opacity: 0; }
    }
    @keyframes sparkle { from { text-shadow: 0 0 2px #fff, 0 0 5px #fff; } to { text-shadow: 0 0 5px #fff, 0 0 15px #ffb6c1; } }
  </style>
</head>
<body>
  <h1>❤ ECRİN İÇİN ÖZEL OYUN ❤</h1>
  <button id="startBtn" onclick="startGame()">Başla</button>
  <div id="quiz"></div>
  <div id="result">💖 Tebrikler aşkım! Sen benim hayatımdaki en güzel şeysin, Ecrin! 💕<br><br> 🌹 Seni sonsuz seviyorum 🌹</div>
  <script>
    const questions = [
      { q: 'Benim en sevdiğim renk hangisi?', a: ['Mavi', 'Yeşil', 'Siyah'], correct: 2 },
      { q: 'Doğum günüm ne zaman?', a: ['28 Ocak', '25 Şubat', '27 Aralık'], correct: 0 },
      { q: 'Beni ne kadar çok seviyorsun?', a: ['Çok çoook sana aşığım ❤'], correct: 0 },
      { q: 'En sevdiğim meyve nedir?', a: ['Elma', 'Çilek', 'Muz'], correct: 2 },
      { q: 'Hangi tatlıyı daha çok severim?', a: ['Baklava', 'Çikolatalı kek', 'Sütlaç'], correct: 0 },
      { q: 'Favori hayvanım hangisi?', a: ['Kedi', 'Köpek', 'Tavşan'], correct: 0 },
      { q: 'Hangi mevsimi daha çok severim?', a: ['Yaz', 'Kış', 'İlkbahar'], correct: 1 },
      { q: 'Favori film türüm nedir?', a: ['Romantik', 'Aksiyon', 'Komedi', 'Erotik'], correct: 1 },
      { q: 'Sana hediye olarak hangi çiçekleri alsam seni mutlu eder?', a: ['Kırmızı güller', 'Sarı papatyalar', 'Beyaz orkide'], correct: 0 }
    ];

    let currentQuestion = 0;

    function startGame(){
      document.getElementById('startBtn').style.display = 'none';
      showQuestion();
      setInterval(createFloating, 500);
    }

    function showQuestion(){
      if(currentQuestion >= questions.length){
        document.getElementById('quiz').style.display = 'none';
        document.getElementById('result').style.display = 'block';
        return;
      }
      const qObj = questions[currentQuestion];
      const quizDiv = document.getElementById('quiz');
      quizDiv.innerHTML = '';
      const questionElem = document.createElement('div');
      questionElem.classList.add('question');
      questionElem.textContent = qObj.q;
      quizDiv.appendChild(questionElem);
      qObj.a.forEach((answer, idx) => {
        const btn = document.createElement('button');
        btn.textContent = answer;
        btn.classList.add('answerBtn');
        btn.onclick = () => checkAnswer(btn, idx === qObj.correct);
        quizDiv.appendChild(btn);
      });
      quizDiv.style.display = 'block';
    }

    function checkAnswer(button, isCorrect){
      if(isCorrect){
        button.classList.add('correct');
        button.innerText = '✔ Doğru cevap';
        createFloatingSymbol('❤');
        createFloatingSymbol('M');
        createFloatingSymbol('E');
        setTimeout(()=>{ currentQuestion++; showQuestion(); }, 1000);
      } else {
        button.classList.add('wrong');
        button.innerText = '✘ Yanlış cevap, tekrar deneyin';
        button.disabled = true;
      }
    }

    function createFloating(){
      const symbols = ['❤','M','E'];
      createFloatingSymbol(symbols[Math.floor(Math.random()*symbols.length)]);
    }

    function createFloatingSymbol(symbol){
      const elem = document.createElement('div');
      elem.classList.add('floating');
      elem.innerText = symbol;
      elem.style.left = Math.random()*90+'vw';
      elem.style.bottom='0px';
      elem.style.fontSize = Math.random()*60 + 40 + 'px';
      elem.style.fontWeight = '900';
      elem.style.color = 'red';
      document.body.appendChild(elem);
      setTimeout(()=>elem.remove(),8000);
    }
  </script>
</body>
</html>
