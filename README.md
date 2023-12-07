<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Q&A Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        .question {
            margin-bottom: 10px;
        }

        .answers {
            display: flex;
            flex-direction: column;
        }

        .button {
            padding: 10px;
            margin: 5px;
            cursor: pointer;
        }

        .button:hover {
            background-color: lightgray;
        }
    </style>
</head>
<body>
    <div id="game"></div>
    <button id="reset">Reset Game</button>

    <script>
        const questions = [
            {
                question: "Siapa Nama Tengahku?",
                choices: ["Michael", "Rivan", "Diego", "Gapunya"],
                correct: 3
            },
            {
                question: "Susu apa yang aku suka?",
                choices: ["Coklat", "Stroberi", "Susu Mu", "Putih"],
                correct: 2
            },
            {
                question: "Sapa Pacal Aku?",
                choices: ["Milly", "Babi", "Coco", "Boba"],
                correct: 1
            },
            {
                question: "Olahraga Paporit Aku?",
                choices: ["Koprol", "Panahan", "Basket", "Poop"],
                correct: 2
            },
            {
                question: "Siapa nama adikku?",
                choices: ["Meki", "Alan", "Juniol", "Budi"],
                correct: 2
            }
        ];

        let currentQuestion = 0;
        let correctCount = 0;

        function startGame() {
            const game = document.getElementById("game");
            game.innerHTML = '';

            if (currentQuestion < questions.length) {
                const questionDiv = document.createElement("div");
                questionDiv.classList.add("question");
                questionDiv.textContent = questions[currentQuestion].question;
                game.appendChild(questionDiv);

                const answersDiv = document.createElement("div");
                answersDiv.classList.add("answers");
                game.appendChild(answersDiv);

                for (let i = 0; i < questions[currentQuestion].choices.length; i++) {
                    const button = document.createElement("button");
                    button.classList.add("button");
                    button.textContent = questions[currentQuestion].choices[i];
                    button.addEventListener("click", function () {
                        if (i === questions[currentQuestion].correct) {
                            correctCount++;
                        }
                        currentQuestion++;
                        startGame();
                    });
                    answersDiv.appendChild(button);
                }
            } else {
                game.textContent = `Game Over! Tingkat Cintamu Padaku ${correctCount} dari ${questions.length}.`;
            }
        }

        document.getElementById("reset").addEventListener("click", function () {
            currentQuestion = 0;
            correctCount = 0;
            startGame();
        });

        startGame();
    </script>
</body>
</html>
