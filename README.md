<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Calculator</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background: #f4f4f4;
      font-family: Arial, sans-serif;
    }
    .calculator {
      background: #fff;
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0px 4px 10px rgba(0,0,0,0.2);
    }
    #display {
      width: 100%;
      height: 60px;
      font-size: 24px;
      text-align: right;
      margin-bottom: 15px;
      padding: 10px;
      border: 2px solid #ccc;
      border-radius: 10px;
    }
    .buttons {
      display: grid;
      grid-template-columns: repeat(4, 70px);
      gap: 10px;
    }
    button {
      height: 60px;
      font-size: 20px;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      background: #f0f0f0;
      transition: 0.2s;
    }
    button:hover {
      background: #ddd;
    }
    .operator {
      background: #ff9500;
      color: white;
    }
    .operator:hover {
      background: #e08900;
    }
    .equal {
      background: #34c759;
      color: white;
      grid-column: span 2;
    }
    .equal:hover {
      background: #28a745;
    }
    .clear {
      background: #ff3b30;
      color: white;
    }
    .clear:hover {
      background: #d32f2f;
    }
  </style>
</head>
<body>
  <div class="calculator">
    <input type="text" id="display" disabled>
    <div class="buttons">
      <button onclick="clearDisplay()" class="clear">C</button>
      <button onclick="appendValue('/')">÷</button>
      <button onclick="appendValue('*')">×</button>
      <button onclick="appendValue('-')">−</button>

      <button onclick="appendValue('7')">7</button>
      <button onclick="appendValue('8')">8</button>
      <button onclick="appendValue('9')">9</button>
      <button onclick="appendValue('+')" class="operator">+</button>

      <button onclick="appendValue('4')">4</button>
      <button onclick="appendValue('5')">5</button>
      <button onclick="appendValue('6')">6</button>
      <button onclick="appendValue('.')">.</button>

      <button onclick="appendValue('1')">1</button>
      <button onclick="appendValue('2')">2</button>
      <button onclick="appendValue('3')">3</button>
      <button onclick="calculate()" class="equal">=</button>

      <button onclick="appendValue('0')" style="grid-column: span 2;">0</button>
    </div>
  </div>

  <script>
    function appendValue(val) {
      document.getElementById("display").value += val;
    }
    function clearDisplay() {
      document.getElementById("display").value = "";
    }
    function calculate() {
      try {
        document.getElementById("display").value = eval(document.getElementById("display").value);
      } catch {
        document.getElementById("display").value = "Error";
      }
    }
  </script>
</body>
</html>
