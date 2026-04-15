# Bio-Quiz-NEET
Revise bio class 11th Cell questions 
 
<!DOCTYPE html>
<html>
<head>
  <title>Biology Quiz Pro</title>
  <style>
    body {
      font-family: Arial;
      background: linear-gradient(to right, #74ebd5, #ACB6E5);
      text-align: center;
    }
    .box {
      background: white;
      padding: 20px;
      margin: 50px auto;
      width: 350px;
      border-radius: 15px;
      box-shadow: 0 0 15px gray;
    }
    button {
      display: block;
      margin: 10px auto;
      padding: 10px;
      width: 80%;
      cursor: pointer;
      border: none;
      border-radius: 5px;
      background: #4CAF50;
      color: white;
    }
    #timer {
      font-weight: bold;
      color: red;
    }
  </style>
</head>
<body>

<div class="box">
  <h2 id="question">Question</h2>
  <div id="options"></div>
  <p>⏱️ Time left: <span id="timer">10</span>s</p>
</div>

<audio id="correctSound" src="https://www.soundjay.com/buttons/sounds/button-3.mp3"></audio>
<audio id="wrongSound" src="https://www.soundjay.com/buttons/sounds/button-10.mp3"></audio>

<script src="script.js"></script>
</body>
</html>

const quiz = [
  {
    q: "Heart pumps which fluid?",
    options: ["Blood", "Water", "Oxygen", "Plasma"],
    answer: "Blood"
  },
  {
    q: "Basic unit of life?",
    options: ["Tissue", "Cell", "Organ", "Atom"],
    answer: "Cell"
  },
  {
    q: "Which organ helps in breathing?",
    options: ["Heart", "Lungs", "Kidney", "Brain"],
    answer: "Lungs"
  }
];

let index = 0;
let score = 0;
let time = 10;
let timer;

function startTimer() {
  time = 10;
  document.getElementById("timer").innerText = time;

  timer = setInterval(() => {
    time--;
    document.getElementById("timer").innerText = time;

    if (time === 0) {
      clearInterval(timer);
      index++;
      loadQuestion();
    }
  }, 1000);
}

function loadQuestion() {
  if (index >= quiz.length) {
    document.querySelector(".box").innerHTML =
      `<h2>🏆 Your Score: ${score}/${quiz.length}</h2>
       <button onclick="restart()">Restart</button>`;
    return;
  }

  document.getElementById("question").innerText = quiz[index].q;

  let optionsHTML = "";
  quiz[index].options.forEach(opt => {
    optionsHTML += `<button onclick="checkAnswer('${opt}')">${opt}</button>`;
  });

  document.getElementById("options").innerHTML = optionsHTML;

  startTimer();
}

function checkAnswer(selected) {
  clearInterval(timer);

  if (selected === quiz[index].answer) {
    score++;
    document.getElementById("correctSound").play();
  } else {
    document.getElementById("wrongSound").play();
  }

  index++;
  setTimeout(loadQuestion, 500);
}

function restart() {
  index = 0;
  score = 0;
  loadQuestion();
}

loadQuestion();