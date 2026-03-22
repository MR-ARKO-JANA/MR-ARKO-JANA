<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ARKO JANA | System Architect</title>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600&family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #0D1117;
            --surface-color: rgba(22, 27, 34, 0.6);
            --primary-color: #7AA2F7;
            --secondary-color: #BB9AF7;
            --text-main: #C0CAF5;
            --text-muted: #565F89;
            --border-color: rgba(122, 162, 247, 0.15);
            --glow-color: rgba(122, 162, 247, 0.4);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: var(--bg-color);
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(122, 162, 247, 0.08) 0%, transparent 40%),
                radial-gradient(circle at 90% 80%, rgba(187, 154, 247, 0.08) 0%, transparent 40%);
            color: var(--text-main);
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            min-height: 100vh;
            overflow-x: hidden;
            background-attachment: fixed;
        }

        ::selection {
            background: var(--primary-color);
            color: #000;
        }

        .container {
            max-width: 1050px;
            margin: 0 auto;
            padding: 2rem;
            opacity: 0;
            animation: fadeIn 1.2s ease-out forwards;
        }

        @keyframes fadeIn {
            to { opacity: 1; }
        }

        /* ----- GLASSMORPHISM PANELS ----- */
        .glass-panel {
            background: var(--surface-color);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 2.5rem;
            margin-bottom: 2rem;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.4);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }

        .glass-panel::before {
            content: '';
            position: absolute;
            top: 0; left: -100%;
            width: 50%; height: 100%;
            background: linear-gradient(to right, transparent, rgba(255,255,255,0.03), transparent);
            transform: skewX(-20deg);
            transition: 0.7s;
        }

        .glass-panel:hover::before {
            left: 150%;
        }

        .glass-panel:hover {
            transform: translateY(-8px);
            box-shadow: 0 15px 50px rgba(122, 162, 247, 0.15);
            border-color: rgba(122, 162, 247, 0.3);
        }

        /* ----- TYPOGRAPHY ----- */
        h1, h2, h3 {
            color: #fff;
            font-weight: 800;
        }

        .section-title {
            display: flex;
            align-items: center;
            gap: 12px;
            font-size: 1.6rem;
            margin-bottom: 2rem;
            color: #fff;
            position: relative;
        }
        
        .section-title span {
            color: var(--primary-color);
            font-family: 'Fira Code', monospace;
        }

        .section-title::after {
            content: '';
            flex: 1;
            height: 1px;
            background: linear-gradient(90deg, var(--border-color) 0%, transparent 100%);
            margin-left: 15px;
        }

        .code-text {
            font-family: 'Fira Code', monospace;
        }

        /* ----- HEADER ----- */
        header {
            text-align: center;
            margin-bottom: 3rem;
        }

        .header-banner {
            width: 100%;
            border-radius: 24px;
            box-shadow: 0 0 30px rgba(0,0,0,0.5);
            margin-bottom: -30px;
            position: relative;
            z-index: 1;
        }

        .profile-badges {
            position: relative;
            z-index: 2;
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 12px;
            margin-bottom: 2rem;
            padding: 0 1rem;
        }

        .profile-badges img {
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            transition: transform 0.3s ease, filter 0.3s ease;
        }

        .profile-badges img:hover {
            transform: translateY(-5px) scale(1.05);
            filter: brightness(1.1);
        }

        .title-typing {
            margin: 2rem 0;
            display: flex;
            justify-content: center;
        }

        .header-title {
            font-size: 2.5rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            background: linear-gradient(to right, #7AA2F7, #BB9AF7);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 0.5rem;
        }

        .header-subtitle {
            font-size: 1.1rem;
            color: var(--text-muted);
            letter-spacing: 1px;
        }

        .social-links {
            margin-top: 1.5rem;
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .social-links img {
            transition: all 0.3s ease;
            border-radius: 6px;
        }

        .social-links img:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px var(--glow-color);
        }

        /* ----- GRID LAYOUTS ----- */
        .about-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2.5rem;
            align-items: center;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        .stats-grid img {
            width: 100%;
            height: 100%;
            object-fit: contain;
            border-radius: 12px;
            background: #0D1117; /* matches tokyonight */
            border: 1px solid var(--border-color);
            transition: border-color 0.3s ease;
        }
        
        .stats-grid img:hover, .single-stat img:hover {
            border-color: var(--primary-color);
        }

        .single-stat {
            text-align: center;
            margin-bottom: 2rem;
        }
        
        .single-stat img {
            border-radius: 12px;
            border: 1px solid var(--border-color);
            transition: border-color 0.3s ease;
            max-width: 100%;
        }

        /* ----- TERMINAL WINDOW ----- */
        .terminal {
            background: #16161E; /* tokyonight bg */
            border-radius: 12px;
            padding: 1.5rem;
            font-family: 'Fira Code', monospace;
            font-size: 0.95rem;
            border: 1px solid #292E42;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.5), 0 10px 30px rgba(0,0,0,0.3);
            position: relative;
        }

        .terminal-header {
            display: flex;
            gap: 8px;
            margin-bottom: 1.2rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid #292E42;
        }

        .dot {
            width: 14px;
            height: 14px;
            border-radius: 50%;
        }
        .dot.red { background: #f7768e; }
        .dot.yellow { background: #e0af68; }
        .dot.green { background: #9ece6a; }

        .term-line {
            line-height: 1.8;
        }
        .term-prompt { color: #9ece6a; font-weight: 600; }
        .term-command { color: #7dcfff; }
        .term-info { color: #7AA2F7; font-weight: 600; }
        .term-highlight { color: #e0af68; text-decoration: underline; text-decoration-color: rgba(224, 175, 104, 0.4); text-underline-offset: 4px; }
        .term-log { color: #bb9af7; font-weight: 600; }

        /* ----- PROJECTS TABLE ----- */
        .projects-wrapper {
            overflow-x: auto;
        }
        .projects-table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0;
            text-align: left;
        }

        .projects-table th {
            padding: 1rem;
            color: var(--text-muted);
            text-transform: uppercase;
            font-size: 0.85rem;
            letter-spacing: 1px;
            border-bottom: 2px solid var(--border-color);
        }

        .projects-table td {
            padding: 1.2rem 1rem;
            border-bottom: 1px solid rgba(122, 162, 247, 0.05);
            vertical-align: middle;
        }

        .projects-table tr:hover td {
            background: rgba(122, 162, 247, 0.03);
        }

        .projects-table tr:last-child td {
            border-bottom: none;
        }

        .project-link {
            color: #fff;
            text-decoration: none;
            font-weight: 600;
            font-size: 1.1rem;
            transition: color 0.3s;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .project-link:hover {
            color: var(--primary-color);
        }

        .tech-pill {
            display: inline-block;
            padding: 4px 10px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 6px;
            font-size: 0.8rem;
            font-family: 'Fira Code', monospace;
            margin-right: 6px;
            color: var(--text-main);
            transition: all 0.2s;
        }
        
        .projects-table tr:hover .tech-pill {
            border-color: rgba(122, 162, 247, 0.3);
            color: var(--primary-color);
        }

        .status-badge {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
        }
        
        .status-badge.live {
            background: rgba(158, 206, 106, 0.1);
            color: #9ece6a;
            border: 1px solid rgba(158, 206, 106, 0.2);
        }
        
        .status-badge.dev {
            background: rgba(224, 175, 104, 0.1);
            color: #e0af68;
            border: 1px solid rgba(224, 175, 104, 0.2);
        }
        
        .status-dot {
            width: 8px; height: 8px;
            border-radius: 50%;
        }
        .status-dot.live { background: #9ece6a; box-shadow: 0 0 10px #9ece6a; }
        .status-dot.dev { background: #e0af68; box-shadow: 0 0 10px #e0af68; }

        /* ----- FOOTER ----- */
        footer {
            text-align: center;
            padding: 3rem 0;
            color: var(--text-muted);
            font-family: 'Fira Code', monospace;
            font-size: 0.9rem;
        }
        
        .footer-counters {
            margin-top: 1.5rem;
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            gap: 1rem;
        }

        /* ----- RESPONSIVE ----- */
        @media (max-width: 850px) {
            .about-grid { grid-template-columns: 1fr; }
            .stats-grid { grid-template-columns: 1fr; }
            .header-title { font-size: 2rem; }
        }
        
        @media (max-width: 600px) {
            .glass-panel { padding: 1.5rem; }
            header img.header-banner { border-radius: 12px; }
            .profile-badges img { height: 24px; }
        }
    </style>
</head>
<body>

    <div class="container">
        
        <!-- HEADER SECTION -->
        <header>
            <img class="header-banner" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=280&section=header&text=ARKO%20JANA&fontSize=80&animation=fadeIn&fontAlignY=35&desc=The%20Full-Stack%20Architect&descSize=25&descAlignY=55" alt="Arko Jana Banner" />
            
            <div class="profile-badges">
                <img src="https://img.shields.io/badge/DEVELOPER-FULL--STACK-FF0055?style=for-the-badge&logo=codepen&logoColor=white" alt="Full Stack" />
                <img src="https://img.shields.io/badge/ENGINEER-AI%20%26%20ML-00DFEE?style=for-the-badge&logo=pytorch&logoColor=white" alt="AI & ML" />
                <img src="https://img.shields.io/badge/OPEN%20SOURCE-CONTRIBUTOR-FFB800?style=for-the-badge&logo=github&logoColor=white" alt="Open Source" />
            </div>

            <div class="title-typing">
                <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=24&pause=1000&color=7AA2F7&center=true&vCenter=true&width=435&lines=SYSTEM+DIAGNOSTIC+INIT...;Specializing+in+Scalable+Web;Mastering+Next.js+15+&+NestJS;Turning+Bugs+into+Solutions" alt="Typing SVG" />
            </div>

            <h1 class="header-title">⚡ System Architect ⚡</h1>
            <p class="header-subtitle">Full-Stack Engineer | AI Enthusiast | Performance Optimizer</p>

            <div class="social-links">
                <a href="https://linkedin.com/in/arko-jana-326941295" target="_blank">
                    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
                </a>
                <a href="mailto:arkojana45@gmail.com">
                    <img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
                </a>
                <a href="https://github.com/MR-ARKO-JANA" target="_blank">
                    <img src="https://img.shields.io/badge/Portfolio-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="GitHub" />
                </a>
            </div>
        </header>

        <!-- ABOUT ME SECTION -->
        <section class="glass-panel">
            <h2 class="section-title"><span>01.</span> System Diagnostic (About Me)</h2>
            
            <div class="about-grid">
                <div class="terminal">
                    <div class="terminal-header">
                        <div class="dot red"></div>
                        <div class="dot yellow"></div>
                        <div class="dot green"></div>
                    </div>
                    <div class="term-line">
                        <span class="term-prompt">User@ArkoJana:~$</span> <span class="term-command">init personal_data.sys</span>
                    </div>
                    <div class="term-line">
                        <span class="term-info">[STATUS]</span> Optimizing workflow...
                    </div>
                    <div class="term-line">
                        <span class="term-info">[INFO]</span> Specializing in <span class="term-highlight">Scalable Web Architectures</span>.
                    </div>
                    <div class="term-line">
                        <span class="term-info">[INFO]</span> Currently mastering <span class="term-highlight">Next.js 15</span> and <span class="term-highlight">NestJS Microservices</span>.
                    </div>
                    <div class="term-line">
                        <span class="term-log">[LOG]</span> I turn complex "critical" bugs into coffee-fueled solutions.
                    </div>
                    
                    <div style="margin-top: 20px; display: flex; gap: 8px;">
                        <a href="https://linkedin.com/in/arkojana"><img src="https://img.shields.io/badge/-LinkedIn-0077B5?style=flat-square&logo=Linkedin&logoColor=white"/></a>
                        <a href="mailto:arkojana45@gmail.com"><img src="https://img.shields.io/badge/-Gmail-D14836?style=flat-square&logo=Gmail&logoColor=white"/></a>
                        <a href="https://instagram.com/mr_arko_j99"><img src="https://img.shields.io/badge/-Instagram-E4405F?style=flat-square&logo=Instagram&logoColor=white"/></a>
                    </div>
                </div>

                <div class="language-stats" style="display: flex; justify-content: center; align-items: center;">
                    <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=MR-ARKO-JANA&layout=compact&theme=tokyonight&hide_border=true&bg_color=0D1117" alt="Top Languages" style="width: 100%; max-width: 400px; border-radius: 12px; box-shadow: 0 10px 25px rgba(0,0,0,0.3);" />
                </div>
            </div>
        </section>

        <!-- TECH STACK SECTION -->
        <section class="glass-panel">
            <h2 class="section-title"><span>02.</span> Operating Capabilities (Tech Stack)</h2>
            <div style="text-align: center; padding: 1rem 0;">
                <img src="https://skillicons.dev/icons?i=nextjs,react,tailwind,nestjs,nodejs,mongodb,postgres,py,pytorch,cpp,linux,docker,aws,git&theme=dark" alt="Tech Stack Icons" style="max-width: 100%; transition: transform 0.3s;" onmouseover="this.style.transform='scale(1.02)'" onmouseout="this.style.transform='scale(1)'" />
            </div>
        </section>

        <!-- METRICS SECTION -->
        <section class="glass-panel">
            <h2 class="section-title"><span>03.</span> Real-Time System Metrics</h2>
            <div class="stats-grid">
                <img src="https://github-readme-stats.vercel.app/api?username=MR-ARKO-JANA&show_icons=true&theme=tokyonight&count_private=true&hide_border=true&bg_color=0D1117" alt="GitHub Stats" />
                <img src="https://github-readme-streak-stats.herokuapp.com/?user=MR-ARKO-JANA&theme=tokyonight&hide_border=true&background=0D1117" alt="GitHub Streak" />
            </div>
        </section>

        <!-- DEPLOYMENTS SECTION -->
        <section class="glass-panel">
            <h2 class="section-title"><span>04.</span> Recent Deployments</h2>
            <div class="projects-wrapper">
                <table class="projects-table">
                    <thead>
                        <tr>
                            <th>Project Module</th>
                            <th>Primary Stack Elements</th>
                            <th>System Status</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>
                                <a href="https://github.com/MR-ARKO-JANA" class="project-link" target="_blank">
                                    NyayaSahayak ↗
                                </a>
                            </td>
                            <td>
                                <span class="tech-pill">React</span>
                                <span class="tech-pill">AI</span>
                                <span class="tech-pill">Node.js</span>
                            </td>
                            <td>
                                <div class="status-badge live">
                                    <div class="status-dot live"></div> Live / Stable
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td>
                                <a href="https://github.com/MR-ARKO-JANA" class="project-link" target="_blank">
                                    Driver Wellness IoT ↗
                                </a>
                            </td>
                            <td>
                                <span class="tech-pill">Python</span>
                                <span class="tech-pill">IoT</span>
                                <span class="tech-pill">AI</span>
                            </td>
                            <td>
                                <div class="status-badge dev">
                                    <div class="status-dot dev"></div> In Development
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td>
                                <a href="https://github.com/MR-ARKO-JANA/3d-web" class="project-link" target="_blank">
                                    3D-Web Particle System ↗
                                </a>
                            </td>
                            <td>
                                <span class="tech-pill">Three.js</span>
                                <span class="tech-pill">MediaPipe</span>
                            </td>
                            <td>
                                <div class="status-badge live">
                                    <div class="status-dot live"></div> Production Ready
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <!-- INTELLIGENCE SECTION -->
        <section class="glass-panel single-stat">
            <h2 class="section-title"><span>05.</span> Intelligence & Contributions</h2>
            <img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=MR-ARKO-JANA&theme=tokyonight" alt="Summary Cards" style="width: 100%;" />
        </section>

        <!-- TROPHIES SECTION -->
        <section class="glass-panel single-stat">
            <h2 class="section-title"><span>06.</span> Technical Milestones</h2>
            <img src="https://github-profile-trophy.vercel.app/?username=MR-ARKO-JANA&theme=tokyonight&no-frame=true&row=1&column=6" alt="Trophies" style="max-width: 100%;" />
        </section>

        <!-- FOOTER -->
        <footer>
            <div style="margin-bottom: 2rem;">
                <img src="https://raw.githubusercontent.com/mayhemantt/mayhemantt/Update/assets/neon_line.png" alt="Neon Line" style="width: 100%; max-width: 600px; opacity: 0.5;">
            </div>
            
            <img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight" alt="Quotes" style="max-width: 100%; margin-bottom: 1.5rem;" />
            <br />
            
            <div class="footer-counters">
                <code>v2.1.0 | Last System Sync: 2026-03-23</code>
                <img src="https://visitcount.itsvg.in/api?id=MR-ARKO-JANA&label=ACCESS_LOG&color=7AA2F7&icon=5&pretty=true" alt="Visit Count" />
            </div>
        </footer>

    </div>

</body>
</html>
