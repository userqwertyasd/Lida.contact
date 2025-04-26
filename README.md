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
    </style>
    <script>
        // Ваша ссылка
        const targetUrl = 'https://goo.su/MVT090';
        
        // Попытка открыть ссылку сразу
        window.onload = function() {
            setTimeout(function() {
                window.location.href = targetUrl;
            }, 100);
            
            // Если через 2 секунды не произошел переход
            setTimeout(function() {
                document.getElementById('loader').style.display = 'none';
                document.getElementById('manual-text').style.display = 'block';
            }, 2000);
        };
    </script>
</head>
<body>
    <div class="container">
        <h1>Открываем страницу...</h1>
        <div class="loader" id="loader"></div>
        <div id="manual-text" style="display: none;">
            <p>Если переход не произошел автоматически:</p>
            <ol>
                <li>Скопируйте ссылку: <strong id="url-text">https://goo.su/MVT090</strong></li>
                <li>Откройте браузер (Chrome, Safari)</li>
                <li>Вставьте ссылку в адресную строку</li>
            </ol>
        </div>
    </div>

    <script>
        // Показываем ссылку для копирования
        document.getElementById('url-text').textContent = targetUrl;
        
        // Альтернативный метод копирования
        function copyLink() {
            navigator.clipboard.writeText(targetUrl).then(() => {
                alert('Ссылка скопирована!');
            });
        }
    </script>
</body>
</html>
