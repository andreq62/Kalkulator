<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Kalkulator Responsif</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: linear-gradient(to right, #00c6ff, #0072ff);
    }

    .calculator {
      background-color: white;
      border-radius: 20px;
      box-shadow: 0 10px 20px rgba(0,0,0,0.2);
      padding: 20px;
      width: 90%;
      max-width: 320px;
    }

    .display {
      background-color: #f0f0f0;
      border-radius: 10px;
      text-align: right;
      padding: 15px;
      font-size: 2rem;
      overflow-x: auto;
    }

    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 10px;
      margin-top: 20px;
    }

    button {
      padding: 20px;
      font-size: 1.2rem;
      border: none;
      border-radius: 10px;
      background-color: #e0e0e0;
      transition: background 0.2s;
      cursor: pointer;
    }

    button:active {
      background-color: #ccc;
    }

    .operator {
      background-color: #ff9500;
      color: white;
    }

    .equal {
      background-color: #34c759;
      color: white;
      grid-column: span 2;
    }

    .clear {
      background-color: #ff3b30;
      color: white;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <div class="display" id="display">0</div>
    <div class="buttons">
      <button class="clear" onclick="clearDisplay()">C</button>
      <button onclick="appendValue('(')">(</button>
      <button onclick="appendValue(')')">)</button>
      <button class="operator" onclick="appendValue('/')">÷</button>

      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button class="operator" onclick="appendValue('*')">×</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button class="operator" onclick="appendValue('-')">−</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button class="operator" onclick="appendValue('+')">+</button>

      <button onclick="appendValue('0')">0</button>
      <button onclick="appendValue('.')">.</button>
      <button class="equal" onclick="calculateResult()">=</button>
    </div>
  </div>

  <script>
    let display = document.getElementById('display');

    function appendValue(value) {
      if (display.textContent === '0') {
        display.textContent = value;
      } else {
        display.textContent += value;
      }
    }

    function clearDisplay() {
      display.textContent = '0';
    }

    function calculateResult() {
      try {
        display.textContent = eval(display.textContent.replace(/÷/g, '/').replace(/×/g, '*'));
      } catch {
        display.textContent = 'Error';
      }
    }
  </script>
</body>
</html>
