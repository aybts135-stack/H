# Happiest 20th Birthday 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Birthday Surprise</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: url('background.jpg') no-repeat center center/cover;
            overflow: hidden;
            color: white;
        }

        /* Glassmorphism Card */
        .card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(15px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 40px;
            border-radius: 25px;
            text-align: center;
            box-shadow: 0 8px 32px 0 rgba(142, 68, 173, 0.37);
            max-width: 400px;
            width: 90%;
            z-index: 10;
        }

        /* Loading Animation */
        .loader {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        .hearts { font-size: 30px; animation: pulse 1.5s infinite; }
        @keyframes pulse {
            0%, 100% { transform: scale(1); opacity: 0.5; }
            50% { transform: scale(1.2); opacity: 1; }
        }

        .loading-text { font-weight: bold; letter-spacing: 1px; }

        /* Hidden Sections */
        .hidden { display: none; }

        h1 { font-size: 24px; margin-bottom: 20px; text-shadow: 2px 2px 4px rgba(0,0,0,0.5); }

        .btn-group { display: flex; justify-content: center; gap: 15px; margin-top: 20px; }

        button {
            padding: 10px 25px;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            transition: 0.3s;
            background: #9b59b6;
            color: white;
        }

        button:hover { transform: scale(1.1); background: #8e44ad; }

        .no-btn { background: rgba(255, 255, 255, 0.2); }

        .footer { margin-top: 30px; font-style: italic; font-size: 14px; opacity: 0.9; }

        /* Sparkling Background Particles */
        #particles { position: fixed; top: 0; left: 0; width: 100%; height: 100%; pointer-events: none; }
    </style>
</head>
<body>

    <canvas id="particles"></canvas>

    <div class="card" id="app">
        <div id="loading" class="loader">
            <div class="hearts">💖 💜 💖</div>
            <div class="loading-text">Loading something special...</div>
        </div>

        <div id="page1" class="hidden">
            <h1 id="q-text">siblings forever????</h1>
            <div class="btn-group">
                <button onclick="goBirthday()">Yes!</button>
                <button class="no-btn" onclick="sayPlease()">No</button>
            </div>
        </div>

        <div id="page2" class="hidden">
            <h1>happiest 20th birthday myyy darling sister💐💕</h1>
            <p>Are you enjoying this?</p>
            <div class="btn-group">
                <button onclick="goFinal()">Yes</button>
            </div>
        </div>

        <div id="page3" class="hidden">
            <h1>me toooo sis🥳</h1>
            <div class="footer">
                with immense love from Akash and Tiya💖💐💕
            </div>
        </div>
    </div>

    <script>
        // Start by showing page 1 after a short "loading" delay
        setTimeout(() => {
            document.getElementById('loading').classList.add('hidden');
            document.getElementById('page1').classList.remove('hidden');
        }, 2500);

        function sayPlease() {
            document.getElementById('q-text').innerText = "prweeeeety pls💖";
        }

        function goBirthday() {
            document.getElementById('page1').classList.add('hidden');
            document.getElementById('page2').classList.remove('hidden');
        }

        function goFinal() {
            document.getElementById('page2').classList.add('hidden');
            document.getElementById('page3').classList.remove('hidden');
        }

        // Sparkling Canvas Logic
        const canvas = document.getElementById('particles');
        const ctx = canvas.getContext('2d');
        let dots = [];

        function init() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            for(let i=0; i<100; i++) {
                dots.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 2,
                    speed: Math.random() * 0.5 + 0.2
                });
            }
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "white";
            dots.forEach(dot => {
                ctx.beginPath();
                ctx.arc(dot.x, dot.y, dot.size, 0, Math.PI * 2);
                ctx.fill();
                dot.y -= dot.speed;
                if(dot.y < 0) dot.y = canvas.height;
            });
            requestAnimationFrame(draw);
        }

        init();
        draw();
    </script>
</body>
</html>
