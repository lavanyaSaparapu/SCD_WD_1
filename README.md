import IPython.display as display

html_content = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Navigation Menu</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            transition: background-color 0.5s ease;
        }

        /* Navigation Styles */
        nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            padding: 20px 50px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        nav.scrolled {
            background-color: rgba(255, 255, 255, 0.95);
            padding: 15px 50px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.1);
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            color: #fff;
            transition: color 0.3s ease;
        }

        nav.scrolled .logo {
            color: #333;
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin-left: 30px;
        }

        .nav-links a {
            text-decoration: none;
            color: #fff;
            font-weight: 500;
            padding: 8px 15px;
            border-radius: 5px;
            transition: all 0.3s ease;
            position: relative;
        }

        nav.scrolled .nav-links a {
            color: #333;
        }

        .nav-links a:hover {
            background-color: rgba(255, 255, 255, 0.2);
            transform: translateY(-2px);
        }

        nav.scrolled .nav-links a:hover {
            background-color: rgba(0, 0, 0, 0.1);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 2px;
            background-color: #fff;
            transition: all 0.3s ease;
            transform: translateX(-50%);
        }

        nav.scrolled .nav-links a::after {
            background-color: #333;
        }

        .nav-links a:hover::after {
            width: 80%;
        }

        .menu-toggle {
            display: none;
            flex-direction: column;
            cursor: pointer;
        }

        .menu-toggle span {
            width: 25px;
            height: 3px;
            background-color: #fff;
            margin: 3px 0;
            transition: 0.3s;
        }

        nav.scrolled .menu-toggle span {
            background-color: #333;
        }

        /* Page Content Styles */
        .page {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            padding: 100px 20px;
            text-align: center;
            color: white;
        }

        .page h1 {
            font-size: 3rem;
            margin-bottom: 20px;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
        }

        .page p {
            font-size: 1.2rem;
            max-width: 700px;
            line-height: 1.6;
        }

        /* Different page colors */
        #home {
            background: linear-gradient(135deg, #6a11cb 0%, #2575fc 100%);
        }

        #about {
            background: linear-gradient(135deg, #ff6b6b 0%, #feca57 100%);
        }

        #services {
            background: linear-gradient(135deg, #00b4db 0%, #0083b0 100%);
        }

        #portfolio {
            background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
        }

        #contact {
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            nav {
                padding: 15px 20px;
            }

            nav.scrolled {
                padding: 10px 20px;
            }

            .nav-links {
                position: fixed;
                top: 70px;
                right: -100%;
                width: 80%;
                height: calc(100vh - 70px);
                background-color: rgba(255, 255, 255, 0.95);
                flex-direction: column;
                align-items: center;
                justify-content: flex-start;
                padding-top: 50px;
                transition: right 0.5s ease;
                box-shadow: -5px 0 15px rgba(0, 0, 0, 0.1);
            }

            .nav-links.active {
                right: 0;
            }

            .nav-links li {
                margin: 20px 0;
            }

            .nav-links a {
                color: #333;
                font-size: 1.2rem;
            }

            .menu-toggle {
                display: flex;
            }

            .menu-toggle.active span:nth-child(1) {
                transform: rotate(-45deg) translate(-5px, 6px);
            }

            .menu-toggle.active span:nth-child(2) {
                opacity: 0;
            }

            .menu-toggle.active span:nth-child(3) {
                transform: rotate(45deg) translate(-5px, -6px);
            }
        }
    </style>
</head>
<body>
    <!-- Navigation Menu -->
    <nav id="navbar">
        <div class="logo">BrandName</div>
        <ul class="nav-links">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#portfolio">Portfolio</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
        <div class="menu-toggle">
            <span></span>
            <span></span>
            <span></span>
        </div>
    </nav>

    <!-- Page Content -->
    <section id="home" class="page">
        <h1>Welcome Home</h1>
        <p>This is the home page with a beautiful gradient background. Scroll down to see the navigation menu change color.</p>
    </section>

    <section id="about" class="page">
        <h1>About Us</h1>
        <p>Learn more about our company and team on this vibrant orange page.</p>
    </section>

    <section id="services" class="page">
        <h1>Our Services</h1>
        <p>Discover the wide range of services we offer on this blue-themed page.</p>
    </section>

    <section id="portfolio" class="page">
        <h1>Portfolio</h1>
        <p>Explore our work and projects on this fresh green page.</p>
    </section>

    <section id="contact" class="page">
        <h1>Contact Us</h1>
        <p>Get in touch with us through this colorful pink and yellow page.</p>
    </section>

    <script>
        // Navbar scroll effect
        window.addEventListener('scroll', function() {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // Mobile menu toggle
        const menuToggle = document.querySelector('.menu-toggle');
        const navLinks = document.querySelector('.nav-links');

        menuToggle.addEventListener('click', function() {
            navLinks.classList.toggle('active');
            menuToggle.classList.toggle('active');
        });

        // Close mobile menu when clicking on a link
        const navItems = document.querySelectorAll('.nav-links a');
        navItems.forEach(item => {
            item.addEventListener('click', function() {
                navLinks.classList.remove('active');
                menuToggle.classList.remove('active');
            });
        });

        // Smooth scrolling for anchor links
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);

                if (targetElement) {
                    window.scrollTo({
                        top: targetElement.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });
    </script>
</body>
</html>
"""

display.display(display.HTML(html_content))
