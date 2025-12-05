<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Университеты Казахстана</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Шапка сайта */
        header {
            background: linear-gradient(135deg, #0032a0 0%, #0057b8 100%);
            color: white;
            padding: 20px 0;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo h1 {
            font-size: 24px;
            font-weight: 700;
        }

        .logo-icon {
            font-size: 32px;
        }

        /* Навигация */
        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-weight: 600;
            font-size: 18px;
            padding: 8px 12px;
            border-radius: 4px;
            transition: all 0.3s ease;
        }

        nav a:hover, nav a.active {
            background-color: rgba(255, 255, 255, 0.2);
        }

        /* Поиск */
        .search-container {
            margin: 30px 0;
            text-align: center;
        }

        .search-box {
            display: flex;
            max-width: 700px;
            margin: 0 auto;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
            border-radius: 50px;
            overflow: hidden;
        }

        .search-box input {
            flex-grow: 1;
            padding: 18px 25px;
            border: none;
            font-size: 18px;
            outline: none;
        }

        .search-box button {
            background-color: #ffd700;
            color: #0032a0;
            border: none;
            padding: 0 35px;
            cursor: pointer;
            font-size: 18px;
            font-weight: 600;
            transition: background-color 0.3s;
        }

        .search-box button:hover {
            background-color: #ffed4e;
        }

        /* Основной контент */
        main {
            padding: 20px 0 40px;
        }

        .section-title {
            font-size: 28px;
            color: #0032a0;
            margin-bottom: 25px;
            padding-bottom: 10px;
            border-bottom: 3px solid #ffd700;
            display: inline-block;
        }

        .news-section, .rating-section, .compare-section, .tour-section {
            margin-bottom: 50px;
        }

        /* Новости */
        .news-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 25px;
        }

        .news-card {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .news-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
        }

        .news-img {
            height: 200px;
            background-color: #ddd;
            background-size: cover;
            background-position: center;
        }

        .news-content {
            padding: 20px;
        }

        .news-title {
            font-size: 20px;
            margin-bottom: 10px;
            color: #0057b8;
        }

        .news-date {
            color: #666;
            font-size: 14px;
            margin-bottom: 15px;
        }

        /* Рейтинг */
        .rating-table {
            width: 100%;
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .rating-table table {
            width: 100%;
            border-collapse: collapse;
        }

        .rating-table th, .rating-table td {
            padding: 15px 20px;
            text-align: left;
        }

        .rating-table thead {
            background-color: #0032a0;
            color: white;
        }

        .rating-table tbody tr:nth-child(even) {
            background-color: #f8f9fa;
        }

        .rating-table tbody tr:hover {
            background-color: #e9f2ff;
        }

        .rank {
            display: inline-block;
            width: 30px;
            height: 30px;
            line-height: 30px;
            text-align: center;
            background-color: #ffd700;
            color: #0032a0;
            border-radius: 50%;
            font-weight: bold;
            margin-right: 10px;
        }

        /* Сравнение */
        .compare-container {
            background-color: white;
            border-radius: 10px;
            padding: 25px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .compare-controls {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin-bottom: 30px;
        }

        .university-select {
            flex-grow: 1;
            min-width: 300px;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
        }

        .compare-btn {
            background-color: #0032a0;
            color: white;
            border: none;
            padding: 12px 30px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: background-color 0.3s;
        }

        .compare-btn:hover {
            background-color: #0057b8;
        }

        .compare-results {
            display: none;
            grid-template-columns: repeat(2, 1fr);
            gap: 30px;
            margin-top: 20px;
        }

        .university-card {
            background-color: #f8f9fa;
            border-radius: 10px;
            padding: 20px;
            border-left: 5px solid #0032a0;
        }

        .university-name {
            font-size: 22px;
            color: #0032a0;
            margin-bottom: 15px;
        }

        /* 3D тур */
        .tour-container {
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .tour-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #0032a0;
            color: white;
            padding: 15px 25px;
        }

        .tour-select {
            padding: 10px;
            border-radius: 5px;
            border: none;
            font-size: 16px;
            min-width: 300px;
        }

        .tour-view {
            height: 500px;
            background-color: #222;
            display: flex;
            justify-content: center;
            align-items: center;
            color: white;
            font-size: 20px;
            position: relative;
        }

        .tour-placeholder {
            text-align: center;
        }

        .tour-icon {
            font-size: 80px;
            margin-bottom: 20px;
            color: #ffd700;
        }

        /* Подвал */
        footer {
            background-color: #0032a0;
            color: white;
            padding: 40px 0;
            margin-top: 40px;
        }

        .footer-content {
            display: flex;
            justify-content: space-between;
            flex-wrap: wrap;
            gap: 40px;
        }

        .footer-section h3 {
            font-size: 20px;
            margin-bottom: 20px;
            color: #ffd700;
        }

        .footer-links {
            list-style: none;
        }

        .footer-links li {
            margin-bottom: 10px;
        }

        .footer-links a {
            color: #ddd;
            text-decoration: none;
            transition: color 0.3s;
        }

        .footer-links a:hover {
            color: #ffd700;
        }

        .copyright {
            text-align: center;
            margin-top: 40px;
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            color: #aaa;
            font-size: 14px;
        }

        /* Адаптивность */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 20px;
            }
            
            nav ul {
                flex-wrap: wrap;
                justify-content: center;
                gap: 15px;
            }
            
            .news-grid {
                grid-template-columns: 1fr;
            }
            
            .compare-results {
                grid-template-columns: 1fr;
            }
            
            .tour-header {
                flex-direction: column;
                gap: 15px;
            }
            
            .tour-select {
                min-width: 100%;
            }
        }
    </style>
