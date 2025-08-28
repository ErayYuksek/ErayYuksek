<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Eray Yüksek - Backend Architect</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
            color: #ffffff;
            overflow-x: hidden;
            min-height: 100vh;
        }

        .matrix-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.1;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 1;
        }

        .header {
            text-align: center;
            margin-bottom: 60px;
            position: relative;
        }

        .avatar {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            background: linear-gradient(45deg, #00d4ff, #ff0080);
            margin: 0 auto 30px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 48px;
            font-weight: bold;
            animation: pulse 2s infinite;
            position: relative;
            overflow: hidden;
        }

        .avatar::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: conic-gradient(transparent, rgba(255, 255, 255, 0.3), transparent);
            animation: rotate 3s linear infinite;
        }

        .avatar span {
            position: relative;
            z-index: 2;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes rotate {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .title {
            font-size: 3.5em;
            font-weight: 900;
            background: linear-gradient(45deg, #00d4ff, #ff0080, #00ff88);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: gradient 3s ease infinite;
            margin-bottom: 20px;
            text-shadow: 0 0 30px rgba(0, 212, 255, 0.5);
        }

        .subtitle {
            font-size: 1.4em;
            color: #8892b0;
            margin-bottom: 30px;
            position: relative;
        }

        .typing-animation {
            border-right: 2px solid #00d4ff;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            50% { border-color: transparent; }
        }

        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin: 60px 0;
        }

        .stat-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(0, 212, 255, 0.3);
            border-radius: 20px;
            padding: 30px;
            text-align: center;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .stat-card:hover {
            transform: translateY(-10px);
            border-color: #00d4ff;
            box-shadow: 0 20px 40px rgba(0, 212, 255, 0.2);
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(0, 212, 255, 0.1), transparent);
            transition: left 0.5s;
        }

        .stat-card:hover::before {
            left: 100%;
        }

        .stat-icon {
            font-size: 3em;
            margin-bottom: 20px;
            color: #00d4ff;
        }

        .stat-number {
            font-size: 2.5em;
            font-weight: bold;
            color: #00ff88;
            margin-bottom: 10px;
            counter-reset: number;
            animation: countUp 2s ease-out;
        }

        .stat-label {
            color: #8892b0;
            font-size: 1.1em;
        }

        .tech-stack {
            margin: 60px 0;
        }

        .section-title {
            font-size: 2.5em;
            font-weight: bold;
            text-align: center;
            margin-bottom: 40px;
            color: #00d4ff;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(45deg, #00d4ff, #ff0080);
            border-radius: 2px;
        }

        .tech-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
        }

        .tech-item {
            background: rgba(255, 255, 255, 0.03);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            padding: 25px 20px;
            text-align: center;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .tech-item:hover {
            background: rgba(0, 212, 255, 0.1);
            border-color: #00d4ff;
            transform: scale(1.05);
        }

        .tech-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: linear-gradient(90deg, #00d4ff, #ff0080);
            transform: scaleX(0);
            transition: transform 0.3s ease;
        }

        .tech-item:hover::before {
            transform: scaleX(1);
        }

        .projects {
            margin: 60px 0;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(0, 212, 255, 0.2);
            border-radius: 20px;
            padding: 40px;
            margin: 30px 0;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .project-card:hover {
            transform: translateX(10px);
            border-color: #00d4ff;
            box-shadow: -10px 0 30px rgba(0, 212, 255, 0.2);
        }

        .project-status {
            position: absolute;
            top: 20px;
            right: 20px;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.8em;
            font-weight: bold;
            text-transform: uppercase;
        }

        .status-active {
            background: rgba(0, 255, 136, 0.2);
            color: #00ff88;
            border: 1px solid #00ff88;
        }

        .status-research {
            background: rgba(255, 200, 0, 0.2);
            color: #ffc800;
            border: 1px solid #ffc800;
        }

        .project-title {
            font-size: 1.8em;
            font-weight: bold;
            color: #00d4ff;
            margin-bottom: 15px;
        }

        .connect-section {
            text-align: center;
            margin: 80px 0 40px;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin: 40px 0;
        }

        .social-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 60px;
            height: 60px;
            background: rgba(255, 255, 255, 0.05);
            border: 2px solid rgba(0, 212, 255, 0.3);
            border-radius: 15px;
            color: #00d4ff;
            text-decoration: none;
            font-size: 1.5em;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .social-link:hover {
            transform: translateY(-5px);
            background: rgba(0, 212, 255, 0.2);
            border-color: #00d4ff;
            box-shadow: 0 10px 25px rgba(0, 212, 255, 0.3);
        }

        .footer {
            text-align: center;
            margin-top: 60px;
            padding: 40px 0;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }

        .quote {
            font-size: 1.3em;
            font-style: italic;
            color: #8892b0;
            margin-bottom: 20px;
            position: relative;
        }

        .quote::before, .quote::after {
            content: '"';
            color: #00d4ff;
            font-size: 2em;
            font-weight: bold;
        }

        .terminal-window {
            background: #0d1117;
            border: 1px solid #30363d;
            border-radius: 10px;
            margin: 40px 0;
            overflow: hidden;
        }

        .terminal-header {
            background: #21262d;
            padding: 15px 20px;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .terminal-button {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }

        .btn-close { background: #ff5f56; }
        .btn-minimize { background: #ffbd2e; }
        .btn-maximize { background: #27ca3f; }

        .terminal-content {
            padding: 20px;
            font-family: 'Courier New', monospace;
            line-height: 1.6;
        }

        .terminal-line {
            margin: 10px 0;
            opacity: 0;
            animation: fadeInUp 0.5s ease forwards;
        }

        .terminal-line:nth-child(1) { animation-delay: 0.5s; }
        .terminal-line:nth-child(2) { animation-delay: 1s; }
        .terminal-line:nth-child(3) { animation-delay: 1.5s; }
        .terminal-line:nth-child(4) { animation-delay: 2s; }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .prompt {
            color: #00d4ff;
        }

        .command {
            color: #00ff88;
        }

        .output {
            color: #8892b0;
            margin-left: 20px;
        }

        @media (max-width: 768px) {
            .title {
                font-size: 2.5em;
            }
            
            .stats-grid {
                grid-template-columns: 1fr;
            }
            
            .social-links {
                flex-wrap: wrap;
            }
        }

        .floating-icons {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
        }

        .floating-icon {
            position: absolute;
            color: rgba(0, 212, 255, 0.1);
            animation: float 20s infinite linear;
        }

        .floating-icon:nth-child(1) { left: 10%; animation-delay: 0s; }
        .floating-icon:nth-child(2) { left: 20%; animation-delay: 2s; }
        .floating-icon:nth-child(3) { left: 30%; animation-delay: 4s; }
        .floating-icon:nth-child(4) { left: 40%; animation-delay: 6s; }
        .floating-icon:nth-child(5) { left: 50%; animation-delay: 8s; }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <canvas class="matrix-bg"></canvas>
    
    <div class="floating-icons">
        <div class="floating-icon" style="font-size: 2em;">⚡</div>
        <div class="floating-icon" style="font-size: 1.5em;">🚀</div>
        <div class="floating-icon" style="font-size: 2.5em;">💻</div>
        <div class="floating-icon" style="font-size: 1.8em;">⭐</div>
        <div class="floating-icon" style="font-size: 2.2em;">🔥</div>
    </div>

    <div class="container">
        <header class="header">
            <div class="avatar">
                <span>EY</span>
            </div>
            <h1 class="title">Eray Yüksek</h1>
            <p class="subtitle">
                <span class="typing-animation">Senior Backend Architect • .NET Specialist • Cloud Engineer</span>
            </p>
        </header>

        <div class="terminal-window">
            <div class="terminal-header">
                <div class="terminal-button btn-close"></div>
                <div class="terminal-button btn-minimize"></div>
                <div class="terminal-button btn-maximize"></div>
                <span style="margin-left: 10px; color: #8892b0;">eray@localhost:~$</span>
            </div>
            <div class="terminal-content">
                <div class="terminal-line">
                    <span class="prompt">eray@backend-master:</span><span class="command">$ whoami</span>
                </div>
                <div class="terminal-line">
                    <span class="output">Senior Backend Developer | Architecture Specialist | Performance Optimizer</span>
                </div>
                <div class="terminal-line">
                    <span class="prompt">eray@backend-master:</span><span class="command">$ cat skills.txt</span>
                </div>
                <div class="terminal-line">
                    <span class="output">Building scalable solutions with .NET Core • Microservices • Real-time systems</span>
                </div>
            </div>
        </div>

        <div class="stats-grid">
            <div class="stat-card">
                <div class="stat-icon">⚡</div>
                <div class="stat-number">5+</div>
                <div class="stat-label">Years of Excellence</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🚀</div>
                <div class="stat-number">50+</div>
                <div class="stat-label">Projects Delivered</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">⭐</div>
                <div class="stat-number">99.9%</div>
                <div class="stat-label">Uptime Achieved</div>
            </div>
            <div class="stat-card">
                <div class="stat-icon">🔥</div>
                <div class="stat-number">24/7</div>
                <div class="stat-label">Problem Solver</div>
            </div>
        </div>

        <section class="tech-stack">
            <h2 class="section-title">⚙️ Technology Arsenal</h2>
            <div class="tech-grid">
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">🔵</div>
                    <div>.NET Core</div>
                </div>
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">⚡</div>
                    <div>C#</div>
                </div>
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">🌐</div>
                    <div>ASP.NET</div>
                </div>
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">🗄️</div>
                    <div>Entity Framework</div>
                </div>
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">🔄</div>
                    <div>SignalR</div>
                </div>
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">🐘</div>
                    <div>PostgreSQL</div>
                </div>
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">⚡</div>
                    <div>Redis</div>
                </div>
                <div class="tech-item">
                    <div style="font-size: 2em; margin-bottom: 10px;">☁️</div>
                    <div>AWS</div>
                </div>
            </div>
        </section>

        <section class="projects">
            <h2 class="section-title">🚀 Active Projects</h2>
            
            <div class="project-card">
                <div class="project-status status-active">Live</div>
                <div class="project-title">Real-time Communication Hub</div>
                <p style="color: #8892b0; line-height: 1.6;">
                    Advanced SignalR-based chat platform with file sharing, real-time notifications, and scalable architecture. 
                    Supporting 10K+ concurrent users with sub-second latency.
                </p>
            </div>

            <div class="project-card">
                <div class="project-status status-active">Production</div>
                <div class="project-title">Microservices Architecture Platform</div>
                <p style="color: #8892b0; line-height: 1.6;">
                    Enterprise-grade microservices ecosystem with API Gateway, service discovery, and distributed caching. 
                    Handling 1M+ requests daily with 99.9% uptime.
                </p>
            </div>

            <div class="project-card">
                <div class="project-status status-research">R&D</div>
                <div class="project-title">AI-Powered Performance Optimizer</div>
                <p style="color: #8892b0; line-height: 1.6;">
                    Machine learning-driven database optimization tool that automatically identifies bottlenecks 
                    and suggests performance improvements. Currently in beta testing.
                </p>
            </div>
        </section>

        <section class="connect-section">
            <h2 class="section-title">🤝 Let's Build Something Amazing</h2>
            <p style="color: #8892b0; font-size: 1.2em; margin-bottom: 30px;">
                Ready to tackle complex challenges and create innovative solutions
            </p>
            
            <div class="social-links">
                <a href="https://www.linkedin.com/in/eray-y-6a671a322/" class="social-link" title="LinkedIn">
                    💼
                </a>
                <a href="https://github.com/ErayYuksek" class="social-link" title="GitHub">
                    🐱
                </a>
                <a href="mailto:eray@example.com" class="social-link" title="Email">
                    📧
                </a>
                <a href="#" class="social-link" title="Portfolio">
                    🌐
                </a>
            </div>
        </section>

        <footer class="footer">
            <div class="quote">
                Code is poetry written in logic, architecture is the symphony that makes it sing
            </div>
            <p style="color: #8892b0;">
                🇹🇷 Based in Turkey • Open to remote opportunities worldwide • Available for consulting
            </p>
        </footer>
    </div>

    <script>
        // Matrix rain effect
        const canvas = document.querySelector('.matrix-bg');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const matrix = "ABCDEFGHIJKLMNOPQRSTUVWXYZ123456789@#$%^&*()*&^%+-/~{[|`]}";
        const matrixArray = matrix.split("");

        const fontSize = 10;
        const columns = canvas.width / fontSize;

        const drops = [];
        for(let x = 0; x < columns; x++) {
            drops[x] = 1;
        }

        function draw() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.04)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.fillStyle = '#00d4ff';
            ctx.font = fontSize + 'px monospace';

            for(let i = 0; i < drops.length; i++) {
                const text = matrixArray[Math.floor(Math.random() * matrixArray.length)];
                ctx.fillText(text, i * fontSize, drops[i] * fontSize);

                if(drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                    drops[i] = 0;
                }
                drops[i]++;
            }
        }

        setInterval(draw, 35);

        // Typing animation
        const subtitle = document.querySelector('.typing-animation');
        const text = subtitle.textContent;
        subtitle.textContent = '';

        let i = 0;
        function typeWriter() {
            if (i < text.length) {
                subtitle.textContent += text.charAt(i);
                i++;
                setTimeout(typeWriter, 100);
            }
        }

        setTimeout(typeWriter, 1000);

        // Smooth scrolling for internal links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Parallax effect for cards
        window.addEventListener('scroll', () => {
            const scrollTop = window.pageYOffset;
            const cards = document.querySelectorAll('.stat-card, .project-card');
            
            cards.forEach((card, index) => {
                const rate = scrollTop * -0.1;
                card.style.transform = `translateY(${rate}px)`;
            });
        });

        // Resize canvas on window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
