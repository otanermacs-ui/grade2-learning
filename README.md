math-quiz/
 └── index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Fun Math Quiz - Grade 2</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      font-family: 'Comic Sans MS', Arial, sans-serif;
      background: #f0f8ff;
      text-align: center;
      padding: 20px;
    }

    h1 {
      color: #ff6f61;
    }

    .quiz-box {
      background: white;
      padding: 25px;
      max-width: 400px;
      margin: auto;
      border-radius: 15px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    .question {
      font-size: 26px;
      margin: 20px 0;
    }

    input {
      font-size: 20px;
      padding: 10px;
      width: 100px;
      text-align: center;
    }

    button {
      background: #4caf50;
      color: white;
      border: none;
      padding: 10px 20px;
      font-size: 18px;
      border-radius: 10px;
      cursor: pointer;
      margin-top: 15px;
    }

    button:hover {
      background: #45a049;
    }

    .feedback {
      font-size: 20px;
      margin-top: 15px;
    }

    .score {
      margin-top: 10px;
      font-size: 18px;
      color: #333;
    }

    select {
      font-size: 16px;
      padding: 5px;
      margin-bottom: 10px;
    }
  </style>
</head>
<body>

  <h1>🎉 Fun Math Quiz 🎉</h1>

  <div class="quiz-box">
    <label>
      Choose Math Type:
      <br>
      <select id="mode">
        <option value="add">Addition ➕</option>
        <option value="sub">Subtraction ➖</option>
        <option value="mul">Multiplication ✖️</option>
        <option value="div">Division ➗</option>
      </select>
    </label>

    <div class="question" id="question">Press Start!</div>

    <input type="number" id="answer" placeholder="Your Answer" />

    <br>
    <button onclick="checkAnswer()">Submit</button>

    <div class="feedback" id="feedback"></div>
    <div class="score" id="score">Score: 0</div>
  </div>

  <script>
    let num1, num2, correctAnswer;
    let score = 0;

    function generateQuestion() {
      const mode = document.getElementById("mode").value;
      num1 = Math.floor(Math.random() * 10) + 1;
      num2 = Math.floor(Math.random() * 10) + 1;

      if (mode === "add") {
        correctAnswer = num1 + num2;
        document.getElementById("question").innerText =
          `${num1} + ${num2} = ?`;
      }

      if (mode === "sub") {
        if (num2 > num1) [num1, num2] = [num2, num1];
        correctAnswer = num1 - num2;
        document.getElementById("question").innerText =
          `${num1} − ${num2} = ?`;
      }

      if (mode === "mul") {
        correctAnswer = num1 * num2;
        document.getElementById("question").innerText =
          `${num1} × ${num2} = ?`;
      }

      if (mode === "div") {
        correctAnswer = num1;
        const product = num1 * num2;
        document.getElementById("question").innerText =
          `${product} ÷ ${num2} = ?`;
      }

      document.getElementById("answer").value = "";
      document.getElementById("feedback").innerText = "";
    }

    function checkAnswer() {
      const userAnswer = Number(document.getElementById("answer").value);

      if (userAnswer === correctAnswer) {
        score++;
        document.getElementById("feedback").innerText =
          "🎉 Correct! Great job!";
      } else {
        document.getElementById("feedback").innerText =
          `❌ Oops! The answer is ${correctAnswer}`;
      }

      document.getElementById("score").innerText = `Score: ${score}`;

      setTimeout(generateQuestion, 1500);
    }

    generateQuestion();
  </script>

</body>
</html>

