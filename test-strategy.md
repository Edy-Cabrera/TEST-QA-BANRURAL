<meta charset="utf-8"> quitar


 <style>
    .black {
      color: black;
    }
    
    .red {
      color: red;
    }
    
    .green {
      color: green;
    }
  </style>    Se agrego esta parte para mejorar el requerimiento de lo solicitado



<div class="form">
  <label for="guessField">Ingresa el número a adivinar: </label><input type="text" id="guessField" class="guessField">
  <input type="submit" value="Ingresar el número aleatorio" class="guessSubmit">
</div>

<div class="resultParas">
  <p class="guesses"></p>
  <p class="lastResult"></p>
  <p class="lowOrHi"></p>
</div>
Se quito ya que no era util para la ejecucion del proyecto




<script>
  let randomNumber = Math.random() * 10;

  const ATTEMPS = 5;
  const guesses = document.querySelector('.guesses');
  const lastResult = document.querySelector('.lastResult');
  const lowOrHi = document.querySelector('lowOrHi');
  const guessSubmit = document.querySelector('.guessSubmit');
  const guessField = document.querySelector('.guessField');

  let guessCount = 1;
  let resetButton;

  function checkGuess() {

    let userGuess = guessField.value;
    if(guessCount === 1) {
      guesses.textContent = 'Número aleatorio anterior: ';
    }
    guesses.textContent += userGuess + ' ';

    if(userGuess === randomNumber) {
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'black';
      lowOrHi.textContent = '';
      setGameOver();
    } else if(guessCount === ATTEMPS) {
      lastResult.textContent = 'Felicitaciones! adivinaste el número!';
      lastResult.style.backgroundColor = 'red';
      setGameOver();
    } else {
      lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'green';
      if(userGuess < randomNumber) {
        lowOrHi.textContent = 'El número es mayor!';
      } else if(userGuess > randomNumber) {
        lowOrHi.textContent = 'El número es menor!';
      }
    }

    guessCount++;
    guessField.value = '';
    guessField.focus();
  }
  guessSubmit.addeventListener('click', checkGuess);

  function setGameOver() {
	  guessField.disabled = true;
	  guessSubmit.disabled = true;
	  resetButton = document.createElement('button');
	  resetButton.textContent = 'Comienza un nuevo juego';
	  document.body.appendChild(resetButton);
	  resetButton.addeventListener('click', resetGame);
  }

  function resetGame() {
	  guessCount = 1;

	  const resetParas = document.querySelectorAll('.resultParas p');
	  for(let i = 0; i < resetParas.length; i++) {
		  resetParas[i].textContent = '';
	  }
	  resetButton.parentNode.removeChild(resetButton);

	  guessField.disabled = false;
	  guessSubmit.disabled = false;
	  guessField.value = '';
	  guessField.focus();

	  lastResult.style.backgroundColor = 'white';

	  randomNumber = Math.floor(Math.random()) + 1;
  }
</script>   

Se quito para mayor ejecucion del proyecto





 <input type="number" id="guess" min="1" max="100">
  <button onclick="checkGuess()">Adivinar</button>
  
  <p id="message"></p>
  
  <script>
    var targetNumber = Math.floor(Math.random() * 100) + 1;
    var attempts = 0;
    
    function checkGuess() {
      var guessInput = document.getElementById("guess");
      var guess = parseInt(guessInput.value);
      
      if (isNaN(guess)) {
        alert("Ingresa un número entero válido.");
        return;
      }
      
      attempts++;
      
      if (guess > targetNumber) {
        showMessage("Incorrecto! El número es menor.", "black");
      } else if (guess < targetNumber) {
        showMessage("Incorrecto! El número es mayor.", "black");
      } else {
        showMessage("Felicitaciones! ¡Adivinaste el número!", "green");
        disableInput();
      }
      
      if (attempts === 10) {
        showMessage("¡Perdiste!", "red");
        disableInput();
      }
      
      guessInput.value = "";
    }
    
    function showMessage(text, color) {
      var messageElement = document.getElementById("message");
      messageElement.textContent = text;
      messageElement.className = color;
    }
    
    function disableInput() {
      var guessInput = document.getElementById("guess");
      guessInput.disabled = true;
    }
  </script>   Se agrego dentro del body para que la ejecucion fuera la mas optima