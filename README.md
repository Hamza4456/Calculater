
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scientific Calculator</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0-alpha1/dist/css/bootstrap.min.css" rel="stylesheet" />
    <link rel="manifest" href="manifest.json">
    <style>
        body {
            background-color: #1e1e1e;
        }
        .calculator {
            width: 80%;
            max-width: 400px;
            margin: auto;
            margin-top: 10px;
            margin-bottom: 10px;
            padding: 20px;
            border-radius: 10px;
            background-color: whitesmoke;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
         
        }
        .display {
            width: 100%;
            height: 80px;
            text-align: right;
            font-size: 2rem;
            border: 1px solid #555;
            padding: 10px;
            margin-bottom: 20px;
            background-color: #333;
            color: #fff;
            border-radius: 5px;
        }
        .btn {
            font-size: 1.5rem;
            width: 70px;
            height: 70px;
            border-radius: 50%;
            margin: 10px;
        }
        .btn-black {
            background-color: black;
            color: #fff;
            border: 2px solid #444;
        }
        .btn-black:hover {
            background-color: goldenrod;
        }
        .btn-gold {
            background-color: #d4af37;
            color: #fff;
            border: 2px solid #c39b34;
        }
        .btn-gold:hover {
            background-color: #c39b34;
        }
        .btn-danger {
            background-color: #dc3545;
            color: #fff;
            border: 2px solid #c82333;
        }
        .btn-danger:hover {
            background-color: #c82333;
        }
        .btn-primary {
            background-color: #007bff;
            color: #fff;
            border: 2px solid #0056b3;
        }
        .btn-primary:hover {
            background-color: #0056b3;
        }
        .row {
            justify-content: center;
        }

        @media (max-width: 576px) {
            .btn {
                width: 60px;
                height: 60px;
                font-size: 1.2rem;
            }
            .display {
                font-size: 1.8rem;
            }
        }

    </style>
</head>
<body>

<div class="calculator">
    <div class="display" id="display">0</div>
    <div class="row">
        <div class="col-3"><button class="btn btn-danger" onclick="clearDisplay()">C</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('7')">7</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('8')">8</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('9')">9</button></div>
    </div>
    <div class="row">
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('4')">4</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('5')">5</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('6')">6</button></div>
        <div class="col-3"><button class="btn btn-gold" onclick="appendToDisplay('/')">/</button></div>
    </div>
    <div class="row">
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('1')">1</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('2')">2</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('3')">3</button></div>
        <div class="col-3"><button class="btn btn-gold" onclick="appendToDisplay('*')">*</button></div>
    </div>
    <div class="row">
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('0')">0</button></div>
        <div class="col-3"><button class="btn btn-black" onclick="appendToDisplay('.')">.</button></div>
        <div class="col-3"><button class="btn btn-primary" onclick="appendToDisplay('+')">+</button></div>
        <div class="col-3"><button class="btn btn-primary" onclick="appendToDisplay('-')">-</button></div>
    </div>
    <div class="row">
        <div class="col-3"><button class="btn btn-danger" onclick="appendToDisplay('(')">(</button></div>
        <div class="col-3"><button class="btn btn-danger" onclick="appendToDisplay(')')">)</button></div>
        <div class="col-3"><button class="btn btn-success" onclick="calculateResult()">=</button></div>
        <div class="col-3"><button class="btn btn-danger" onclick="appendToDisplay('sqrt(')">√</button></div>
    </div>
    <div class="row">
        <div class="col-3"><button class="btn btn-danger" onclick="appendToDisplay('sin(')">sin</button></div>
        <div class="col-3"><button class="btn btn-danger" onclick="appendToDisplay('cos(')">cos</button></div>
        <div class="col-3"><button class="btn btn-danger" onclick="appendToDisplay('tan(')">tan</button></div>
        <div class="col-3"><button class="btn btn-danger" onclick="appendToDisplay('log(')">log</button></div>
    </div>
</div>

<script>
    function appendToDisplay(value) {
        let display = document.getElementById('display');
        if (display.innerText === '0') {
            display.innerText = value;
        } else {
            display.innerText += value;
        }
    }

    function clearDisplay() {
        document.getElementById('display').innerText = '0';
    }

    function calculateResult() {
        let display = document.getElementById('display');
        let expression = display.innerText;

        try {
            // Handling special cases
            if (expression.includes('sqrt(')) {
                expression = expression.replace('sqrt(', 'Math.sqrt(');
            }
            if (expression.includes('sin(')) {
                expression = expression.replace('sin(', 'Math.sin(');
            }
            if (expression.includes('cos(')) {
                expression = expression.replace('cos(', 'Math.cos(');
            }
            if (expression.includes('tan(')) {
                expression = expression.replace('tan(', 'Math.tan(');
            }
            if (expression.includes('log(')) {
                expression = expression.replace('log(', 'Math.log10(');
            }

            // Evaluate the expression safely
            display.innerText = eval(expression);
        } catch (e) {
            display.innerText = 'Error';
        }
    }
</script>

</body>
</html>
