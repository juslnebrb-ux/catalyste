<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Catalyst Eats - Modern Interactive Mukbang Experience</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.7.1/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: linear-gradient(-45deg, #ff6b6b, #ffd88f, #ff8c96, #ff6347);
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            color: #333;
            overflow-x: hidden;
            transition: background 0.5s, color 0.5s;
            text-align: center;
            font-size: 18px; /* Increased base font size */
        }

        body.dark {
            background: linear-gradient(-45deg, #2c3e50, #34495e, #1a1a2e, #16213e);
            color: #ecf0f1;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        header {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 20px;
            text-align: center;
            box-shadow: 0 4px 20px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 100;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header h1 {
            font-size: 3rem; /* Increased */
            font-weight: 700;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        nav {
            display: flex;
            gap: 20px;
        }

        nav a {
            color: inherit;
            text-decoration: none;
            font-weight: 600;
            padding: 10px 15px;
            border-radius: 20px;
            transition: background 0.3s, transform 0.3s;
        }

        nav a:hover {
            background: rgba(255,255,255,0.2);
            transform: translateY(-5px);
        }

        .theme-toggle {
            background: rgba(255,255,255,0.2);
            border: none;
            padding: 10px;
            border-radius: 50%;
            cursor: pointer;
            transition: background 0.3s;
        }

        .theme-toggle:hover {
            background: rgba(255,255,255,0.4);
        }

        section {
            padding: 60px 20px;
            text-align: center;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            position: relative;
        }

        .hero {
            background: rgba(255,255,255,0.1);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            margin: 0 auto;
        }

        .hero h2 {
            font-size: 2.5rem;
        }

        .hero p {
            font-size: 1.5rem; /* Increased paragraph size in hero */
        }

        .hero iframe {
            width: 100%;
            max-width: 600px;
            height: 400px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            margin-top: 20px;
            display: block;
            margin-left: auto;
            margin-right: auto;
            border: none;
        }

        .btn {
            background: linear-gradient(45deg, #ff4500, #ff6347);
            background-size: 200% 200%;
            animation: btnGlow 3s ease infinite;
            color: white;
            border: none;
            padding: 15px 30px;
            font-size: 1.2rem;
            font-weight: 600;
            border-radius: 30px;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            margin: 10px;
        }

        @keyframes btnGlow {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .btn:hover {
            transform: scale(1.05);
            box-shadow: 0 0 20px rgba(255,69,0,0.8);
        }

        .card {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.2);
            transition: transform 0.3s, box-shadow 0.3s;
            width: 100%;
            max-width: 600px;
            margin: 0 auto;
        }

        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
        }

        .card h2 {
            font-size: 2.2rem;
        }

        .card p {
            font-size: 1.4rem; /* Increased paragraph size in cards */
        }

        /* New wrapper for side-by-side sections */
        .side-by-side {
            display: flex;
            flex-direction: row;
            gap: 20px;
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            justify-content: center;
            align-items: flex-start;
        }

        .side-by-side .card {
            flex: 1;
            max-width: none;
        }

        .stream-outline ul {
            list-style-type: none;
            padding: 0;
            text-align: left;
        }

        .stream-outline li {
            font-size: 1.3rem;
            margin-bottom: 10px;
            padding: 10px;
            background: rgba(255,255,255,0.1);
            border-radius: 10px;
        }

        .poll button {
            display: block;
            width: 100%;
            margin: 10px 0;
            background: linear-gradient(45deg, #32cd32, #00ff00);
            border: none;
            padding: 12px;
            border-radius: 10px;
            cursor: pointer;
            transition: background 0.3s, transform 0.3s;
            font-size: 1.1rem;
        }

        .poll button:hover {
            background: linear-gradient(45deg, #228b22, #006400);
            transform: scale(1.05);
        }

        .poll h3 {
            font-size: 1.8rem;
        }

        .chat input {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 10px;
            margin-bottom: 10px;
            background: rgba(255,255,255,0.2);
            color: inherit;
            font-size: 1.1rem;
        }

        .chat-messages {
            max-height: 200px;
            overflow-y: auto;
            background: rgba(0,0,0,0.1);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 10px;
            font-size: 1.2rem; /* Increased chat message size */
        }

        .chat h3 {
            font-size: 1.8rem;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
            margin: 0 auto;
        }

        .social-links a {
            display: inline-flex;
            justify-content: center;
            align-items: center;
            width: 60px;
            height: 60px;
            background: rgba(255,255,255,0.1);
            border-radius: 50%;
            color: inherit;
            text-decoration: none;
            font-size: 1.5rem;
            transition: transform 0.3s, background 0.3s;
        }

        .social-links a:hover {
            transform: scale(1.2);
            background: rgba(255,69,0,0.3);
        }

        footer {
            background: rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            padding: 20px;
            text-align: center;
            box-shadow: 0 -4px 20px rgba(0,0,0,0.1);
        }

        footer p {
            font-size: 1.3rem; /* Increased footer paragraph size */
        }

        .fab {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: linear-gradient(45deg, #ff4500, #ff6347);
            color: white;
            border: none;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            cursor: pointer;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
            transition: transform 0.3s;
        }

        .fab:hover {
            transform: scale(1.1);
        }

        @media (max-width: 768px) {
            header h1 {
                font-size: 2.5rem;
            }
            .hero iframe {
                width: 100%;
                height: 300px;
            }
            nav {
                flex-direction: column;
                gap: 10px;
            }
            .social-links {
                gap: 15px;
            }
            .social-links a {
                width: 50px;
                height: 50px;
                font-size: 1.2rem;
            }
            body {
                font-size: 16px;
            }
            .hero p {
                font-size: 1.3rem; /* Adjusted for mobile */
            }
            .card p {
                font-size: 1.2rem; /* Adjusted for mobile */
            }
            footer p {
                font-size: 1.1rem; /* Adjusted for mobile */
            }
            .chat-messages {
                font-size: 1rem; /* Adjusted for mobile */
            }
            .side-by-side {
                flex-direction: column; /* Stack on mobile */
            }
            .stream-outline li {
                font-size: 1.1rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <h1>Catalyst Eats</h1>
        <nav>
            <a href="#hero">Home</a>
            <a href="#about">About</a>
            <a href="#stream-outline">Stream Outline</a>
            <a href="#interactive">Interact</a>
            <a href="#social">Social</a>
        </nav>
        <button class="theme-toggle" onclick="toggleTheme()"><i class="fa-solid fa-moon"></i></button>
    </header>

    <section id="hero" class="hero">
        <h2>Welcome to Catalyst Eats!</h2>
        <p>Experience the ultimate food transformation—while simultaneously being educated about APEC Las Piñas' relevant news. Watch, chat, and enjoy while we devour delicious meals live in our promotional platforms!</p>
        <iframe src="https://drive.google.com/file/d/1MOvzcAb3yQbv3y84sN3ZujIBl9iZWrzr/preview" allowfullscreen></iframe> <!-- Embedded Google Drive video on main page -->
        <button class="btn" onclick="playVideo()">Start the Feast</button>
    </section>

    <!-- Wrapped #about and #stream-outline in a side-by-side container -->
    <div class="side-by-side">
        <section id="about" class="card">
            <h2>About Catalyst Eats</h2>
            <p>At Catalyst Eats, we transform ordinary meals into extraordinary mukbang experiences. Join our live streams for education, entertaining segments, lively chats, and overall fun!</p>
            <img src="https://via.placeholder.com/400x200/ff6b6b/ffffff?text=Catalyst+Food" alt="Catalyst Eats Food" style="border-radius: 15px; margin-top: 20px; width: 100%;">
        </section>

        <section id="stream-outline" class="card">
            <h2>Stream Outline</h2>
            <ul>
                <li><strong>Samyang Challenge:</strong> Spicy noodle eating challenge with viewer interactions.</li>
                <li><strong>Live Music Requests:</strong> Take song requests from the chat and perform or play them.</li>
                <li><strong>Q&A Session:</strong> Answer questions about food, streams, and more.</li>
                <li><strong>Giveaways:</strong> Random viewer giveaways for subscribers.</li>
            </ul>
        </section>
    </div>

    <section id="interactive" class="card">
        <h2>Interact with Catalyst Eats!</h2>
        <div class="poll">
            <h3>What's Your Favorite Catalyst Food?</h3>
            <button onclick="vote('Samyang')">Samyang</button>
            <button onclick="vote('Chicken')">Chicken</button>
            <button onclick="vote('Burgers')">Burgers</button>
            <p id="pollResult"></p>
        </div>
        <div class="chat">
            <h3>Live Chat</h3>
            <div class="chat-messages" id="chatMessages">
                <p><strong>Host:</strong> Welcome to Catalyst Eats! <small>12:00 PM</small></p>
            </div>
            <input type="text" id="chatInput" placeholder="Type a message...">
            <button class="btn" onclick="sendMessage()">Send</button>
        </div>
    </section>

    <section id="social" class="card">
        <h2>Follow Us on Social Media</h2>
        <p>Stay updated with our latest mukbang adventures and food transformations!</p>
        <div class="social-links">
            <a href="https://www.instagram.com/catalysteats/" title="Instagram"><i class="fa-brands fa-instagram"></i></a>
            <a href="https://www.twitch.tv/catalysteats" title="Twitch"><i class="fa-brands fa-twitch"></i></a>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 Catalyst Eats. All rights reserved. <i class="fa-solid fa-utensils"></i></p>
    </footer>

    <button class="fab" onclick="scrollToTop()"><i class="fa-solid fa-arrow-up"></i></button>

    <script>
        // Theme toggle
        function toggleTheme() {
            document.body.classList.toggle('dark');
            const icon = document.querySelector('.theme-toggle i');
            icon.classList.toggle('fa-moon');
            icon.classList.toggle('fa-sun');
        }

        // Video play (now for iframe, but keeping for compatibility)
        function playVideo() {
            // Since it's an iframe, play might not work directly; user can interact with iframe
            alert('Play the video in the embedded player!');
        }

        // Poll voting
        let votes = { Pizza: 0, Sushi: 0, Burgers: 0 };
        function vote(option) {
            votes[option]++;
            document.getElementById('pollResult').innerText = `Votes: Pizza: ${votes.Pizza}, Sushi: ${votes.Sushi}, Burgers: ${votes.Burgers}`;
        }

        // Chat with timestamps
        function sendMessage() {
            const input = document.getElementById('chatInput');
            const messages = document.getElementById('chatMessages');
            if (input.value.trim()) {
                const time = new Date().toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'});
                messages.innerHTML += `<p><strong>You:</strong> ${input.value} <small>${time}</small></p>`;
                input.value = '';
                messages.scrollTop = messages.scrollHeight;
            }
        }

        // Scroll to top
        function scrollToTop() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }
    </script>
</body>
</html>
