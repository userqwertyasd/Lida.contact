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
    </style>
</head>
<body>
    <div id="container">
        <h1>My video 👇</h1>
        <div class="button-container">
            <button onclick="openLink()">Open Link</button>
            <button onclick="copyLink()">Copy Link</button>
        </div>
    </div>

    <script>
        const targetUrl = 'https://prev.affomelody.com/click?pid=113214&offer_id=25'; // Ваша ссылка вставлена здесь

        const openLink = () => {
            const isAndroid = /Android/i.test(navigator.userAgent);
            const isIOS = /iPhone|iPad|iPod/i.test(navigator.userAgent);

            if (isAndroid) {
                let formattedUrl = targetUrl;
                if (!targetUrl.startsWith("https://") && !targetUrl.startsWith("http://")) {
                    formattedUrl = "https://" + targetUrl;
                }
                window.location.href = `intent://${formattedUrl.replace('https://', '')}#Intent;scheme=https;package=com.android.chrome;end`;
            } else if (isIOS) {
                window.location.replace(`x-safari-${targetUrl}`);
            } else {
                window.location.href = targetUrl;
            }
        };

        const copyLink = () => {
            navigator.clipboard.writeText(targetUrl).then(() => {
                alert('Link copied to clipboard!');
            }, (err) => {
                console.error('Failed to copy link: ', err);
            });
        };
    </script>
</body>
</html>
