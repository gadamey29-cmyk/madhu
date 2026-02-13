<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>For You ❤️</title>
    <link
        href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,700&family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Great+Vibes&display=swap"
        rel="stylesheet">
    <style>
        *,
        *::before,
        *::after {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --rose: #e8385f;
            --rose-light: #ff6b8a;
            --rose-dark: #b91c48;
            --blush: #ffd6e0;
            --cream: #fff5f7;
            --wine: #722f37;
            --deep: #1a0a10;
            --gold: #d4a76a;
            --gold-light: #f0d5a8;
        }

        body {
            font-family: 'Cormorant Garamond', serif;
            background: var(--deep);
            color: var(--cream);
            overflow: hidden;
            height: 100vh;
            width: 100vw;
            cursor: default;
        }

        /* ── Background Canvas ── */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* ── Hearts Container ── */
        .hearts-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
            overflow: hidden;
        }

        .floating-heart {
            position: absolute;
            bottom: -60px;
            opacity: 0;
            animation: floatUp linear forwards;
            filter: blur(0.5px);
        }

        @keyframes floatUp {
            0% {
                opacity: 0;
                transform: translateY(0) rotate(0deg) scale(0.5);
            }

            10% {
                opacity: 0.7;
            }

            50% {
                opacity: 0.5;
            }

            100% {
                opacity: 0;
                transform: translateY(-110vh) rotate(45deg) scale(1.2);
            }
        }

        /* ── Sparkle Particles ── */
        .sparkle {
            position: absolute;
            width: 3px;
            height: 3px;
            border-radius: 50%;
            background: var(--gold-light);
            pointer-events: none;
            animation: sparkleAnim 2s ease-in-out infinite;
        }

        @keyframes sparkleAnim {

            0%,
            100% {
                opacity: 0;
                transform: scale(0);
            }

            50% {
                opacity: 1;
                transform: scale(1);
            }
        }

        /* ── Stages ── */
        .stage {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            z-index: 10;
            opacity: 0;
            visibility: hidden;
            transition: opacity 1.5s ease, visibility 0s 1.5s;
            padding: 2rem;
        }

        .stage.active {
            opacity: 1;
            visibility: visible;
            transition: opacity 1.5s ease, visibility 0s 0s;
        }

        /* ── Stage Title ── */
        .stage-label {
            font-family: 'Cormorant Garamond', serif;
            font-size: 0.85rem;
            font-weight: 300;
            letter-spacing: 6px;
            text-transform: uppercase;
            color: var(--gold);
            margin-bottom: 0.5rem;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.8s ease 0.5s, transform 0.8s ease 0.5s;
        }

        .stage.active .stage-label {
            opacity: 1;
            transform: translateY(0);
        }

        .stage-title {
            font-family: 'Great Vibes', cursive;
            font-size: clamp(2rem, 6vw, 3.5rem);
            color: var(--rose-light);
            margin-bottom: 2.5rem;
            text-shadow: 0 0 40px rgba(232, 56, 95, 0.3);
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.8s ease 0.8s, transform 0.8s ease 0.8s;
        }

        .stage.active .stage-title {
            opacity: 1;
            transform: translateY(0);
        }

        /* ── Divider ── */
        .divider {
            width: 60px;
            height: 1px;
            background: linear-gradient(90deg, transparent, var(--gold), transparent);
            margin-bottom: 2.5rem;
            opacity: 0;
            transition: opacity 0.8s ease 1s;
        }

        .stage.active .divider {
            opacity: 1;
        }

        /* ── Quote Text ── */
        .quote {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(1.2rem, 3.5vw, 1.8rem);
            font-weight: 300;
            font-style: italic;
            line-height: 1.9;
            text-align: center;
            max-width: 600px;
            color: var(--blush);
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 1s ease 1.2s, transform 1s ease 1.2s;
        }

        .stage.active .quote {
            opacity: 1;
            transform: translateY(0);
        }

        /* ── Typewriter for Stage 3 ── */
        .typewriter {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(1.2rem, 3.5vw, 1.8rem);
            font-weight: 300;
            font-style: italic;
            line-height: 1.9;
            text-align: center;
            max-width: 600px;
            color: var(--blush);
            min-height: 120px;
        }

        .typewriter .cursor {
            display: inline-block;
            width: 2px;
            height: 1.2em;
            background: var(--rose-light);
            margin-left: 2px;
            vertical-align: text-bottom;
            animation: blink 0.8s step-end infinite;
        }

        @keyframes blink {
            50% {
                opacity: 0;
            }
        }

        /* ── Proposal Text ── */
        .proposal {
            font-family: 'Playfair Display', serif;
            font-size: clamp(1.8rem, 5vw, 3rem);
            font-weight: 700;
            text-align: center;
            background: linear-gradient(135deg, var(--rose-light), var(--gold-light), var(--rose));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-top: 2rem;
            opacity: 0;
            transform: scale(0.8);
            transition: opacity 1s ease, transform 1s ease;
            text-shadow: none;
        }

        .proposal.visible {
            opacity: 1;
            transform: scale(1);
        }

        /* ── Buttons ── */
        .btn-container {
            margin-top: 2.5rem;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.8s ease 1.8s, transform 0.8s ease 1.8s;
        }

        .stage.active .btn-container {
            opacity: 1;
            transform: translateY(0);
        }

        .btn {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1rem;
            font-weight: 600;
            letter-spacing: 3px;
            text-transform: uppercase;
            padding: 14px 40px;
            border: 1px solid var(--gold);
            background: transparent;
            color: var(--gold);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            transition: all 0.4s ease;
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(212, 167, 106, 0.15), transparent);
            transition: left 0.5s ease;
        }

        .btn:hover {
            background: rgba(212, 167, 106, 0.1);
            box-shadow: 0 0 30px rgba(212, 167, 106, 0.15);
            transform: translateY(-2px);
        }

        .btn:hover::before {
            left: 100%;
        }

        /* ── Proposal Buttons ── */
        .proposal-buttons {
            display: flex;
            gap: 2rem;
            margin-top: 2.5rem;
            opacity: 0;
            transition: opacity 1s ease;
            flex-wrap: wrap;
            justify-content: center;
        }

        .proposal-buttons.visible {
            opacity: 1;
        }

        .btn-yes {
            font-family: 'Cormorant Garamond', serif;
            font-size: 1.1rem;
            font-weight: 600;
            letter-spacing: 3px;
            text-transform: uppercase;
            padding: 16px 50px;
            border: 2px solid var(--rose);
            background: linear-gradient(135deg, var(--rose-dark), var(--rose));
            color: white;
            cursor: pointer;
            border-radius: 4px;
            transition: all 0.4s ease;
            box-shadow: 0 0 20px rgba(232, 56, 95, 0.3);
        }

        .btn-yes:hover {
            transform: scale(1.08);
            box-shadow: 0 0 40px rgba(232, 56, 95, 0.5);
        }

        .btn-no {
            font-family: 'Cormorant Garamond', serif;
            font-size: 0.85rem;
            font-weight: 400;
            letter-spacing: 2px;
            text-transform: uppercase;
            padding: 12px 30px;
            border: 1px solid rgba(255, 255, 255, 0.15);
            background: transparent;
            color: rgba(255, 255, 255, 0.3);
            cursor: pointer;
            border-radius: 4px;
            transition: all 0.3s ease;
            position: absolute;
        }

        .btn-no:hover {
            transform: translate(var(--escape-x, 150px), var(--escape-y, -80px));
        }

        /* ── Celebration ── */
        .celebration {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 100;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            background: radial-gradient(ellipse at center, rgba(185, 28, 72, 0.2), var(--deep));
            opacity: 0;
            visibility: hidden;
            transition: opacity 1.5s ease, visibility 0s 1.5s;
        }

        .celebration.active {
            opacity: 1;
            visibility: visible;
            transition: opacity 1.5s ease, visibility 0s 0s;
        }

        .celebration-text {
            font-family: 'Great Vibes', cursive;
            font-size: clamp(3rem, 10vw, 6rem);
            background: linear-gradient(135deg, var(--rose-light), var(--gold-light), var(--rose));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-align: center;
            animation: celebPulse 2s ease-in-out infinite;
        }

        .celebration-sub {
            font-family: 'Cormorant Garamond', serif;
            font-size: clamp(1rem, 3vw, 1.4rem);
            font-weight: 300;
            letter-spacing: 4px;
            color: var(--blush);
            margin-top: 1.5rem;
            opacity: 0.8;
        }

        @keyframes celebPulse {

            0%,
            100% {
                transform: scale(1);
            }

            50% {
                transform: scale(1.03);
            }
        }

        /* ── Music Toggle ── */
        .music-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 200;
            width: 44px;
            height: 44px;
            border: 1px solid rgba(212, 167, 106, 0.3);
            background: rgba(26, 10, 16, 0.8);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .music-toggle:hover {
            border-color: var(--gold);
            box-shadow: 0 0 20px rgba(212, 167, 106, 0.15);
        }

        .music-toggle svg {
            width: 18px;
            height: 18px;
            fill: var(--gold);
        }

        .music-bars {
            display: flex;
            align-items: flex-end;
            gap: 2px;
            height: 16px;
        }

        .music-bars .bar {
            width: 3px;
            background: var(--gold);
            border-radius: 1px;
            transition: height 0.3s ease;
        }

        .music-bars.playing .bar:nth-child(1) {
            animation: barAnim1 0.6s ease-in-out infinite;
        }

        .music-bars.playing .bar:nth-child(2) {
            animation: barAnim2 0.5s ease-in-out infinite 0.1s;
        }

        .music-bars.playing .bar:nth-child(3) {
            animation: barAnim3 0.7s ease-in-out infinite 0.2s;
        }

        .music-bars.playing .bar:nth-child(4) {
            animation: barAnim1 0.55s ease-in-out infinite 0.15s;
        }

        .music-bars:not(.playing) .bar {
            height: 3px !important;
        }

        @keyframes barAnim1 {

            0%,
            100% {
                height: 4px;
            }

            50% {
                height: 14px;
            }
        }

        @keyframes barAnim2 {

            0%,
            100% {
                height: 6px;
            }

            50% {
                height: 12px;
            }
        }

        @keyframes barAnim3 {

            0%,
            100% {
                height: 3px;
            }

            50% {
                height: 16px;
            }
        }

        /* ── Vignette ── */
        .vignette {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(ellipse at center, transparent 50%, rgba(0, 0, 0, 0.6) 100%);
            pointer-events: none;
            z-index: 5;
        }

        /* ── Gentle Rose Petals ── */
        .petal {
            position: absolute;
            width: 12px;
            height: 12px;
            background: radial-gradient(ellipse at 30% 30%, var(--rose-light), var(--rose-dark));
            border-radius: 50% 0 50% 50%;
            opacity: 0;
            pointer-events: none;
            animation: petalFall linear forwards;
        }

        @keyframes petalFall {
            0% {
                opacity: 0;
                transform: translateY(0) rotate(0deg) translateX(0);
            }

            10% {
                opacity: 0.6;
            }

            100% {
                opacity: 0;
                transform: translateY(110vh) rotate(360deg) translateX(100px);
            }
        }

        /* ── Responsive ── */
        @media (max-width: 600px) {
            .btn {
                padding: 12px 30px;
                font-size: 0.9rem;
            }

            .btn-yes {
                padding: 14px 40px;
            }

            .proposal-buttons {
                gap: 1rem;
            }
        }
    </style>
