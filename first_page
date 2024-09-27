<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mental Wellness Activity Tracker</title>
    <style>
        body, html {
            margin: 0;
            padding: 0;
            overflow-x: hidden;
            font-family: 'Helvetica Neue', sans-serif;
            background-color: #f0f8ff;
            scroll-behavior: smooth;
        }

        .background-tracker {
            position: relative;
            width: 100%;
            height: 100vh;
            background: linear-gradient(135deg, #e0f7fa 0%, #b2ebf2 100%);
            overflow: hidden;
        }

        .floating-bubble {
            position: absolute;
            width: 80px;
            height: 80px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: rgba(255, 255, 255, 0.8);
            cursor: pointer;
            background: radial-gradient(circle at 30% 30%, 
                rgba(255, 255, 255, 0.9) 0%, 
                rgba(173, 216, 230, 0.8) 30%, 
                rgba(0, 191, 255, 0.6) 70%,
                rgba(65, 105, 225, 0.4) 100%
            );
            box-shadow: 
                inset 0 0 20px rgba(255, 255, 255, 0.5),
                inset 0 0 100px rgba(173, 216, 230, 0.2),
                0 0 15px rgba(173, 216, 230, 0.5);
            overflow: hidden;
            z-index: 10;
        }

        .floating-bubble::before,
        .floating-bubble::after {
            content: '';
            position: absolute;
            border-radius: 50%;
            filter: blur(2px);
        }

        .floating-bubble::before {
            top: 5%;
            left: 10%;
            width: 35%;
            height: 35%;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.8) 0%, rgba(255, 255, 255, 0) 100%);
        }

        .floating-bubble::after {
            bottom: 15%;
            right: 20%;
            width: 25%;
            height: 25%;
            background: radial-gradient(circle, rgba(255, 255, 255, 0.6) 0%, rgba(255, 255, 255, 0) 100%);
        }

        @keyframes pop {
            0% { transform: scale(1); opacity: 1; }
            50% { transform: scale(1.2); opacity: 0.5; }
            100% { transform: scale(1.5); opacity: 0; }
        }

        .pop {
            animation: pop 0.5s forwards;
            pointer-events: none;
        }

        .logo-container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 5;
        }

        .logo {
            width: 350px;
            height: 350px;
            object-fit: contain;
        }

        .quote-container {
            position: absolute;
            bottom: 100px;
            left: 50%;
            transform: translateX(-50%);
            text-align: center;
            color: #2c2471;
            font-size: 1.2em;
            z-index: 5;
            padding: 10px;
            background: #ffffff00; /* Fully transparent */
            font-family: 'Avenir Next LT Pro', sans-serif;
        }

        .button-container {
            position: absolute;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 10px;
            z-index: 100;
        }

        .link-button, #playButton, #aboutButton {
            padding: 10px 20px;
            background-color: #00796b;
            color: white;
            text-decoration: none;
            border: none;
            border-radius: 5px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transition: background-color 0.3s, transform 0.3s;
            cursor: pointer;
            font-size: 16px;
        }

        .link-button:hover, #playButton:hover, #aboutButton:hover {
            background-color: #004d40;
            transform: scale(1.05);
        }

        /* About Us Section Styles */
        #aboutUsSection {
            padding: 50px 20px;
            background-color: #e0f7fa;
            text-align: center;
        }

        #aboutUsSection h2 {
            font-size: 2.5em;
            color: #00796b;
            margin-bottom: 20px;
        }

        #aboutUsSection p {
            font-size: 1.2em;
            color: #333;
            max-width: 800px;
            margin: 0 auto;
        }

        #aboutUsSection a {
            display: inline-block;
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #00796b;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transition: background-color 0.3s;
        }

        #aboutUsSection a:hover {
            background-color: #004d40;
        }

    </style>
