/* ============================================
   Valentine's Proposal – For Vibha
   Interactive Script
   ============================================ */

// ============ STATE ============
let musicPlaying = false;
let currentPage = 'intro';
const heartEmojis = ['❤️', '💕', '💖', '💗', '💝', '💘', '🩷', '♥️'];

// ============ INITIALIZATION ============
document.addEventListener('DOMContentLoaded', () => {
    startIntro();
    createFloatingHearts();
    createParticles();
    setupNoButton();
    tryAutoplayMusic();
});

// ============ INTRO TYPEWRITER ============
function startIntro() {
    const title = document.getElementById('introTitle');
    const text = 'For Vibha – From Miles Away';
    let i = 0;

    function type() {
        if (i < text.length) {
            title.textContent += text.charAt(i);
            i++;
            setTimeout(type, 70);
        } else {
            title.classList.add('done');
            triggerFadeGroup('intro');
        }
    }

    setTimeout(type, 800);
}

// ============ FADE-IN ANIMATIONS ============
function triggerFadeGroup(pageId) {
    const page = document.getElementById(pageId);
    const fadeElements = page.querySelectorAll('.fade-in');

    fadeElements.forEach(el => {
        const delay = parseInt(el.getAttribute('data-delay')) || 0;
        setTimeout(() => {
            el.classList.add('visible');
        }, delay);
    });
}

// ============ PAGE NAVIGATION ============
function goToPage(targetId) {
    const currentEl = document.getElementById(currentPage);
    const targetEl = document.getElementById(targetId);

    // Fade out current
    currentEl.classList.remove('active');

    // After transition, show target
    setTimeout(() => {
        targetEl.classList.add('active');
        currentPage = targetId;

        // Trigger fade-in animations for new page
        setTimeout(() => triggerFadeGroup(targetId), 200);

        // Special handling for proposal page - increase hearts
        if (targetId === 'proposal') {
            intensifyHearts();
        }
    }, 600);
}

// ============ FLOATING HEARTS ============
function createFloatingHearts() {
    const container = document.getElementById('heartsContainer');

    function spawnHeart() {
        const heart = document.createElement('div');
        heart.classList.add('heart');
        heart.textContent = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];

        // Random properties
        const size = Math.random() * 20 + 14;
        const left = Math.random() * 100;
        const duration = Math.random() * 6 + 6;
        const delay = Math.random() * 2;
        const swayAmount = (Math.random() - 0.5) * 100;

        heart.style.cssText = `
            left: ${left}%;
            font-size: ${size}px;
            animation-duration: ${duration}s;
            animation-delay: ${delay}s;
        `;

        // Add sway with CSS custom animation
        heart.animate([
            { transform: 'translateY(0) translateX(0) rotate(0deg)', opacity: 0 },
            { transform: `translateY(15vh) translateX(${swayAmount * 0.3}px) rotate(45deg)`, opacity: 0.7 },
            { transform: `translateY(50vh) translateX(${swayAmount}px) rotate(180deg)`, opacity: 0.4 },
            { transform: `translateY(110vh) translateX(${swayAmount * 0.5}px) rotate(360deg)`, opacity: 0 }
        ], {
            duration: duration * 1000,
            delay: delay * 1000,
            easing: 'ease-in',
            fill: 'forwards'
        });

        container.appendChild(heart);

        // Remove after animation
        setTimeout(() => {
            if (heart.parentNode) heart.remove();
        }, (duration + delay) * 1000 + 500);
    }

    // Spawn hearts continuously
    setInterval(spawnHeart, 800);

    // Initial burst
    for (let i = 0; i < 8; i++) {
        setTimeout(spawnHeart, i * 200);
    }
}

function intensifyHearts() {
    const container = document.getElementById('heartsContainer');

    // Burst of hearts for proposal
    for (let i = 0; i < 20; i++) {
        setTimeout(() => {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.textContent = heartEmojis[Math.floor(Math.random() * heartEmojis.length)];

            const size = Math.random() * 25 + 16;
            const left = Math.random() * 100;
            const duration = Math.random() * 4 + 4;

            heart.style.cssText = `
                left: ${left}%;
                font-size: ${size}px;
            `;

            heart.animate([
                { transform: 'translateY(0) rotate(0deg)', opacity: 0 },
                { transform: 'translateY(15vh) rotate(90deg)', opacity: 0.8 },
                { transform: 'translateY(110vh) rotate(360deg)', opacity: 0 }
            ], {
                duration: duration * 1000,
                easing: 'ease-in',
                fill: 'forwards'
            });

            container.appendChild(heart);
            setTimeout(() => { if (heart.parentNode) heart.remove(); }, duration * 1000 + 500);
        }, i * 150);
    }
}

// ============ PARTICLES ============
function createParticles() {
    const container = document.getElementById('particles');

    for (let i = 0; i < 30; i++) {
        const particle = document.createElement('div');
        particle.classList.add('particle');

        const x = Math.random() * 100;
        const y = Math.random() * 100;
        const size = Math.random() * 3 + 1;
        const delay = Math.random() * 8;
        const duration = Math.random() * 6 + 6;

        particle.style.cssText = `
            left: ${x}%;
            top: ${y}%;
            width: ${size}px;
            height: ${size}px;
            animation-delay: ${delay}s;
            animation-duration: ${duration}s;
        `;

        container.appendChild(particle);
    }
}

