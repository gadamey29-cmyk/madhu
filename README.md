<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Be My Valentine ❤️</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
            background: linear-gradient(to right, #ff758c, #ff7eb3);
            text-align: center;
            color: white;
            overflow: hidden;
        }

        h1 {
            margin-top: 80px;
            font-size: 40px;
        }

        .heart {
            font-size: 70px;
            animation: heartbeat 1s infinite;
        }

        @keyframes heartbeat {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }

        .buttons {
            margin-top: 40px;
        }

        button {
            padding: 15px 30px;
            font-size: 18px;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            margin: 10px;
            transition: 0.3s;
        }

        #yesBtn {
            background-color: white;
            color: #ff4b7d;
        }

        #yesBtn:hover {
            background-color: #ff4b7d;
            color: white;
        }

        #noBtn {
            background-color: #222;
            color: white;
            position: absolute;
        }

        #message {
            font-size: 28px;
            margin-top: 30px;
            display: none;
        }
    </style>
</head>
<body>

    <!-- Background Music -->
    <audio autoplay loop>
        <source src="music.mp3" type="audio/mpeg">
    </audio>

    <div class="heart">❤️</div>
    <h1>Will You Be My Valentine? 💕</h1>

    <div class="buttons">
        <button id="yesBtn" onclick="yesClicked()">Yes 💖</button>
        <button id="noBtn" onmouseover="moveButton()">No 😢</button>
    </div>

    <div id="message">Yayyyy!!! I Love You So Much 💍💞</div>

    <script>
        function yesClicked() {
            document.getElementById("message").style.display = "block";
        }

        function moveButton() {
            var button = document.getElementById("noBtn");
            var x = Math.random() * (window.innerWidth - 100);
            var y = Math.random() * (window.innerHeight - 50);

            button.style.left = x + "px";
            button.style.top = y + "px";
        }
    </script>

</body>
</html>
