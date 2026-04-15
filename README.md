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