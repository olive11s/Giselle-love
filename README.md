<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>For Giselle ✨</title>
    <style>
        :root {
            --gold: #d4af37;
            --vibrant-pink: #ff4d6d;
            --soft-bg: #fffaf0;
        }

        body, html {
            margin: 0; padding: 0; height: 100%;
            background: var(--soft-bg);
            font-family: 'Georgia', serif;
            overflow: hidden;
            touch-action: none;
        }

        /* Entrance Screen */
        #entrance {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: white;
            z-index: 200;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            transition: opacity 1.5s ease;
        }

        .unlock-heart {
            font-size: 80px;
            cursor: pointer;
            animation: pulse 1.5s infinite;
            filter: drop-shadow(0 0 15px rgba(212, 175, 55, 0.4));
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }

        /* Main Display */
        .container {
            display: none;
            opacity: 0;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            transition: opacity 2s ease;
            padding: 20px;
        }

        .card {
            background: white;
            padding: 25px;
            border-radius: 20px;
            width: 100%;
            max-width: 360px;
            text-align: center;
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
            border: 2px solid var(--gold);
        }

        /* Memory Photo */
        .photo-frame {
            background: white;
            padding: 12px 12px 45px 12px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
            transform: rotate(-2deg);
            margin-bottom: 25px;
        }

        .photo-frame img {
            width: 100%;
            border-radius: 5px;
            display: block;
        }

        .caption {
            font-family: 'Brush Script MT', cursive;
            font-size: 1.6rem;
            margin-top: 15px;
            color: #444;
        }

        .message-title {
            color: var(--vibrant-pink);
            font-size: 1.8rem;
            font-weight: bold;
            margin-bottom: 10px;
        }

        .btn-box {
            display: flex;
            justify-content: center;
            gap: 15px;
            margin-top: 20px;
            height: 55px;
        }

        .btn {
            padding: 12px 35px;
            border-radius: 50px;
            border: none;
            font-weight: bold;
            font-size: 1.1rem;
            cursor: pointer;
        }

        #yesBtn {
            background: linear-gradient(45deg, var(--vibrant-pink), #d63384);
            color: white;
            box-shadow: 0 5px 15px rgba(255, 77, 109, 0.4);
        }

        #noBtn { background: #f0f0f0; color: #aaa; position: relative; }

        #countdown {
            margin-top: 25px;
            font-size: 0.85rem;
            color: #777;
            letter-spacing: 1px;
        }

        .sparkle {
            position: fixed;
            width: 5px; height: 5px;
            background: var(--gold);
            border-radius: 50%;
            pointer-events: none;
            z-index: 1000;
        }
    </style>
</head>
<body onclick="initMagic()">

    <iframe id="music" width="0" height="0" src="https://www.youtube.com/embed/l74uPrL-M6g?enablejsapi=1" frameborder="0"></iframe>

    <div id="entrance">
        <div class="unlock-heart">❤️</div>
        <p style="color: var(--gold); font-weight: bold; letter-spacing: 2px;">FOR GISELLE</p>
    </div>

    <div class="container" id="mainDisplay">
        <div class="card">
            <div class="message-title">My Giselle</div>
            
            <div class="photo-frame">
                <img src="us.png" alt="Our Memory">
                <div class="caption">Forever & Always</div>
            </div>

            <p style="font-size: 1.1rem; color: #555;">Will you be my Valentine?</p>

            <div class="btn-box">
                <button class="btn" id="yesBtn" onclick="celebrate()">Yes! ❤️</button>
                <button class="btn" id="noBtn" onmouseover="dodge()" onclick="dodge()">No</button>
            </div>

            <div id="countdown">
                SEATTLE IN: <br>
                <span id="timer" style="color: var(--gold); font-weight: bold; font-size: 1.1rem;"></span>
            </div>
        </div>
    </div>

    <script>
        let hasStarted = false;

        function initMagic() {
            if (hasStarted) return;
            hasStarted = true;
            
            // Start Music
            document.getElementById('music').src += "&autoplay=1";

            // Reveal Content
            document.getElementById('entrance').style.opacity = '0';
            setTimeout(() => {
                document.getElementById('entrance').style.display = 'none';
                document.getElementById('mainDisplay').style.display = 'flex';
                setTimeout(() => document.getElementById('mainDisplay').style.opacity = '1', 100);
            }, 1000);
        }

        // Countdown Logic
        const target = new Date("Feb 14, 2026 00:00:00").getTime();
        setInterval(() => {
            const now = new Date().getTime();
            const diff = target - now;
            const d = Math.floor(diff / 86400000);
            const h = Math.floor((diff % 86400000) / 3600000);
            const m = Math.floor((diff % 3600000) / 60000);
            const s = Math.floor((diff % 60000) / 1000);
            document.getElementById("timer").innerHTML = `${d}d ${h}h ${m}m ${s}s`;
        }, 1000);

        function dodge() {
            const btn = document.getElementById('noBtn');
            btn.style.position = 'fixed';
            btn.style.left = Math.random() * (window.innerWidth - 100) + 'px';
            btn.style.top = Math.random() * (window.innerHeight - 50) + 'px';
        }

        function celebrate() {
            const card = document.querySelector('.card');
            card.style.transform = "scale(0.5)";
            card.style.opacity = "0";
            
            setTimeout(() => {
                card.innerHTML = `
                    <h1 style="color: var(--vibrant-pink); font-size: 2.5rem;">YAY! 🥰</h1>
                    <p style="font-size: 1.2rem; line-height: 1.6;">
                        You've made me the luckiest man in the world, Giselle.<br>
                        Our Seattle trip is going to be unforgettable!
                    </p>
                    <div style="font-size: 50px; margin: 20px;">🌹✈️🏙️✨</div>
                    <p style="color: var(--gold); font-weight: bold;">I LOVE YOU!</p>
                `;
                card.style.transform = "scale(1)";
                card.style.opacity = "1";
                setInterval(spawnHeart, 200);
            }, 500);
        }

        function spawnHeart() {
            const h = document.createElement('div');
            h.innerHTML = '❤️';
            h.style.position = 'fixed';
            h.style.left = Math.random() * 100 + 'vw';
            h.style.bottom = '-50px';
            h.style.fontSize = (Math.random() * 20 + 20) + 'px';
            h.style.color = '#ff4d6d';
            h.style.transition = 'all 4s linear';
            document.body.appendChild(h);
            setTimeout(() => {
                h.style.transform = `translateY(-110vh) rotate(${Math.random() * 360}deg)`;
                h.style.opacity = '0';
            }, 50);
            setTimeout(() => h.remove(), 4000);
        }

        // Gold Sparkle Trail
        document.addEventListener('touchmove', (e) => {
            const s = document.createElement('div');
            s.className = 'sparkle';
            s.style.left = e.touches[0].pageX + 'px';
            s.style.top = e.touches[0].pageY + 'px';
            document.body.appendChild(s);
            setTimeout(() => {
                s.style.transform = 'scale(2) translateY(20px)';
                s.style.opacity = '0';
            }, 100);
            setTimeout(() => s.remove(), 1000);
        });
    </script>
</body>
</html>
