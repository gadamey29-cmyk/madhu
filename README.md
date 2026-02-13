<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💝 For Vibha – From Miles Away</title>
    <meta name="description" content="A special Valentine's message for Vibha">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,600;0,700;1,400;1,600&family=Lora:ital,wght@0,400;0,500;0,600;1,400;1,500&family=Dancing+Script:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- Falling Hearts Background -->
    <div class="hearts-container" id="heartsContainer"></div>

    <!-- Floating Particles -->
    <div class="particles" id="particles"></div>

    <!-- Audio -->
    <audio id="bgMusic" loop>
        <source src="https://cdn.pixabay.com/audio/2024/11/04/audio_4956b4ece1.mp3" type="audio/mpeg">
    </audio>

    <!-- ============ INTRO SECTION ============ -->
    <section class="page active" id="intro">
        <div class="content-wrapper">
            <div class="emoji-header">💝</div>
            <h1 class="main-title typewriter" id="introTitle"></h1>
            <div class="intro-text fade-group">
                <div class="quote fade-in" data-delay="2500">
                    <p>"They say distance makes love harder...</p>
                    <p>But for us, it made it <em>stronger</em>."</p>
                </div>
                <div class="quote fade-in" data-delay="4500">
                    <p>"2.3 years...</p>
                    <p>Different places...</p>
                    <p>Same heartbeat."</p>
                </div>
                <div class="quote fade-in" data-delay="6500">
                    <p>"And her name is <span class="highlight-name">Vibha</span> ❤️"</p>
                </div>
            </div>
            <button class="btn-romantic fade-in" data-delay="8500" onclick="goToPage('chapter1')">
                <span>Continue</span>
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </button>
        </div>
    </section>

    <!-- ============ CHAPTER 1 ============ -->
    <section class="page" id="chapter1">
        <div class="content-wrapper">
            <div class="chapter-badge">📖 Chapter 1</div>
            <h2 class="chapter-title">The Distance</h2>
            <div class="divider"></div>
            <div class="chapter-body fade-group">
                <div class="quote fade-in" data-delay="500">
                    <p>"We don't meet every day.</p>
                    <p>We don't hold hands on every bad day.</p>
                </div>
                <div class="quote fade-in" data-delay="1500">
                    <p>But we stay.</p>
                    <p>We call.</p>
                    <p>We wait.</p>
                </div>
                <div class="quote fade-in" data-delay="2500">
                    <p>We choose each other... again and again."</p>
                </div>
            </div>
            <button class="btn-romantic fade-in" data-delay="3500" onclick="goToPage('chapter2')">
                <span>Next</span>
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </button>
        </div>
    </section>

    <!-- ============ CHAPTER 2 ============ -->
    <section class="page" id="chapter2">
        <div class="content-wrapper">
            <div class="chapter-badge">💌 Chapter 2</div>
            <h2 class="chapter-title">Love Letter</h2>
            <div class="chapter-subtitle">(Deep Version)</div>
            <div class="divider"></div>
            <div class="chapter-body fade-group">
                <div class="quote fade-in" data-delay="500">
                    <p>"Vibha,</p>
                    <p>Loving you from a distance has taught me something powerful...</p>
                </div>
                <div class="quote fade-in" data-delay="1800">
                    <p>Love is not about physical presence.</p>
                    <p>It's about emotional connection.</p>
                </div>
                <div class="quote fade-in" data-delay="3000">
                    <p>Even when you are miles away,</p>
                    <p>you are my first thought in the morning</p>
                    <p>and my last thought at night.</p>
                </div>
                <div class="quote fade-in" data-delay="4200">
                    <p>Sometimes I miss you so much it hurts...</p>
                    <p>but even that pain feels worth it</p>
                    <p>because it means <em>you matter</em>."</p>
                </div>
            </div>
            <button class="btn-romantic fade-in" data-delay="5500" onclick="goToPage('chapter3')">
                <span>One More Thing...</span>
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </button>
        </div>
    </section>

    <!-- ============ CHAPTER 3 ============ -->
    <section class="page" id="chapter3">
        <div class="content-wrapper">
            <div class="chapter-badge">💫 Chapter 3</div>
            <h2 class="chapter-title">Our Strength</h2>
            <div class="divider"></div>
            <div class="chapter-body fade-group">
                <div class="quote fade-in" data-delay="500">
                    <p>"2.3 years of waiting.</p>
                    <p>2.3 years of late night calls.</p>
                    <p>2.3 years of trusting each other.</p>
                </div>
                <div class="quote fade-in" data-delay="2000">
                    <p>Not everyone survives long distance.</p>
                    <p>But we did.</p>
                    <p>Because what we have... is <em>real</em>."</p>
                </div>
            </div>
            <button class="btn-romantic fade-in" data-delay="3500" onclick="goToPage('proposal')">
                <span>The Big Question...</span>
                <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
            </button>
        </div>
    </section>

    <!-- ============ PROPOSAL ============ -->
    <section class="page darker" id="proposal">
        <div class="content-wrapper">
            <div class="emoji-header ring-spin">💍</div>
            <h2 class="chapter-title proposal-title">Final Proposal</h2>
            <div class="divider gold"></div>
            <div class="chapter-body fade-group">
                <div class="quote fade-in" data-delay="500">
                    <p>"Distance may keep our hands apart...</p>
                    <p>but nothing can separate our hearts."</p>
                </div>
                <div class="quote proposal-question fade-in" data-delay="2500">
                    <p>"So Vibha...</p>
                    <p>Even if we are miles away right now...</p>
                    <p class="big-question">Will you be my Valentine?</p>
                    <p>Today... tomorrow... and until</p>
                    <p>distance becomes just a memory?"</p>
                </div>
            </div>
            <div class="proposal-buttons fade-in" data-delay="5000">
                <button class="btn-yes" onclick="handleYes()">
                    <span>💖 Yes</span>
                </button>
                <button class="btn-no" id="btnNo">
                    <span>😢 No</span>
                </button>
            </div>
        </div>
    </section>

    <!-- ============ AFTER YES ============ -->
    <section class="page celebration" id="afterYes">
        <div class="content-wrapper">
            <div class="emoji-header celebration-emoji">💝</div>
            <h2 class="chapter-title celebration-title">She Said Yes!</h2>
            <div class="divider gold"></div>
            <div class="chapter-body fade-group">
                <div class="quote fade-in" data-delay="500">
                    <p>"One day...</p>
                    <p>There will be no goodbyes after calls.</p>
                    <p>No countdown for next meeting.</p>
                </div>
                <div class="quote fade-in" data-delay="2500">
                    <p>Just us.</p>
                    <p>Together.</p>
                    <p>Finally.</p>
                </div>
                <div class="quote fade-in" data-delay="4000">
                    <p>Until that day comes,</p>
                    <p>I'll keep loving you...</p>
                    <p>from miles away. 💕"</p>
                </div>
                <div class="final-message fade-in" data-delay="5500">
                    <p class="forever-text">Happy Valentine's Day, Vibha ❤️</p>
                    <p class="sub-text">— Yours, from miles away, but never far from your heart.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Music Toggle -->
    <button class="music-toggle" id="musicToggle" onclick="toggleMusic()">
        <span id="musicIcon">🔇</span>
    </button>

    <script src="script.js"></script>
</body>
</html>
