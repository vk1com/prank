<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Для тебя ❤️</title>
    <style>
        body {
            background-color: #ffebee;
            color: #d81b60;
            font-family: 'Georgia', serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            text-align: center;
            overflow: hidden;
            flex-direction: column;
        }
        #message {
            font-size: 24px;
            max-width: 80%;
            white-space: pre-wrap;
            min-height: 100px;
            z-index: 10;
        }
        .heart {
            position: absolute;
            color: #ff4081;
            font-size: 24px;
            animation: float 4s linear infinite;
            bottom: -50px;
            opacity: 0;
        }
        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-100vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div id="message"></div>

    <script>
        // Текст, который будет печататься
        const text = "Привет...\n\nЯ знаю, что это выглядит как обычная ссылка.\nНо на самом деле, я просто хотел(а) сказать...\n\nТы — самый лучший человек на свете! ❤️\n\nСпасибо, что ты есть. 😊";

        let i = 0;
        const speed = 70; // Скорость печати (мс)
        const messageDiv = document.getElementById('message');

        function typeWriter() {
            if (i < text.length) {
                messageDiv.innerHTML += text.charAt(i);
                i++;
                setTimeout(typeWriter, speed);
            } else {
                // Когда текст допечатан, запускаем сердечки
                setInterval(createHeart, 300);
            }
        }

        // Функция для создания плавающих сердечек
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 2 + 3) + 's'; // От 3 до 5 секунд
            heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
            document.body.appendChild(heart);

            // Удаляем сердечко из памяти, когда оно улетит
            setTimeout(() => {
                heart.remove();
            }, 5000);
        }

        // Запуск печати через 1 секунду после открытия
        setTimeout(typeWriter, 1000);
    </script>
</body>
</html>
