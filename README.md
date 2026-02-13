<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>For Vibha ❤️</title>

<style>
body {
    margin: 0;
    padding: 0;
    background: linear-gradient(to right, #ff758c, #ff7eb3);
    font-family: 'Segoe UI', sans-serif;
    text-align: center;
    color: white;
    overflow: hidden;
}

.container {
    margin-top: 50px;
}

/* Intro Screen */
#intro {
    position: fixed;
    width: 100%;
    height: 100%;
    background: black;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    z-index: 10;
}

#intro button {
    padding: 15px 30px;
    border: none;
    border-radius: 30px;
    background: #ff4b7d;
    color: white;
    font-size: 18px;
    cursor: pointer;
}

/* Bears */
.bear-container {
    position: relative;
    height: 160px;
    margin-top: 20px;
}

.bear {
    font-size: 80px;
    position: absolute;
    transition: 1s;
}

#bear1 { left: 25%; }
#bear2 { right: 25%; }

#loveHeart {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    font-size: 40px;
    display: none;
}

/* Buttons */
button {
    padding: 12px 25px;
    font-size: 16px;
    border: none;
    border-radius: 25px;
    cursor: pointer;
    margin: 10px;
}

#yesBtn {
    background: white;
    color: #ff4b7d;
}

#noBtn {
    background: black;
    color: white;
    position: absolute;
}

#finalMessage {
    display: none;
    font-size: 22px;
    margin-top: 20px;
}

/* Falling Hearts */
.heart {
    position: fixed;
    top: -10px;
    color: pink;
    animation: fall 5s linear infinite;
}

@keyframes fall {
    0% { transform: translateY(0); opacity: 1; }
    100% { transform: translateY(110vh); opacity: 0; }
}
</style>
</head>

<body>

<!-- Intro -->
<div id="intro">
    <h1>❤️ For Vibha ❤️</h1>
    <button onclick="startLove()">Open My Heart 💖</button>
</div>

<audio id="bgMusic" loop>
    <source src="music.mp3" type="audio/mpeg">
</audio>

<div class="container">
    <h2>2.3 Years. Different Places. Same Love. 💕</h2>

    <div class="bear-container">
        <div id="bear1" class="bear">🐻</div>
        <div id="bear2" class="bear">🐻‍❄️</div>
        <div id="loveHeart">❤️</div>
    </div>

    <h2>Will You Be My Valentine? 💍</h2>

    <button id="yesBtn" onclick="yesClicked()">Yes 💖</button>
    <button id="noBtn" onmouseover="moveButton()">No 😢</button>

    <div id="finalMessage">
        Long distance was harder than clicking yes 🥺<br><br>
        One day… no more calls ending.<br>
        No more countdowns.<br>
        Just us. Together. Always. ❤️
    </div>
</div>

<script>
let noCount = 0;

function startLove() {
    document.getElementById("intro").style.display = "none";
    document.getElementById("bgMusic").play();
    createHearts();
}

function yesClicked() {
    // Move bears together
    document.getElementById("bear1").style.left = "40%";
    document.getElementById("bear2").style.right = "40%";

    // Show heart between them
    document.getElementById("loveHeart").style.display = "block";

    document.getElementById("finalMessage").style.display = "block";
}

function moveButton() {
    var button = document.getElementById("noBtn");
    var x = Math.random() * (window.innerWidth - 100);
    var y = Math.random() * (window.innerHeight - 50);
    button.style.left = x + "px";
    button.style.top = y + "px";

    noCount++;
    if(noCount >= 3){
        alert("Long distance was harder than clicking yes 🥺");
    }
}

function createHearts() {
    setInterval(() => {
        var heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = "❤️";
        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize = (Math.random() * 20 + 20) + "px";
        document.body.appendChild(heart);

        setTimeout(() => {
            heart.remove();
        }, 5000);
    }, 400);
}
</script>

</body>
</html>
