<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Перенаправление</title>
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
    </style>
</head>
<body>
    <div class="container">
        <h1>Идёт перенаправление...</h1>
        <div class="loader"></div>
    </div>

    <script>
        // Таймер перенаправления (2000 мс = 2 секунды)
        setTimeout(function() {
            window.location.href = "https://prev.affomelody.com/click?pid=113214&offer_id=25";
        }, 2000);
    </script>
</body>
</html>
