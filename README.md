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
            background: linear-gradient(45deg, #3a0ca3, #4361ee, #7209b7);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            box-sizing: border-box;
        }
        .card {
            background: rgba(255,255,255,0.9);
            border-radius: 20px;
            padding: 25px;
            width: 95%;
            max-width: 400px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            text-align: center;
        }
        h1 {
            color: #3a0ca3;
            margin-top: 0;
            font-size: 24px;
        }
        .step {
            display: flex;
            align-items: center;
            margin: 25px 0;
            position: relative;
        }
        .arrow {
            font-size: 40px;
            color: #7209b7;
            margin-right: 15px;
            flex-shrink: 0;
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
            background: linear-gradient(45deg, #4361ee, #3a0ca3);
            color: white;
            border: none;
            padding: 15px;
            width: 100%;
            border-radius: 10px;
            font-size: 18px;
            margin-top: 20px;
            font-weight: bold;
            cursor: pointer;
            box-shadow: 0 4px 15px rgba(58,12,163,0.4);
        }
        .note {
            font-size: 14px;
            margin-top: 20px;
            color: #666;
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
        
        <div class="step">
            <div class="arrow">➤</div>
            <div class="step-text">
                Перейди на страницу знакомства<br>
                в твоём браузере
            </div>
        </div>
        
        <button onclick="window.open('https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0', '_blank')">ОТКРЫТЬ ССЫЛКУ</button>
        
        <div class="note">
            Если не открывается автоматически - нажми кнопку выше
        </div>
    </div>
</body>
</html>