// ============ PROPOSAL LOGIC ============
function handleYes() {
    // Celebration burst
    launchConfetti();
    intensifyHearts();

    // Navigate to celebration page
    goToPage('afterYes');

    // Extra confetti waves
    setTimeout(launchConfetti, 1000);
    setTimeout(launchConfetti, 2500);
}

function setupNoButton() {
    const btnNo = document.getElementById('btnNo');
    let noAttempts = 0;

    const noMessages = [
        "Are you sure? 🥺",
        "Think again... 💭",
        "Pretty please? 🙏",
        "I'll wait forever... ⏳",
        "My heart says you'll say yes 💓"
    ];

    btnNo.addEventListener('mouseover', () => {
        noAttempts++;

        if (noAttempts <= 3) {
            // Run away from cursor
            const maxX = window.innerWidth - btnNo.offsetWidth - 40;
            const maxY = window.innerHeight - btnNo.offsetHeight - 40;
            const newX = Math.random() * maxX;
            const newY = Math.random() * maxY;

            btnNo.style.position = 'fixed';
            btnNo.style.left = newX + 'px';
            btnNo.style.top = newY + 'px';
            btnNo.style.zIndex = '200';
            btnNo.style.transition = 'all 0.3s ease';
        } else {
            // After 3 attempts, shrink and change text
            const msgIndex = Math.min(noAttempts - 4, noMessages.length - 1);
            btnNo.querySelector('span').textContent = noMessages[msgIndex];
            btnNo.style.transform = `scale(${Math.max(0.3, 1 - (noAttempts - 3) * 0.15)})`;
            btnNo.style.opacity = `${Math.max(0.2, 1 - (noAttempts - 3) * 0.15)}`;
        }
    });

    // Also handle touch for mobile
    btnNo.addEventListener('touchstart', (e) => {
        e.preventDefault();
        noAttempts++;

        if (noAttempts <= 5) {
            const maxX = window.innerWidth - 120;
            const maxY = window.innerHeight - 60;
            const newX = Math.random() * maxX;
            const newY = Math.random() * maxY;

            btnNo.style.position = 'fixed';
            btnNo.style.left = newX + 'px';
            btnNo.style.top = newY + 'px';
            btnNo.style.zIndex = '200';
        } else {
            // Eventually just make it say yes
            btnNo.querySelector('span').textContent = '💖 Yes!';
            btnNo.onclick = handleYes;
            btnNo.style.background = 'linear-gradient(135deg, #e8456b, #ff6b8a)';
            btnNo.style.color = 'white';
            btnNo.style.transform = 'scale(1)';
            btnNo.style.opacity = '1';
        }
    });
}

// ============ CONFETTI ============
function launchConfetti() {
    const colors = ['#ff6b8a', '#d4a853', '#ff8fa3', '#f0c96e', '#e8456b', '#ffd700', '#ff69b4', '#ff1493'];

    for (let i = 0; i < 60; i++) {
        setTimeout(() => {
            const confetti = document.createElement('div');
            confetti.classList.add('confetti');

            const color = colors[Math.floor(Math.random() * colors.length)];
            const left = Math.random() * 100;
            const size = Math.random() * 8 + 5;
            const duration = Math.random() * 3 + 2;
            const shape = Math.random() > 0.5 ? '50%' : '2px';

            confetti.style.cssText = `
                left: ${left}%;
                width: ${size}px;
                height: ${size}px;
                background: ${color};
                border-radius: ${shape};
                animation-duration: ${duration}s;
            `;

            // Add swaying animation
            const swayX = (Math.random() - 0.5) * 200;
            confetti.animate([
                { transform: `translateY(0) translateX(0) rotate(0deg)`, opacity: 1 },
                { transform: `translateY(50vh) translateX(${swayX}px) rotate(360deg)`, opacity: 0.8 },
                { transform: `translateY(100vh) translateX(${swayX * 1.5}px) rotate(720deg)`, opacity: 0 }
            ], {
                duration: duration * 1000,
                easing: 'cubic-bezier(0.25, 0.46, 0.45, 0.94)',
                fill: 'forwards'
            });

            document.body.appendChild(confetti);

            setTimeout(() => {
                if (confetti.parentNode) confetti.remove();
            }, duration * 1000 + 500);
        }, i * 40);
    }
}

// ============ MUSIC ============
function tryAutoplayMusic() {
    const music = document.getElementById('bgMusic');
    music.volume = 0.3;

    // Try to autoplay (will likely be blocked by browser)
    const playPromise = music.play();
    if (playPromise !== undefined) {
        playPromise.then(() => {
            musicPlaying = true;
            updateMusicButton();
        }).catch(() => {
            // Autoplay blocked - wait for user interaction
            document.addEventListener('click', () => {
                if (!musicPlaying) {
                    music.play().then(() => {
                        musicPlaying = true;
                        updateMusicButton();
                    }).catch(() => {});
                }
            }, { once: true });
        });
    }
}

function toggleMusic() {
    const music = document.getElementById('bgMusic');

    if (musicPlaying) {
        music.pause();
        musicPlaying = false;
    } else {
        music.play().then(() => {
            musicPlaying = true;
        }).catch(() => {});
    }

    updateMusicButton();
}

function updateMusicButton() {
    const btn = document.getElementById('musicToggle');
    const icon = document.getElementById('musicIcon');

    if (musicPlaying) {
        icon.textContent = '🔊';
        btn.classList.add('playing');
    } else {
        icon.textContent = '🔇';
        btn.classList.remove('playing');
    }
}
