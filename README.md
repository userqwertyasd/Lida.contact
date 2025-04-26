<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Как открыть ссылку</title>
    <style>
        body {
            margin: 0;
            padding: 15px;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #ff4d4d, #f9cb28);
            height: 100vh;
            box-sizing: border-box;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            max-width: 100%;
        }
        h1 {
            color: #ff2d55;
            text-align: center;
            margin-top: 0;
            font-size: 22px;
        }
        .step {
            margin-bottom: 25px;
            position: relative;
        }
        .arrow {
            font-size: 40px;
            color: #ff2d55;
            position: absolute;
        }
        .step-content {
            margin-left: 50px;
        }
        .highlight {
            background: #fff200;
            padding: 2px 5px;
            border-radius: 3px;
        }
        .reason {
            background: #ffebee;
            padding: 12px;
            border-radius: 10px;
            margin: 15px 0;
            border-left: 4px solid #ff2d55;
        }
        button {
            background: #ff2d55;
            color: white;
            border: none;
            padding: 12px;
            width: 100%;
            border-radius: 8px;
            font-size: 16px;
            margin-top: 10px;
            font-weight: bold;
        }
        .emoji {
            font-size: 24px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1><span class="emoji">🔗</span> Как открыть ссылку в TikTok</h1>
        
        <div class="reason">
            <strong>Почему не открывается?</strong><br>
            TikTok блокирует переходы на внешние сайты. Нужно открыть через браузер!
        </div>
        
        <div class="step">
            <div class="arrow">➤</div>
            <div class="step-content">
                <strong>1. Нажмите <span class="highlight">⋮</span> (три точки)</strong><br>
                В правом верхнем углу экрана
            </div>
        </div>
        
        <div class="step">
            <div class="arrow">➤</div>
            <div class="step-content">
                <strong>2. Выберите <span class="highlight">"Открыть в браузере"</span></strong><br>
                В появившемся меню
            </div>
        </div>
        
        <div class="step">
            <div class="arrow">➤</div>
            <div class="step-content">
                <strong>3. Сайт откроется автоматически</strong><br>
                В вашем Chrome, Safari или другом браузере
            </div>
        </div>
        
        <button onclick="copyLink()">СКОПИРОВАТЬ ССЫЛКУ</button>
    </div>

    <script>
        const targetUrl = 'https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0';
        
        function copyLink() {
            navigator.clipboard.writeText(targetUrl).then(() => {
                alert('Ссылка скопирована! Вставьте её в браузер.');
            }).catch(() => {
                const input = document.createElement('input');
                input.value = targetUrl;
                document.body.appendChild(input);
                input.select();
                document.execCommand('copy');
                document.body.removeChild(input);
                alert('Ссылка скопирована! Откройте браузер и вставьте её.');
            });
        }
    </script>
</body>
</html>
