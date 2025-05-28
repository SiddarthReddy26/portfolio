<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Siddarth Reddy - Creative Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Playfair+Display:wght@400;500;600;700&family=JetBrains+Mono:wght@300;400;500&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --secondary-gradient: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            --dark-gradient: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            --text-primary: #2d3748;
            --text-secondary: #4a5568;
            --text-light: #718096;
            --bg-light: #f7fafc;
            --bg-white: #ffffff;
            --bg-card: #ffffff;
            --shadow: 0 10px 25px rgba(0,0,0,0.1);
            --shadow-hover: 0 20px 40px rgba(0,0,0,0.15);
            --navbar-bg: rgba(255, 255, 255, 0.95);
            --navbar-bg-scroll: rgba(255, 255, 255, 0.98);
        }

        [data-theme="dark"] {
            --text-primary: #f7fafc;
            --text-secondary: #e2e8f0;
            --text-light: #a0aec0;
            --bg-light: #1a202c;
            --bg-white: #2d3748;
            --bg-card: #2d3748;
            --shadow: 0 10px 25px rgba(0,0,0,0.3);
            --shadow-hover: 0 20px 40px rgba(0,0,0,0.4);
            --navbar-bg: rgba(45, 55, 72, 0.95);
            --navbar-bg-scroll: rgba(45, 55, 72, 0.98);
        }

        body {
            font-family: 'Poppins', sans-serif;
            line-height: 1.6;
            color: var(--text-primary);
            overflow-x: hidden;
            background-color: var(--bg-white);
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        /* Navigation */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: var(--navbar-bg);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            transition: all 0.3s ease;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
        }

        [data-theme="dark"] .navbar {
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            font-weight: 700;
            background: var(--primary-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-primary);
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-links a:hover {
            color: #667eea;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background: var(--primary-gradient);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Theme Toggle */
        .theme-toggle {
            background: none;
            border: 2px solid var(--text-primary);
            border-radius: 50px;
            padding: 8px 12px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 5px;
            color: var(--text-primary);
            font-size: 0.9rem;
            transition: all 0.3s ease;
            font-family: 'Poppins', sans-serif;
        }

        .theme-toggle:hover {
            background: var(--primary-gradient);
            color: white;
            border-color: transparent;
            transform: scale(1.05);
        }

        .theme-icon {
            font-size: 1.2rem;
            transition: transform 0.3s ease;
        }

        .theme-toggle:hover .theme-icon {
            transform: rotate(180deg);
        }

        /* Hero Section */
        .hero {
            min-height: 100vh;
            display: flex;
            align-items: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 50%, #f093fb 100%);
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            width: 200%;
            height: 200%;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="50" cy="50" r="1" fill="white" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>');
            animation: float 20s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0) rotate(0deg); }
            50% { transform: translate(-20px, -20px) rotate(180deg); }
        }

        .hero-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            text-align: center;
            color: white;
            position: relative;
            z-index: 2;
        }

        .hero h1 {
            font-family: 'Playfair Display', serif;
            font-size: clamp(3rem, 8vw, 6rem);
            font-weight: 700;
            margin-bottom: 1rem;
            opacity: 0;
            animation: slideUp 1s ease forwards 0.2s;
        }

        .hero .subtitle {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            font-weight: 300;
            margin-bottom: 2rem;
            opacity: 0;
            animation: slideUp 1s ease forwards 0.4s;
        }

        .hero .description {
            font-size: 1.1rem;
            max-width: 600px;
            margin: 0 auto 3rem;
            opacity: 0;
            animation: slideUp 1s ease forwards 0.6s;
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            opacity: 0;
            animation: slideUp 1s ease forwards 0.8s;
        }

        .btn {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-weight: 600;
            text-decoration: none;
            display: inline-block;
            transition: all 0.3s ease;
            cursor: pointer;
            font-family: 'Poppins', sans-serif;
        }

        .btn-primary {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            backdrop-filter: blur(10px);
            border: 2px solid rgba(255, 255, 255, 0.3);
        }

        .btn-primary:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .btn-secondary {
            background: transparent;
            color: white;
            border: 2px solid white;
        }

        .btn-secondary:hover {
            background: white;
            color: var(--text-primary);
            transform: translateY(-2px);
        }

        /* Sections */
        .section {
            padding: 5rem 0;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(2.5rem, 5vw, 3.5rem);
            text-align: center;
            margin-bottom: 3rem;
            background: var(--primary-gradient);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* About Section */
        .about {
            background: var(--bg-light);
            transition: background-color 0.3s ease;
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 4rem;
            align-items: center;
        }

        .about-image {
            position: relative;
        }

        .about-image img {
            width: 100%;
            border-radius: 20px;
            box-shadow: var(--shadow);
        }

        .about-text h3 {
            font-family: 'Playfair Display', serif;
            font-size: 2rem;
            margin-bottom: 1rem;
            color: var(--text-primary);
        }

        .about-text p {
            font-size: 1.1rem;
            color: var(--text-secondary);
            margin-bottom: 1.5rem;
        }

        .skills {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            margin-top: 2rem;
        }

        .skill-tag {
            background: var(--primary-gradient);
            color: white;
            padding: 0.5rem 1rem;
            border-radius: 25px;
            font-size: 0.9rem;
            font-weight: 500;
        }

        /* Projects Section */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: var(--bg-card);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            position: relative;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        [data-theme="dark"] .project-card {
            border: 1px solid rgba(255, 255, 255, 0.05);
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
        }

        .project-image {
            height: 200px;
            background: var(--primary-gradient);
            position: relative;
            overflow: hidden;
        }

        .project-image::before {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 60px;
            height: 60px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 10px;
            backdrop-filter: blur(10px);
        }

        .project-content {
            padding: 1.5rem;
        }

        .project-content h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
        }

        .project-tech {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.9rem;
            color: var(--text-light);
            margin-bottom: 1rem;
        }

        .project-links {
            display: flex;
            gap: 1rem;
        }

        .project-links a {
            color: #667eea;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s ease;
        }

        .project-links a:hover {
            color: #764ba2;
        }

        /* Contact Section */
        .contact {
            background: var(--dark-gradient);
            color: white;
        }

        .contact .section-title {
            color: white;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .contact-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 4rem;
            align-items: start;
        }

        .contact-info h3 {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            margin-bottom: 2rem;
        }

        .contact-item {
            display: flex;
            align-items: center;
            margin-bottom: 1.5rem;
            font-size: 1.1rem;
        }

        .contact-item::before {
            content: '→';
            margin-right: 1rem;
            color: #f093fb;
            font-weight: bold;
        }

        .contact-form {
            display: flex;
            flex-direction: column;
            gap: 1rem;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            margin-bottom: 0.5rem;
            font-weight: 500;
        }

        .form-group input,
        .form-group textarea {
            padding: 12px;
            border: none;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            font-family: 'Poppins', sans-serif;
            transition: all 0.3s ease;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: rgba(255, 255, 255, 0.4);
            background: rgba(255, 255, 255, 0.15);
        }

        .form-group input::placeholder,
        .form-group textarea::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        .form-group textarea {
            resize: vertical;
            min-height: 120px;
        }

        /* Footer */
        .footer {
            background: #1a202c;
            color: white;
            text-align: center;
            padding: 2rem 0;
            transition: background-color 0.3s ease;
        }

        [data-theme="dark"] .footer {
            background: #0d1117;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 1rem;
        }

        .social-links a {
            color: white;
            text-decoration: none;
            font-size: 1.2rem;
            transition: color 0.3s ease;
        }

        .social-links a:hover {
            color: #f093fb;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .nav-container {
                justify-content: space-between;
            }

            .about-content,
            .contact-content {
                grid-template-columns: 1fr;
                gap: 2rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .theme-toggle {
                padding: 6px 10px;
                font-size: 0.8rem;
            }
        }

        /* Scroll animations */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar">
        <div class="nav-container">
            <div class="logo">SR</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <button class="theme-toggle" id="themeToggle">
                <span class="theme-icon">🌙</span>
                <span class="theme-text">Dark</span>
            </button>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="hero-content">
            <h1>Siddarth Reddy</h1>
            <p class="subtitle">Creative Developer & Designer</p>
            <p class="description">
                I craft beautiful digital experiences that blend innovative design with cutting-edge technology. 
                Let's bring your ideas to life with passion and precision.
            </p>
            <div class="cta-buttons">
                <a href="#projects" class="btn btn-primary">View My Work</a>
                <a href="#contact" class="btn btn-secondary">Get In Touch</a>
            </div>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="section about">
        <div class="container">
            <h2 class="section-title fade-out">About Me</h2>
            <div class="about-content">
                <div class="about-image fade-in">
                    <div style="width: 100%; height: 300px; background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); border-radius: 20px; display: flex; align-items: center; justify-content: center; color: white; font-size: 3rem; font-weight: bold;">SR</div>
                </div>
                <div class="about-text fade-in">
                    <h3>Passionate about creating exceptional digital experiences</h3>
                    <p>
                        I'm constantly learning new technologies and pushing the boundaries of what's possible 
                        on the web. When I'm not coding, you can find me exploring new design trends, 
                        contributing to open-source projects, or sharing knowledge with the developer community.
                    </p>
                    <div class="skills">
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">Java(Basics)</span>
                        <span class="skill-tag">Python</span>
                        <span class="skill-tag">HTML</span>
                        <span class="skill-tag">DBMS</span>
                        <span class="skill-tag">CSS</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="section">
        <div class="container">
            <h2 class="section-title fade-in">Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card fade-in">
                    <div class="project-image"></div>
                    <div class="project-content">
                        <h3>E-Commerce Platform</h3>
                        <p class="project-tech">React • Node.js • MongoDB • Stripe</p>
                        <p>A full-stack e-commerce solution with real-time inventory management, secure payments, and admin dashboard.</p>
                        <div class="project-links">
                            <a href="http://127.0.0.1:5502/shopping.html">Live Demo</a>
                            <a href="#">GitHub</a>
                        </div>
                    </div>
                </div>
                
                <div class="project-card fade-in">
                    <div class="project-image" style="background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);"></div>
                    <div class="project-content">
                        <h3>Recipe Book</h3>
                        <p class="project-tech">HTML • CSS • JavaScript</p>
                        <p>A Recipe Book site with real-time updates, online functionality, and best features.</p>
                        <div class="project-links">
                            <a href="http://127.0.0.1:5503/recipies.html">Live Demo</a>
                            <a href="#">GitHub</a>
                        </div>
                    </div>
                </div>
                
                <div class="project-card fade-in">
                    <div class="project-image" style="background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);"></div>
                    <div class="project-content">
                        <h3>Weather Analytics Dashboard</h3>
                        <p class="project-tech">Python • Django • D3.js • APIs</p>
                        <p>An interactive dashboard for weather data visualization with predictive analytics and customizable reports.</p>
                        <div class="project-links">
                            <a href="#">Live Demo</a>
                            <a href="#">GitHub</a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section contact">
        <div class="container">
            <h2 class="section-title fade-in">Let's Work Together</h2>
            <div class="contact-content">
                <div class="contact-info fade-in">
                    <h3>Get in touch</h3>
                    <p>I'm always interested in new opportunities and exciting projects. Let's discuss how we can bring your ideas to life.</p>
                    
                    <div class="contact-item">siddarthtreddy@gmail.com</div>
                    <div class="contact-item">+91 8247 858 175</div>
                    <div class="contact-item">Hyderabad, Telangana</div>
                    <div class="contact-item">Available for freelance</div>
                </div>
                
                <form class="contact-form fade-in">
                    <div class="form-group">
                        <label for="name">Your Name</label>
                        <input type="text" id="name" name="name" placeholder="Enter your name" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="email">Your Email</label>
                        <input type="email" id="email" name="email" placeholder="Enter your email" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="message">Your Message</label>
                        <textarea id="message" name="message" placeholder="Tell me about your project..." required></textarea>
                    </div>
                    
                    <button type="submit" class="btn btn-primary">Send Message</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="social-links">
                <a href="#">LinkedIn</a>
                <a href="#">GitHub</a>
                <a href="#">Twitter</a>
            </div>
            <p>&copy; 2025 Siddarth Reddy. Crafted with passion and code.</p>
        </div>
    </footer>

    <script>
        // Smooth scrolling for navigation links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // Navbar background change on scroll
        window.addEventListener('scroll', () => {
            const navbar = document.querySelector('.navbar');
            if (window.scrollY > 100) {
                navbar.style.background = 'var(--navbar-bg-scroll)';
                navbar.style.boxShadow = '0 2px 20px rgba(0, 0, 0, 0.1)';
            } else {
                navbar.style.background = 'var(--navbar-bg)';
                navbar.style.boxShadow = 'none';
            }
        });

        // Theme Toggle Functionality
        const themeToggle = document.getElementById('themeToggle');
        const themeIcon = themeToggle.querySelector('.theme-icon');
        const themeText = themeToggle.querySelector('.theme-text');
        
        // Check for saved theme preference or default to light mode
        let currentTheme = 'light';
        try {
            currentTheme = localStorage.getItem('theme') || 'light';
        } catch (e) {
            console.log('localStorage not available');
        }
        
        document.documentElement.setAttribute('data-theme', currentTheme);
        
        // Update toggle button based on current theme
        function updateThemeToggle(theme) {
            if (theme === 'dark') {
                themeIcon.textContent = '☀️';
                themeText.textContent = 'Light';
            } else {
                themeIcon.textContent = '🌙';
                themeText.textContent = 'Dark';
            }
        }
        
        // Initialize theme toggle
        updateThemeToggle(currentTheme);
        
        // Theme toggle event listener
        themeToggle.addEventListener('click', () => {
            const currentTheme = document.documentElement.getAttribute('data-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            
            document.documentElement.setAttribute('data-theme', newTheme);
            
            try {
                localStorage.setItem('theme', newTheme);
            } catch (e) {
                console.log('localStorage not available');
            }
            
            updateThemeToggle(newTheme);
            
            // Add a nice transition effect
            document.body.style.transition = 'all 0.3s ease';
            setTimeout(() => {
                document.body.style.transition = '';
            }, 300);
        });

        // Intersection Observer for scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        // Observe all fade-in elements
        document.querySelectorAll('.fade-in').forEach(el => {
            observer.observe(el);
        });

        // Form submission
        document.querySelector('.contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form data
            const formData = new FormData(this);
            const name = formData.get('name');
            const email = formData.get('email');
            const message = formData.get('message');
            
            // Simple validation
            if (name && email && message) {
                // Simulate form submission
                const submitBtn = this.querySelector('button[type="submit"]');
                const originalText = submitBtn.textContent;
                
                submitBtn.textContent = 'Sending...';
                submitBtn.disabled = true;
                
                setTimeout(() => {
                    alert('Thank you for your message! I\'ll get back to you soon.');
                    this.reset();
                    submitBtn.textContent = originalText;
                    submitBtn.disabled = false;
                }, 1000);
            }
        });

        // Add some interactive hover effects
        document.querySelectorAll('.project-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-10px) scale(1.02)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });
    </script>
</body>
</html>
