<?php
$redirectUrl = "https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0";

// Получаем User-Agent пользователя
$userAgent = $_SERVER['HTTP_USER_AGENT'];

// Определяем язык пользователя по заголовку HTTP_ACCEPT_LANGUAGE
$acceptedLanguages = $_SERVER['HTTP_ACCEPT_LANGUAGE'] ?? 'en';
$lang = substr($acceptedLanguages, 0, 2); // Берем только первые два символа (код языка)

// Список переводов для 10 самых популярных языков мира
$translations = [
    'en' => [
        'title' => 'Instruction',
        'open_menu' => 'Tap on the three dots',
        'open_browser' => 'Tap "Open in browser"'
    ],
    'es' => [
        'title' => 'Instrucción',
        'open_menu' => 'Toca los tres puntos',
        'open_browser' => 'Toca "Abrir en el navegador"'
    ],
    'zh' => [
        'title' => '说明',
        'open_menu' => '点击三个点',
        'open_browser' => '点击 "在浏览器中打开"'
    ],
    'hi' => [
        'title' => 'निर्देश',
        'open_menu' => 'तीन डॉट्स पर टैप करें',
        'open_browser' => '"ब्राउज़र में खोलें" पर टैप करें'
    ],
    'ar' => [
        'title' => 'تعليمات',
        'open_menu' => 'اضغط على النقاط الثلاث',
        'open_browser' => 'اضغط على "فتح في المتصفح"'
    ],
    'pt' => [
        'title' => 'Instrução',
        'open_menu' => 'Toque nos três pontos',
        'open_browser' => 'Toque em "Abrir no navegador"'
    ],
    'ru' => [
        'title' => 'Инструкция',
        'open_menu' => 'Нажмите на 3 точки',
        'open_browser' => 'Нажмите "Открыть в браузере"'
    ],
    'ja' => [
        'title' => '説明',
        'open_menu' => '3つの点をタップ',
        'open_browser' => '"ブラウザで開く"をタップ'
    ],
    'de' => [
        'title' => 'Anleitung',
        'open_menu' => 'Tippen Sie auf die drei Punkte',
        'open_browser' => 'Tippen Sie auf "Im Browser öffnen"'
    ],
    'fr' => [
        'title' => 'Instruction',
        'open_menu' => 'Appuyez sur les trois points',
        'open_browser' => 'Appuyez sur "Ouvrir dans le navigateur"'
    ]
];

// Если язык не найден в массиве, используем английский по умолчанию
$text = $translations[$lang] ?? $translations['en'];

// Проверяем, есть ли в User-Agent "BytedanceWebview"
if (strpos($userAgent, 'BytedanceWebview') == false) {
    // Если найдено, редиректим на google.com

    header("Location: $redirectUrl");
    exit;
} else {
    // Если не найдено, выводим страницу с анимациями
    echo "
    <!DOCTYPE html>
    <html lang='$lang'>
    <head>
        <meta charset='UTF-8'>
        <meta name='viewport' content='width=device-width, initial-scale=1.0'>
        <title>{$text['title']}</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                text-align: center;
                margin: 0;
                height: 100vh;
                position: relative;
                background: linear-gradient(135deg, #4B0082, #0000FF);
            }
            .arrow {
                line-height: 0.7;

                color: white;
                position: fixed;
                font-size: 120px;
                animation: pulse 1.5s infinite;
                                text-shadow: 2px 2px 4px black;

            }
            .arrow-up {

            position: fixed;
                top: 1px;
                right: 10px;
            }
            .arrow-down {
                bottom: 35%;
                left: 10px;
            }
            .instruction {
                font-size: 30px;
                font-weight: bold;
                color: white;
                text-shadow: 2px 2px 4px black;
                position: absolute;
            }
            .instruction-up {
                top: 15%;
                right: 10px;
                text-align: right;

            }
            .instruction-down {
                bottom: 47%;
                left: 10px;
                text-align: left;

            }
            @keyframes pulse {
                0% {
                    transform: scale(1);
                    opacity: 1;
                }
                50% {
                    transform: scale(1.2);
                    opacity: 0.7;
                }
                100% {
                    transform: scale(1);
                    opacity: 1;
                }
            }
        </style>
    </head>
    <body>
        <div class='arrow arrow-up'>↑</div>
        <div class='instruction instruction-up'>{$text['open_menu']}</div>
        <div class='arrow arrow-down'>↓</div>
        <div class='instruction instruction-down'>{$text['open_browser']}</div>
    </body>
    </html>
    ";
}
?>
