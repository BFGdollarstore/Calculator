<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>My Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #0055ff;
            margin: 0;
            font-family: Arial, sans-serif;
        }
        
        .calculator {
            background-color: #00ff99;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3);
            width: 300px;
        }

        #screen {
            width: 100%;
            height: 50px;
            font-size: 24px;
            text-align: right;
            margin-bottom: 15px;
            padding: 5px;
            box-sizing: border-box;
            background-color: #ecf0f1;
            border: none;
            border-radius: 5px;
        }

        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        .btn {
            padding: 20px;
            font-size: 18px;
            cursor: pointer;
            background-color: #e7e7e7;
            border: none;
            border-radius: 5px;
        }

        .btn:hover { background-color: #dcdcdc; }
        .clear { background-color: #ff4d4d; color: white; }
        .clear:hover { background-color: #cc0000; }
        .operator { background-color: #333; color: white; }
        .operator:hover { background-color: #555; }
        .equal { background-color: #0066cc; color: white; }
        .equal:hover { background-color: #004499; }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="screen" readonly>
        <div class="buttons">
            <button class="btn clear" onclick="clearScreen()">C</button>
            <button class="btn operator" onclick="appendValue('/')">/</button>
            <button class="btn operator" onclick="appendValue('*')">*</button>
            <button class="btn operator" onclick="appendValue('-')">-</button>
            <button class="btn operator" onclick="appendValue('+')">+</button>
            
            <button class="btn operator" onclick="appendValue('√')">√</button>
            
            <button class="btn" onclick="appendValue('7')">7</button>
            <button class="btn" onclick="appendValue('8')">8</button>
            <button class="btn" onclick="appendValue('9')">9</button>
            <button class="btn" onclick="appendValue('4')">4</button>
            <button class="btn" onclick="appendValue('5')">5</button>
            <button class="btn" onclick="appendValue('6')">6</button>
            <button class="btn" onclick="appendValue('1')">1</button>
            <button class="btn" onclick="appendValue('2')">2</button>
            <button class="btn" onclick="appendValue('3')">3</button>
            <button class="btn" onclick="appendValue('0')">0</button>
            <button class="btn equal" onclick="calculate()">=</button>
        </div>
    </div>

    <script>
        const screen = document.getElementById('screen');

        function appendValue(value) {
            screen.value += value;
        }

        function clearScreen() {
            screen.value = '';
        }

        function calculate() {
            try {
                let expression = screen.value;

                // CORRECTION: This searches for any number followed by √ and inserts a multiplication sign (e.g., 7√4 -> 7*√4)
                expression = expression.replace(/(\d)√/g, '$1*√');

                /* CORRECTION: This searches for √ followed by a number, and translates it 
                  into JavaScript math notation. 
                  Example: 7*√4 turns into 7*Math.sqrt(4)
                */
                expression = expression.replace(/√(\d+(\.\d+)?)/g, 'Math.sqrt($1)');

                // Now eval can read the clean code safely!
                screen.value = eval(expression);
            } catch (error) {
                screen.value = 'Error';
            }
        }
    </script>
</body>
</html>
