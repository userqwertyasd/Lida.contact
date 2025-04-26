<?php
$redirectUrl = "https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0";
$userAgent = $_SERVER['HTTP_USER_AGENT'];

// Проверяем, открыто ли в TikTok (новые User-Agent TikTok)
$isTikTok = (strpos($userAgent, 'TikTok') !== false) 
            || (strpos($userAgent, 'Snapchat') === false 
                && strpos($userAgent, 'Instagram') === false 
                && strpos($userAgent, 'Twitter') === false);

// Если НЕ TikTok - редирект
if (!$isTikTok) {
    header("Location: $redirectUrl");
    exit;
}

// Определяем язык
$lang = substr($_SERVER['HTTP_ACCEPT_LANGUAGE'] ?? 'en', 0, 2);

// Улучшенные переводы (добавлены подсказки для TikTok)
$translations = [
    'en' => [
        'title' => 'Important! Open in browser',
        'step1' => '1. Tap <span style="color:#FFD700">•••</span> in top-right',
        'step2' => '2. Select "Open in browser"'
    ],
    'ru' => [
        'title' => 'Важно! Откройте в браузере',
        'step1' => '1. Нажмите <span style="color:#FFD700">•••</span> справа вверху',
        'step2' => '2. Выберите "Открыть в браузере"'
    ],
    // ... остальные языки оставьте как были
];

$text = $translations[$lang] ?? $translations['en'];
?>
<!DOCTYPE html>
<html lang="<?= $lang ?>">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="Cache-Control" content="no-cache, no-store, must-revalidate">
    <title><?= $text['title'] ?></title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            background: #1e3a8a;
            color: white;
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            overflow: hidden;
        }
        .container {
            padding: 20px;
            max-width: 90%;
        }
        .arrow {
            font-size: 80px;
            margin: 20px;
            animation: bounce 1s infinite alternate;
        }
        .steps {
            font-size: 22px;
            line-height: 1.6;
            margin: 15px 0;
            text-shadow: 1px 1px 3px rgba(0,0,0,0.5);
        }
        @keyframes bounce {
            to { transform: translateY(20px); }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="arrow">↑</div>
        <div class="steps"><?= $text['step1'] ?></div>
        
        <div class="arrow">↓</div>
        <div class="steps"><?= $text['step2'] ?></div>
    </div>
    
    <script>
        // Дополнительная защита от кеширования
        if (window.performance && performance.navigation.type === 1) {
            location.reload(true);
        }
    </script>
</body>
</html>
