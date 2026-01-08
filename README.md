<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Youssef - Front-End Developer</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, rgb(13, 17, 23) 0%, rgb(20, 30, 48) 100%);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: rgb(224, 224, 224);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* Animated Background */
        .background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(-45deg, rgb(102, 126, 234), rgb(240, 147, 251), rgb(79, 172, 254), rgb(255, 165, 0));
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(13, 17, 23, 0.92);
            z-index: -1;
        }

        /* Container */
        .container {
            max-width: 1000px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        /* Header with Animated Name */
        .header {
            text-align: center;
            margin-bottom: 60px;
            animation: slideDown 0.8s ease;
        }

        @keyframes slideDown {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .profile-pic {
            width: 180px;
            height: 180px;
            margin: 0 auto 30px;
            border-radius: 50%;
            box-shadow: 0 8px 32px 0 rgba(0, 217, 255, 0.5);
            animation: float 3s ease-in-out infinite;
            border: 4px solid rgba(0, 217, 255, 0.3);
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
        }

        /* Animated Name */
        .name-wrapper {
            perspective: 1000px;
            margin: 30px 0;
        }

        .name {
            font-size: 48px;
            font-weight: 800;
            background: linear-gradient(135deg, rgb(0, 217, 255) 0%, rgb(255, 105, 180) 50%, rgb(255, 165, 0) 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: 2px;
            animation: nameGlow 3s ease-in-out infinite;
            text-shadow: 0 0 20px rgba(0, 217, 255, 0.5);
        }

        @keyframes nameGlow {
            0%, 100% {
                filter: drop-shadow(0 0 10px rgba(0, 217, 255, 0.4));
            }
            50% {
                filter: drop-shadow(0 0 25px rgba(0, 217, 255, 0.8));
            }
        }

        .subtitle {
            font-size: 20px;
            color: rgb(150, 220, 255);
            margin-top: 15px;
            animation: fadeInUp 1s ease 0.3s both;
        }

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

        /* Status Badges */
        .badges-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            margin: 30px 0;
            animation: fadeInUp 1s ease 0.5s both;
        }

        .badge {
            padding: 10px 20px;
            border-radius: 50px;
            font-size: 14px;
            font-weight: 600;
            border: 2px solid;
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .badge-1 {
            border-color: rgb(255, 107, 107);
            color: rgb(255, 107, 107);
            background: rgba(255, 107, 107, 0.1);
        }

        .badge-1:hover {
            background: rgba(255, 107, 107, 0.3);
            box-shadow: 0 0 20px rgba(255, 107, 107, 0.5);
            transform: scale(1.1);
        }

        .badge-2 {
            border-color: rgb(0, 217, 255);
            color: rgb(0, 217, 255);
            background: rgba(0, 217, 255, 0.1);
        }

        .badge-2:hover {
            background: rgba(0, 217, 255, 0.3);
            box-shadow: 0 0 20px rgba(0, 217, 255, 0.5);
            transform: scale(1.1);
        }

        .badge-3 {
            border-color: rgb(255, 217, 61);
            color: rgb(255, 217, 61);
            background: rgba(255, 217, 61, 0.1);
        }

        .badge-3:hover {
            background: rgba(255, 217, 61, 0.3);
            box-shadow: 0 0 20px rgba(255, 217, 61, 0.5);
            transform: scale(1.1);
        }

        .badge-4 {
            border-color: rgb(255, 105, 180);
            color: rgb(255, 105, 180);
            background: rgba(255, 105, 180, 0.1);
        }

        .badge-4:hover {
            background: rgba(255, 105, 180, 0.3);
            box-shadow: 0 0 20px rgba(255, 105, 180, 0.5);
            transform: scale(1.1);
        }

        /* Section Title */
        .section-title {
            font-size: 32px;
            font-weight: 700;
            text-align: center;
            margin: 50px 0 30px 0;
            color: rgb(0, 217, 255);
            position: relative;
            display: inline-block;
            width: 100%;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, transparent, rgb(0, 217, 255), transparent);
            animation: expandWidth 1.5s ease-in-out infinite;
        }

        @keyframes expandWidth {
            0%, 100% { width: 100px; }
            50% { width: 150px; }
        }

        /* Skills Grid */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
            gap: 20px;
            margin-bottom: 50px;
            animation: fadeInUp 1s ease 0.6s both;
        }

        .skill-card {
            background: rgba(102, 126, 234, 0.15);
            border: 2px solid rgba(0, 217, 255, 0.3);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s ease;
        }

        .skill-card:hover::before {
            left: 100%;
        }

        .skill-card:hover {
            transform: translateY(-15px) scale(1.05);
            border-color: rgb(0, 217, 255);
            box-shadow: 0 20px 50px rgba(0, 217, 255, 0.4);
            background: rgba(0, 217, 255, 0.2);
        }

        .skill-icon {
            font-size: 40px;
            margin-bottom: 10px;
            animation: bounce 2s ease-in-out infinite;
        }

        .skill-card:nth-child(1) .skill-icon { animation-delay: 0s; }
        .skill-card:nth-child(2) .skill-icon { animation-delay: 0.2s; }
        .skill-card:nth-child(3) .skill-icon { animation-delay: 0.4s; }
        .skill-card:nth-child(4) .skill-icon { animation-delay: 0.6s; }
        .skill-card:nth-child(5) .skill-icon { animation-delay: 0.8s; }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }

        .skill-name {
            font-weight: 700;
            font-size: 16px;
            color: rgb(0, 217, 255);
        }

        /* Stats Section */
        .stats-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 20px;
            margin-bottom: 50px;
            animation: fadeInUp 1s ease 0.7s both;
        }

        .stat-card {
            background: linear-gradient(135deg, rgb(102, 126, 234) 0%, rgb(118, 75, 162) 100%);
            padding: 30px;
            border-radius: 15px;
            text-align: center;
            box-shadow: 0 12px 40px rgba(102, 126, 234, 0.4);
            transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
            cursor: pointer;
            border: 2px solid rgba(255, 255, 255, 0.15);
            position: relative;
            overflow: hidden;
        }

        .stat-card:nth-child(2) {
            background: linear-gradient(135deg, rgb(240, 147, 251) 0%, rgb(245, 87, 108) 100%);
        }

        .stat-card:nth-child(3) {
            background: linear-gradient(135deg, rgb(79, 172, 254) 0%, rgb(0, 242, 254) 100%);
        }

        .stat-card:nth-child(4) {
            background: linear-gradient(135deg, rgb(255, 165, 0) 0%, rgb(255, 69, 0) 100%);
        }

        .stat-card:nth-child(5) {
            background: linear-gradient(135deg, rgb(156, 39, 176) 0%, rgb(233, 30, 99) 100%);
        }

        .stat-card:hover {
            transform: translateY(-15px) scale(1.08);
            box-shadow: 0 25px 60px rgba(0, 217, 255, 0.6);
        }

        .stat-number {
            font-size: 36px;
            font-weight: 800;
            color: rgb(255, 255, 255);
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.3);
        }

        .stat-label {
            font-size: 14px;
            color: rgba(255, 255, 255, 0.9);
            margin-top: 10px;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 50px;
            animation: fadeInUp 1s ease 0.8s both;
        }

        .project-card {
            background: rgba(0, 217, 255, 0.1);
            border: 2px solid rgba(0, 217, 255, 0.3);
            padding: 25px;
            border-radius: 15px;
            text-align: center;
            transition: all 0.4s ease;
            cursor: pointer;
            position: relative;
        }

        .project-card:hover {
            background: rgba(0, 217, 255, 0.2);
            border-color: rgb(0, 217, 255);
            transform: translateY(-10px);
            box-shadow: 0 20px 50px rgba(0, 217, 255, 0.4);
        }

        .project-icon {
            font-size: 36px;
            margin-bottom: 15px;
            animation: spin 3s linear infinite;
        }

        .project-card:hover .project-icon {
            animation-duration: 1s;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .project-name {
            font-weight: 700;
            color: rgb(0, 217, 255);
            font-size: 16px;
        }

        /* Social Links */
        .social-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
            margin: 50px 0;
            animation: fadeInUp 1s ease 0.9s both;
        }

        .social-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: rgba(0, 217, 255, 0.15);
            border: 2px solid rgba(0, 217, 255, 0.3);
            font-size: 28px;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            transition: all 0.3s ease;
            color: rgb(0, 217, 255);
        }

        .social-btn:hover {
            transform: translateY(-10px) scale(1.15);
            box-shadow: 0 15px 40px rgba(0, 217, 255, 0.5);
            background: rgba(0, 217, 255, 0.3);
            border-color: rgb(0, 217, 255);
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 30px;
            color: rgb(100, 150, 180);
            border-top: 1px solid rgba(0, 217, 255, 0.2);
            margin-top: 50px;
            animation: fadeInUp 1s ease 1s both;
        }

        .footer p {
            margin: 5px 0;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .name {
                font-size: 36px;
            }

            .subtitle {
                font-size: 16px;
            }

            .section-title {
                font-size: 24px;
            }

            .skills-grid {
                grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            }

            .stats-container {
                grid-template-columns: repeat(2, 1fr);
            }
        }
    </style>
