<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>5 Seconds Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f9f9f9;
            margin: 0;
            padding: 0;
        }
        h1 {
            background-color: #4CAF50;
            color: white;
            padding: 10px;
        }
        #timer {
            font-size: 50px;
            color: red;
        }
        #question {
            font-size: 24px;
            margin-top: 20px;
            font-weight: bold;
        }
        .btn {
            background-color: #4CAF50;
            color: white;
            padding: 15px 32px;
            text-align: center;
            display: inline-block;
            font-size: 16px;
            margin-top: 20px;
            cursor: pointer;
            border: none;
            border-radius: 5px;
        }
        .btn:hover {
            background-color: #45a049;
        }
        #next-btn {
            background-color: #008CBA;
            margin-top: 30px;
        }
        #result {
            margin-top: 30px;
            font-size: 20px;
        }
    </style>
</head>
<body>

    <h1>5 Seconds Game</h1>
    <p>Answer the question within 5 seconds!</p>

    <div id="timer">5</div>
    <div id="question"></div>

    <button class="btn" onclick="startGame()">Start Game</button>
    <button id="next-btn" class="btn" onclick="nextQuestion()" disabled>Next Question</button>
    <div id="result"></div>

    <script>
        const questions = [
            "Name 3 countries in Europe",
            "Name 3 types of fruit",
            "Name 3 colors",
            "Name 3 animals",
            "Name 3 sports",
            "Name 3 famous singers",
            "Name 3 types of food",
            "Name 3 movies",
            "Name 3 things that are red",
            "Name 3 famous actors",
            "Name 3 types of weather",
            "Name 3 days of the week",
            "Name 3 planets",
            "Name 3 famous authors",
            "Name 3 famous painters",
            "Name 3 books you've read",
            "Name 3 famous TV shows",
            "Name 3 countries in Africa",
            "Name 3 types of music genres",
            "Name 3 things you can find in a classroom",
            "Name 3 animals that live in the ocean",
            "Name 3 sports played with a ball",
            "Name 3 famous athletes",
            "Name 3 things that are yellow",
            "Name 3 types of trees",
            "Name 3 famous cities",
            "Name 3 school subjects",
            "Name 3 musical instruments",
            "Name 3 things you can eat for breakfast",
            "Name 3 things you wear",
            "Name 3 drinks",
            "Name 3 things you find in a kitchen",
            "Name 3 languages spoken in Europe",
            "Name 3 popular video games",
            "Name 3 superheroes",
            "Name 3 sea animals",
            "Name 3 types of transportation",
            "Name 3 types of birds",
            "Name 3 parts of the body",
            "Name 3 animals you can see in the zoo",
            "Name 3 things that are green",
            "Name 3 holidays",
            "Name 3 winter activities",
            "Name 3 fast food chains",
            "Name 3 ice cream flavors",
            "Name 3 famous brands",
            "Name 3 things you do on the weekend",
            "Name 3 types of fruit juice",
            "Name 3 animals that live in the jungle",
            "Name 3 ways to travel",
            "Name 3 types of flowers",
            "Name 3 sports you can play outdoors",
            "Name 3 hobbies",
            "Name 3 famous YouTubers"
        ];

        let timeLeft = 5;
        let currentQuestionIndex = 0;
        let score = 0;
        let timer;

        function startGame() {
            document.querySelector(".btn").disabled = true;
            document.getElementById("next-btn").disabled = false; // Enable the next question button
            score = 0;
            currentQuestionIndex = 0;
            nextQuestion(); // Start with the first question
        }

        function nextQuestion() {
            if (currentQuestionIndex < questions.length) {
                document.getElementById("result").textContent = "";  // Clear previous results
                document.getElementById("timer").textContent = 5;
                document.getElementById("question").textContent = questions[currentQuestionIndex];
                timeLeft = 5; // Reset the timer to 5 seconds
                startTimer(); // Start the timer when question is displayed
                currentQuestionIndex++;
            } else {
                document.getElementById("question").textContent = "Game Over!";
                document.getElementById("result").textContent = `Your score: ${score}/${questions.length}`;
                clearInterval(timer);
                document.querySelector(".btn").disabled = false; // Enable the start button after the game ends
                document.getElementById("next-btn").disabled = true; // Disable the next button after the game ends
            }
        }

        function startTimer() {
            timer = setInterval(function () {
                timeLeft--;
                document.getElementById("timer").textContent = timeLeft;

                if (timeLeft <= 0) {
                    clearInterval(timer); // Stop the timer when time runs out
                    score++; // Increment the score when time runs out
                    document.getElementById("next-btn").disabled = false; // Enable "Next Question" button
                }
            }, 1000);
        }
    </script>

</body>
</html>
