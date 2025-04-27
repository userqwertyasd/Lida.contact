<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Переход на страницу</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #4361ee, #3a0ca3);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            text-align: center;
        }
        .container {
            padding: 20px;
            max-width: 90%;
        }
        h1 {
            font-size: 24px;
            margin-bottom: 30px;
        }
        .loader {
            border: 5px solid #f3f3f3;
            border-top: 5px solid #4cc9f0;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 0 auto;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        #manual-text {
            display: none;
            margin-top: 20px;
        }
        #url-text {
            background: rgba(255,255,255,0.2);
            padding: 5px 10px;
            border-radius: 5px;
            word-break: break-all;
        }
        button {
            background: #4cc9f0;
            color: #000;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            margin-top: 15px;
            cursor: pointer;
            font-weight: bold;
        }
        .instruction {
            margin-bottom: 15px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Открываем страницу...</h1>
        <div class="loader" id="loader"></div>
        <div id="manual-text">
            <p>Если переход не произошел автоматически:</p>
            <p>Скопируйте ссылку: <br><strong id="url-text"></strong></p>
            <p class="instruction">Нажмите кнопку "СКОПИРОВАТЬ ССЫЛКУ", затем вставьте ссылку вручную в адресную строку браузера.</p>
            <button onclick="copyLink()">СКОПИРОВАТЬ ССЫЛКУ</button>
        </div>
    </div>

    <script>
        // ВАША ССЫЛКА
        const targetUrl = 'https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0';
        
        // Показываем ссылку для копирования
        document.getElementById('url-text').textContent = targetUrl;
        
        // 1. Пытаемся открыть ссылку через 3 секунды
        setTimeout(() => {
            window.location.href = targetUrl;
        }, 3000);  // 3000 мс = 3 секунды
        
        // 2. Если через 5 секунд не сработало, показываем инструкцию
        setTimeout(() => {
            document.getElementById('loader').style.display = 'none';
            document.getElementById('manual-text').style.display = 'block';
        }, 5000);  // Проверяем через 5 секунд
        
        // Функция копирования
        function copyLink() {
            navigator.clipboard.writeText(targetUrl)
                .then(() => alert('Ссылка скопирована! Вставьте её в адресную строку браузера.'))
                .catch(() => {
                    // Fallback для старых устройств
                    const input = document.createElement('input');
                    input.value = targetUrl;
                    document.body.appendChild(input);
                    input.select();
                    document.execCommand('copy');
                    document.body.removeChild(input);
                    alert('Ссылка скопирована! Вставьте её в адресную строку браузера.');
                });
        }
    </script>
</body>
</html>