</head>
<body>
    <div class="background"></div>
    <div class="overlay"></div>

    <div class="container">
        <!-- Header -->
        <div class="header">
            <img src="https://media.giphy.com/media/l0MYC0LajbaPoEADu/giphy.gif" alt="Youssef" class="profile-pic">
            
            <div class="name-wrapper">
                <h1 class="name">YOUSSEF</h1>
            </div>
            
            <p class="subtitle">💻 Front-End Developer | HTML • CSS • JavaScript</p>
            
            <div class="badges-container">
                <div class="badge badge-1">📍 Casablanca, Morocco</div>
                <div class="badge badge-2">🎯 Front-End Focus</div>
                <div class="badge badge-3">🚀 Learning & Building</div>
                <div class="badge badge-4">🎨 Web Design</div>
            </div>
        </div>

        <!-- Skills Section -->
        <h2 class="section-title">🛠️ Skills & Technologies</h2>
        <div class="skills-grid">
            <div class="skill-card">
                <div class="skill-icon">📄</div>
                <div class="skill-name">HTML5</div>
            </div>
            <div class="skill-card">
                <div class="skill-icon">🎨</div>
                <div class="skill-name">CSS3</div>
            </div>
            <div class="skill-card">
                <div class="skill-icon">⚙️</div>
                <div class="skill-name">JavaScript</div>
            </div>
            <div class="skill-card">
                <div class="skill-icon">⚛️</div>
                <div class="skill-name">React</div>
            </div>
            <div class="skill-card">
                <div class="skill-icon">🔗</div>
                <div class="skill-name">Git</div>
            </div>
        </div>

        <!-- Stats Section -->
        <h2 class="section-title">⚡ Achievements</h2>
        <div class="stats-container">
            <div class="stat-card">
                <div class="stat-number">10+</div>
                <div class="stat-label">Completed Projects</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">100%</div>
                <div class="stat-label">Learning Dedicated</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">∞</div>
                <div class="stat-label">Open for Collaboration</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">🔥</div>
                <div class="stat-label">Always Improving</div>
            </div>
            <div class="stat-card">
                <div class="stat-number">⚡</div>
                <div class="stat-label">Fast Problem Solver</div>
            </div>
        </div>

        <!-- Projects Section -->
        <h2 class="section-title">📂 Featured Projects</h2>
        <div class="projects-grid">
            <div class="project-card">
                <div class="project-icon">🌐</div>
                <div class="project-name">Portfolio Website</div>
            </div>
            <div class="project-card">
                <div class="project-icon">📱</div>
                <div class="project-name">Responsive Landing</div>
            </div>
            <div class="project-card">
                <div class="project-icon">🤖</div>
                <div class="project-name">Discord Bot</div>
            </div>
            <div class="project-card">
                <div class="project-icon">💻</div>
                <div class="project-name">Web App</div>
            </div>
        </div>

        <!-- Social Section -->
        <h2 class="section-title">📱 Connect With Me</h2>
        <div class="social-container">
            <div class="social-btn" onclick="window.open('https://github.com/sahlout12')">🐙</div>
            <div class="social-btn" onclick="window.open('https://discord.gg/ebkSt5dcyt')">💜</div>
            <div class="social-btn" onclick="window.open('mailto:your.email@example.com')">📧</div>
            <div class="social-btn">🌐</div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p>✨ Built with Love, HTML, CSS & JavaScript</p>
            <p>💫 Made by Youssef - Front-End Developer from Morocco 🇲🇦</p>
        </div>
    </div>
</body>
</html>
