<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            font-family: Arial, sans-serif;
        }
        .calculator {
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        .display {
            width: 100%;
            height: 50px;
            text-align: right;
            margin-bottom: 10px;
            padding: 10px;
            font-size: 24px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }
        .button {
            padding: 20px;
            font-size: 18px;
            text-align: center;
            cursor: pointer;
            background-color: #f9f9f9;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .button.operator {
            background-color: #f0ad4e;
            color: #fff;
        }
        .button.equal {
            background-color: #5cb85c;
            color: #fff;
            grid-column: span 2;
        }
        .button.clear {
            background-color: #d9534f;
            color: #fff;
            grid-column: span 2;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" class="display" id="display" disabled>
        <div class="buttons">
            <div class="button clear" onclick="clearDisplay()">C</div>
            <div class="button" onclick="appendToDisplay('7')">7</div>
            <div class="button" onclick="appendToDisplay('8')">8</div>
            <div class="button" onclick="appendToDisplay('9')">9</div>
            <div class="button operator" onclick="appendToDisplay('/')">/</div>
            <div class="button" onclick="appendToDisplay('4')">4</div>
            <div class="button" onclick="appendToDisplay('5')">5</div>
            <div class="button" onclick="appendToDisplay('6')">6</div>
            <div class="button operator" onclick="appendToDisplay('*')">*</div>
            <div class="button" onclick="appendToDisplay('1')">1</div>
            <div class="button" onclick="appendToDisplay('2')">2</div>
            <div class="button" onclick="appendToDisplay('3')">3</div>
            <div class="button operator" onclick="appendToDisplay('-')">-</div>
            <div class="button" onclick="appendToDisplay('0')">0</div>
            <div class="button" onclick="appendToDisplay('.')">.</div>
            <div class="button equal" onclick="calculate()">=</div>
            <div class="button operator" onclick="appendToDisplay('+')">+</div>
        </div>
    </div>

    <script>
        function appendToDisplay(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function calculate() {
            try {
                const display = document.getElementById('display');
                display.value = eval(display.value);
            } catch (error) {
                alert('Invalid calculation');
            }
        }
    </script>
</body>
</html>
