<!DOCTYPE html>
<html>
<head>
  <title>Jogo Fodase!</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: black;
      color: white;
      text-align: center;
    }

    #game-container {
      width: 400px;
      height: 400px;
      margin: 50px auto;
      background-color: darkgray;
      position: relative;
    }

    .square {
      width: 50px;
      height: 50px;
      border: 1px solid white;
      position: absolute;
    }

    .red {
      background-color: red;
    }

    .blue {
      background-color: blue;
    }

    .green {
      background-color: green;
    }
  </style>
</head>
<body>
  <h1>Jogo Fodase!</h1>

  <div id="game-container"></div>

  <script>
    const gameContainer = document.getElementById('game-container');
    let squares = [];
    let score = 0;
    let gameInterval;

    function createSquare() {
      const square = document.createElement('div');
      square.classList.add('square');
      square.style.left = Math.random() * 400 - 50 + 'px';
      square.style.top = Math.random() * 400 - 50 + 'px';
      gameContainer.appendChild(square);
      squares.push(square);

      square.addEventListener('click', () => {
        score++;
        document.body.textContent = `Score: ${score}`;
        square.remove();
        squares = squares.filter(s => s !== square);
        createSquare();
      });
    }

    function startGame() {
      score = 0;
      document.body.textContent = `Score: ${score}`;
      squares = [];
      gameContainer.innerHTML = '';
      createSquare();

      gameInterval = setInterval(() => {
        createSquare();
      }, 1500);
    }

    startGame();
  </script>
</body>
</html>
