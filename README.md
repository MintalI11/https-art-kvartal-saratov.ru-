<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>АртКвартал | Платформа для творческих профессионалов</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary: #2a2a72;
            --secondary: #ffa400;
            --accent: #00b4d8;
            --dark: #1a1a2e;
            --light: #f8f9fa;
            --kandinsky-blue: #0d324d;
            --kandinsky-red: #ff3c38;
            --kandinsky-yellow: #ffd166;
        }

       {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--light);
            color: var(--dark);
            overflow-x: hidden;
        }

        .kandinsky-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.1;
            background: 
                radial-gradient(circle at 20% 30%, var(--kandinsky-blue), transparent 30%),
                radial-gradient(circle at 80% 20%, var(--kandinsky-red), transparent 30%),
                radial-gradient(circle at 30% 70%, var(--kandinsky-yellow), transparent 30%),
                linear-gradient(45deg, var(--primary), var(--accent));
        }

        header {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo h1 {
            font-size: 1.8rem;
            background: linear-gradient(45deg, var(--primary), var(--accent));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            font-weight: 800;
            letter-spacing: 1px;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: linear-gradient(45deg, var(--primary), var(--accent));
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
            font-size: 1.2rem;
        }

        nav ul {
            display: flex;
            gap: 20px;
            list-style: none;
        }

        nav a {
            text-decoration: none;
            color: var(--dark);
            font-weight: 600;
            padding: 8px 15px;
            border-radius: 20px;
            transition: all 0.3s ease;
        }

        nav a:hover, nav a.active {
            background: var(--primary);
            color: white;
        }

        .auth-buttons {
            display: flex;
            gap: 15px;
        }

        .btn {
            padding: 8px 20px;
            border-radius: 20px;
            border: none;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-outline {
            background: transparent;
            border: 2px solid var(--primary);
            color: var(--primary);
        }

        .btn-primary:hover {
            background: var(--accent);
            transform: translateY(-2px);
        }

        .btn-outline:hover {
            background: var(--primary);
            color: white;
            transform: translateY(-2px);
        }

        .hero {
            padding: 5rem 2rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .hero h2 {
            font-size: 3rem;
            margin-bottom: 1.5rem;
            background: linear-gradient(45deg, var(--primary), var(--accent), var(--secondary));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 2rem;
            color: var(--dark);
            line-height: 1.6;
        }

        .abstract-shapes {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            z-index: -1;
            opacity: 0.3;
        }

        .shape {
            position: absolute;
            border-radius: 50%;
        }

        .shape-1 {
            width: 200px;
            height: 200px;
            background: var(--kandinsky-blue);
            top: 10%;
            left: 5%;
            filter: blur(30px);
        }

        .shape-2 {
            width: 150px;
            height: 150px;
            background: var(--kandinsky-red);
            bottom: 15%;
            right: 10%;
            filter: blur(25px);
        }

        .shape-3 {
            width: 100px;
            height: 100px;
            background: var(--kandinsky-yellow);
            top: 50%;
            left: 30%;
            filter: blur(20px);
        }

        .tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 2rem;
            border-bottom: 2px solid #eee;
            padding-bottom: 10px;
        }

        .tab-btn {
            padding: 10px 25px;
            background: none;
            border: none;
            font-size: 1.1rem;
            font-weight: 600;
            color: #666;
            cursor: pointer;
            position: relative;
            transition: all 0.3s ease;
        }

        .tab-btn.active {
            color: var(--primary);
        }

        .tab-btn.active::after {
            content: '';
            position: absolute;
            bottom: -12px;
            left: 0;
            width: 100%;
            height: 3px;
            background: var(--primary);
            border-radius: 3px;
        }

        .tab-content {
            display: none;
            padding: 0 2rem;
        }

        .tab-content.active {
            display: block;
        }

        .portfolio-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 2rem;
        }

        .portfolio-item {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            transition: all 0.3s ease;
            position: relative;
        }

        .portfolio-item:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2);
        }

        .portfolio-img {
            height: 250px;
            background-size: cover;
            background-position: center;
        }

        .portfolio-info {
            padding: 20px;
        }

        .portfolio-info h3 {
            margin-bottom: 10px;
            color: var(--primary);
        }

        .portfolio-info p {
            color: #666;
            margin-bottom: 15px;
            font-size: 0.9rem;
            line-height: 1.5;
        }

        .portfolio-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .portfolio-rating {
            color: var(--secondary);
            font-weight: bold;
        }

        .portfolio-author {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .author-avatar {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            background: var(--accent);
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-weight: bold;
            font-size: 0.8rem;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .modal.active {
            display: flex;
            opacity: 1;
        }

        .modal-content {
            background: white;
            width: 80%;
            max-width: 900px;
            border-radius: 15px;
            overflow: hidden;
            position: relative;
            transform: scale(0.9);
            transition: transform 0.3s ease;
        }

        .modal.active .modal-content {
            transform: scale(1);
        }

        .modal-header {
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: var(--primary);
            color: white;
        }

        .modal-header h3 {
            font-size: 1.5rem;
        }

        .close-modal {
            background: none;
            border: none;
            color: white;
            font-size: 1.5rem;
            cursor: pointer;
        }

        .modal-body {
            display: flex;
            min-height: 400px;
        }

        .modal-image {
            flex: 1;
            min-height: 400px;
            background-size: cover;
            background-position: center;
        }

        .modal-details {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
            max-height: 400px;
        }

        .modal-details h4 {
            margin-bottom: 15px;
            color: var(--primary);
            font-size: 1.2rem;
        }

        .modal-details p {
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .modal-actions {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .projects-list {
            display: flex;
            flex-direction: column;
            gap: 20px;
            margin-top: 2rem;
        }

        .project-card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: all 0.3s ease;
        }

        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.1);
        }

        .project-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 15px;
        }

        .project-title {
            font-size: 1.2rem;
            color: var(--primary);
            font-weight: 600;
        }

        .project-budget {
            background: var(--secondary);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-weight: 600;
        }

        .project-description {
            margin-bottom: 15px;
            color: #555;
        }

        .project-meta {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .project-deadline {
            color: #777;
            font-size: 0.9rem;
        }

        .project-client {
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .client-rating {
            color: var(--secondary);
            font-weight: bold;
        }

        footer {
            background: var(--dark);
            color: white;
            padding: 3rem 2rem;
            margin-top: 5rem;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .footer-column h3 {
            font-size: 1.2rem;
            margin-bottom: 20px;
            color: var(--accent);
        }

        .footer-column ul {
            list-style: none;
        }

        .footer-column li {
            margin-bottom: 10px;
        }

        .footer-column a {
            color: #ddd;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .footer-column a:hover {
            color: var(--accent);
        }

        .social-links {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-links a {
            color: white;
            background: rgba(255, 255, 255, 0.1);
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: all 0.3s ease;
        }

        .social-links a:hover {
            background: var(--accent);
            transform: translateY(-3px);
        }

        .copyright {
            text-align: center;
            margin-top: 3rem;
            padding-top: 2rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #aaa;
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            header {
                flex-direction: column;
                gap: 20px;
                padding: 1rem;
            }

            nav ul {
                flex-wrap: wrap;
                justify-content: center;
            }

            .hero h2 {
                font-size: 2rem;
            }

            .modal-body {
                flex-direction: column;
            }

            .modal-image {
                min-height: 200px;
            }
        }
    </style>
</head>
<body>
    <div class="kandinsky-bg"></div>
    
    <header>
        <div class="logo">
            <div class="logo-icon">АК</div>
            <h1>АртКвартал</h1>
        </div>
        
        <nav>
            <ul>
                <li><a href="#" class="active">Главная</a></li>
                <li><a href="#">Рекомендации</a></li>
                <li><a href="#">Заказы</a></li>
                <li><a href="#">Рейтинги</a></li>
                <li><a href="#">О нас</a></li>
            </ul>
        </nav>
        
        <div class="auth-buttons">
            <button class="btn btn-outline">Вход</button>
            <button class="btn btn-primary">Регистрация</button>
        </div>
    </header>
    
    <section class="hero">
        <div class="abstract-shapes">
            <div class="shape shape-1"></div>
            <div class="shape shape-2"></div>
            <div class="shape shape-3"></div>
        </div>
        
        <h2>Творчество без границ</h2>
        <p>АртКвартал — это уникальная платформа, соединяющая талантливых дизайнеров с клиентами, которые ценят искусство и креативность. Найдите идеального исполнителя или покажите миру свои работы.</p>
        
        <div class="auth-buttons">
            <button class="btn btn-primary">Я дизайнер</button>
            <button class="btn btn-outline">Я заказчик</button>
        </div>
    </section>
    
    <section class="recommendations">
        <div class="tabs">
            <button class="tab-btn active" data-tab="designers">Работы дизайнеров</button>
            <button class="tab-btn" data-tab="projects">Активные заказы</button>
        </div>
        
        <div class="tab-content active" id="designers">
            <div class="portfolio-grid">
                <div class="portfolio-item">
                    <div class="portfolio-img" style="background-image: url('https://source.unsplash.com/random/600x400/?abstract,art')"></div>
                    <div class="portfolio-info">
                        <h3>Геометрическая абстракция</h3>
                        <p>Серия работ в стиле конструктивизма с элементами цифрового искусства. Идеально подойдет для современных интерьеров.</p>
                        <div class="portfolio-meta">
                            <div class="portfolio-rating">
                                <i class="fas fa-star"></i> 4.8
                            </div>
                            <div class="portfolio-author">
                                <div class="author-avatar">ИП</div>
                                <span>Иван Петров</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="portfolio-item">
                    <div class="portfolio-img" style="background-image: url('https://source.unsplash.com/random/600x400/?painting,modern')"></div>
                    <div class="portfolio-info">
                        <h3>Эмоции в цвете</h3>
                        <p>Экспрессивная серия картин, передающая всю гамму человеческих эмоций через цвет и форму.</p>
                        <div class="portfolio-meta">
                            <div class="portfolio-rating">
                                <i class="fas fa-star"></i> 4.9
                            </div>
                            <div class="portfolio-author">
                                <div class="author-avatar">АС</div>
                                <span>Анна Смирнова</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="portfolio-item">
                    <div class="portfolio-img" style="background-image: url('https://source.unsplash.com/random/600x400/?design,graphic')"></div>
                    <div class="portfolio-info">
                        <h3>Минимализм в деталях</h3>
                        <p>Современный дизайн с акцентом на функциональность и чистые линии. Подойдет для брендинга и упаковки.</p>
                        <div class="portfolio-meta">
                            <div class="portfolio-rating">
                                <i class="fas fa-star"></i> 4.7
                            </div>
                            <div class="portfolio-author">
                                <div class="author-avatar">ДК</div>
                                <span>Дмитрий Козлов</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="portfolio-item">
                    <div class="portfolio-img" style="background-image: url('https://source.unsplash.com/random/600x400/?illustration,digital')"></div>
                    <div class="portfolio-info">
                        <h3>Сказочные миры</h3>
                        <p>Серия цифровых иллюстраций для детских книг и игр. Яркие персонажи и запоминающиеся сюжеты.</p>
                        <div class="portfolio-meta">
                            <div class="portfolio-rating">
                                <i class="fas fa-star"></i> 4.6
                            </div>
                            <div class="portfolio-author">
                                <div class="author-avatar">ЕЛ</div>
                                <span>Елена Лебедева</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="portfolio-item">
                    <div class="portfolio-img" style="background-image: url('https://source.unsplash.com/random/600x400/?art,texture')"></div>
                    <div class="portfolio-info">
                        <h3>Текстуры и паттерны</h3>
                        <p>Коллекция уникальных текстур для использования в дизайне интерьеров, моде и цифровых продуктах.</p>
                        <div class="portfolio-meta">
                            <div class="portfolio-rating">
                                <i class="fas fa-star"></i> 4.5
                            </div>
                            <div class="portfolio-author">
                                <div class="author-avatar">МВ</div>
                                <span>Максим Воробьев</span>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div class="portfolio-item">
                    <div class="portfolio-img" style="background-image: url('https://source.unsplash.com/random/600x400/?abstract,colorful')"></div>
                    <div class="portfolio-info">
                        <h3>Цветовые эксперименты</h3>
                        <p>Смелые сочетания цветов и неожиданные формы. Каждая работа — это исследование возможностей цвета.</p>
                        <div class="portfolio-meta">
                            <div class="portfolio-rating">
                                <i class="fas fa-star"></i> 4.8
                            </div>
                            <div class="portfolio-author">
                                <div class="author-avatar">ОЗ</div>
                                <span>Ольга Зайцева</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="tab-content" id="projects">
            <div class="projects-list">
                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">Дизайн логотипа для кафе</div>
                        <div class="project-budget">15 000 ₽</div>
                    </div>
                    <div class="project-description">
                        Ищем дизайнера для создания логотипа нового кафе в центре города. Стиль — минимализм с элементами ар-деко. Цветовая гамма: золотой, черный, бежевый.
                    </div>
                    <div class="project-meta">
                        <div class="project-deadline">Срок: 2 недели</div>
                        <div class="project-client">
                            <div class="client-rating">
                                <i class="fas fa-star"></i> 4.9
                            </div>
                            <span>Кафе "Уют"</span>
                        </div>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">Иллюстрации для детской книги</div>
                        <div class="project-budget">45 000 ₽</div>
                    </div>
                    <div class="project-description">
                        Требуется художник для создания 10 полноцветных иллюстраций к детской книге о приключениях котенка. Стиль — мягкий, добрый, с элементами мультипликации.
                    </div>
                    <div class="project-meta">
                        <div class="project-deadline">Срок: 1 месяц</div>
                        <div class="project-client">
                            <div class="client-rating">
                                <i class="fas fa-star"></i> 4.7
                            </div>
                            <span>Издательство "Сказка"</span>
                        </div>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">Абстрактная картина для офиса</div>
                        <div class="project-budget">25 000 ₽</div>
                    </div>
                    <div class="project-description">
                        Ищем художника для создания большой абстрактной картины (120x80 см) для украшения офисного пространства. Предпочтительны синие и зеленые тона, динамичные формы.
                    </div>
                    <div class="project-meta">
                        <div class="project-deadline">Срок: 3 недели</div>
                        <div class="project-client">
                            <div class="client-rating">
                                <i class="fas fa-star"></i> 4.8
                            </div>
                            <span>IT-компания "ТехноЛогика"</span>
                        </div>
                    </div>
                </div>
                
                <div class="project-card">
                    <div class="project-header">
                        <div class="project-title">Упаковка для косметики</div>
                        <div class="project-budget">30 000 ₽</div>
                    </div>
                    <div class="project-description">
                        Необходимо разработать дизайн упаковки для линейки органической косметики. Стиль — эко, натуральные материалы, пастельные тона. Включает логотип, этикетки и коробки.
                    </div>
                    <div class="project-meta">
                        <div class="project-deadline">Срок: 4 недели</div>
                        <div class="project-client">
                            <div class="client-rating">
                                <i class="fas fa-star"></i> 4.6
                            </div>
                            <span>Бренд "Natural Beauty"</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
    
    <div class="modal" id="portfolio-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Геометрическая абстракция</h3>
                <button class="close-modal">&times;</button>
            </div>
            <div class="modal-body">
                <div class="modal-image" style="background-image: url('https://source.unsplash.com/random/800x600/?abstract,art')"></div>
                <div class="modal-details">
                    <h4>Описание работы</h4>
                    <p>Эта серия работ представляет собой исследование взаимодействия геометрических форм и цвета. Каждая композиция создана с учетом принципов золотого сечения и визуального баланса. Работа выполнена акрилом на холсте, размер 80x80 см.</p>
                    
                    <h4>Техника</h4>
                    <p>Акриловая живопись, цифровая обработка, смешанная техника. Использованы профессиональные материалы: холст на подрамнике, акриловые краски высокой пигментации.</p>
                    
                    <h4>О художнике</h4>
                    <p>Иван Петров — профессиональный художник с 10-летним опытом работы в области абстрактного искусства. Участник международных выставок, работы находятся в частных коллекциях по всему миру.</p>
                    
                    <div class="modal-actions">
                        <button class="btn btn-primary">
                            <i class="fas fa-envelope"></i> Написать сообщение
                        </button>
                        <button class="btn btn-outline">
                            <i class="fas fa-heart"></i> В избранное
                        </button>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <footer>
        <div class="footer-content">
            <div class="footer-column">
                <h3>АртКвартал</h3>
                <p>Платформа для творческих профессионалов и ценителей искусства. Соединяем таланты с возможностями.</p>
                <div class="social-links">
                    <a href="#"><i class="fab fa-vk"></i></a>
                    <a href="#"><i class="fab fa-telegram"></i></a>
                    <a href="#"><i class="fab fa-instagram"></i></a>
                    <a href="#"><i class="fab fa-behance"></i></a>
                </div>
            </div>
            
            <div class="footer-column">
                <h3>Разделы</h3>
                <ul>
                    <li><a href="#">Главная</a></li>
                    <li><a href="#">Рекомендации</a></li>
                    <li><a href="#">Заказы</a></li>
                    <li><a href="#">Рейтинги</a></li>
                    <li><a href="#">О нас</a></li>
                </ul>
            </div>
            
            <div class="footer-column">
                <h3>Помощь</h3>
                <ul>
                    <li><a href="#">Как это работает</a></li>
                    <li><a href="#">Частые вопросы</a></li>
                    <li><a href="#">Правила платформы</a></li>
                    <li><a href="#">Безопасность</a></li>
                    <li><a href="#">Контакты</a></li>
                </ul>
            </div>
            
            <div class="footer-column">
                <h3>Подписка</h3>
                <p>Будьте в курсе новых работ и заказов. Подпишитесь на нашу рассылку.</p>
                <form>
                    <input type="email" placeholder="Ваш email" style="padding: 10px; border-radius: 20px; border: none; width: 100%; margin-bottom: 10px;">
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Подписаться</button>
                </form>
            </div>
        </div>
        
        <div class="copyright">
            &copy; 2023 АртКвартал. Все права защищены.
        </div>
    </footer>
    
    <script>
        // Tab switching
        const tabBtns = document.querySelectorAll('.tab-btn');
        const tabContents = document.querySelectorAll('.tab-content');
        
        tabBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                const tabId = btn.getAttribute('data-tab');
                
                tabBtns.forEach(b => b.classList.remove('active'));
                tabContents.forEach(c => c.classList.remove('active'));
                
                btn.classList.add('active');
                document.getElementById(tabId).classList.add('active');
            });
        });
        
        // Portfolio item click
        const portfolioItems = document.querySelectorAll('.portfolio-item');
        const modal = document.getElementById('portfolio-modal');
        const closeModal = document.querySelector('.close-modal');
        
        portfolioItems.forEach(item => {
            item.addEventListener('click', () => {
                modal.classList.add('active');
                document.body.style.overflow = 'hidden';
            });
        });
        
        closeModal.addEventListener('click', () => {
            modal.classList.remove('active');
            document.body.style.overflow = 'auto';
        });
        
        // Close modal when clicking outside
        modal.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.classList.remove('active');
                document.body.style.overflow = 'auto';
            }
        });
        
        // Animate abstract shapes
        const shapes = document.querySelectorAll('.shape');
        
        function animateShapes() {
            shapes.forEach((shape, index) => {
                const speed = 0.5 + index * 0.2;
                const x = Math.sin(Date.now() / 1000 * speed) * 20;
                const y = Math.cos(Date.now() / 1000 * speed) * 20;
                
                shape.style.transform = `translate(${x}px, ${y}px)`;
            });
            
            requestAnimationFrame(animateShapes);
        }
        
        animateShapes();
    </script>
</body>
</html>


