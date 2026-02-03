# Giselle-love
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For Giselle ✨</title>
    <style>
        :root {
            --primary-pink: #ff85a1;
            --dark-pink: #d63384;
            --soft-bg: #fff0f3;
        }

        body {
            background: var(--soft-bg);
            margin: 0;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
            overflow-x: hidden;
            padding: 20px;
            box-sizing: border-box;
        }

        .card {
            background: white;
            padding: 25px;
            border-radius: 25px;
            box-shadow: 0 10px 30px rgba(255, 133, 161, 0.2);
            text-align: center;
            width: 100%;
            max-width: 350px;
            z-index: 10;
            transition: all 0.5s ease;
        }

        h1 { color: var(--dark-pink); font-size: 2rem; margin-top: 0; }

        .main-img {
            width: 100%;
            height: 200px;
            object-fit: cover;
            border-radius: 15px;
            margin-bottom: 15px;
        }

        .countdown-container {
            margin-top: 20px;
            padding: 10px;
            background: #fff5f7;
            border-radius: 15px;
            border: 1px dashed var(--primary-pink);
        }

        #timer { font-weight: bold; color: var(--dark-pink); font-size: 1.1rem; }

        .btn-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 25px;
            position: relative;
            height: 50px;
        }

        .btn {
            padding: 12px 25px;
            font-size: 1rem;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-weight: bold;
            touch-action: manipulation;
        }

        #yes-btn { background: var(--primary-pink); color: white; box-shadow: 0 4px 10px rgba(255, 133, 161, 0.3); }
        #no-btn { background: #eee; color: #888; position: absolute; right: 20px; }

        .heart {
            position: fixed;
            color: var(--primary-pink);
            font-size: 20px;
            pointer-events: none;
            z-index: 1;
            animation: floatUp 4s linear forwards;
        }

        @keyframes floatUp {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }

        #video-container { display: none; }
    </style>
</head>
<body onclick="playMusic()">

    <div id="video-container">
        <iframe id="player" width="1" height="1" src="https://www.youtube.com/embed/l74uPrL-M6g?enablejsapi=1" frameborder="0"></iframe>
    </div>

    <div class="card" id="card">
        <h1>Giselle ✨</h1>
        <img class="main-img" src="https://images.unsplash.com/photo-1518199266791-5375a83190b7?q=80&w=500&auto=format&fit=crop" alt="Valentine">
        <p>Will you be my Valentine? 💘</p>
        
        <div class="btn-container">
            <button class="btn" id="yes-btn" onclick="sayYes()">Yes! ❤️</button>
            <button class="btn" id="no-btn" onmouseover="dodge()" onclick="dodge()">No</button>
        </div>

        <div class="countdown-container">
            <p style="font-size: 0.8rem; margin: 0; color: #888;">Countdown to Seattle:</p>
            <div id="timer">Loading...</div>
        </div>
    </div>

    <script>
        // Music Logic
        let musicStarted = false;
        function playMusic() {
            if (!musicStarted) {
                const iframe = document.getElementById('player');
                iframe.src += "&autoplay=1";
                musicStarted = true;
            }
        }

        // Countdown Logic
        const valentineDate = new Date("Feb 14, 2026 00:00:00").getTime();
        setInterval(() => {
            const now = new Date().getTime();
            const distance = valentineDate - now;
            const days = Math.floor(distance / (1000 * 60 * 60 * 24));
            const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const mins = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
            const secs = Math.floor((distance % (1000 * 60)) / 1000);
            document.getElementById("timer").innerHTML = `${days}d ${hours}h ${mins}m ${secs}s`;
        }, 1000);

        // "No" button dodging
        function dodge() {
            const btn = document.getElementById('no-btn');
            const x = Math.random() * (window.innerWidth - btn.offsetWidth);
            const y = Math.random() * (window.innerHeight - btn.offsetHeight);
            btn.style.position = 'fixed';
            btn.style.left = x + 'px';
            btn.style.top = y + 'px';
        }

        // Celebration
        function sayYes() {
            const card = document.getElementById('card');
            card.innerHTML = `
                <h1 style="font-size: 2.5rem;">YAY! 🥰</h1>
                <p>I love you so much!</p>
                <div style="font-size: 40px; margin: 20px 0;">✈️🏙️💖</div>
                <p>See you in Seattle soon!</p>
            `;
            setInterval(createHeart, 300);
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.className = 'heart';
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.bottom = '-20px';
            heart.style.animation = `floatUp ${Math.random() * 2 + 3}s linear forwards`;
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 4000);
        }
    </script>
</body>
</html>
