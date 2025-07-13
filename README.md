# larn-git<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Trigonometry Quiz Game</title>
    <style>
        body {
            font-family: 'Segoe UI', sans-serif;
            background: #46a9eb;
            color: rgb(255, 255, 255);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }

        .quiz-container {
            background-color: #447D9B;
            padding: 30px;
            border-radius: 35px;
            box-shadow: 0 0 20px #f14a20;
            width: 80%;
            /* height: 100%; */
            text-align: center;
        }

        #question {
            height: auto;
            font-size: 60px;
        }

        .btn-grid {
            margin: 20px 0;
            display: grid;
            gap: 60px;
        }

        button {
            padding: 20px;
            font-size: 25px;
            /* ✅ Bigger text */
            border: none;
            border-radius: 30px;
            cursor: pointer;
            background-color: #FE7743;
            color: white;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #9fd49f;
            /* ✅ Light green on hover */
        }

        .next-btn {
            margin-top: 10px;
        }

        .hide {
            display: none;
        }
    </style>
</head>

<body>
    <div class="quiz-container">
        <h1> Trigonometry Quiz Game</h1>
        <div id="question-container">
            <div id="question">Loading...</div>
            <div id="answer-buttons" class="btn-grid"></div>
            <button id="next-btn" class="next-btn">Next</button>
            <button id="skipBtn">Skip</button>
        </div>
        <div id="score-container" class="hide">
            <h2 id="score"></h2>
            <button onclick="location.reload()">Restart</button>
        </div>
    </div>
    <script>
        const questions = [
            {
                question: "What is the value of sin(90°)?",
                answers: [
                    { text: "0", correct: false },
                    { text: "1", correct: true },
                    { text: "√3/2", correct: false },
                    { text: "1/2", correct: false }
                ]
            },
            {
                question: "cos(0°) = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "√2/2", correct: false },
                    { text: "1/2", correct: false }
                ]
            },
            {
                question: "tan(45°) = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "√3", correct: false },
                    { text: "1/√3", correct: false }
                ]
            },
            {
                question: "What is cosec(30°)?",
                answers: [
                    { text: "2", correct: true },
                    { text: "1/2", correct: false },
                    { text: "√3", correct: false },
                    { text: "1", correct: false }
                ]
            },
            {
                question: "What is the value of cos(60°)?",
                answers: [
                    { text: "1", correct: false },
                    { text: "0", correct: false },
                    { text: "1/2", correct: true },
                    { text: "√3/2", correct: false }
                ]
            },
            {
                question: "sin(30°) = ?",
                answers: [
                    { text: "1/2", correct: true },
                    { text: "√3/2", correct: false },
                    { text: "1", correct: false },
                    { text: "0", correct: false }
                ]
            },
            {
                question: "cos(60°) = ?",
                answers: [
                    { text: "1/2", correct: true },
                    { text: "√3/2", correct: false },
                    { text: "0", correct: false },
                    { text: "1", correct: false }
                ]
            },
            {
                question: "tan(45°) = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "√3", correct: false },
                    { text: "1/√3", correct: false }
                ]
            },
            {
                question: "cosec(30°) = ?",
                answers: [
                    { text: "2", correct: true },
                    { text: "1/2", correct: false },
                    { text: "1", correct: false },
                    { text: "√3", correct: false }
                ]
            },
            {
                question: "sec(60°) = ?",
                answers: [
                    { text: "2", correct: true },
                    { text: "1/2", correct: false },
                    { text: "2/√3", correct: false },
                    { text: "√3", correct: false }
                ]
            },
            {
                question: "cot(45°) = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "√3", correct: false },
                    { text: "1/√3", correct: false }
                ]
            },
            {
                question: "sin(0°) = ?",
                answers: [
                    { text: "0", correct: true },
                    { text: "1", correct: false },
                    { text: "1/2", correct: false },
                    { text: "√3/2", correct: false }
                ]
            },
            {
                question: "cos(0°) = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "1/2", correct: false },
                    { text: "√3/2", correct: false }
                ]
            },
            {
                question: "tan(0°) = ?",
                answers: [
                    { text: "0", correct: true },
                    { text: "1", correct: false },
                    { text: "∞", correct: false },
                    { text: "Undefined", correct: false }
                ]
            },
            {
                question: "cosec(90°) = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "∞", correct: false },
                    { text: "Undefined", correct: false }
                ]
            }, {
                question: "cot(0°) = ?",
                answers: [
                    { text: "Undefined(∞)", correct: true },
                    { text: "0", correct: false },
                    { text: "1", correct: false },
                    { text: "∞", correct: false }
                ]
            },
            {
                question: "tan(90°) = ?",
                answers: [
                    { text: "Undefined(∞)", correct: true },
                    { text: "0", correct: false },
                    { text: "1", correct: false },
                    { text: "∞", correct: false }
                ]
            },
            {
                question: "sec(0°) = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "Undefined", correct: false },
                    { text: "∞", correct: false }
                ]
            },
            {
                question: "sin²θ + cos²θ = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "sinθ", correct: false },
                    { text: "cosθ", correct: false }
                ]
            },
            {
                question: "tan²θ + 1 = ?",
                answers: [
                    { text: "sec²θ", correct: true },
                    { text: "cosec²θ", correct: false },
                    { text: "cot²θ", correct: false },
                    { text: "1", correct: false }
                ]
            },
            {
                question: "sec²θ − 1 = ?",
                answers: [
                    { text: "tan²θ", correct: true },
                    { text: "cot²θ", correct: false },
                    { text: "cosec²θ", correct: false },
                    { text: "1", correct: false }
                ]
            },
            {
                question: "cosec²θ − cot²θ = ?",
                answers: [
                    { text: "1", correct: true },
                    { text: "0", correct: false },
                    { text: "tanθ", correct: false },
                    { text: "sin²θ", correct: false }
                ]
            },
            {
                question: "cos(90°) = ?",
                answers: [
                    { text: "0", correct: true },
                    { text: "1", correct: false },
                    { text: "√3/2", correct: false },
                    { text: "1/2", correct: false },
                ]
            },
            {
                question: "cot(90°) = ?",
                answers: [
                    { text: "1", correct: false },
                    { text: "√3/2", correct: false },
                    { text: "∞", correct: false },
                    { text: "Undefined", correct: true },
                ]
            },
            {
                question: "sin(45°) = ?",
                answers: [
                    { text: "1/√2", correct: true },
                    { text: "1/2", correct: false },
                    { text: "√3/2", correct: false },
                    { text: "1", correct: false }
                ]
            },
            {
                question: "cos(45°) = ?",
                answers: [
                    { text: "1/√2", correct: true },
                    { text: "1/2", correct: false },
                    { text: "√3/2", correct: false },
                    { text: "0", correct: false }
                ]
            },
            {
                question: "cot(30°) = ?",
                answers: [
                    { text: "√3", correct: true },
                    { text: "1/√3", correct: false },
                    { text: "1", correct: false },
                    { text: "0", correct: false }
                ]
            },
            {
                question: "tan(30°) = ?",
                answers: [
                    { text: "1/√3", correct: true },
                    { text: "√3", correct: false },
                    { text: "1", correct: false },
                    { text: "0", correct: false }
                ]
            },
            {
                question: "sec(30°) = ?",
                answers: [
                    { text: "2/√3", correct: true },
                    { text: "√3/2", correct: false },
                    { text: "1/2", correct: false },
                    { text: "1", correct: false }
                ]
            },
            {
                question: "cosec(60°) = ?",
                answers: [
                    { text: "2/√3", correct: true },
                    { text: "1", correct: false },
                    { text: "2", correct: false },
                    { text: "1/2", correct: false }
                ]
            },
            {
                question: "sinθ(90−θ)",
                answers: [
                    { text: "cosθ", correct: true },
                    { text: "−sinθ", correct: false },
                    { text: "cosecθ", correct: false },
                    { text: "cotθ", correct: false }
                ]
            },
            {
                question: "cosθ(90−θ)",
                answers : [
                    { text: "secθ", correct: false },
                    { text: "cosecθ", correct: false },
                    { text: "sinθ", correct: true },
                    { text: "−cosθ", correct: false }
                ]
            }
            // Add  more questions here the same way...
        ];



        const questionEl = document.getElementById('question');
        const answerButtons = document.getElementById('answer-buttons');
        const nextBtn = document.getElementById('next-btn');
        const scoreContainer = document.getElementById('score-container');
        const scoreText = document.getElementById('score');

        let currentQuestionIndex = 0;
        let score = 0;

        function startQuiz() {
            showQuestion();
        }

        function showQuestion() {
            resetState();
            const currentQuestion = questions[currentQuestionIndex];
            questionEl.innerText = currentQuestion.question;

            currentQuestion.answers.forEach(answer => {
                const btn = document.createElement('button');
                btn.innerText = answer.text;
                btn.classList.add('btn');
                if (answer.correct) {
                    btn.dataset.correct = answer.correct;
                }
                btn.addEventListener('click', selectAnswer);
                answerButtons.appendChild(btn);
            });
        }

        function resetState() {
            nextBtn.classList.add('hide');
            answerButtons.innerHTML = '';
        }

        function selectAnswer(e) {
            const selectedBtn = e.target;
            const isCorrect = selectedBtn.dataset.correct === 'true';

            if (isCorrect) score++;

            Array.from(answerButtons.children).forEach(button => {
                if (button.dataset.correct === 'true') {
                    button.style.backgroundColor = '#2ECC71'; // green
                } else {
                    button.style.backgroundColor = '#E74C3C'; // red
                }
                button.disabled = true;
            });

            nextBtn.classList.remove('hide');
        }

        nextBtn.addEventListener('click', () => {
            currentQuestionIndex++;
            if (currentQuestionIndex < questions.length) {
                showQuestion();
            } else {
                showScore();
            }
        });

        function showScore() {
            document.getElementById('question-container').classList.add('hide');
            scoreContainer.classList.remove('hide');
            scoreText.innerText = `You scored ${score} out of ${questions.length}`;
        }

        startQuiz();
        function showScore() {
            document.getElementById('question-container').classList.add('hide');
            scoreContainer.classList.remove('hide');
            scoreText.innerText = `You scored ${score} out of ${questions.length}`;
        }

        startQuiz();

        // Listen for Enter key to trigger next question
        document.addEventListener("keydown", function (e) {
            if (e.key === "Enter" && !nextBtn.classList.contains("hide")) {
                nextBtn.click();
                if (e.key === "Space" && !nextBtn.classList.contains("hide")) {
                    nextBtn.click(); // Space scroll na kare
                    nextQuestion();     // Space = Skip
                }
            }
        });
        document.getElementById("skipBtn").addEventListener("click", function () {
            // Simply move to next question without storing answer
            currentQuestionIndex++;
            if (currentQuestionIndex < questions.length) {
                showQuestion(currentQuestionIndex);  // ya tumhara jo bhi function ho
            } else {
                showScore();  // ya jo result dikha raha ho
            }
        });
        loadRandomQuestions(10);
        showQuestion(currentQuestionIndex);

    </script>
</body>

</html>