</head>
<body>
    <!-- Шапка сайта -->
    <header>
        <div class="container header-content">
            <div class="logo">
                <div class="logo-icon">
                    <i class="fas fa-university"></i>
                </div>
                <h1>Университеты Казахстана</h1>
            </div>
            <nav>
                <ul>
                    <li><a href="#news" class="active">Новости</a></li>
                    <li><a href="#rating">Рейтинг</a></li>
                    <li><a href="#compare">Сравнить</a></li>
                    <li><a href="#tour">3D Тур</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Поиск -->
    <div class="container search-container">
        <div class="search-box">
            <input type="text" placeholder="Введите название университета, специальность или город...">
            <button><i class="fas fa-search"></i> Найти</button>
        </div>
    </div>

    <!-- Основной контент -->
    <main class="container">
        <!-- Новости университетов -->
        <section id="news" class="news-section">
            <h2 class="section-title">Новости университетов Казахстана</h2>
            <div class="news-grid">
                <div class="news-card">
                    <div class="news-img" style="background-image: url('https://images.unsplash.com/photo-1523050854058-8df90110c9f1?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80');"></div>
                    <div class="news-content">
                        <h3 class="news-title">Назарбаев Университет открывает новые лаборатории</h3>
                        <p class="news-date">15 мая 2023</p>
                        <p>В рамках развития научного потенциала открыты 5 новых исследовательских лабораторий по направлениям биотехнологий и искусственного интеллекта.</p>
                    </div>
                </div>
                <div class="news-card">
                    <div class="news-img" style="background-image: url('https://images.unsplash.com/photo-1562774053-701939374585?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80');"></div>
                    <div class="news-content">
                        <h3 class="news-title">КазНУ им. Аль-Фараби подписал соглашение с европейскими вузами</h3>
                        <p class="news-date">10 мая 2023</p>
                        <p>Университет заключил договоры о двойных дипломах с тремя ведущими университетами Германии и Франции.</p>
                    </div>
                </div>
                <div class="news-card">
                    <div class="news-img" style="background-image: url('https://images.unsplash.com/photo-1541339907198-e08756dedf3f?ixlib=rb-1.2.1&auto=format&fit=crop&w=600&q=80');"></div>
                    <div class="news-content">
                        <h3 class="news-title">Студенты КБТУ победили на международной олимпиаде по робототехнике</h3>
                        <p class="news-date">5 мая 2023</p>
                        <p>Команда Карагандинского государственного технического университета заняла первое место на соревнованиях в Сингапуре.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Рейтинг университетов -->
        <section id="rating" class="rating-section">
            <h2 class="section-title">Рейтинг университетов Казахстана</h2>
            <div class="rating-table">
                <table>
                    <thead>
                        <tr>
                            <th>Место</th>
                            <th>Университет</th>
                            <th>Город</th>
                            <th>Баллы</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><span class="rank">1</span></td>
                            <td>Назарбаев Университет</td>
                            <td>Нур-Султан</td>
                            <td>98.7</td>
                        </tr>
                        <tr>
                            <td><span class="rank">2</span></td>
                            <td>КазНУ им. Аль-Фараби</td>
                            <td>Алматы</td>
                            <td>95.2</td>
                        </tr>
                        <tr>
                            <td><span class="rank">3</span></td>
                            <td>КБТУ</td>
                            <td>Алматы</td>
                            <td>92.8</td>
                        </tr>
                        <tr>
                            <td><span class="rank">4</span></td>
                            <td>Евразийский национальный университет</td>
                            <td>Нур-Султан</td>
                            <td>90.5</td>
                        </tr>
                        <tr>
                            <td><span class="rank">5</span></td>
                            <td>КазНТУ им. К. Сатпаева</td>
                            <td>Алматы</td>
                            <td>89.3</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <!-- Сравнение университетов -->
        <section id="compare" class="compare-section">
            <h2 class="section-title">Сравнить университеты</h2>
            <div class="compare-container">
                <div class="compare-controls">
                    <select class="university-select" id="uni1">
                        <option value="">Выберите первый университет</option>
                        <option value="nu">Назарбаев Университет</option>
                        <option value="kaznu">КазНУ им. Аль-Фараби</option>
                        <option value="kbtu">КБТУ</option>
                        <option value="enu">Евразийский национальный университет</option>
                        <option value="kazntu">КазНТУ им. К. Сатпаева</option>
                    </select>
                    <select class="university-select" id="uni2">
                        <option value="">Выберите второй университет</option>
                        <option value="nu">Назарбаев Университет</option>
                        <option value="kaznu">КазНУ им. Аль-Фараби</option>
                        <option value="kbtu">КБТУ</option>
                        <option value="enu">Евразийский национальный университет</option>
                        <option value="kazntu">КазНТУ им. К. Сатпаева</option>
                    </select>
                    <button class="compare-btn" onclick="compareUniversities()">Сравнить</button>
                </div>
                <div class="compare-results" id="compareResults">
                    <div class="university-card" id="uni1Card">
                        <h3 class="university-name">Университет 1</h3>
                        <p><strong>Город:</strong> <span id="uni1City">-</span></p>
                        <p><strong>Рейтинг:</strong> <span id="uni1Rating">-</span></p>
                        <p><strong>Год основания:</strong> <span id="uni1Year">-</span></p>
                        <p><strong>Количество студентов:</strong> <span id="uni1Students">-</span></p>
                        <p><strong>Проходной балл:</strong> <span id="uni1Score">-</span></p>
                    </div>
                    <div class="university-card" id="uni2Card">
                        <h3 class="university-name">Университет 2</h3>
                        <p><strong>Город:</strong> <span id="uni2City">-</span></p>
                        <p><strong>Рейтинг:</strong> <span id="uni2Rating">-</span></p>
                        <p><strong>Год основания:</strong> <span id="uni2Year">-</span></p>
                        <p><strong>Количество студентов:</strong> <span id="uni2Students">-</span></p>
                        <p><strong>Проходной балл:</strong> <span id="uni2Score">-</span></p>
                    </div>
                </div>
            </div>
        </section>

        <!-- 3D тур по университетам -->
        <section id="tour" class="tour-section">
            <h2 class="section-title">3D тур по университетам</h2>
            <div class="tour-container">
                <div class="tour-header">
                    <h3>Виртуальный тур по кампусам университетов</h3>
                    <select class="tour-select" onchange="changeTour()">
                        <option value="">Выберите университет для 3D тура</option>
                        <option value="nu">Назарбаев Университет</option>
                        <option value="kaznu">КазНУ им. Аль-Фараби</option>
                        <option value="kbtu">КБТУ</option>
                    </select>
                </div>
                <div class="tour-view">
                    <div class="tour-placeholder">
                        <div class="tour-icon">
                            <i class="fas fa-vr-cardboard"></i>
                        </div>
                        <p>Выберите университет из списка для запуска 3D тура</p>
                        <p>Используйте мышь для навигации по кампусу</p>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <!-- Подвал сайта -->
    <footer>
        <div class="container footer-content">
            <div class="footer-section">
                <h3>Университеты Казахстана</h3>
                <p>Информационный портал о высшем образовании в Республике Казахстан. Новости, рейтинги, сравнение и виртуальные туры по университетам.</p>
            </div>
            <div class="footer-section">
                <h3>Быстрые ссылки</h3>
                <ul class="footer-links">
                    <li><a href="#news">Новости</a></li>
                    <li><a href="#rating">Рейтинг</a></li>
                    <li><a href="#compare">Сравнение</a></li>
                    <li><a href="#tour">3D Тур</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Контакты</h3>
                <ul class="footer-links">
                    <li><i class="fas fa-envelope"></i> info@universities.kz</li>
                    <li><i class="fas fa-phone"></i> +7 (777) 123-45-67</li>
                    <li><i class="fas fa-map-marker-alt"></i> г. Нур-Султан, пр. Кабанбай батыра, 8</li>
                </ul>
            </div>
        </div>
        <div class="copyright container">
            <p>&copy; 2023 Университеты Казахстана. Все права защищены.</p>
        </div>
    </footer>

    <script>
        // Данные для сравнения университетов
        const universities = {
            nu: {
                name: "Назарбаев Университет",
                city: "Нур-Султан",
                rating: "98.7",
                year: "2010",
                students: "6000",
                score: "125"
            },
            kaznu: {
                name: "КазНУ им. Аль-Фараби",
                city: "Алматы",
                rating: "95.2",
                year: "1934",
                students: "20000",
                score: "105"
            },
            kbtu: {
                name: "КБТУ",
                city: "Алматы",
                rating: "92.8",
                year: "2001",
                students: "8000",
                score: "110"
            },
            enu: {
                name: "Евразийский национальный университет",
                city: "Нур-Султан",
                rating: "90.5",
                year: "1996",
                students: "16000",
                score: "100"
            },
            kazntu: {
                name: "КазНТУ им. К. Сатпаева",
                city: "Алматы",
                rating: "89.3",
                year: "1934",
                students: "18000",
                score: "98"
            }
        };

        // Функция сравнения университетов
        function compareUniversities() {
            const uni1Id = document.getElementById('uni1').value;
            const uni2Id = document.getElementById('uni2').value;
            const results = document.getElementById('compareResults');
            
            if (!uni1Id || !uni2Id) {
                alert('Пожалуйста, выберите оба университета для сравнения');
                return;
            }
            
            if (uni1Id === uni2Id) {
                alert('Пожалуйста, выберите разные университеты для сравнения');
                return;
            }
            
            // Заполняем данные для первого университета
            const uni1 = universities[uni1Id];
            document.getElementById('uni1Card').querySelector('.university-name').textContent = uni1.name;
            document.getElementById('uni1City').textContent = uni1.city;
            document.getElementById('uni1Rating').textContent = uni1.rating;
            document.getElementById('uni1Year').textContent = uni1.year;
            document.getElementById('uni1Students').textContent = uni1.students;
            document.getElementById('uni1Score').textContent = uni1.score;
            
            // Заполняем данные для второго университета
            const uni2 = universities[uni2Id];
            document.getElementById('uni2Card').querySelector('.university-name').textContent = uni2.name;
            document.getElementById('uni2City').textContent = uni2.city;
            document.getElementById('uni2Rating').textContent = uni2.rating;
            document.getElementById('uni2Year').textContent = uni2.year;
            document.getElementById('uni2Students').textContent = uni2.students;
            document.getElementById('uni2Score').textContent = uni2.score;
            
            // Показываем результаты сравнения
            results.style.display = 'grid';
            
            // Прокручиваем к результатам
            results.scrollIntoView({ behavior: 'smooth' });
        }

        // Функция изменения 3D тура
        function changeTour() {
            const tourSelect = document.querySelector('.tour-select');
            const tourView = document.querySelector('.tour-view');
            
            if (tourSelect.value) {
                const uni = universities[tourSelect.value];
                tourView.innerHTML = `
                    <div class="tour-placeholder">
                        <div class="tour-icon">
                            <i class="fas fa-university"></i>
                        </div>
                        <h3>3D тур по ${uni.name}</h3>
                        <p>Загрузка виртуального тура по кампусу...</p>
                        <div style="margin-top: 20px; width: 80%; height: 4px; background-color: #444; border-radius: 2px;">
                            <div style="width: 30%; height: 100%; background-color: #ffd700; border-radius: 2px;"></div>
                        </div>
                        <p style="margin-top: 30px;">Используйте мышь для осмотра по сторонам и колесико для перемещения</p>
                        <button style="margin-top: 20px; padding: 10px 25px; background-color: #ffd700; color: #0032a0; border: none; border-radius: 5px; font-weight: bold; cursor: pointer;">
                            <i class="fas fa-play"></i> Запустить тур в полном экране
                        </button>
                    </div>
                `;
            } else {
                tourView.innerHTML = `
                    <div class="tour-placeholder">
                        <div class="tour-icon">
                            <i class="fas fa-vr-cardboard"></i>
                        </div>
                        <p>Выберите университет из списка для запуска 3D тура</p>
                        <p>Используйте мышь для навигации по кампусу</p>
                    </div>
                `;
            }
        }

        // Плавная прокрутка по навигации
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                if (targetElement) {
                    // Обновляем активный элемент навигации
                    document.querySelectorAll('nav a').forEach(a => a.classList.remove('active'));
                    this.classList.add('active');
                    
                    // Прокручиваем к цели
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
