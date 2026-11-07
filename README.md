<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PixelPlay Arcade | Ultimate Indie & Browser Games</title>
    <style>
        :root {
            --bg-color: #0b0f19;
            --surface-color: #131c2e;
            --surface-hover: #1e293b;
            --accent-primary: #38bdf8;
            --accent-secondary: #818cf8;
            --accent-hover: #0ea5e9;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --border-color: #334155;
            --success-color: #22c55e;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Header & Navigation */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.2rem 6%;
            background: rgba(19, 28, 46, 0.85);
            backdrop-filter: blur(12px);
            position: sticky;
            top: 0;
            z-index: 1000;
            border-bottom: 1px solid var(--border-color);
        }

        .logo {
            font-size: 1.6rem;
            font-weight: 800;
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 2.5rem;
        }

        nav button, nav a {
            background: none;
            border: none;
            color: var(--text-muted);
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        nav button:hover, nav a:hover, nav button.active {
            color: var(--accent-primary);
        }

        /* Hero Section */
        .hero {
            text-align: center;
            padding: 7rem 2rem;
            background: linear-gradient(rgba(11, 15, 25, 0.85), rgba(11, 15, 25, 0.95)), 
                        url('https://images.unsplash.com/photo-1550745165-9bc0b252726f?auto=format&fit=crop&w=1600&q=80') no-repeat center center/cover;
            border-bottom: 1px solid var(--border-color);
        }

        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 1.2rem;
            letter-spacing: -1px;
        }

        .hero p {
            font-size: 1.25rem;
            color: var(--text-muted);
            max-width: 600px;
            margin: 0 auto 2.5rem auto;
        }

        .btn {
            display: inline-block;
            background: linear-gradient(135deg, var(--accent-primary), var(--accent-secondary));
            color: var(--bg-color);
            padding: 0.85rem 2.2rem;
            border-radius: 8px;
            font-weight: 700;
            text-decoration: none;
            border: none;
            cursor: pointer;
            box-shadow: 0 4px 14px rgba(56, 189, 248, 0.3);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(56, 189, 248, 0.5);
        }

        /* Main Container Layout */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 2rem;
        }

        .section-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        h2 {
            font-size: 2.2rem;
            position: relative;
            padding-left: 1rem;
        }

        h2::before {
            content: '';
            position: absolute;
            left: 0;
            top: 15%;
            height: 70%;
            width: 5px;
            background: var(--accent-primary);
            border-radius: 4px;
        }

        /* Tab Content Panel Handler */
        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.4s ease;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Games Grid */
        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 2rem;
        }

        .game-card {
            background-color: var(--surface-color);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid var(--border-color);
            transition: transform 0.3s ease, border-color 0.3s ease;
        }

        .game-card:hover {
            transform: translateY(-6px);
            border-color: var(--accent-primary);
        }

        .game-thumb {
            width: 100%;
            height: 180px;
            object-fit: cover;
            background-color: var(--surface-hover);
        }

        .game-info {
            padding: 1.8rem;
        }

        .game-info h3 {
            font-size: 1.35rem;
            margin-bottom: 0.6rem;
        }

        .game-info p {
            color: var(--text-muted);
            font-size: 0.95rem;
            margin-bottom: 1.5rem;
        }

        /* Built-In Mini Clicker Game Styles */
        .arcade-arena {
            background-color: var(--surface-color);
            border-radius: 12px;
            padding: 3rem 2rem;
            border: 1px solid var(--border-color);
            text-align: center;
            max-width: 800px;
            margin: 0 auto;
        }

        .clicker-box {
            background: var(--bg-color);
            padding: 3rem;
            border-radius: 12px;
            border: 1px solid var(--border-color);
            margin-top: 1.5rem;
        }

        .score-display {
            font-size: 3.5rem;
            font-weight: 800;
            color: var(--accent-primary);
            margin: 1rem 0;
        }

        .click-target-btn {
            background: linear-gradient(135deg, #f59e0b, #ef4444);
            color: white;
            font-size: 1.5rem;
            padding: 1.2rem 3rem;
            border-radius: 50px;
            border: none;
            cursor: pointer;
            font-weight: bold;
            box-shadow: 0 4px 20px rgba(245, 158, 11, 0.4);
            transition: transform 0.1s ease;
        }

        .click-target-btn:active {
            transform: scale(0.95);
        }

        /* Leaderboard Table */
        .leaderboard-table {
            width: 100%;
            border-collapse: collapse;
            background: var(--surface-color);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid var(--border-color);
        }

        .leaderboard-table th, .leaderboard-table td {
            padding: 1rem 1.5rem;
            text-align: left;
        }

        .leaderboard-table th {
            background-color: var(--surface-hover);
            color: var(--accent-primary);
            font-weight: 700;
        }

        .leaderboard-table tr:not(:last-child) td {
            border-bottom: 1px solid var(--border-color);
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 3rem 2rem;
            background-color: #070910;
            color: var(--text-muted);
            border-top: 1px solid var(--border-color);
            margin-top: 5rem;
        }
    </style>
</head>
<body>

    <!-- Header & Interactive Nav -->
    <header>
        <a href="#" class="logo">⚡ PixelPlay Arcade</a>
        <nav>
            <ul>
                <li><button class="nav-btn active" onclick="switchTab('games', event)">Games Library</button></li>
                <li><button class="nav-btn" onclick="switchTab('arcade', event)">Play Mini Game</button></li>
                <li><button class="nav-btn" onclick="switchTab('leaderboard', event)">Leaderboard</button></li>
            </ul>
        </nav>
    </header>

    <!-- Hero Area -->
    <section class="hero">
        <h1>Next-Gen Web Gaming Hub</h1>
        <p>Discover independent web titles, test your skills in real-time browser arcade challenges, and climb the global charts.</p>
        <button class="btn" onclick="switchTab('arcade', event)">Launch Arcade</button>
    </section>

    <!-- Content Area Container -->
    <div class="container">

        <!-- TAB 1: Games Library -->
        <div id="games" class="tab-content active">
            <div class="section-header">
                <h2>Featured Web Releases</h2>
            </div>
            <div class="games-grid">
                <div class="game-card">
                    <img src="https://images.unsplash.com/photo-1612287233202-b51d3ed6173c?auto=format&fit=crop&w=600&q=80" alt="Cyber Runner" class="game-thumb">
                    <div class="game-info">
                        <h3>Cyber Runner 2077</h3>
                        <p>A fast-paced neon platformer featuring rooftop chases and high-speed obstacle navigation.</p>
                        <button class="btn" style="padding: 0.5rem 1.2rem; font-size: 0.9rem;" onclick="switchTab('arcade', event)">Play Now</button>
                    </div>
                </div>

                <div class="game-card">
                    <img src="https://images.unsplash.com/photo-1534447677768-be436bb09401?auto=format&fit=crop&w=600&q=80" alt="Pixel Dungeon" class="game-thumb">
                    <div class="game-info">
                        <h3>Pixel Crypt</h3>
                        <p>Explore procedurally generated dungeon chambers, battle monsters, and collect rare artifacts.</p>
                        <button class="btn" style="padding: 0.5rem 1.2rem; font-size: 0.9rem;" onclick="switchTab('arcade', event)">Play Now</button>
                    </div>
                </div>

                <div class="game-card">
                    <img src="https://images.unsplash.com/photo-1511512578047-dfb367046420?auto=format&fit=crop&w=600&q=80" alt="Space Blaster" class="game-thumb">
                    <div class="game-info">
                        <h3>Cosmic Vanguard</h3>
                        <p>Defend the outer planetary sectors against escalating waves of hostile alien dreadnoughts.</p>
                        <button class="btn" style="padding: 0.5rem 1.2rem; font-size: 0.9rem;" onclick="switchTab('arcade', event)">Play Now</button>
                    </div>
                </div>
            </div>
        </div>

        <!-- TAB 2: Built-in Interactive Arcade Game -->
        <div id="arcade" class="tab-content">
            <div class="arcade-arena">
                <h2>⚡ Energy Clicker Challenge</h2>
                <p style="color: var(--text-muted); margin-top: 0.5rem;">Click the reactor core button as fast as you can to build power!</p>
                
                <div class="clicker-box">
                    <div style="font-size: 0.9rem; text-transform: uppercase; color: var(--text-muted);">Current Energy Score</div>
                    <div id="score" class="score-display">0</div>
                    <button class="click-target-btn" onclick="incrementScore()">⚡ GENERATE</button>
                </div>
            </div>
        </div>

        <!-- TAB 3: Leaderboard -->
        <div id="leaderboard" class="tab-content">
            <div class="section-header">
                <h2>Global High Scores</h2>
            </div>
            <table class="leaderboard-table">
                <thead>
                    <tr>
                        <th>Rank</th>
                        <th>Player Username</th>
                        <th>Game Title</th>
                        <th>Score</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>🥇 1</td>
                        <td>CyberKnight_99</td>
                        <td>Cosmic Vanguard</td>
                        <td>142,500 pts</td>
                    </tr>
                    <tr>
                        <td>🥈 2</td>
                        <td>NeonGlitch</td>
                        <td>Cyber Runner 2077</td>
                        <td>128,340 pts</td>
                    </tr>
                    <tr>
                        <td>🥉 3</td>
                        <td>PixelMaster</td>
                        <td>Pixel Crypt</td>
                        <td>95,200 pts</td>
                    </tr>
                    <tr>
                        <td>4</td>
                        <td>WebDevHero</td>
                        <td>Energy Clicker</td>
                        <td>4,120 clicks</td>
                    </tr>
                </tbody>
            </table>
        </div>

    </div>

    <!-- Footer -->
    <footer>
        <p>&copy; 2026 PixelPlay Arcade. Designed for game developers and web enthusiasts.</p>
    </footer>

    <!-- Interactive JS Script for Tabs & Game -->
    <script>
        function switchTab(tabId, event) {
            // Hide all tab content panes
            const contents = document.querySelectorAll('.tab-content');
            contents.forEach(content => content.classList.remove('active'));

            // Remove active states from navigation buttons
            const buttons = document.querySelectorAll('.nav-btn');
            buttons.forEach(btn => btn.classList.remove('active'));

            // Show selected tab & highlight clicked button
            document.getElementById(tabId).classList.add('active');
            if (event && event.currentTarget) {
                event.currentTarget.classList.add('active');
            }
        }

        // Mini Clicker Game Logic
        let currentScore = 0;
        function incrementScore() {
            currentScore++;
            document.getElementById('score').innerText = currentScore;
        }
    </script>

</body>
</html>
