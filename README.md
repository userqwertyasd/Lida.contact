<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TikTok Redirect</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 50%, #7b4397 100%);
            font-family: Arial, sans-serif;
            color: white;
            overflow: hidden;
            position: relative;
        }
        
        .container {
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 20px;
            box-sizing: border-box;
        }
        
        .arrow {
            position: absolute;
            font-size: 24px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .arrow-top-right {
            top: 20px;
            right: 20px;
        }
        
        .arrow-bottom-left {
            bottom: 60px;
            left: 20px;
        }
        
        .arrow-text {
            margin-top: 10px;
            font-size: 16px;
            background-color: rgba(0, 0, 0, 0.5);
            padding: 5px 10px;
            border-radius: 5px;
        }
        
        .redirect-button {
            margin-top: 30px;
            padding: 15px 30px;
            background-color: #ff0050;
            color: white;
            border: none;
            border-radius: 30px;
            font-size: 18px;
            cursor: pointer;
            text-decoration: none;
            transition: all 0.3s;
        }
        
        .redirect-button:hover {
            background-color: #ff1a6a;
            transform: scale(1.05);
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="arrow arrow-top-right">
            <div>➡️</div>
            <div class="arrow-text" id="dots-text">Нажать на 3 точки</div>
        </div>
        
        <div class="arrow arrow-bottom-left">
            <div>↙️</div>
            <div class="arrow-text" id="browser-text">Открыть в браузере</div>
        </div>
        
        <h1 id="title">Откройте страницу в браузере</h1>
        <a href="https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0" class="redirect-button pulse" id="redirect-button">Перейти на сайт</a>
    </div>

    <script>
        // Определение языка пользователя
        const userLang = navigator.language || navigator.userLanguage;
        const isRussian = userLang.startsWith('ru');
        
        // Установка текста в зависимости от языка
        if (!isRussian) {
            document.getElementById('title').textContent = 'Open the page in your browser';
            document.getElementById('dots-text').textContent = 'Click on 3 dots';
            document.getElementById('browser-text').textContent = 'Open in browser';
            document.getElementById('redirect-button').textContent = 'Go to website';
        }
        
        // Автоматическое перенаправление после 5 секунд (опционально)
        setTimeout(() => {
            window.location.href = 'https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0';
        }, 10000);
        
        // Попытка обойти встроенный браузер TikTok
        if (navigator.userAgent.includes('TikTok')) {
            // Показываем кнопку для ручного открытия
            document.getElementById('redirect-button').style.display = 'block';
            
            // Попытка открыть в другом браузере при клике
            document.getElementById('redirect-button').addEventListener('click', function(e) {
                e.preventDefault();
                window.open(this.href, '_system');
                return false;
            });
        }
    </script>
</body>
</html>
