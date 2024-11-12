<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rock Paper Scissors Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            text-align: center;
            background-color: white;
            border-radius: 10px;
            box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
            padding: 20px;
            width: 300px;
        }
        h1 {
            margin-bottom: 20px;
        }
        .choices {
            display: flex;
            justify-content: space-evenly;
            margin-bottom: 20px;
        }
        .choice {
            cursor: pointer;
            padding: 10px;
            font-size: 20px;
            border: 2px solid #ddd;
            border-radius: 5px;
            transition: all 0.3s ease;
        }
        .choice:hover {
            background-color: #f1f1f1;
        }
        .result {
            font-size: 18px;
            margin: 10px 0;
        }
        .score {
            margin-top: 20px;
            font-size: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Rock, Paper, Scissors</h1>
        <div class="choices">
            <div class="choice" onclick="makeChoice('rock')">Rock</div>
            <div class="choice" onclick="makeChoice('paper')">Paper</div>
            <div class="choice" onclick="makeChoice('scissors')">Scissors</div>
        </div>
        <div class="result" id="result">Choose your move!</div>
        <div class="score" id="score">Player: 0 - Computer: 0</div>
    </div>

    <script>
        let playerScore = 0;
        let computerScore = 0;

        function makeChoice(playerChoice) {
            const choices = ['rock', 'paper', 'scissors'];
            const computerChoice = choices[Math.floor(Math.random() * 3)];
            const resultMessage = document.getElementById('result');
            const scoreMessage = document.getElementById('score');

            // Determine the result of the game
            if (playerChoice === computerChoice) {
                resultMessage.innerHTML = `It's a tie! Both chose ${playerChoice}.`;
            } else if (
                (playerChoice === 'rock' && computerChoice === 'scissors') ||
                (playerChoice === 'paper' && computerChoice === 'rock') ||
                (playerChoice === 'scissors' && computerChoice === 'paper')
            ) {
                playerScore++;
                resultMessage.innerHTML = `You win! ${playerChoice.charAt(0).toUpperCase() + playerChoice.slice(1)} beats ${computerChoice}.`;
            } else {
                computerScore++;
                resultMessage.innerHTML = `You lose! ${computerChoice.charAt(0).toUpperCase() + computerChoice.slice(1)} beats ${playerChoice}.`;
            }

            // Update the score
            scoreMessage.innerHTML = `Player: ${playerScore} - Computer: ${computerScore}`;
        }
    </script>
</body>
</html>
