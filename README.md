# best-education-app
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Best Education</title>
  <style>
    body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f4f4f4; }
    header { background: #007bff; color: white; padding: 1rem; text-align: center; font-size: 1.5rem; }
    .container { padding: 1rem; }
    .card { background: white; padding: 1rem; margin-bottom: 1rem; border-radius: 8px; box-shadow: 0 0 5px rgba(0,0,0,0.1); }
    button { background: #007bff; color: white; border: none; padding: 0.5rem 1rem; margin-top: 1rem; border-radius: 4px; cursor: pointer; }
    .hidden { display: none; }
  </style>
</head>
<body>
  <header>Best Education</header>
  <div class="container">
    <div id="home">
      <div class="card"><strong>Subjects</strong></div>
      <div class="card" onclick="showLesson('math')">Math</div>
      <div class="card" onclick="showLesson('science')">Science</div>
      <div class="card" onclick="showLesson('history')">History</div>
      <div class="card" onclick="showQuiz()">Take Quiz</div>
    </div><div id="lesson" class="hidden">
  <div class="card" id="lesson-title"></div>
  <div class="card" id="lesson-content"></div>
  <button onclick="goHome()">Back</button>
</div>

<div id="quiz" class="hidden">
  <div class="card" id="quiz-question">Loading...</div>
  <div class="card" id="quiz-options"></div>
  <button onclick="nextQuestion()">Next</button>
  <button onclick="goHome()">Back</button>
</div>

  </div>  <script>
    const lessons = {
      math: { title: "Math", content: "Math is about numbers, shapes, and patterns." },
      science: { title: "Science", content: "Science is the study of the natural world." },
      history: { title: "History", content: "History is the study of past events." }
    };

    const quizData = [
      { q: "What is 2 + 2?", options: ["3", "4", "5"], answer: 1 },
      { q: "What planet do we live on?", options: ["Mars", "Earth", "Venus"], answer: 1 },
      { q: "Who discovered gravity?", options: ["Newton", "Einstein", "Tesla"], answer: 0 }
    ];

    let quizIndex = 0;

    function showLesson(subject) {
      document.getElementById('home').classList.add('hidden');
      document.getElementById('lesson').classList.remove('hidden');
      document.getElementById('lesson-title').innerText = lessons[subject].title;
      document.getElementById('lesson-content').innerText = lessons[subject].content;
    }

    function showQuiz() {
      quizIndex = 0;
      document.getElementById('home').classList.add('hidden');
      document.getElementById('quiz').classList.remove('hidden');
      loadQuestion();
    }

    function loadQuestion() {
      const q = quizData[quizIndex];
      document.getElementById('quiz-question').innerText = q.q;
      const optionsHtml = q.options.map((opt, i) => <div><input type='radio' name='opt' id='opt${i}'><label for='opt${i}'> ${opt}</label></div>).join('');
      document.getElementById('quiz-options').innerHTML = optionsHtml;
    }

    function nextQuestion() {
      quizIndex++;
      if (quizIndex < quizData.length) {
        loadQuestion();
      } else {
        document.getElementById('quiz-question').innerText = "Quiz complete!";
        document.getElementById('quiz-options').innerHTML = "Well done!";
      }
    }

    function goHome() {
      document.getElementById('home').classList.remove('hidden');
      document.getElementById('lesson').classList.add('hidden');
      document.getElementById('quiz').classList.add('hidden');
    }
  </script></body>
</html>
