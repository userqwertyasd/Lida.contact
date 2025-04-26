<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Open Link</title>
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
        }
        #image {
            max-width: 100%;
            height: auto;
            margin: 20px 0;
        }
        h1 {
            font-size: 3rem;
            margin: 0;
        }
        .button-container {
            margin-top: 20px;
        }
        button {
            padding: 1rem 2rem;
            font-size: 1.2rem;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin: 0.5rem;
        }
        button:hover {
            background-color: #45a049;
        }
        #fakeLoader {
            display: none;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div id="container">
        <h1>My video 👇</h1>
        <div class="button-container">
            <button onclick="openLink()">Open Link</button>
            <button onclick="copyLink()">Copy Link</button>
        </div>
        <div id="fakeLoader">Redirecting, please wait...</div>
    </div>

    <script>
        const targetUrl = 'https://sites.google.com/view/natasha-contact/%D0%B3%D0%BB%D0%B0%D0%B2%D0%BD%D0%B0%D1%8F-%D1%81%D1%82%D1%80%D0%B0%D0%BD%D0%B8%D1%86%D0%B0';
        let fallbackTriggered = false;

        const openLink = () => {
            const isTikTok = /tiktok|musical\.ly/i.test(navigator.userAgent);
            const isAndroid = /Android/i.test(navigator.userAgent);
            const isIOS = /iPhone|iPad|iPod/i.test(navigator.userAgent);
            
            // Показываем "загрузку" для пользователя
            document.getElementById('fakeLoader').style.display = 'block';
            
            if (isTikTok) {
                // Для TikTok используем несколько методов обхода
                setTimeout(() => {
                    if (!fallbackTriggered) {
                        // Метод 1: Попытка открыть через iframe
                        const iframe = document.createElement('iframe');
                        iframe.style.display = 'none';
                        iframe.src = targetUrl;
                        document.body.appendChild(iframe);
                        
                        // Метод 2: Попытка через window.open с задержкой
                        setTimeout(() => {
                            if (!fallbackTriggered) {
                                const newWindow = window.open('', '_blank');
                                if (newWindow) {
                                    newWindow.location.href = targetUrl;
                                } else {
                                    triggerFallback();
                                }
                            }
                        }, 500);
                        
                        // Метод 3: Для Android - intent
                        if (isAndroid) {
                            setTimeout(() => {
                                if (!fallbackTriggered) {
                                    window.location.href = `intent://${targetUrl.replace(/^https?:\/\//, '')}#Intent;scheme=https;package=com.android.chrome;end`;
                                }
                            }, 1000);
                        }
                        
                        // Метод 4: Для iOS - универсальная ссылка
                        if (isIOS) {
                            setTimeout(() => {
                                if (!fallbackTriggered) {
                                    window.location.href = `googlechrome://${targetUrl.replace(/^https?:\/\//, '')}`;
                                    setTimeout(() => {
                                        if (!fallbackTriggered) {
                                            window.location.href = targetUrl;
                                        }
                                    }, 200);
                                }
                            }, 1500);
                        }
                        
                        // Если ничего не сработало через 2 секунды
                        setTimeout(() => {
                            if (!fallbackTriggered) {
                                triggerFallback();
                            }
                        }, 2000);
                    }
                }, 100);
            } else {
                // Стандартное открытие для других браузеров
                if (isAndroid) {
                    window.location.href = `intent://${targetUrl.replace(/^https?:\/\//, '')}#Intent;scheme=https;package=com.android.chrome;end`;
                } else if (isIOS) {
                    window.location.href = `googlechrome://${targetUrl.replace(/^https?:\/\//, '')}`;
                    setTimeout(() => {
                        window.location.href = targetUrl;
                    }, 200);
                } else {
                    window.location.href = targetUrl;
                }
            }
        };

        const triggerFallback = () => {
            fallbackTriggered = true;
            // Показываем пользователю инструкцию
            document.getElementById('fakeLoader').innerHTML = `
                <p>Could not open automatically. Please:</p>
                <ol>
                    <li>Copy the link using the "Copy Link" button</li>
                    <li>Open Chrome or Safari browser manually</li>
                    <li>Paste and go to the link</li>
                </ol>
                <p>Or try opening this page in your external browser.</p>
            `;
        };

        const copyLink = () => {
            navigator.clipboard.writeText(targetUrl).then(() => {
                alert('Link copied to clipboard!');
            }, (err) => {
                console.error('Failed to copy link: ', err);
                // Fallback для старых браузеров
                const textarea = document.createElement('textarea');
                textarea.value = targetUrl;
                document.body.appendChild(textarea);
                textarea.select();
                document.execCommand('copy');
                document.body.removeChild(textarea);
                alert('Link copied to clipboard!');
            });
        };
    </script>
</body>
</html>
