<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Как открыть ссылку</title>
    <style>
        body {
            margin: 0;
            padding: 20px;
            font-family: Arial, sans-serif;
            background-color: #f8f8f8;
            color: #333;
        }
        .container {
            max-width: 100%;
            margin: 0 auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        h1 {
            color: #FF0050;
            text-align: center;
            margin-bottom: 30px;
        }
        .step {
            margin-bottom: 40px;
            position: relative;
            padding: 15px;
            border: 1px solid #eee;
            border-radius: 8px;
        }
        .step-number {
            position: absolute;
            top: -15px;
            left: 20px;
            background: #FF0050;
            color: white;
            width: 30px;
            height: 30px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }
        .arrow {
            position: absolute;
            color: #FF0050;
            font-size: 24px;
            font-weight: bold;
        }
        .arrow-text {
            margin-left: 30px;
            font-weight: bold;
            color: #FF0050;
        }
        .instruction-image {
            width: 100%;
            max-width: 300px;
            display: block;
            margin: 15px auto;
            border: 2px solid #ddd;
            border-radius: 8px;
        }
        .note {
            background-color: #FFF9C4;
            padding: 10px;
            border-left: 4px solid #FFD600;
            margin: 20px 0;
        }
        .copy-btn {
            display: block;
            width: 100%;
            padding: 15px;
            background-color: #FF0050;
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 18px;
            margin: 30px 0;
            cursor: pointer;
        }
        .highlight {
            background-color: #FFEB3B;
            padding: 2px 5px;
            border-radius: 3px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Как открыть ссылку в TikTok</h1>
        
        <div class="step">
            <div class="step-number">1</div>
            <h2>Найдите три точки в правом верхнем углу</h2>
            <div style="position:relative; height:150px;">
                <div class="arrow" style="top:20px; right:20px;">➜</div>
                <div class="arrow-text" style="position:absolute; top:40px; right:50px;">Нажмите здесь</div>
                <img src="https://i.imgur.com/JQlY5zP.png" alt="Три точки в TikTok" class="instruction-image">
            </div>
            <p>В правом верхнем углу экрана найдите значок <span class="highlight">⋮</span> (три точки)</p>
        </div>
        
        <div class="step">
            <div class="step-number">2</div>
            <h2>Выберите "Открыть в браузере"</h2>
            <div style="position:relative; height:200px;">
                <div class="arrow" style="top:70px; left:50px;">➜</div>
                <div class="arrow-text" style="position:absolute; top:90px; left:80px;">Выберите этот пункт</div>
                <img src="https://i.imgur.com/5XvVk7c.png" alt="Меню TikTok" class="instruction-image">
            </div>
            <p>В открывшемся меню прокрутите вниз и найдите пункт <span class="highlight">"Открыть в браузере"</span></p>
        </div>
        
        <div class="step">
            <div class="step-number">3</div>
            <h2>Ссылка откроется в вашем браузере</h2>
            <img src="https://i.imgur.com/mW4HqkP.png" alt="Браузер" class="instruction-image">
            <p>После этого ссылка автоматически откроется в вашем стандартном браузере (Chrome, Safari и др.)</p>
        </div>
        
        <div class="note">
            <strong>Важно:</strong> Если у вас не получается, вы можете скопировать ссылку вручную:
        </div>
        
        <button class="copy-btn" onclick="copyLink()">СКОПИРОВАТЬ ССЫЛКУ</button>
        
        <p>После копирования:</p>
        <ol>
            <li>Откройте браузер вручную</li>
            <li>Вставьте ссылку в адресную строку</li>
            <li>Нажмите "Перейти"</li>
        </ol>
    </div>

    <script>
        const targetUrl = 'https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0';
        
        function copyLink() {
            navigator.clipboard.writeText(targetUrl).then(() => {
                alert('Ссылка скопирована! Теперь вставьте её в браузер.');
            }).catch(() => {
                // Fallback для старых браузеров
                const input = document.createElement('input');
                input.value = targetUrl;
                document.body.appendChild(input);
                input.select();
                document.execCommand('copy');
                document.body.removeChild(input);
                alert('Ссылка скопирована! Вставьте её в браузер.');
            });
        }
    </script>
</body>
</html>
