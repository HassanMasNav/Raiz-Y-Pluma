<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Raíz y Pluma - Huevos de Libre Pastoreo</title>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Caveat:wght@400;600&family=Open+Sans:wght@300;400;600&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --beige: #F5F1E8;
            --verde: #8B956D;
            --cafe: #8B4513;
            --crema: #FFF8E7;
            --tierra: #D2B48C;
            --verde-oscuro: #6B7A4F;
            --cafe-claro: #CD853F;
        }

        body {
            font-family: 'Open Sans', sans-serif;
            line-height: 1.6;
            color: var(--cafe);
            background-color: var(--crema);
            overflow-x: hidden;
        }

        /* Header */
        header {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(245, 241, 232, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            transition: all 0.3s ease;
            border-bottom: 2px solid var(--verde);
        }

        nav {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        .logo {
            font-family: 'Dancing Script', cursive;
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--verde);
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--cafe);
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-links a:hover {
            color: var(--verde);
            transform: translateY(-2px);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--verde);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .mobile-menu {
            display: none;
            flex-direction: column;
            cursor: pointer;
        }

        .mobile-menu span {
            width: 25px;
            height: 3px;
            background: var(--verde);
            margin: 3px 0;
            transition: 0.3s;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            background: linear-gradient(135deg, var(--beige) 0%, var(--crema) 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="20" cy="20" r="1" fill="%23d2b48c" opacity="0.1"/><circle cx="60" cy="40" r="1.5" fill="%238b956d" opacity="0.1"/><circle cx="80" cy="70" r="1" fill="%238b4513" opacity="0.1"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>') repeat;
            opacity: 0.3;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            animation: fadeInUp 1s ease-out;
        }

        .hero h1 {
            font-family: 'Dancing Script', cursive;
            font-size: 4rem;
            color: var(--verde);
            margin-bottom: 1rem;
            text-shadow: 3px 3px 6px rgba(0,0,0,0.1);
            animation: fadeInScale 1.2s ease-out;
        }

        .hero-subtitle {
            font-family: 'Caveat', cursive;
            font-size: 1.8rem;
            color: var(--cafe);
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease-out 0.3s both;
        }

        .hero-description {
            font-size: 1.2rem;
            max-width: 600px;
            margin: 0 auto 2rem;
            opacity: 0.9;
            animation: fadeInUp 1s ease-out 0.6s both;
        }

        .cta-button {
            display: inline-block;
            background: linear-gradient(135deg, var(--verde), var(--verde-oscuro));
            color: white;
            padding: 1rem 2rem;
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(139, 149, 109, 0.3);
            animation: fadeInUp 1s ease-out 0.9s both;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(139, 149, 109, 0.4);
        }

        /* Sections */
        section {
            padding: 5rem 0;
            max-width: 1200px;
            margin: 0 auto;
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease;
        }

        section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .section-title {
            font-family: 'Dancing Script', cursive;
            font-size: 3rem;
            color: var(--verde);
            text-align: center;
            margin-bottom: 3rem;
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
            background: linear-gradient(90deg, var(--verde), var(--cafe));
            border-radius: 2px;
        }

        .container {
            padding: 0 2rem;
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }

        .about-text {
            font-size: 1.1rem;
            line-height: 1.8;
        }

        .about-text p {
            margin-bottom: 1.5rem;
        }

        .about-image {
            position: relative;
            overflow: hidden;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }

        .about-image:hover {
            transform: scale(1.05);
        }

        .about-image img {
            width: 100%;
            height: 300px;
            object-fit: cover;
            transition: transform 0.3s ease;
        }

        /* Care Section */
        .care-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .care-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.08);
            text-align: center;
            transition: all 0.3s ease;
            border: 2px solid var(--beige);
        }

        .care-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.12);
            border-color: var(--verde);
        }

        .care-icon {
            font-size: 3rem;
            color: var(--verde);
            margin-bottom: 1rem;
        }

        .care-card h3 {
            font-family: 'Caveat', cursive;
            font-size: 1.5rem;
            color: var(--cafe);
            margin-bottom: 1rem;
        }

        /* Products Section */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .product-card {
            background: linear-gradient(135deg, white, var(--beige));
            padding: 2rem;
            border-radius: 20px;
            text-align: center;
            box-shadow: 0 8px 25px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .product-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 4px;
            background: linear-gradient(90deg, var(--verde), var(--cafe));
        }

        .product-card:hover {
            transform: translateY(-8px) scale(1.02);
            box-shadow: 0 15px 40px rgba(0,0,0,0.15);
        }

        .product-icon {
            font-size: 4rem;
            margin-bottom: 1rem;
        }

        .product-card h3 {
            font-family: 'Caveat', cursive;
            font-size: 1.8rem;
            color: var(--verde);
            margin-bottom: 1rem;
        }

        .feature-list {
            list-style: none;
            margin: 1rem 0;
        }

        .feature-list li {
            padding: 0.3rem 0;
            position: relative;
            padding-left: 1.5rem;
        }

        .feature-list li::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: var(--verde);
            font-weight: bold;
        }

        /* Pricing Section */
        .pricing-content {
            text-align: center;
            max-width: 800px;
            margin: 0 auto;
        }

        .pricing-card {
            background: linear-gradient(135deg, var(--crema), white);
            padding: 3rem 2rem;
            border-radius: 25px;
            margin: 2rem 0;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            border: 3px solid var(--verde);
            position: relative;
            overflow: hidden;
        }

        .pricing-card::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(139, 149, 109, 0.1), transparent);
            transform: rotate(45deg);
            transition: transform 0.6s ease;
        }

        .pricing-card:hover::before {
            transform: rotate(45deg) translate(50%, 50%);
        }

        .price {
            font-family: 'Dancing Script', cursive;
            font-size: 3rem;
            color: var(--verde);
            margin-bottom: 1rem;
        }

        .whatsapp-btn {
            background: #25D366;
            color: white;
            padding: 1rem 2rem;
            border-radius: 50px;
            text-decoration: none;
            font-weight: 600;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            transition: all 0.3s ease;
            margin-top: 1rem;
        }

        .whatsapp-btn:hover {
            background: #20BA5A;
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(37, 211, 102, 0.3);
        }

        /* Testimonials */
        .testimonials-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .testimonial-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.08);
            position: relative;
            transition: all 0.3s ease;
        }

        .testimonial-card::before {
            content: '"';
            position: absolute;
            top: -10px;
            left: 20px;
            font-size: 4rem;
            color: var(--verde);
            opacity: 0.3;
            font-family: serif;
        }

        .testimonial-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.12);
        }

        .testimonial-text {
            font-style: italic;
            margin-bottom: 1rem;
            line-height: 1.6;
        }

        .testimonial-author {
            font-weight: 600;
            color: var(--verde);
            text-align: right;
        }

        .stars {
            color: #FFD700;
            margin-bottom: 1rem;
        }

        /* Footer */
        footer {
            background: linear-gradient(135deg, var(--cafe), var(--verde-oscuro));
            color: white;
            padding: 3rem 0 1rem;
            text-align: center;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .footer-section h3 {
            font-family: 'Caveat', cursive;
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: var(--beige);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-links a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            background: rgba(255,255,255,0.1);
            color: white;
            border-radius: 50%;
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            background: rgba(255,255,255,0.2);
            transform: translateY(-3px);
        }

        /* WhatsApp Floating Button */
        .whatsapp-float {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 60px;
            height: 60px;
            background: #25D366;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
            text-decoration: none;
            box-shadow: 0 4px 15px rgba(37, 211, 102, 0.4);
            z-index: 1000;
            transition: all 0.3s ease;
            animation: pulse 2s infinite;
        }

        .whatsapp-float:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 20px rgba(37, 211, 102, 0.6);
        }

        /* Animations */
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInScale {
            from {
                opacity: 0;
                transform: scale(0.8);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes pulse {
            0% {
                box-shadow: 0 4px 15px rgba(37, 211, 102, 0.4);
            }
            50% {
                box-shadow: 0 4px 15px rgba(37, 211, 102, 0.6), 0 0 0 10px rgba(37, 211, 102, 0.1);
            }
            100% {
                box-shadow: 0 4px 15px rgba(37, 211, 102, 0.4);
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu {
                display: flex;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero-subtitle {
                font-size: 1.4rem;
            }

            .section-title {
                font-size: 2.2rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .care-grid,
            .products-grid,
            .testimonials-grid {
                grid-template-columns: 1fr;
            }

            .container {
                padding: 0 1rem;
            }

            nav {
                padding: 0 1rem;
            }

            .whatsapp-float {
                bottom: 15px;
                right: 15px;
                width: 50px;
                height: 50px;
                font-size: 1.2rem;
            }
        }

        @media (max-width: 480px) {
            .hero {
                padding: 0 1rem;
            }

            .hero h1 {
                font-size: 2rem;
            }

            .hero-subtitle {
                font-size: 1.2rem;
            }

            .logo {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <nav>
            <div class="logo">🌿 Raíz y Pluma</div>
            <ul class="nav-links">
                <li><a href="#inicio">Inicio</a></li>
                <li><a href="#nosotros">Nosotros</a></li>
                <li><a href="#cuidados">Cuidados</a></li>
                <li><a href="#productos">Productos</a></li>
                <li><a href="#precios">Precios</a></li>
                <li><a href="#testimonios">Testimonios</a></li>
            </ul>
            <div class="mobile-menu">
                <span></span>
                <span></span>
                <span></span>
            </div>
        </nav>
    </header>

    <!-- Hero Section -->
    <section id="inicio" class="hero">
        <div class="hero-content">
            <h1>Raíz y Pluma</h1>
            <p class="hero-subtitle">Huevos frescos de libre pastoreo 🥚</p>
            <p class="hero-description">
                Descubre la diferencia de los huevos auténticos, donde nuestras gallinas felices 
                viven en libertad y amor por la naturaleza se refleja en cada huevo que llega a tu mesa.
            </p>
            <a href="#productos" class="cta-button">Conoce Nuestros Huevos</a>
        </div>
    </section>

    <!-- About Section -->
    <section id="nosotros" class="container">
        <h2 class="section-title">¿Quiénes Somos?</h2>
        <div class="about-content">
            <div class="about-text">
                <p>
                    Somos un emprendimiento joven y apasionado que nació del amor por la naturaleza 
                    y el compromiso con la alimentación saludable. En <strong>Raíz y Pluma</strong>, 
                    creemos que los mejores huevos provienen de gallinas felices y libres.
                </p>
                <p>
                    Nuestro proyecto familiar comenzó con la convicción de que podíamos hacer la diferencia 
                    en la mesa de las familias, ofreciendo productos frescos, naturales y llenos de vida. 
                    Cada día trabajamos con dedicación para mantener los más altos estándares de calidad 
                    y bienestar animal.
                </p>
                <p>
                    <em>"Porque cuando las gallinas son felices, los huevos saben mejor."</em>
                </p>
            </div>
            <div class="about-image">
                <img src="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 400 300'><rect fill='%23F5F1E8' width='400' height='300'/><circle cx='200' cy='150' r='80' fill='%238B956D' opacity='0.3'/><text x='200' y='130' text-anchor='middle' font-size='24' fill='%238B4513' font-family='serif'>🐔</text><text x='200' y='170' text-anchor='middle' font-size='16' fill='%238B4513'>Gallinas Felices</text><text x='200' y='190' text-anchor='middle' font-size='12' fill='%238B956D'>Vida en Libertad</text></svg>" alt="Nuestras gallinas felices">
            </div>
        </div>
    </section>

    <!-- Care Section -->
    <section id="cuidados" class="container">
        <h2 class="section-title">Cómo Cuidamos a Nuestras Gallinas</h2>
        <div class="care-grid">
            <div class="care-card">
                <div class="care-icon">🌱</div>
                <h3>Alimentación Natural</h3>
                <p>Nuestras gallinas se alimentan de granos seleccionados, hierbas frescas y todo lo que la naturaleza les ofrece en nuestros amplios pastizales.</p>
            </div>
            <div class="care-card">
                <div class="care-icon">🏡</div>
                <h3>Espacios Amplios</h3>
                <p>Cada gallina cuenta con suficiente espacio para correr, explorar y expresar sus comportamientos naturales en un ambiente libre de estrés.</p>
            </div>
            <div class="care-card">
                <div class="care-icon">💚</div>
                <h3>Cuidado Amoroso</h3>
                <p>Brindamos atención veterinaria preventiva, cariño diario y un ambiente seguro que respeta su bienestar y dignidad animal.</p>
            </div>
            <div class="care-card">
                <div class="care-icon">☀️</div>
                <h3>Vida al Aire Libre</h3>
                <p>Nuestras gallinas disfrutan del sol, la lluvia y el viento. Viven como la naturaleza manda, en armonía con su entorno.</p>
            </div>
        </div>
    </section>

    <!-- Products Section -->
    <section id="productos" class="container">
        <h2 class="section-title">Nuestros Huevos Especiales</h2>
        <div class="products-grid">
            <div class="product-card">
                <div class="product-icon">🥚</div>
                <h3>Huevos Frescos de Libre Pastoreo</h3>
                <ul class="feature-list">
                    <li>Yema más naranja y nutritiva</li>
                    <li>Sabor auténtico e intenso</li>
                    <li>Rica en omega-3 natural</li>
                    <li>Sin hormonas ni antibióticos</li>
                    <li>Cáscara más resistente</li>
                    <li>Gallinas 100% libres</li>
                </ul>
                <p style="margin-top: 1rem;"><em>La diferencia se nota desde el primer bocado</em></p>
            </div>
            <div class="product-card">
                <div class="product-icon">⭐</div>
                <h3>¿Por Qué Son Mejores?</h3>
                <ul class="feature-list">
                    <li>Mayor contenido proteico</li>
                    <li>Vitaminas A, D y E elevadas</li>
                    <li>Menos colesterol malo</li>
                    <li>Mejor textura al cocinar</li>
                    <li>Vida útil extendida</li>
                    <li>Compromiso con el planeta</li>
                </ul>
                <p style="margin-top: 1rem;"><em>Calidad que puedes ver, oler y saborear</em></p>
            </div>
        </div>
    </section>

    <!-- Pricing Section -->
    <section id="precios" class="container">
        <h2 class="section-title">Precios y Pedidos</h2>
        <div class="pricing-content">
            <div class="pricing-card">
                <h3 style="font-family: 'Caveat', cursive; font-size: 2rem; color: var(--verde); margin-bottom: 1rem;">
                    Cartón de 30 Huevos Frescos
                </h3>
                <div class="price">$120 pesos</div>
                <p style="font-size: 1.1rem; margin: 1rem 0;">
                    • Huevos del día, directo de la granja<br>
                    • Entrega en tu domicilio<br>
                    • Garantía de frescura<br>
                    • Apoyas la economía local y sustentable
                </p>
                <p style="font-style: italic; color: var(--verde); margin: 1rem 0;">
                    "Pedido mínimo: 1 cartón | Entregas martes y viernes"
                </p>
                <a href="https://wa.me/523391234567?text=¡Hola! Quiero pedir huevos frescos de Raíz y Pluma" class="whatsapp-btn">
                    <i class="fab fa-whatsapp"></i> Pedir por WhatsApp
                </a>
            </div>
        </div>
    </section>

    <!-- Testimonials Section -->
    <section id="testimonios" class="container">
        <h2 class="section-title">Lo Que Dicen Nuestros Clientes</h2>
        <div class="testimonials-grid">
            <div class="testimonial-card">
                <div class="stars">⭐⭐⭐⭐⭐</div>
                <p class="testimonial-text">
                    "Desde que compro en Raíz y Pluma, mis desayunos son completamente diferentes. 
                    La yema es súper naranja y el sabor es increíble. ¡No puedo volver a los huevos del súper!"
                </p>
                <p class="testimonial-author">- María González</p>
            </div>
            <div class="testimonial-card">
                <div class="stars">⭐⭐⭐⭐⭐</div>
                <p class="testimonial-text">
                    "Me encanta apoyar este proyecto local. Los chavos son muy responsables con las entregas 
                    y se nota el amor que le ponen. Mis hijos ya no quieren otros huevos."
                </p>
                <p class="testimonial-author">- Roberto Martínez</p>
            </div>
            <div class="testimonial-card">
                <div class="stars">⭐⭐⭐⭐⭐</div>
                <p class="testimonial-text">
                    "La diferencia en la repostería es impresionante. Los pasteles quedan más esponjosos 
                    y el color es hermoso. Definitivamente son huevos de calidad superior."
                </p>
                <p class="testimonial-author">- Ana Herrera</p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="footer-content">
            <div class="footer-grid">
                <div class="footer-section">
                    <h3>Contacto</h3>
                    <p><i class="fas fa-phone"></i> +52 339 123 4567</p>
                    <p><i class="fas fa-envelope"></i> hola@raizypluma.com</p>
                    <p><i class="fas fa-map-marker-alt"></i> Ocotlán, Jalisco</p>
                </div>
                <div class="footer-section">
                    <h3>Horarios de Entrega</h3>
                    <p>Martes y Viernes</p>
                    <p>9:00 AM - 6:00 PM</p>
                    <p>Pedidos con 24h de anticipación</p>
                </div>
                <div class="footer-section">
                    <h3>Síguenos</h3>
                    <div class="social-links">
                        <a href="https://instagram.com/raizypluma" target="_blank">
                            <i class="fab fa-instagram"></i>
                        </a>
                        <a href="https://wa.me/523391234567" target="_blank">
                            <i class="fab fa-whatsapp"></i>
                        </a>
                        <a href="https://facebook.com/raizypluma" target="_blank">
                            <i class="fab fa-facebook"></i>
                        </a>
                    </div>
                    <p style="margin-top: 1rem; font-size: 0.9rem;">
                        Síguenos para ver a nuestras gallinas felices y recetas deliciosas
                    </p>
                </div>
            </div>
            <div style="border-top: 1px solid rgba(255,255,255,0.2); padding-top: 2rem; margin-top: 2rem;">
                <p>&copy; 2025 Raíz y Pluma. Hecho con amor para tu familia 💚</p>
                <p style="font-size: 0.9rem; margin-top: 0.5rem; opacity: 0.8;">
                    Comprometidos con el bienestar animal y la sostenibilidad
                </p>
            </div>
        </div>
    </footer>

    <!-- WhatsApp Floating Button -->
    <a href="https://wa.me/523391234567?text=¡Hola! Me interesa conocer más sobre los huevos de Raíz y Pluma 🥚" class="whatsapp-float" target="_blank">
        <i class="fab fa-whatsapp"></i>
    </a>

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

        // Intersection Observer for animations
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

        // Observe all sections
        document.querySelectorAll('section').forEach(section => {
            observer.observe(section);
        });

        // Header scroll effect
        window.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            if (window.scrollY > 100) {
                header.style.background = 'rgba(245, 241, 232, 0.98)';
                header.style.boxShadow = '0 2px 20px rgba(0,0,0,0.1)';
            } else {
                header.style.background = 'rgba(245, 241, 232, 0.95)';
                header.style.boxShadow = 'none';
            }
        });

        // Mobile menu toggle
        const mobileMenu = document.querySelector('.mobile-menu');
        const navLinks = document.querySelector('.nav-links');

        mobileMenu.addEventListener('click', () => {
            navLinks.classList.toggle('active');
            mobileMenu.classList.toggle('active');
        });

        // Add mobile menu styles
        const style = document.createElement('style');
        style.textContent = `
            @media (max-width: 768px) {
                .nav-links.active {
                    display: flex;
                    position: absolute;
                    top: 100%;
                    left: 0;
                    right: 0;
                    background: rgba(245, 241, 232, 0.98);
                    flex-direction: column;
                    padding: 2rem;
                    box-shadow: 0 5px 20px rgba(0,0,0,0.1);
                    backdrop-filter: blur(10px);
                }

                .mobile-menu.active span:nth-child(1) {
                    transform: rotate(45deg) translate(5px, 5px);
                }

                .mobile-menu.active span:nth-child(2) {
                    opacity: 0;
                }

                .mobile-menu.active span:nth-child(3) {
                    transform: rotate(-45deg) translate(7px, -6px);
                }
            }
        `;
        document.head.appendChild(style);

        // Add hover effects for cards
        const cards = document.querySelectorAll('.care-card, .product-card, .testimonial-card');
        cards.forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = this.classList.contains('product-card') 
                    ? 'translateY(-8px) scale(1.02)' 
                    : 'translateY(-5px)';
            });

            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) scale(1)';
            });
        });

        // WhatsApp button interaction
        const whatsappFloat = document.querySelector('.whatsapp-float');
        whatsappFloat.addEventListener('click', function() {
            // Add click effect
            this.style.transform = 'scale(0.95)';
            setTimeout(() => {
                this.style.transform = 'scale(1.1)';
            }, 100);
            setTimeout(() => {
                this.style.transform = 'scale(1)';
            }, 200);
        });

        // Add typing effect to hero subtitle
        const subtitle = document.querySelector('.hero-subtitle');
        const text = subtitle.textContent;
        subtitle.textContent = '';
        
        let i = 0;
        const typeWriter = () => {
            if (i < text.length) {
                subtitle.textContent += text.charAt(i);
                i++;
                setTimeout(typeWriter, 100);
            }
        };

        // Start typing effect after page load
        setTimeout(typeWriter, 2000);

        // Add parallax effect to hero section
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const hero = document.querySelector('.hero');
            const heroContent = document.querySelector('.hero-content');
            
            if (scrolled < window.innerHeight) {
                heroContent.style.transform = `translateY(${scrolled * 0.5}px)`;
                hero.style.opacity = 1 - scrolled / window.innerHeight;
            }
        });

        // Add stagger animation to feature lists
        const featureLists = document.querySelectorAll('.feature-list');
        featureLists.forEach(list => {
            const items = list.querySelectorAll('li');
            items.forEach((item, index) => {
                item.style.animationDelay = `${index * 0.1}s`;
                item.style.animation = 'fadeInUp 0.6s ease-out forwards';
                item.style.opacity = '0';
                item.style.transform = 'translateY(20px)';
            });
        });

        // Add floating animation to icons
        const icons = document.querySelectorAll('.care-icon, .product-icon');
        icons.forEach((icon, index) => {
            icon.style.animation = `float 3s ease-in-out infinite ${index * 0.5}s`;
        });

        // Add float keyframe animation
        const floatStyle = document.createElement('style');
        floatStyle.textContent = `
            @keyframes float {
                0%, 100% { transform: translateY(0px); }
                50% { transform: translateY(-10px); }
            }
        `;
        document.head.appendChild(floatStyle);

        // Add scroll progress indicator
        const progressBar = document.createElement('div');
        progressBar.style.cssText = `
            position: fixed;
            top: 0;
            left: 0;
            width: 0%;
            height: 3px;
            background: linear-gradient(90deg, var(--verde), var(--cafe));
            z-index: 9999;
            transition: width 0.3s ease;
        `;
        document.body.appendChild(progressBar);

        window.addEventListener('scroll', () => {
            const winScroll = document.body.scrollTop || document.documentElement.scrollTop;
            const height = document.documentElement.scrollHeight - document.documentElement.clientHeight;
            const scrolled = (winScroll / height) * 100;
            progressBar.style.width = scrolled + '%';
        });

        // Add loading animation
        window.addEventListener('load', () => {
            document.body.style.opacity = '0';
            document.body.style.transition = 'opacity 0.5s ease';
            setTimeout(() => {
                document.body.style.opacity = '1';
            }, 100);
        });

        // Easter egg: Konami code for special animation
        let konamiCode = [];
        const konamiSequence = [38, 38, 40, 40, 37, 39, 37, 39, 66, 65];
        
        document.addEventListener('keydown', (e) => {
            konamiCode.push(e.keyCode);
            if (konamiCode.length > konamiSequence.length) {
                konamiCode.shift();
            }
            
            if (konamiCode.join(',') === konamiSequence.join(',')) {
                // Special chicken animation
                const chicken = document.createElement('div');
                chicken.innerHTML = '🐔';
                chicken.style.cssText = `
                    position: fixed;
                    font-size: 3rem;
                    z-index: 10000;
                    pointer-events: none;
                    animation: chickenRun 3s linear;
                    top: 50%;
                    left: -100px;
                `;
                document.body.appendChild(chicken);
                
                const chickenAnimation = document.createElement('style');
                chickenAnimation.textContent = `
                    @keyframes chickenRun {
                        from { left: -100px; }
                        to { left: calc(100% + 100px); }
                    }
                `;
                document.head.appendChild(chickenAnimation);
                
                setTimeout(() => {
                    chicken.remove();
                    chickenAnimation.remove();
                }, 3000);
                
                konamiCode = [];
            }
        });
    </script>
</body>
</html>
