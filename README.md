<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>简易计算器</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #f0f0f0;
        }

        .calculator {
            background-color: #222;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
        }

        #input-box {
            width: 100%;
            padding: 15px;
            margin-bottom: 15px;
            font-size: 28px;
            text-align: right;
            border: none;
            border-radius: 8px;
            background: #fff;
        }

        .btn-grid {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
        }

        button {
            padding: 16px;
            font-size: 20px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.2s;
        }

        button:hover {
            opacity: 0.85;
        }

        .num-btn {
            background-color: #ffffff;
        }

        .op-btn {
            background-color: #ff9500;
            color: white;
        }

        .clear-btn {
            background-color: #ff3b30;
            color: white;
        }

        .equal-btn {
            background-color: #34c759;
            color: white;
            grid-column: span 2;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <input type="text" id="input-box" readonly>
        <div class="btn-grid">
            <button class="clear-btn" onclick="clearInput()">C</button>
            <button class="op-btn" onclick="appendValue('/')">/</button>
            <button class="op-btn" onclick="appendValue('*')">×</button>
            <button class="op-btn" onclick="appendValue('-')">-</button>

            <button class="num-btn" onclick="appendValue('7')">7</button>
            <button class="num-btn" onclick="appendValue('8')">8</button>
            <button class="num-btn" onclick="appendValue('9')">9</button>
            <button class="op-btn" onclick="appendValue('+')">+</button>

            <button class="num-btn" onclick="appendValue('4')">4</button>
            <button class="num-btn" onclick="appendValue('5')">5</button>
            <button class="num-btn" onclick="appendValue('6')">6</button>
            <button onclick="backspace()">⌫</button>

            <button class="num-btn" onclick="appendValue('1')">1</button>
            <button class="num-btn" onclick="appendValue('2')">2</button>
            <button class="num-btn" onclick="appendValue('3')">3</button>

            <button class="num-btn" onclick="appendValue('0')">0</button>
            <button class="num-btn" onclick="appendValue('.')">.</button>
            <button class="equal-btn" onclick="calculateResult()">=</button>
        </div>
    </div>

    <script>
        const inputBox = document.getElementById('input-box');

        // 追加字符
        function appendValue(val) {
            inputBox.value += val;
        }

        // 清空
        function clearInput() {
            inputBox.value = '';
        }

        // 退格
        function backspace() {
            inputBox.value = inputBox.value.slice(0, -1);
        }

        // 计算结果
        function calculateResult() {
            try {
                let exp = inputBox.value.replace(/×/g, '*');
                let result = eval(exp);
                inputBox.value = result;
            } catch (e) {
                inputBox.value = '错误';
                setTimeout(clearInput, 1000);
            }
        }
    </script>
</body>
</html>
