<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>A Surprise for You</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: #fff0f3;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
        }

        .container { text-align: center; z-index: 10; }

        @keyframes pulse {
            0% { transform: scale(1); box-shadow: 0 10px 20px rgba(255, 77, 109, 0.3); }
            50% { transform: scale(1.1); box-shadow: 0 15px 30px rgba(255, 77, 109, 0.5); }
            100% { transform: scale(1); box-shadow: 0 10px 20px rgba(255, 77, 109, 0.3); }
        }

        .btn-open {
            background: #ff4d6d;
            color: white;
            padding: 20px 40px;
            border-radius: 50px;
            font-size: 1.2rem;
            border: none;
            cursor: pointer;
            animation: pulse 2s infinite;
            transition: 0.3s;
        }

        .card {
            background: white;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(255, 77, 109, 0.2);
            display: none;
            animation: fadeIn 1.5s ease;
            max-width: 380px;
            width: 90%;
        }

        .couple-photo {
            width: 100%;
            max-height: 400px; 
            object-fit: cover;
            object-position: center 20%; /* Adjusted to focus on your face */
            border-radius: 15px;
            margin-bottom: 15px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .counter {
            background: #fff0f3;
            padding: 10px;
            border-radius: 10px;
            margin: 15px 0;
            font-weight: bold;
            color: #ff4d6d;
            font-size: 0.9rem;
        }

        h1 { color: #ff4d6d; margin: 10px 0; font-size: 1.4rem; }
        p { color: #594d5b; line-height: 1.5; font-size: 0.95rem; margin: 10px 0; }
        
        .signature {
            margin-top: 15px;
            font-family: 'cursive', 'Brush Script MT', sans-serif;
            font-size: 1.3rem;
            color: #ff4d6d;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .heart {
            position: absolute;
            bottom: -100px;
            color: #ffb3c1;
            font-size: 20px;
            animation: float 4s linear infinite;
            z-index: 1;
        }

        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <audio id="bgMusic" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
        <source src="https://raw.githubusercontent.com/robsonpoojary/be-my-baby/main/be-my-baby.mp3" type="audio/mpeg">
    </audio>

    <div class="container">
        <button class="btn-open" id="openBtn">Tap to open your surprise! 💌</button>
        
        <div class="card" id="loveCard">
            <img src="IMG_1429.jpeg" alt="A Surprise for You" class="couple-photo">
            
            <h1>Hi Gorgeous! ❤️</h1>
            
            <div class="counter" id="dayCounter">Loading our time together...</div>

            <p>I wanted to make something special just for you. You mean the world to me, and I'm so lucky to have you by my side.</p>
            
            <div class="signature">Forever yours, <br> [Your Name]</div>
        </div>
    </div>

    <script>
        // Set your anniversary date here: (Year, Month-1, Day)
        const startDate = new Date(2023, 0, 15); 

        const btn = document.getElementById('openBtn');
        const card = document.getElementById('loveCard');
        const music = document.getElementById('bgMusic');

        btn.addEventListener('click', () => {
            btn.style.display = 'none';
            card.style.display = 'block';
            
            // Play "Be My Baby"
            music.play().catch(e => console.log("Music play was prevented by browser settings."));
            
            calculateDays();
            startHearts();
        });

        function calculateDays() {
            const now = new Date();
            const diffTime = Math.abs(now - startDate);
            const diffDays = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
            document.getElementById('dayCounter').innerHTML = `Together for ${diffDays} Days`;
        }

        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = Math.random() * 2 + 3 + 's';
            document.body.appendChild(heart);
            setTimeout(() => { heart.remove(); }, 4000);
        }

        function startHearts() {
            setInterval(createHeart, 200);
        }
    </script>
</body>
</html>
