<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Getinet Belayneh | Futuristic GitHub Profile</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.11.4/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.11.4/ScrollTrigger.min.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #00f7ff;
            --secondary: #8a2be2;
            --dark: #0a0a1a;
            --darker: #050510;
            --light: #e0f7fa;
            --accent: #ff2a6d;
        }

        body {
            background: linear-gradient(135deg, var(--darker), var(--dark));
            color: var(--light);
            min-height: 100vh;
            overflow-x: hidden;
            position: relative;
        }

        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 10% 20%, rgba(138, 43, 226, 0.1) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(0, 247, 255, 0.1) 0%, transparent 20%);
            pointer-events: none;
            z-index: -1;
        }

        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Header Styles */
        header {
            padding: 40px 0;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .avatar-container {
            position: relative;
            width: 180px;
            height: 180px;
            margin: 0 auto 20px;
            border-radius: 50%;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            padding: 5px;
            animation: float 6s ease-in-out infinite;
            box-shadow: 0 0 30px rgba(0, 247, 255, 0.5);
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: url('https://avatars.githubusercontent.com/u/109335949?v=4') center/cover;
            border: 3px solid var(--dark);
        }

        .hologram {
            position: absolute;
            top: -20px;
            left: -20px;
            width: 220px;
            height: 220px;
            border-radius: 50%;
            background: radial-gradient(circle, rgba(0, 247, 255, 0.2), transparent 70%);
            z-index: -1;
            animation: rotate 20s linear infinite;
        }

        h1 {
            font-size: 3.5rem;
            margin-bottom: 10px;
            background: linear-gradient(90deg, var(--primary), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 0 20px rgba(0, 247, 255, 0.3);
        }

        .title {
            font-size: 1.5rem;
            color: var(--primary);
            margin-bottom: 30px;
            position: relative;
            display: inline-block;
        }

        .title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--primary), transparent);
        }

        /* Stats Section */
        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin: 40px 0;
        }

        .stat-card {
            background: rgba(10, 15, 30, 0.7);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0, 247, 255, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: -2px;
            left: -2px;
            right: -2px;
            bottom: -2px;
            background: linear-gradient(45deg, var(--primary), var(--secondary), var(--accent));
            z-index: -1;
            border-radius: 16px;
        }

        .stat-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 10px 30px rgba(0, 247, 255, 0.3);
        }

        .stat-card i {
            font-size: 3rem;
            margin-bottom: 15px;
            color: var(--primary);
        }

        .stat-card h3 {
            font-size: 2rem;
            margin-bottom: 10px;
            color: var(--primary);
        }

        /* Skills Section */
        .skills {
            margin: 60px 0;
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 40px;
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 0;
            width: 100%;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--primary), transparent);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }

        .skill-category {
            background: rgba(10, 15, 30, 0.7);
            border-radius: 15px;
            padding: 25px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0, 247, 255, 0.1);
            position: relative;
            overflow: hidden;
        }

        .skill-category::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 5px;
            height: 100%;
            background: linear-gradient(to bottom, var(--primary), var(--secondary));
        }

        .skill-category h3 {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: var(--primary);
        }

        .skill-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 15px;
        }

        .skill-item {
            background: rgba(0, 247, 255, 0.1);
            border-radius: 8px;
            padding: 12px;
            text-align: center;
            transition: transform 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .skill-item:hover {
            transform: translateY(-5px);
            background: rgba(0, 247, 255, 0.2);
        }

        .skill-item::before {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 3px;
            background: var(--primary);
            transform: scaleX(0);
            transform-origin: left;
            transition: transform 0.3s ease;
        }

        .skill-item:hover::before {
            transform: scaleX(1);
        }

        /* Projects Section */
        .projects {
            margin: 60px 0;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
        }

        .project-card {
            background: rgba(10, 15, 30, 0.7);
            border-radius: 15px;
            overflow: hidden;
            position: relative;
            border: 1px solid rgba(0, 247, 255, 0.1);
            transition: transform 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .project-card:hover {
            transform: translateY(-10px);
        }

        .project-image {
            height: 200px;
            background: linear-gradient(45deg, #0a0a1a, #1a1a3a);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        .project-image::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, 
                rgba(0, 247, 255, 0.1) 0%, 
                rgba(138, 43, 226, 0.1) 50%, 
                rgba(255, 42, 109, 0.1) 100%);
            z-index: 1;
        }

        .project-image .hex-container {
            position: relative;
            width: 120px;
            height: 120px;
            display: grid;
            place-items: center;
            z-index: 2;
        }

        .hex {
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(10, 15, 30, 0.8);
            clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2.5rem;
            color: var(--primary);
            border: 2px solid var(--primary);
            transition: all 0.3s ease;
        }

        .project-card:hover .hex {
            transform: rotate(30deg);
            color: var(--accent);
            border-color: var(--accent);
        }

        .project-content {
            padding: 25px;
        }

        .project-content h3 {
            font-size: 1.5rem;
            margin-bottom: 10px;
            color: var(--primary);
        }

        .project-content p {
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 20px;
        }

        .tech {
            background: rgba(0, 247, 255, 0.1);
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.9rem;
        }

        .btn {
            display: inline-block;
            padding: 10px 25px;
            background: linear-gradient(45deg, var(--primary), var(--secondary));
            color: var(--dark);
            text-decoration: none;
            border-radius: 30px;
            font-weight: bold;
            position: relative;
            overflow: hidden;
            transition: all 0.3s ease;
            border: none;
            cursor: pointer;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(0, 247, 255, 0.4);
        }

        .btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: 0.5s;
        }

        .btn:hover::before {
            left: 100%;
        }

        /* Contact Section */
        .contact {
            margin: 60px 0;
            text-align: center;
        }

        .contact-form {
            max-width: 600px;
            margin: 40px auto;
            background: rgba(10, 15, 30, 0.7);
            padding: 30px;
            border-radius: 15px;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(0, 247, 255, 0.1);
        }

        .form-group {
            margin-bottom: 20px;
            text-align: left;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            color: var(--primary);
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px 15px;
            background: rgba(0, 0, 0, 0.3);
            border: 1px solid rgba(0, 247, 255, 0.2);
            border-radius: 8px;
            color: var(--light);
            font-size: 1rem;
        }

        .form-group textarea {
            min-height: 150px;
            resize: vertical;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 10px rgba(0, 247, 255, 0.3);
        }

        /* Footer */
        footer {
            text-align: center;
            padding: 30px 0;
            margin-top: 60px;
            border-top: 1px solid rgba(0, 247, 255, 0.1);
            position: relative;
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 25px;
            margin: 25px 0;
        }

        .social-link {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            background: rgba(0, 247, 255, 0.1);
            color: var(--primary);
            font-size: 1.5rem;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .social-link:hover {
            transform: translateY(-5px);
            background: rgba(0, 247, 255, 0.2);
            color: var(--accent);
            box-shadow: 0 5px 15px rgba(0, 247, 255, 0.3);
        }

        .social-link::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: linear-gradient(45deg, var(--primary), transparent);
            transform: scale(0);
            transition: transform 0.3s ease;
            z-index: -1;
        }

        .social-link:hover::before {
            transform: scale(1.2);
        }

        .copyright {
            margin-top: 20px;
            color: rgba(255, 255, 255, 0.6);
        }

        /* Animations */
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-20px);
            }
        }

        @keyframes rotate {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        /* Responsive */
        @media (max-width: 768px) {
            h1 {
                font-size: 2.5rem;
            }
            
            .title {
                font-size: 1.2rem;
            }
            
            .stats {
                grid-template-columns: 1fr;
            }
            
            .projects-grid {
                grid-template-columns: 1fr;
            }
            
            .section-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Particle Background -->
    <div id="particles" class="particles"></div>
    
    <div class="container">
        <!-- Header Section -->
        <header>
            <div class="avatar-container">
                <div class="hologram"></div>
                <div class="avatar"></div>
            </div>
            <h1>Getinet Belayneh</h1>
            <div class="title">FullStack Developer | AI Enthusiast</div>
            <p>Building the future with innovative web solutions and cutting-edge technology</p>
        </header>
        
        <!-- Stats Section -->
        <section class="stats">
            <div class="stat-card">
                <i class="fas fa-code"></i>
                <h3>100+</h3>
                <p>Projects Completed</p>
            </div>
            <div class="stat-card">
                <i class="fas fa-star"></i>
                <h3>5.0</h3>
                <p>Average Rating</p>
            </div>
            <div class="stat-card">
                <i class="fas fa-clock"></i>
                <h3>5+</h3>
                <p>Years Experience</p>
            </div>
            <div class="stat-card">
                <i class="fas fa-globe"></i>
                <h3>20+</h3>
                <p>Happy Clients</p>
            </div>
        </section>
        
        <!-- Skills Section -->
        <section class="skills">
            <h2 class="section-title">Technical Skills</h2>
            <div class="skills-grid">
                <div class="skill-category">
                    <h3>Frontend</h3>
                    <div class="skill-list">
                        <div class="skill-item">React</div>
                        <div class="skill-item">Vue.js</div>
                        <div class="skill-item">Angular</div>
                        <div class="skill-item">JavaScript</div>
                        <div class="skill-item">TypeScript</div>
                        <div class="skill-item">HTML5/CSS3</div>
                        <div class="skill-item">SASS</div>
                        <div class="skill-item">Tailwind CSS</div>
                    </div>
                </div>
                
                <div class="skill-category">
                    <h3>Backend</h3>
                    <div class="skill-list">
                        <div class="skill-item">Node.js</div>
                        <div class="skill-item">Express</div>
                        <div class="skill-item">Django</div>
                        <div class="skill-item">Flask</div>
                        <div class="skill-item">PHP</div>
                        <div class="skill-item">Laravel</div>
                        <div class="skill-item">Python</div>
                        <div class="skill-item">REST API</div>
                    </div>
                </div>
                
                <div class="skill-category">
                    <h3>Database & DevOps</h3>
                    <div class="skill-list">
                        <div class="skill-item">MongoDB</div>
                        <div class="skill-item">MySQL</div>
                        <div class="skill-item">PostgreSQL</div>
                        <div class="skill-item">Firebase</div>
                        <div class="skill-item">Docker</div>
                        <div class="skill-item">Kubernetes</div>
                        <div class="skill-item">AWS</div>
                        <div class="skill-item">Git</div>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Projects Section -->
        <section class="projects">
            <h2 class="section-title">Featured Projects</h2>
            <div class="projects-grid">
                <div class="project-card">
                    <div class="project-image">
                        <div class="hex-container">
                            <div class="hex"><i class="fas fa-brain"></i></div>
                        </div>
                    </div>
                    <div class="project-content">
                        <h3>AI-Powered Analytics Dashboard</h3>
                        <p>A comprehensive analytics platform with real-time data visualization and predictive insights powered by machine learning algorithms.</p>
                        <div class="tech-stack">
                            <div class="tech">React</div>
                            <div class="tech">Node.js</div>
                            <div class="tech">TensorFlow</div>
                            <div class="tech">MongoDB</div>
                        </div>
                        <a href="#" class="btn">View Project</a>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-image">
                        <div class="hex-container">
                            <div class="hex"><i class="fas fa-shopping-cart"></i></div>
                        </div>
                    </div>
                    <div class="project-content">
                        <h3>E-commerce Platform</h3>
                        <p>A full-featured e-commerce solution with payment integration, inventory management, and personalized recommendations.</p>
                        <div class="tech-stack">
                            <div class="tech">Vue.js</div>
                            <div class="tech">Express</div>
                            <div class="tech">PostgreSQL</div>
                            <div class="tech">Stripe API</div>
                        </div>
                        <a href="#" class="btn">View Project</a>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-image">
                        <div class="hex-container">
                            <div class="hex"><i class="fas fa-mobile-alt"></i></div>
                        </div>
                    </div>
                    <div class="project-content">
                        <h3>Fitness Tracking App</h3>
                        <p>A mobile-first application that tracks workouts, nutrition, and progress with AI-generated fitness plans.</p>
                        <div class="tech-stack">
                            <div class="tech">React Native</div>
                            <div class="tech">Firebase</div>
                            <div class="tech">Redux</div>
                            <div class="tech">GraphQL</div>
                        </div>
                        <a href="#" class="btn">View Project</a>
                    </div>
                </div>
            </div>
        </section>
        
        <!-- Contact Section -->
        <section class="contact">
            <h2 class="section-title">Get In Touch</h2>
            <div class="contact-form">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" id="name" placeholder="Your name">
                </div>
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" id="email" placeholder="Your email">
                </div>
                <div class="form-group">
                    <label for="message">Message</label>
                    <textarea id="message" placeholder="Your message"></textarea>
                </div>
                <button class="btn">Send Message</button>
                <div style="margin-top: 20px; font-size: 1.2rem;">
                    <i class="fas fa-envelope"></i> getinet1223@gmail.com
                </div>
            </div>
        </section>
    </div>
    
    <!-- Footer -->
    <footer>
        <div class="social-links">
            <a href="#" class="social-link"><i class="fab fa-github"></i></a>
            <a href="#" class="social-link"><i class="fab fa-linkedin-in"></i></a>
            <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
            <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
        </div>
        <p class="copyright">© 2023 Getinet Belayneh. All rights reserved.</p>
    </footer>
    
    <script>
        // Particle System
        document.addEventListener('DOMContentLoaded', function() {
            // Initialize Three.js for particle background
            const scene = new THREE.Scene();
            const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
            const renderer = new THREE.WebGLRenderer({ alpha: true });
            renderer.setSize(window.innerWidth, window.innerHeight);
            document.getElementById('particles').appendChild(renderer.domElement);
            
            // Create particles
            const particlesGeometry = new THREE.BufferGeometry();
            const particlesCount = 5000;
            const posArray = new Float32Array(particlesCount * 3);
            const colorArray = new Float32Array(particlesCount * 3);
            
            for (let i = 0; i < particlesCount * 3; i += 3) {
                // Position
                posArray[i] = (Math.random() - 0.5) * 50;
                posArray[i + 1] = (Math.random() - 0.5) * 50;
                posArray[i + 2] = (Math.random() - 0.5) * 50;
                
                // Color
                colorArray[i] = Math.random() * 0.5 + 0.5; // R
                colorArray[i + 1] = Math.random() * 0.8 + 0.2; // G
                colorArray[i + 2] = Math.random() * 0.8 + 0.2; // B
            }
            
            particlesGeometry.setAttribute('position', new THREE.BufferAttribute(posArray, 3));
            particlesGeometry.setAttribute('color', new THREE.BufferAttribute(colorArray, 3));
            
            // Material
            const particlesMaterial = new THREE.PointsMaterial({
                size: 0.05,
                vertexColors: true,
                transparent: true,
                opacity: 0.8,
                blending: THREE.AdditiveBlending
            });
            
            // Points system
            const particlesSystem = new THREE.Points(particlesGeometry, particlesMaterial);
            scene.add(particlesSystem);
            
            // Position camera
            camera.position.z = 5;
            
            // Animation
            function animate() {
                requestAnimationFrame(animate);
                
                particlesSystem.rotation.x += 0.0005;
                particlesSystem.rotation.y += 0.0005;
                
                renderer.render(scene, camera);
            }
            
            animate();
            
            // GSAP Animations
            gsap.registerPlugin(ScrollTrigger);
            
            // Animate elements on scroll
            gsap.utils.toArray('.stat-card').forEach(card => {
                gsap.from(card, {
                    scrollTrigger: {
                        trigger: card,
                        start: 'top 80%'
                    },
                    y: 50,
                    opacity: 0,
                    duration: 0.8,
                    ease: 'power2.out'
                });
            });
            
            gsap.utils.toArray('.project-card').forEach(card => {
                gsap.from(card, {
                    scrollTrigger: {
                        trigger: card,
                        start: 'top 85%'
                    },
                    y: 60,
                    opacity: 0,
                    duration: 0.8,
                    ease: 'back.out(1.7)',
                    delay: 0.1
                });
            });
            
            // Avatar animation
            gsap.to('.avatar-container', {
                scrollTrigger: {
                    trigger: '.avatar-container',
                    start: 'top top',
                    end: '+=300',
                    scrub: 1
                },
                scale: 0.8,
                opacity: 0.7,
                y: 50
            });
            
            // Handle window resize
            window.addEventListener('resize', () => {
                camera.aspect = window.innerWidth / window.innerHeight;
                camera.updateProjectionMatrix();
                renderer.setSize(window.innerWidth, window.innerHeight);
            });
        });
    </script>
</body>
</html>