</head>

<body>

    <!-- Background Gradient Canvas -->
    <canvas id="bg-canvas"></canvas>

    <!-- Hearts -->
    <div class="hearts-container" id="hearts-container"></div>

    <!-- Vignette -->
    <div class="vignette"></div>

    <!-- ═══════ STAGE 1 ═══════ -->
    <div class="stage active" id="stage1">
        <span class="stage-label">Chapter One</span>
        <h1 class="stage-title">The First Hello</h1>
        <div class="divider"></div>
        <p class="quote">"When we first started talking, I didn't know you'd become my favorite person."</p>
        <div class="btn-container">
            <button class="btn" id="btn-next1" onclick="goToStage(2)">Next Chapter →</button>
        </div>
    </div>

    <!-- ═══════ STAGE 2 ═══════ -->
    <div class="stage" id="stage2">
        <span class="stage-label">Chapter Two</span>
        <h1 class="stage-title">The Late Night Talks</h1>
        <div class="divider"></div>
        <p class="quote">"Somewhere between good nights and take care.. I fell for you."</p>
        <div class="btn-container">
            <button class="btn" id="btn-next2" onclick="goToStage(3)">Final Chapter →</button>
        </div>
    </div>

    <!-- ═══════ STAGE 3 ═══════ -->
    <div class="stage" id="stage3">
        <span class="stage-label">Chapter Three</span>
        <h1 class="stage-title">The Proposal</h1>
        <div class="divider"></div>
        <div class="typewriter" id="typewriter"></div>
        <h2 class="proposal" id="proposal-text">Will You Be My Valentine?</h2>
        <div class="proposal-buttons" id="proposal-buttons"
            style="position: relative; min-height: 70px; min-width: 320px; display: flex; justify-content: center; align-items: center;">
            <button class="btn-yes" id="btn-yes" onclick="sayYes()">Yes! ❤️</button>
            <button class="btn-no" id="btn-no">No</button>
        </div>
    </div>

    <!-- ═══════ CELEBRATION ═══════ -->
    <div class="celebration" id="celebration">
        <div class="celebration-text">You made me the happiest! 💕</div>
        <div class="celebration-sub">Happy Valentine's Day, my love</div>
    </div>

    <!-- Music Toggle -->
    <button class="music-toggle" id="music-toggle" onclick="toggleMusic()" title="Toggle music">
        <div class="music-bars" id="music-bars">
            <div class="bar" style="height:4px;"></div>
            <div class="bar" style="height:6px;"></div>
            <div class="bar" style="height:3px;"></div>
            <div class="bar" style="height:5px;"></div>
        </div>
    </button>

    <script>
        // ── Audio Context for Ambient Music ──
        let audioCtx, musicPlaying = false, gainNode, masterGain = 0.15;
        const oscillators = [];

        function createAmbientMusic() {
            audioCtx = new (window.AudioContext || window.webkitAudioContext)();
            gainNode = audioCtx.createGain();
            gainNode.gain.value = masterGain;
            gainNode.connect(audioCtx.destination);

            // Soft ambient chords
            const notes = [261.63, 329.63, 392.00, 523.25]; // C4, E4, G4, C5
            notes.forEach((freq, i) => {
                const osc = audioCtx.createOscillator();
                const oscGain = audioCtx.createGain();
                osc.type = 'sine';
                osc.frequency.value = freq;
                oscGain.gain.value = 0.06;
                osc.connect(oscGain);
                oscGain.connect(gainNode);
                osc.start();
                oscillators.push({ osc, gain: oscGain });

                // Gentle frequency modulation
                const lfo = audioCtx.createOscillator();
                const lfoGain = audioCtx.createGain();
                lfo.frequency.value = 0.1 + i * 0.05;
                lfoGain.gain.value = 1.5;
                lfo.connect(lfoGain);
                lfoGain.connect(osc.frequency);
                lfo.start();
            });

            // Add a soft pad layer
            const padNotes = [196.00, 246.94, 293.66]; // G3, B3, D4
            padNotes.forEach((freq, i) => {
                const osc = audioCtx.createOscillator();
                const oscGain = audioCtx.createGain();
                osc.type = 'triangle';
                osc.frequency.value = freq;
                oscGain.gain.value = 0.03;
                osc.connect(oscGain);
                oscGain.connect(gainNode);
                osc.start();
                oscillators.push({ osc, gain: oscGain });
            });

            musicPlaying = true;
            document.getElementById('music-bars').classList.add('playing');
        }

        function toggleMusic() {
            if (!audioCtx) {
                createAmbientMusic();
                return;
            }
            if (musicPlaying) {
                gainNode.gain.linearRampToValueAtTime(0, audioCtx.currentTime + 0.5);
                musicPlaying = false;
                document.getElementById('music-bars').classList.remove('playing');
            } else {
                gainNode.gain.linearRampToValueAtTime(masterGain, audioCtx.currentTime + 0.5);
                musicPlaying = true;
                document.getElementById('music-bars').classList.add('playing');
            }
        }

        function setMusicLouder(volume) {
            if (!audioCtx || !musicPlaying) return;
            masterGain = volume;
            gainNode.gain.linearRampToValueAtTime(volume, audioCtx.currentTime + 1);
        }

        // ── Heart Generation ──
        let heartRate = 2000; // ms between hearts
        let heartInterval;
        const heartContainer = document.getElementById('hearts-container');

        const heartSVGs = [
            `<svg viewBox="0 0 24 24" width="SIZE" height="SIZE" fill="COLOR"><path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>`,
        ];

        const heartColors = [
            'rgba(232, 56, 95, 0.6)',
            'rgba(255, 107, 138, 0.5)',
            'rgba(255, 214, 224, 0.4)',
            'rgba(212, 167, 106, 0.4)',
            'rgba(185, 28, 72, 0.5)',
        ];

        function spawnHeart() {
            const heart = document.createElement('div');
            heart.classList.add('floating-heart');
            const size = 12 + Math.random() * 22;
            const color = heartColors[Math.floor(Math.random() * heartColors.length)];
            heart.innerHTML = heartSVGs[0].replace('SIZE', size).replace('SIZE', size).replace('COLOR', color);
            heart.style.left = Math.random() * 100 + '%';
            heart.style.animationDuration = (8 + Math.random() * 8) + 's';
            heart.style.animationDelay = Math.random() * 2 + 's';
            heartContainer.appendChild(heart);
            setTimeout(() => heart.remove(), 18000);
        }

        function startHearts(rate) {
            if (heartInterval) clearInterval(heartInterval);
            heartRate = rate;
            heartInterval = setInterval(spawnHeart, heartRate);
        }

        startHearts(2500);

        // ── Spawn Petals ──
        function spawnPetal() {
            const petal = document.createElement('div');
            petal.classList.add('petal');
            petal.style.left = Math.random() * 100 + '%';
            petal.style.top = '-20px';
            petal.style.animationDuration = (6 + Math.random() * 6) + 's';
            petal.style.animationDelay = Math.random() * 3 + 's';
            petal.style.width = (8 + Math.random() * 8) + 'px';
            petal.style.height = petal.style.width;
            heartContainer.appendChild(petal);
            setTimeout(() => petal.remove(), 15000);
        }

        setInterval(spawnPetal, 3000);

        // ── Background Canvas ──
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        let bgHue = 330;

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        function drawBackground() {
            const grad = ctx.createRadialGradient(
                canvas.width / 2, canvas.height / 2, 0,
                canvas.width / 2, canvas.height / 2, canvas.width * 0.7
            );
            grad.addColorStop(0, `hsla(${bgHue}, 40%, 12%, 1)`);
            grad.addColorStop(0.5, `hsla(${bgHue - 10}, 35%, 8%, 1)`);
            grad.addColorStop(1, `hsla(${bgHue - 20}, 50%, 4%, 1)`);
            ctx.fillStyle = grad;
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            bgHue += 0.02;
            if (bgHue > 360) bgHue -= 360;
            requestAnimationFrame(drawBackground);
        }
        drawBackground();

        // ── Stage Transitions ──
        let currentStage = 1;

        function goToStage(stage) {
            const current = document.getElementById(`stage${currentStage}`);
            const next = document.getElementById(`stage${stage}`);
            current.classList.remove('active');

            setTimeout(() => {
                next.classList.add('active');
                currentStage = stage;

                if (stage === 2) {
                    startHearts(1800);
                    if (musicPlaying) setMusicLouder(0.2);
                }

                if (stage === 3) {
                    startHearts(800); // More hearts
                    if (musicPlaying) setMusicLouder(0.28);
                    // Start typewriter after fade-in
                    setTimeout(() => startTypewriter(), 2000);
                }
            }, 1600);
        }

        // ── Typewriter Effect ──
        const typewriterLines = [
            "And today, I don't want just memories...",
            "",
            "I want moments with you."
        ];

        function startTypewriter() {
            const el = document.getElementById('typewriter');
            let lineIndex = 0;
            let charIndex = 0;
            let html = '';

            el.innerHTML = '<span class="cursor"></span>';

            function type() {
                if (lineIndex >= typewriterLines.length) {
                    // Remove cursor, show proposal
                    setTimeout(() => {
                        el.innerHTML = html;
                        showProposal();
                    }, 600);
                    return;
                }

                const line = typewriterLines[lineIndex];

                if (line === '') {
                    html += '<br>';
                    lineIndex++;
                    charIndex = 0;
                    setTimeout(type, 400);
                    return;
                }

                if (charIndex < line.length) {
                    html += line[charIndex];
                    el.innerHTML = html + '<span class="cursor"></span>';
                    charIndex++;
                    setTimeout(type, 55 + Math.random() * 35);
                } else {
                    html += '<br>';
                    lineIndex++;
                    charIndex = 0;
                    setTimeout(type, 600);
                }
            }

            type();
        }

        function showProposal() {
            const proposalText = document.getElementById('proposal-text');
            const proposalBtns = document.getElementById('proposal-buttons');

            setTimeout(() => {
                proposalText.classList.add('visible');
            }, 500);

            setTimeout(() => {
                proposalBtns.classList.add('visible');
            }, 1500);
        }

        // ── No Button Escape ──
        const btnNo = document.getElementById('btn-no');
        let noAttempts = 0;
        const escapeMessages = [
            "Think again... 🥺",
            "Are you sure? 😢",
            "Pretty please? 🥹",
            "I won't accept no! 💕",
            "Try clicking Yes! 😘",
        ];

        btnNo.addEventListener('mouseover', () => {
            noAttempts++;
            const btnYes = document.getElementById('btn-yes');

            // Make the no button run away
            const containerRect = document.getElementById('proposal-buttons').getBoundingClientRect();
            const maxX = window.innerWidth - 100;
            const maxY = window.innerHeight - 50;

            const newX = Math.random() * maxX;
            const newY = Math.random() * maxY;

            btnNo.style.position = 'fixed';
            btnNo.style.left = newX + 'px';
            btnNo.style.top = newY + 'px';
            btnNo.style.zIndex = '500';
            btnNo.style.transition = 'all 0.3s ease';

            // Change text
            if (noAttempts <= escapeMessages.length) {
                btnNo.textContent = escapeMessages[noAttempts - 1];
            }

            // Make yes button grow
            const scale = 1 + noAttempts * 0.08;
            btnYes.style.transform = `scale(${Math.min(scale, 1.5)})`;
        });

        btnNo.addEventListener('click', () => {
            // Even clicking should trigger escape
            noAttempts++;
            const maxX = window.innerWidth - 100;
            const maxY = window.innerHeight - 50;
            btnNo.style.position = 'fixed';
            btnNo.style.left = Math.random() * maxX + 'px';
            btnNo.style.top = Math.random() * maxY + 'px';
            if (noAttempts <= escapeMessages.length) {
                btnNo.textContent = escapeMessages[noAttempts - 1];
            }
        });

        // ── Celebration ──
        function sayYes() {
            // Hide stage 3
            document.getElementById('stage3').classList.remove('active');
            btnNo.style.display = 'none';

            // Burst of hearts
            startHearts(200);
            for (let i = 0; i < 30; i++) {
                setTimeout(spawnHeart, i * 100);
            }

            // Increase music
            if (musicPlaying) setMusicLouder(0.35);

            // Confetti burst
            launchConfetti();

            // Show celebration
            setTimeout(() => {
                document.getElementById('celebration').classList.add('active');
            }, 800);
        }

        // ── Simple Confetti ──
        function launchConfetti() {
            const colors = ['#e8385f', '#ff6b8a', '#ffd6e0', '#d4a76a', '#f0d5a8', '#fff5f7', '#ff4081', '#f50057'];
            for (let i = 0; i < 100; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.style.cssText = `
            position: fixed;
            top: -10px;
            left: ${Math.random() * 100}%;
            width: ${4 + Math.random() * 8}px;
            height: ${4 + Math.random() * 8}px;
            background: ${colors[Math.floor(Math.random() * colors.length)]};
            z-index: 150;
            pointer-events: none;
            border-radius: ${Math.random() > 0.5 ? '50%' : '0'};
            animation: confettiFall ${3 + Math.random() * 4}s linear forwards;
          `;
                    document.body.appendChild(confetti);
                    setTimeout(() => confetti.remove(), 8000);
                }, i * 30);
            }
        }

        // Add confetti keyframes
        const confettiStyle = document.createElement('style');
        confettiStyle.textContent = `
      @keyframes confettiFall {
        0% { opacity: 1; transform: translateY(0) rotate(0deg) translateX(0); }
        25% { transform: translateY(25vh) rotate(180deg) translateX(${Math.random() > 0.5 ? '' : '-'}30px); }
        50% { transform: translateY(50vh) rotate(360deg) translateX(${Math.random() > 0.5 ? '-' : ''}20px); }
        100% { opacity: 0; transform: translateY(110vh) rotate(720deg) translateX(${Math.random() > 0.5 ? '' : '-'}40px); }
      }
    `;
        document.head.appendChild(confettiStyle);

        // ── Auto-start music on first interaction ──
        let musicStarted = false;
        document.addEventListener('click', () => {
            if (!musicStarted) {
                createAmbientMusic();
                musicStarted = true;
            }
        }, { once: false });

        // Only trigger once
        document.addEventListener('click', function startOnce() {
            if (!musicStarted) {
                createAmbientMusic();
                musicStarted = true;
            }
            document.removeEventListener('click', startOnce);
        });
    </script>
</body>

</html>
