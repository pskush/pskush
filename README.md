<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Prem Sagar | Developer Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        :root {
            --bg-dark: #0f0f0f;
            --text-primary: #ffffff;
            --text-secondary: #a0a0a0;
            --accent-color: #00ff87;
            --accent-glow: 0 0 20px #00ff87, 0 0 40px #00ff87;
            --bg-secondary: #1a1a1a;
            --gradient: linear-gradient(120deg, #00ff87 0%, #1a1a1a 100%);
        }

        body {
            font-family: 'Inter', sans-serif;
            background: var(--bg-dark);
            color: var(--text-primary);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* Navigation */
        .nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 5%;
            background: rgba(15, 15, 15, 0.9);
            backdrop-filter: blur(10px);
            z-index: 1000;
        }

        .nav-logo {
            font-size: 1.7rem;
            font-weight: 700;
            color: var(--accent-color);
            text-shadow: var(--accent-glow);
            letter-spacing: 2px;
            animation: logoFloat 3s infinite alternate;
        }

        .nav-links {
            display: flex;
            gap: 30px;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-secondary);
            position: relative;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: var(--accent-color);
            transition: width 0.3s ease;
        }

        .nav-links a:hover {
            color: var(--accent-color);
            text-shadow: var(--accent-glow);
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-toggle {
            display: none;
            cursor: pointer;
            flex-direction: column;
        }

        .nav-toggle-line {
            width: 25px;
            height: 3px;
            background-color: var(--text-primary);
            margin: 3px 0;
            transition: 0.4s;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            background: linear-gradient(135deg, #0f0f0f 0%, #00ff87 100%);
            background-size: 200% 200%;
            animation: gradientMove 8s ease-in-out infinite;
            position: relative;
            overflow: hidden;
        }

        @keyframes gradientMove {
            0% {background-position: 0% 50%;}
            50% {background-position: 100% 50%;}
            100% {background-position: 0% 50%;}
        }

        .hero-title {
            font-size: 4rem;
            margin-bottom: 20px;
            background: linear-gradient(to right, var(--text-primary), var(--accent-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: var(--accent-glow);
            animation: pulse 2s infinite alternate;
        }

        @keyframes pulse {
            0% {text-shadow: 0 0 10px #00ff87;}
            100% {text-shadow: 0 0 30px #00ff87;}
        }

        .hero-subtitle {
            font-size: 1.5rem;
            color: var(--text-secondary);
            margin-bottom: 30px;
            letter-spacing: 1px;
        }

        .btn {
            display: inline-block;
            padding: 14px 32px;
            background: var(--accent-color);
            color: var(--bg-dark);
            text-decoration: none;
            border-radius: 30px;
            font-weight: 600;
            font-size: 1.1rem;
            box-shadow: var(--accent-glow);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .btn:hover {
            transform: scale(1.07);
            box-shadow: 0 0 40px #00ff87, 0 0 80px #00ff87;
        }

        /* Section Styles */
        .section {
            padding: 80px 10%;
            background-color: var(--bg-dark);
        }

        .section-title {
            text-align: center;
            color: var(--accent-color);
            margin-bottom: 50px;
            font-size: 2.5rem;
            position: relative;
            text-shadow: var(--accent-glow);
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 4px;
            background: var(--accent-color);
            box-shadow: var(--accent-glow);
        }

        /* About Section */
        .about {
            display: flex;
            align-items: center;
            gap: 50px;
        }

        .profile-img {
            width: 300px;
            height: 300px;
            border-radius: 50%;
            object-fit: cover;
            border: 4px solid var(--accent-color);
            transition: transform 0.5s ease, box-shadow 0.5s;
            box-shadow: 0 10px 25px rgba(0,255,135,0.3), 0 0 40px #00ff87;
        }

        .profile-img:hover {
            transform: scale(1.07) rotate(3deg);
            box-shadow: 0 20px 40px rgba(0,255,135,0.5), 0 0 80px #00ff87;
        }

        /* Projects Section */
        .projects {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: linear-gradient(120deg, #1a1a1a 60%, #00ff87 100%);
            padding: 30px;
            border-radius: 16px;
            transition: transform 0.3s, box-shadow 0.3s;
            display: flex;
            flex-direction: column;
            box-shadow: 0 4px 24px rgba(0,255,135,0.07);
            border: 2px solid transparent;
        }

        .project-card:hover {
            transform: translateY(-10px) scale(1.03);
            box-shadow: 0 15px 40px rgba(0,255,135,0.15);
            border-color: var(--accent-color);
        }

        .project-title {
            color: var(--accent-color);
            margin-bottom: 15px;
            font-size: 1.3rem;
            font-weight: 600;
            text-shadow: var(--accent-glow);
        }

        .project-links {
            margin-top: auto;
            display: flex;
            justify-content: space-between;
        }

        .project-links a {
            color: var(--text-secondary);
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s, text-shadow 0.3s;
        }

        .project-links a:hover {
            color: var(--accent-color);
            text-shadow: var(--accent-glow);
        }

        /* Skills Section */
        .skills {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .skill-card {
            background: linear-gradient(120deg, #1a1a1a 60%, #00ff87 100%);
            padding: 20px;
            text-align: center;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: 500;
            color: var(--text-primary);
            box-shadow: 0 2px 12px rgba(0,255,135,0.08);
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .skill-card i {
            font-size: 1.5rem;
            color: var(--accent-color);
            text-shadow: var(--accent-glow);
        }

        .skill-card:hover {
            transform: scale(1.08);
            box-shadow: 0 8px 24px rgba(0,255,135,0.18);
        }

        /* Contact Section */
        .contact-form {
            max-width: 500px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px;
            background-color: var(--bg-secondary);
            border: 1px solid var(--accent-color);
            color: var(--text-primary);
            border-radius: 5px;
            font-size: 1rem;
            transition: box-shadow 0.3s, border-color 0.3s;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--accent-color);
            box-shadow: 0 0 10px #00ff87;
        }

        .submit-btn {
            display: block;
            width: 100%;
            padding: 15px;
            background: var(--accent-color);
            color: var(--bg-dark);
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-weight: 600;
            font-size: 1.1rem;
            box-shadow: var(--accent-glow);
            transition: background 0.3s, box-shadow 0.3s;
        }

        .submit-btn:hover {
            background: #00cc6e;
            box-shadow: 0 0 40px #00ff87;
        }

        .contact-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-top: 30px;
        }

        .contact-links a {
            color: var(--text-secondary);
            font-size: 2rem;
            transition: color 0.3s, transform 0.3s, text-shadow 0.3s;
        }

        .contact-links a:hover {
            color: var(--accent-color);
            transform: scale(1.2);
            text-shadow: var(--accent-glow);
        }

        /* Footer */
        footer {
            background-color: var(--bg-secondary);
            color: var(--text-secondary);
            text-align: center;
            padding: 20px;
            font-size: 1rem;
            position: relative;
        }

        .store-links {
            margin: 10px 0;
            display: flex;
            justify-content: center;
            gap: 20px;
        }

        .store-links a {
            color: var(--accent-color);
            font-size: 2rem;
            transition: color 0.3s, text-shadow 0.3s;
        }

        .store-links a:hover {
            color: #fff;
            text-shadow: var(--accent-glow);
        }

        /* Animations */
        @keyframes logoFloat {
            0% { transform: translateY(-5px); }
            100% { transform: translateY(5px); }
        }

        @media (max-width: 768px) {
            .nav {
                flex-direction: column;
                align-items: center;
            }

            .nav-links {
                margin-top: 20px;
                flex-direction: column;
                align-items: center;
            }

            .hero-title {
                font-size: 2.5rem;
            }

            .about {
                flex-direction: column;
                text-align: center;
            }
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="nav">
        <div class="nav-logo">Prem Sagar</div>
        <div class="nav-toggle" onclick="toggleNav()">
            <div class="nav-toggle-line"></div>
            <div class="nav-toggle-line"></div>
            <div class="nav-toggle-line"></div>
        </div>
        <div class="nav-links">
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#projects">Projects</a>
            <a href="#skills">Skills</a>
            <a href="#contact">Contact</a>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <h1 class="hero-title">Prem Sagar</h1>
        <p class="hero-subtitle">Web Developer | Designer | Tech Innovator</p>
        <a href="#contact" class="btn">Get In Touch</a>
    </section>

    <!-- About Section -->
    <section id="about" class="section about">
        <img src="/api/placeholder/300/300" alt="Prem Sagar" class="profile-img">
        <div>
            <h2 class="section-title">About Me</h2>
            <p>A passionate full-stack web developer dedicated to creating innovative digital solutions. With expertise in modern web technologies, I transform complex ideas into elegant, user-friendly applications. My approach combines technical proficiency with creative problem-solving to deliver exceptional web experiences.</p>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="section">
        <h2 class="section-title">Projects</h2>
        <div class="projects">
            <div class="project-card">
                <h3 class="project-title">E-Commerce Platform</h3>
                <p>A comprehensive e-commerce solution built with React and Node.js, featuring robust product management, user authentication, and secure payment integration.</p>
                <div class="project-links">
                    <a href="#" target="_blank"><i class="fas fa-external-link-alt"></i> View Project</a>
                    <a href="#" target="_blank"><i class="fab fa-github"></i> GitHub</a>
                </div>
            </div>
            <div class="project-card">
                <h3 class="project-title">Task Management App</h3>
                <p>A productivity-focused task management application with real-time updates, collaborative features, and intuitive user interface.</p>
                <div class="project-links">
                    <a href="#" target="_blank"><i class="fas fa-external-link-alt"></i> View Project</a>
                    <a href="#" target="_blank"><i class="fab fa-github"></i> GitHub</a>
                </div>
            </div>
            <div class="project-card">
                <h3 class="project-title">Portfolio Website</h3>
                <p>Responsive and modern personal portfolio showcasing skills and projects, built with cutting-edge web technologies.</p>
                <div class="project-links">
                    <a href="#" target="_blank"><i class="fas fa-external-link-alt"></i> View Project</a>
                    <a href="#" target="_blank"><i class="fab fa-github"></i> GitHub</a>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="section">
        <h2 class="section-title">Skills</h2>
        <div class="skills">
            <div class="skill-card"><i class="fab fa-js-square"></i> JavaScript</div>
            <div class="skill-card"><i class="fab fa-react"></i> React</div>
            <div class="skill-card"><i class="fab fa-node-js"></i> Node.js</div>
            <div class="skill-card"><i class="fab fa-python"></i> Python</div>
            <div class="skill-card"><i class="fab fa-html5"></i> HTML/CSS</div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section">
        <h2 class="section-title">Contact Me</h2>
        <form class="contact-form">
            <div class="form-group">
                <input type="text" placeholder="Your Name" required>
            </div>
            <div class="form-group">
                <input type="email" placeholder="Your Email" required>
            </div>
            <div class="form-group">
                <textarea placeholder="Your Message" rows="5" required></textarea>
            </div>
            <button type="submit" class="submit-btn">Send Message</button>
        </form>
        <div class="contact-links">
            <a href="#" target="_blank"><i class="fab fa-github"></i></a>
            <a href="#" target="_blank"><i class="fab fa-linkedin"></i></a>
            <a href="mailto:your@email.com" target="_blank"><i class="fas fa-envelope"></i></a>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="store-links">
            <a href="https://www.apple.com/app-store/" target="_blank" title="Apple App Store"><i class="fab fa-apple"></i></a>
            <a href="https://play.google.com/store" target="_blank" title="Google Play Store"><i class="fab fa-google-play"></i></a>
        </div>
        <p>&copy; 2024 Prem Sagar. All Rights Reserved.</p>
    </footer>

    <script>
        function toggleNav() {
            const navLinks = document.querySelector('.nav-links');
            const navToggle = document.querySelector('.nav-toggle');
            
            navLinks.classList.toggle('active');
            navToggle.classList.toggle('active');
        }

        // Close mobile menu when a link is clicked
        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', () => {
                const navLinks = document.querySelector('.nav-links');
                const navToggle = document.querySelector('.nav-toggle');
                
                navLinks.classList.remove('active');
                navToggle.classList.remove('active');
            });
        });
    </script>
</body>
</html># Hi there it's me 
