<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
        }
        .calculator {
            background-color: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .display {
            width: 100%;
            height: 50px;
            font-size: 2em;
            text-align: right;
            padding: 10px;
            box-sizing: border-box;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        .button {
            width: 100%;
            padding: 20px;
            font-size: 1.5em;
            border: none;
            border-radius: 5px;
            background-color: #f9f9f9;
            cursor: pointer;
            box-shadow: 0 2px #ddd;
        }
        .button:active {
            box-shadow: none;
            transform: translateY(2px);
        }
        .button.operator {
            background-color: #f0f0f0;
        }
        .button.equal {
            background-color: #4caf50;
            color: white;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" class="display" id="display" disabled>
        <div class="buttons">
            <button class="button" onclick="appendNumber('7')">7</button>
            <button class="button" onclick="appendNumber('8')">8</button>
            <button class="button" onclick="appendNumber('9')">9</button>
            <button class="button operator" onclick="chooseOperation('/')">/</button>

            <button class="button" onclick="appendNumber('4')">4</button>
            <button class="button" onclick="appendNumber('5')">5</button>
            <button class="button" onclick="appendNumber('6')">6</button>
            <button class="button operator" onclick="chooseOperation('*')">*</button>

            <button class="button" onclick="appendNumber('1')">1</button>
            <button class="button" onclick="appendNumber('2')">2</button>
            <button class="button" onclick="appendNumber('3')">3</button>
            <button class="button operator" onclick="chooseOperation('-')">-</button>

            <button class="button" onclick="appendNumber('0')">0</button>
            <button class="button" onclick="appendNumber('.')">.</button>
            <button class="button" onclick="clearDisplay()">C</button>
            <button class="button equal" onclick="compute()">=</button>
            <button class="button operator" onclick="chooseOperation('+')">+</button>
        </div>
    </div>
 <script>
        let display = document.getElementById('display');
        let currentOperand = '';
        let previousOperand = '';
        let operation = undefined;

        function appendNumber(number) {
            if (number === '0' && display.value === '0') return;
            if (display.value === '0' && number !== '.') {
                display.value = number;
            } else {
                display.value += number;
            }
            currentOperand = display.value;
        }

        function chooseOperation(op) {
            if (currentOperand === '') return;
            if (previousOperand !== '') {
                compute();
            }
            operation = op;
            previousOperand = currentOperand;
            currentOperand = '';
            display.value = '0';
        }

        function compute() {
            let computation;
            const prev = parseFloat(previousOperand);
            const current = parseFloat(currentOperand);
            if (isNaN(prev) || isNaN(current)) return;
            switch (operation) {
                case '+':
                    computation = prev + current;
                    break;
                case '-':
                    computation = prev - current;
                    break;
                case '*':
                    computation = prev * current;
                    break;
                case '/':
                    computation = prev / current;
                    break;
                default:
                    return;
            }
            currentOperand = computation;
            operation = undefined;
            previousOperand = '';
            display.value = computation;
        }

        function clearDisplay() {
            display.value = '0';
            currentOperand = '';
            previousOperand = '';
            operation = undefined;
        }
    </script>
</body>
</html>