</head>
<body>
    <audio id="backgroundAudio" loop>
        <source src="bubbles.mp3" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>

    <div class="background-tracker" id="bubbleContainer">
        <div class="logo-container">
            <img src="logo.png" alt="Mental Wellness Tracker Logo" class="logo">
        </div>
        <div class="quote-container" id="quoteDisplay"></div>

        <div class="button-container">
            <a href="second_page.html" class="link-button">Explore Wellness Activities</a>
            <button id="playButton">Play Music</button>
            <button id="aboutButton" onclick="document.getElementById('aboutUsSection').scrollIntoView()">About Us</button>
        </div>
    </div>

    <!-- About Us Section -->
    <section id="aboutUsSection">
        <h2>About Us</h2>
        <p>Welcome to the Mental Wellness Activity Tracker! Our mission is to help you cultivate mental well-being by tracking daily activities, journaling, and participating in mental health challenges. Through insights and personalized recommendations, we support your journey towards a balanced and fulfilling life.</p>
        <a href="#bubbleContainer">Back to Top</a>
    </section>

    <script>
        const quotes = [
            "Your mental health is a priority.",
            "Your happiness is an inside job.",
            "It's okay to not be okay.",
            "Healing takes time, and asking for help is a courageous step.",
            "What you think, you become. What you feel, you attract. What you imagine, you create.",
            "Self-care is not a luxury; it's a necessity.",
            "Take a deep breath. It's just a bad day, not a bad life.",
            "You don't have to control your thoughts. You just have to stop letting them control you.",
            "Progress, not perfection.",
            "The best time for new beginnings is now.",
            "You are stronger than you think.",
            "Sometimes, the most productive thing you can do is rest.",
            "Believe you can, and you're halfway there.",
            "Do something today that your future self will thank you for."
        ];

        function displayQuote() {
            const quoteDisplay = document.getElementById('quoteDisplay');
            const randomIndex = Math.floor(Math.random() * quotes.length);
            quoteDisplay.textContent = quotes[randomIndex];
        }

        function createBubble() {
            const bubble = document.createElement('div');
            bubble.className = 'floating-bubble';
            bubble.style.left = Math.random() * 100 + '%';
            bubble.style.top = Math.random() * 100 + '%';
            bubble.onclick = () => popBubble(bubble);

            const angle = Math.random() * 360;
            const speed = 2 + Math.random() * 2.5;
            bubble.dataset.angle = angle;
            bubble.dataset.speed = speed;

            return bubble;
        }

        function moveBubble(bubble) {
            const rect = bubble.getBoundingClientRect();
            let angle = parseFloat(bubble.dataset.angle);
            const speed = parseFloat(bubble.dataset.speed);

            let x = rect.left + Math.cos(angle * Math.PI / 180) * speed;
            let y = rect.top + Math.sin(angle * Math.PI / 180) * speed;

            if (x < 0 || x > window.innerWidth - rect.width) {
                angle = 180 - angle;
            }
            if (y < 0 || y > window.innerHeight - rect.height) {
                angle = 360 - angle;
            }

            bubble.style.left = x + 'px';
            bubble.style.top = y + 'px';
            bubble.dataset.angle = angle;
        }

        function popBubble(bubble) {
            bubble.classList.add('pop');
            bubble.addEventListener('animationend', () => {
                bubble.remove();
                createBubble(); // Create a new bubble on pop
                container.appendChild(createBubble()); // Append new bubble
            });
        }

        const container = document.getElementById('bubbleContainer');
        for (let i = 0; i < 20; i++) {
            const bubble = createBubble();
            container.appendChild(bubble);
        }

        function animateBubbles() {
            const bubbles = document.querySelectorAll('.floating-bubble');
            bubbles.forEach(moveBubble);
            requestAnimationFrame(animateBubbles);
        }

        displayQuote(); // Display a quote on load
        setInterval(displayQuote, 5000); // Change quote every 5 seconds
        animateBubbles(); // Start bubble animation

        const audio = document.getElementById('backgroundAudio');
        const playButton = document.getElementById('playButton');

        playButton.addEventListener('click', () => {
            if (audio.paused) {
                audio.play();
                playButton.textContent = 'Pause Music';
            } else {
                audio.pause();
                playButton.textContent = 'Play Music';
            }
        });
    </script>
</body>
</html>
