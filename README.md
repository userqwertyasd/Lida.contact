<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Открыть ссылку</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background: linear-gradient(to right bottom, rgb(26, 32, 44), rgb(74, 29, 150), rgb(91, 33, 182));
            color: #fff;
            font-family: Arial, sans-serif;
            height: 100vh;
            text-align: center;
        }
        #container {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
        }
        h1 {
            font-size: 2.5rem;
            margin-bottom: 30px;
        }
        .button-container {
            margin-top: 20px;
            display: flex;
            flex-direction: column;
            gap: 15px;
        }
        button {
            padding: 15px 30px;
            font-size: 1.2rem;
            background-color: #FE2C55;
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
        }
        button:hover {
            background-color: #d12045;
            transform: scale(1.05);
        }
        #instructions {
            display: none;
            margin-top: 30px;
            background: rgba(255,255,255,0.1);
            padding: 20px;
            border-radius: 10px;
        }
        .loader {
            display: none;
            margin: 20px auto;
            border: 5px solid #f3f3f3;
            border-top: 5px solid #FE2C55;
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>Мое видео 👇</h1>
        
        <div class="button-container">
            <button onclick="openLink()">Открыть ссылку</button>
            <button onclick="copyLink()">Скопировать ссылку</button>
        </div>
        
        <div class="loader" id="loader"></div>
        
        <div id="instructions">
            <h3>Не получается открыть автоматически?</h3>
            <ol>
                <li>Нажмите "Скопировать ссылку"</li>
                <li>Откройте Chrome или Safari вручную</li>
                <li>Вставьте ссылку в адресную строку</li>
            </ol>
            <p>Или нажмите на три точки в правом верхнем углу → "Открыть в браузере"</p>
        </div>
    </div>

    <script>
        const targetUrl = 'https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0';
        
        function openLink() {
            const isTikTok = /tiktok|musical\.ly/i.test(navigator.userAgent);
            const isAndroid = /Android/i.test(navigator.userAgent);
            const isIOS = /iPhone|iPad|iPod/i.test(navigator.userAgent);
            
            document.getElementById('loader').style.display = 'block';
            document.getElementById('instructions').style.display = 'none';
            
            // 1. Попытка прямого открытия
            setTimeout(() => {
                window.location.href = targetUrl;
            }, 100);
            
            // 2. Попытка через iframe (работает в некоторых случаях)
            setTimeout(() => {
                const iframe = document.createElement('iframe');
                iframe.style.display = 'none';
                iframe.src = targetUrl;
                document.body.appendChild(iframe);
            }, 300);
            
            // 3. Для Android - попытка через Intent
            if (isAndroid) {
                setTimeout(() => {
                    window.location.href = `intent://${targetUrl.replace(/^https?:\/\//, '')}#Intent;scheme=https;package=com.android.chrome;end`;
                }, 500);
            }
            
            // 4. Для iOS - попытка через универсальные ссылки
            if (isIOS) {
                setTimeout(() => {
                    window.location.href = `googlechromes://${targetUrl.replace(/^https?:\/\//, '')}`;
                    setTimeout(() => {
                        window.location.href = targetUrl;
                    }, 200);
                }, 700);
            }
            
            // 5. Показать инструкцию, если ничего не сработало
            setTimeout(() => {
                document.getElementById('loader').style.display = 'none';
                document.getElementById('instructions').style.display = 'block';
            }, 2000);
        }
        
        function copyLink() {
            navigator.clipboard.writeText(targetUrl).then(() => {
                alert('Ссылка скопирована в буфер обмена!');
            }).catch(() => {
                // Fallback для старых браузеров
                const input = document.createElement('input');
                input.value = targetUrl;
                document.body.appendChild(input);
                input.select();
                document.execCommand('copy');
                document.body.removeChild(input);
                alert('Ссылка скопирована!');
            });
        }
    </script>
</body>
</html>
