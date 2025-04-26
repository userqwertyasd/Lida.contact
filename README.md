<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Начать знакомство</title>
    <style>
        body {
            margin: 0;
            padding: 15px;
            font-family: Arial, sans-serif;
            background: #4361ee; /* Синий фон */
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            box-sizing: border-box;
        }
        .card {
            background: white;
            border-radius: 20px;
            padding: 25px;
            width: 95%;
            max-width: 400px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            text-align: center;
        }
        h1 {
            color: #4361ee;
            margin-top: 0;
            font-size: 24px;
        }
        .step {
            display: flex;
            align-items: center;
            margin: 25px 0;
        }
        .arrow {
            font-size: 40px;
            color: #4361ee;
            margin-right: 15px;
        }
        .step-text {
            text-align: left;
            color: #333;
        }
        .highlight {
            background: #4cc9f0;
            color: #000;
            padding: 2px 5px;
            border-radius: 4px;
        }
        button {
            background: #4361ee;
            color: white;
            border: none;
            padding: 15px;
            width: 100%;
            border-radius: 10px;
            font-size: 18px;
            margin-top: 20px;
            font-weight: bold;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <div class="card">
        <h1>🌟 Начать знакомство 🌟</h1>
        
        <div class="step">
            <div class="arrow">➤</div>
            <div class="step-text">
                Нажми <span class="highlight">⋮ три точки</span><br>
                в правом углу экрана
            </div>
        </div>
        
        <div class="step">
            <div class="arrow">➤</div>
            <div class="step-text">
                Выбери <span class="highlight">"Открыть в браузере"</span>
            </div>
        </div>
        
        <button onclick="window.location.href='https://goo.su/MVT090'">
            ПЕРЕЙТИ НА СТРАНИЦУ
        </button>
    </div>
</body>
</html>
