# loccaa.github.io
!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ultimate Love Quiz</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 0;
        }

        .container {
            max-width: 800px;
            margin: 50px auto;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
            padding: 40px;
            text-align: center;
        }

        h1, h2, p {
            margin-bottom: 20px;
        }

        button {
            background-color: #4CAF50;
            border: none;
            color: white;
            padding: 15px 32px;
            text-align: center;
            text-decoration: none;
            display: inline-block;
            font-size: 16px;
            border-radius: 8px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #45a049;
        }

        .quiz {
            display: none;
        }

        .question-container {
            margin-top: 40px;
            text-align: left;
        }

        .question {
            font-size: 24px;
            font-weight: bold;
            color: #333;
            margin-bottom: 20px;
        }

        .options {
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .option {
            background-color: #4CAF50;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            margin: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            font-size: 16px;
        }

        .option:hover {
            background-color: #45a049;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Ultimate Love Quiz</h1>
        <p>Before we start, let's get to know each other a bit better.</p>
        <button onclick="startQuiz()">Start Quiz</button>

        <div class="quiz">
            <div class="question-container">
                <div class="question"></div>
                <div class="options"></div>
            </div>
        </div>
    </div>

    <script>
        let score = 0;
        let girlfriendName;

        function startQuiz() {
            girlfriendName = prompt("What's your name?");
            if (!girlfriendName) return;

            alert("Hi, " + girlfriendName + "! I'm just kidding, I know you! Let's start.");

            document.querySelector('.quiz').style.display = 'block';
            askQuestion("What is my deepest fear?", ["Getting rejected by " + girlfriendName, "Heights", "Being alone in the dark"], "a");
        }

        function askQuestion(question, options, correctOption) {
            let questionElement = document.querySelector('.question');
            let optionsContainer = document.querySelector('.options');

            questionElement.textContent = question;
            optionsContainer.innerHTML = '';

            options.forEach((option, index) => {
                let button = document.createElement('button');
                button.classList.add('option');
                button.textContent = option;
                button.addEventListener('click', function() {
                    checkAnswer(correctOption, String.fromCharCode(97 + index));
                });
                optionsContainer.appendChild(button);
            });
        }

        function checkAnswer(correctOption, selectedOption) {
            if (correctOption === selectedOption) {
                score++;
                alert("Correct! Great job!");
            } else {
                alert("Incorrect! The correct answer is: " + String.fromCharCode(97 + correctOption.charCodeAt(0) - 97));
            }

            if (score < 3) {
                askNextQuestion();
            } else {
                endQuiz();
            }
        }

        function askNextQuestion() {
            let questions = [
                {
                    question: "What's my guilty pleasure?",
                    options: ["Watching horror movies alone at midnight", "Eating ice cream for breakfast", "Talking to myself in the mirror"],
                    correctOption: "c"
                },
                {
                    question: "What's the best dream I've ever had?",
                    options: ["Flying on a giant pizza slice", "Go on a trip around the world.", "Us on a date and finally together"],
                    correctOption: "c"
                }
            ];

            let questionIndex = score - 1;
            let currentQuestion = questions[questionIndex];
            askQuestion(currentQuestion.question, currentQuestion.options, currentQuestion.correctOption);
        }

        function endQuiz() {
            alert("Congratulations, " + girlfriendName + "! Your final score is: " + score + "/3");
            if (score === 3) {
                alert("Wow! You know me so well! I love you, " + girlfriendName + "!");
            } else {
                alert("It's okay, do better next time! I still love you though, " + girlfriendName + ".");
            }
        }
    </script>
</body>
</html>
