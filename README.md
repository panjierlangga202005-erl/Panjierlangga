<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PanjiErlangga</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
	<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
	<link rel="preload" href="https://i.pinimg.com/1200x/55/c6/e6/55c6e6b947eeda67b1bfa761c1013663.jpg" as="image">
	<meta name="theme-color" content="#0f172a">
    
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Poppins', sans-serif; }
        body {
            background: url("https://i.pinimg.com/1200x/55/c6/e6/55c6e6b947eeda67b1bfa761c1013663.jpg") no-repeat center center fixed;
            background-size: cover;
            color: #ffffff;
        }
        .overlay { min-height: 100vh; display: flex; flex-direction: column; background: rgba(255, 255, 255, 0.2); }
        
        nav { 
            display: flex; 
            justify-content: space-between; 
            align-items: center; 
            background: rgba(15, 23, 42, 0.9); 
            padding: 15px 40px; 
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3); 
            position: sticky; 
            top: 0; 
            z-index: 100; 
            flex-wrap: wrap; 
            gap: 10px; 
        }
        .nav-left { display: flex; gap: 20px; flex-wrap: wrap; }
        .nav-right { display: flex; gap: 10px; align-items: center; }
        .nav-left a, .nav-right a { color: #ffffff; text-decoration: none; font-weight: 600; font-size: 1rem; transition: 0.3s; padding-bottom: 5px; cursor: pointer; }
        .nav-right a { background: #ffd700; color: #0f172a; padding: 8px 20px; border-radius: 5px; }
        .nav-left a:hover, .nav-left a.active { color: #ffd700; border-bottom: 2px solid #ffd700; }
        .nav-right a:hover { background: #e6c200; }
        
        .container { background: rgba(15, 23, 42, 0.85); backdrop-filter: blur(1px); max-width: 800px; margin: 40px auto; padding: 40px; border-radius: 15px; box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5); flex-grow: 1; width: 90%; }
        
        .section { display: none; animation: fadeIn 0.4s ease-in-out; }
        .section.active { display: block; }
        @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
        
        h1, h2 { color: #ffd700; margin-bottom: 15px; text-align: center; }
        .tagline { text-align: center; font-size: 1.1rem; margin-bottom: 20px; }
        hr { border: 0; height: 1px; background: #334155; margin: 20px 0; }
        
        /* Dashboard Links */
        .link-box { text-align: center; margin-top: 25px; }
        .link-box a { 
            display: inline-block; margin: 10px; color: #ffd700; font-size: 1.1rem; text-decoration: none; 
            padding: 15px 25px; border: 2px solid #ffd700; border-radius: 8px; transition: all 0.3s; 
            font-weight: 600;
        }
        .link-box a:hover { background: rgba(255, 215, 0, 0.2); transform: translateY(-2px); }
        
        .video-box { text-align: center; margin-top: 40px; }
        .video-box iframe { border-radius: 15px; box-shadow: 0 10px 30px rgba(0,0,0,0.5); max-width: 100%; }
        
        /* Katalog */
        .search-box { text-align: center; margin-bottom: 20px; }
        .search-box input { width: 100%; padding: 12px 20px; border: none; border-radius: 8px; font-size: 1rem; outline: none; }
        #bookList { list-style: none; }
        #bookList li { background: rgba(255, 255, 255, 0.1); margin-bottom: 10px; padding: 15px; border-radius: 8px; transition: 0.3s; cursor: pointer; }
        #bookList li:hover { background: rgba(255, 255, 255, 0.2); transform: translateX(5px); }
        
        /* Kegiatan - FIXED CSS */
		.activities-list {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            padding: 0;
        }

        .activity-item {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
            transition: all 0.4s ease;
            cursor: pointer;
            border: 1px solid rgba(255, 215, 0, 0.2);
            position: relative;
        }

        .activity-item::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(135deg, rgba(255,215,0,0.1), transparent);
            opacity: 0;
            transition: opacity 0.4s ease;
            z-index: 1;
        }

        .activity-item:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(255,215,0,0.3);
            border-color: #ffd700;
        }

        .activity-item:hover::before {
            opacity: 1;
        }

        .activity-image {
            width: 100%;
            height: 220px;
            object-fit: cover;
            transition: transform 0.4s ease;
        }

        .activity-item:hover .activity-image {
            transform: scale(1.1);
        }

        .activity-content {
            padding: 25px;
            position: relative;
            z-index: 2;
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(10px);
        }

        .activity-icon {
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #ffd700, #ffed4a);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.8rem;
            margin-bottom: 15px;
            box-shadow: 0 8px 20px rgba(255,215,0,0.4);
        }

        .activity-title {
            color: #ffd700;
            font-size: 1.4rem;
            font-weight: 600;
            margin-bottom: 10px;
            line-height: 1.3;
        }

        .activity-date {
            color: #94a3b8;
            font-size: 0.95rem;
            margin-bottom: 12px;
            font-weight: 500;
        }

        .activity-desc {
            color: #cbd5e1;
            line-height: 1.6;
            margin-bottom: 20px;
            font-size: 0.98rem;
        }

        .activity-btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: linear-gradient(135deg, #ffd700, #ffed4a);
            color: #0f172a;
            padding: 12px 25px;
            border-radius: 25px;
            text-decoration: none;
            font-weight: 600;
            font-size: 0.95rem;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(255,215,0,0.4);
        }

        .activity-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(255,215,0,0.6);
            color: #0f172a;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .activities-list {
                grid-template-columns: 1fr;
                gap: 20px;
            }
            
            .activity-content {
                padding: 20px;
            }
        }
        
        .modal {
            display: none;
            position: fixed;
            z-index: 1000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(5px);
        }

        .modal-content {
            position: relative;
            margin: 5% auto;
            max-width: 90%;
            max-height: 90%;
            background: rgba(15, 23, 42, 0.95);
            backdrop-filter: blur(15px);
            border-radius: 20px;
            box-shadow: 0 25px 50px rgba(0,0,0,0.8);
            animation: modalSlideIn 0.4s ease-out;
            overflow: hidden;
        }

        @keyframes modalSlideIn {
            from {
                opacity: 0;
                transform: scale(0.8) translateY(-50px);
            }
            to {
                opacity: 1;
                transform: scale(1) translateY(0);
            }
        }

        .modal-image {
            width: 100%;
            height: 300px;
            object-fit: cover;
        }

        .modal-body {
            padding: 30px;
            color: #ffffff;
        }

        .modal-title {
            color: #ffd700;
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 15px;
            text-align: center;
        }

        .modal-date {
            background: rgba(255, 215, 0, 0.2);
            color: #ffd700;
            padding: 10px 20px;
            border-radius: 25px;
            display: inline-block;
            font-weight: 600;
            margin-bottom: 20px;
            font-size: 1rem;
        }

        .modal-description {
            line-height: 1.7;
            color: #cbd5e1;
            font-size: 1.05rem;
            margin-bottom: 25px;
        }

        .modal-close {
            position: absolute;
            top: 20px;
            right: 25px;
            color: #ffd700;
            font-size: 2.5rem;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            z-index: 1001;
        }

        .modal-close:hover {
            color: #ffffff;
            transform: rotate(90deg) scale(1.1);
        }

        @media (max-width: 768px) {
            .modal-content {
                margin: 10% auto;
                max-width: 95%;
            }
            
            .modal-image {
                height: 250px;
            }
            
            .modal-body {
                padding: 25px 20px;
            }
        }
        
        
        .form-container { max-width: 400px; margin: 0 auto; }
        form { display: flex; flex-direction: column; width: 100%; }
        form label { margin-bottom: 5px; font-size: 0.9rem; color: #cbd5e1; }
        form input, form textarea, form select { padding: 12px; margin-bottom: 15px; border: none; border-radius: 5px; font-size: 1rem; outline: none; font-family: 'Poppins', sans-serif; background: rgba(255,255,255,0.1); color: white; }
        form input::placeholder, form textarea::placeholder { color: #94a3b8; }
        form button { padding: 12px; background: #ffd700; color: #0f172a; border: none; border-radius: 5px; font-weight: bold; font-size: 1rem; cursor: pointer; transition: 0.3s; }
        form button:hover { background: #e6c200; }
        
        /* Contact Card - VERTICAL LAYOUT */
        .contact-card { 
            background: rgba(255, 255, 255, 0.1); 
            padding: 25px; 
            border-radius: 10px; 
            margin-bottom: 30px; 
            border-left: 4px solid #ffd700; 
        }
        .contact-info { 
            display: flex; 
            flex-direction: column; 
            gap: 30px; 
            margin-bottom: 0; 
        }
        .contact-item { 
            display: flex; 
            align-items: center; 
			flex-direction: column;
            gap: 20px; 
            padding: 30px; 
            background: rgba(255,255,255,0.05); 
            border-radius: 15px; 
            text-align: center; 
        }	
        .contact-item strong { 
            color: #ffd700; 
            font-size: 1.1rem; 
            min-width: 300px; 
		}
        
        /* Footer */
       .main-footer {
            background: #0f172a;
            color: #ffd700;
            padding: 60px 0 30px;
            font-family: 'Poppins', sans-serif;
            border-top: 4px solid #38bdf8;
            margin-top: auto;
        }

        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            padding: 0 20px;
        }

        .footer-column {
            color: #cbd5e1;
        }

        .footer-column h4 {
            color: white;
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
        }

        .footer-column h4::after {
            content: '';
            width: 30px;
            height: 2px;
            background: #ffd700;
            position: absolute;
            bottom: -10px;
            left: 0;
        }

        .jam-operasional p {
            margin: 5px 0;
            font-size: 0.95rem;
        }

        .social-box {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-box a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 45px;
            height: 45px;
            background: rgba(255, 215, 0, 0.2);
            color: #ffd700;
            border-radius: 50%;
            font-size: 1.2rem;
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .social-box a:hover {
            background: #ffd700;
            color: #0f172a;
            transform: translateY(-3px);
        }

        .footer-bottom {
            text-align: center;
            margin-top: 50px;
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.1);
            font-size: 0.85rem;
            color: #64748b;
        }
    </style>
</head>
<body>

<div class="overlay">

<nav>
    <div class="nav-left">
        <a onclick="showMenu('dashboard', this)" class="active">Dashboard</a>
        <a onclick="showMenu('katalog', this)">Katalog</a>
        <a onclick="showMenu('kegiatan', this)">Kegiatan</a>
        <a onclick="showMenu('contact', this)">Contact</a>
    </div>
    <div class="nav-right">
        <a onclick="showMenu('login', this)">Login</a>
        <a onclick="showMenu('daftar', this)">Daftar</a>
    </div>
</nav>

<div class="container">
    
    <!-- DASHBOARD -->
    <div id="dashboard" class="section active">
        <h1>Library Panji</h1>
        <p class="tagline">Welcome to my profile</p>
        
        <div class="link-box">
            <a href="https://www.facebook.com/panji.erlangga.77" target="_blank">
                📘 Look at Me
            </a>
            <a href="https://drive.google.com/drive/folders/1KyE7ubNtW2E0yUoDRS_2pGuJB3SHfi4f" target="_blank">
                📁 Profile
            </a>
        </div>

        <div class="video-box">
            <h3>Best Video</h3>
            <iframe 
                width="560" 
                height="315" 
                src="https://www.youtube.com/embed/NWQ13Y4G0fw"
                title="YouTube Video" 
                frameborder="0" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen>
            </iframe>
        </div>
    </div>

    <!-- KATALOG -->
    <div id="katalog" class="section">
        <h2>Daftar Buku Perpustakaan</h2>
        <div class="search-box">
            <input type="text" id="searchInput" onkeyup="searchBooks()" placeholder="Cari buku perpustakaan...">
        </div>
        <ul id="bookList">
            <li>Pengantar Ilmu Perpustakaan</li>
            <li>Dasar-dasar Perpustakaan</li>
            <li>Manajemen Perpustakaan</li>
            <li>Pengembangan Koleksi Perpustakaan</li>
            <li>Layanan Perpustakaan</li>
        </ul>
    </div>

    <!-- KEGIATAN LITERASI -->
     <div id="kegiatan" class="section">
    <h2>Kegiatan/Event</h2>
    <p style="text-align: center; color: #cbd5e1; margin-bottom: 40px; font-size: 1.1rem;">
        Ikuti berbagai kegiatan menarik seputar perpustakaan
    </p>
    
    <div class="activities-list">
        
        
        <div class="activity-item" onclick="openModal(https://i.pinimg.com/736x/58/cd/c0/58cdc0f47523bdbf78768f8fa019377a.jpg), 'Seminar perkembangan perpustakaan', 'Selasa, 26 Agustus 2025 | 08.30-Selesai', 'Foto seminar perkembangan perpustakaan bertema "perkembangan">
            <img src="https://i.pinimg.com/736x/58/cd/c0/58cdc0f47523bdbf78768f8fa019377a.jpg" 
                 alt="Seminar perkembangan perpustakaan" class="activity-image">
            <div class="activity-content">
                <div class="activity-icon">📚</div>
                <div class="activity-title">Seminar perkembangan perpustakaan</div>
                <div class="activity-date">
                    <i class="fas fa-calendar-alt"></i> Selasa, 26 Agustus 2025 | 08.30-Selesai
                </div>
                <p class="activity-desc">
                    Dalam rangka pengembangan koleksi fisik menjadi koleksi digital dan menambah koleksi buku menjadi lebih banyak lagi.
                </p>
                <a href="#" class="activity-btn">
                    <i class="fas fa-arrow-right"></i> Info Lengkap
                </a>
            </div>
        </div>
        
        
        <div class="activity-item" onclick="openModal(https://i.pinimg.com/736x/74/e6/a9/74e6a93a7d2bd32b5c611131e51f1fd7.jpg', 'workshop - Pworkshop literasi 2026', '9-10 Februari 2026 | 10:00 - 14:00 WIB', 'Poster kegiatan workshop 2026 bertema "workshop literasi)">
            <img src="https://i.pinimg.com/736x/74/e6/a9/74e6a93a7d2bd32b5c611131e51f1fd7.jpg" 
                 alt="workshop literasi" class="activity-image">
            <div class="activity-content">
                <div class="activity-icon">👥</div>
                <div class="activity-title">workshop literasi</div>
                <div class="activity-date">
                    <i class="fas fa-calendar-alt"></i> 9-10 Februari 2026 | 10:00 - 14:00 WIB
                </div>
                <p class="activity-desc">
                    Dalam rangka penjelasan materi mengenai literasi di perpustakaan yang di mana pemateri memberikan penjelasan bagaimana anggota perpustakaan harus literasi dalam kebutuhan pengguna".
                </p>
                <a href="#" class="activity-btn">
                    <i class="fas fa-info-circle"></i> Info Lengkap
                </a>
            </div>
        </div>
        
        
        <div class="activity-item" onclick="openModal(https://i.pinimg.com/1200x/15/da/4c/15da4c9fe120269a5632098d6bd0e8f2.jpg, 'dies natalis perpustakaan', 'Senin, 30 Maret 2026 | 10:00 - 15:00 WIB', 'Foto dies natalis perpustakaan)">
            <img src="https://i.pinimg.com/1200x/15/da/4c/15da4c9fe120269a5632098d6bd0e8f2.jpg" 
                 alt="Simulasi Peradilan" class="activity-image">
            <div class="activity-content">
                <div class="activity-icon">⚖️</div>
                <div class="activity-title">dies natalis perpustakaan</div>
                <div class="activity-date">
                    <i class="fas fa-calendar-alt"></i> Senin, 30 Maret 2026 | 10:00 - 15:00 WIB
                </div>
                <p class="activity-desc">
                    Memeperingati hari terdirinya perpustakaan yang di mana hari tersebutlah berperosesnya perpustakaan menjadi sebaik mungkin 
                </p>
                <a href="#" class="activity-btn">
                    <i class="fas fa-arrow-right"></i> Info Lengkap
                </a>
            </div>
        </div>
    </div>

         <!-- CONTACT -->
    <div id="contact" class="section">
        <h2>Contact Pemilik</h2>
        
        <div class="contact-card">
            <div class="contact-item">
                <i class="fas fa-user"></i>
                <strong>Panji Erlangga</strong>
            </div>
            <div class="contact-item">
                <i class="fas fa-envelope"></i>
                <strong>panjierlangga202005@gmail.com</strong>
            </div>
            <div class="contact-item">
          { max-width: 400px; margin: 0 auto; }
        form { display: flex; flex-direction: column; width: 100%; }
        form label { margin-bottom: 5px; font-size: 0.9rem; color: #cbd5e1; }
        form input, form textarea, form select { padding: 12px; margin-bottom: 15px; border: none; border-radius: 5px; font-size: 1rem; outline: none; font-family: 'Poppins', sans-serif; background: rgba(255,255,255,0.1); color: white; }
        form input::placeholder, form textarea::placeholder { color: #94a3b8; }
        form button { padding: 12px; background: #ffd700; color: #0f172a; border: none; border-radius: 5px; font-weight: bold; font-size: 1rem; cursor: pointer; transition: 0.3s; }
        form button:hover { background: #e6c200; }
        
        /* Contact Card - VERTICAL LAYOUT */
        .contact-card { 
            background: rgba(255, 255, 255, 0.1); 
            padding: 25px; 
            border-radius: 10px; 
            margin-bottom: 30px; 
            border-left: 4px solid #ffd700; 
        }
        .contact-info { 
            display: flex; 
            flex-direction: column; 
            gap: 30px; 
            margin-bottom: 0; 
        }
        .contact-item { 
            display: flex; 
            align-items: center; 
			flex-direction: column;
            gap: 20px; 
            padding: 30px; 
            background: rgba(255,255,255,0.05); 
            border-radius: 15px; 
            text-align: center; 
        }	
        .contact-item strong { 
            color: #ffd700; 
            font-size: 1.1rem; 
            min-width: 300px; 
		}
        
        /* Footer */
       .main-footer {
            background: #0f172a;
            color: #ffd700;
            padding: 60px 0 30px;
            font-family: 'Poppins', sans-serif;
            border-top: 4px solid #38bdf8;
            margin-top: auto;
        }

        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 40px;
            padding: 0 20px;
        }

        .footer-column {
            color: #cbd5e1;
        }

        .footer-column h4 {
            color: white;
            margin-bottom: 20px;
            position: relative;
            display: inline-block;
        }

        .footer-column h4::after {
            content: '';
            width: 30px;
            height: 2px;
            background: #ffd700;
            position: absolute;
            bottom: -10px;
            left: 0;
        }

        .jam-operasional p {
            margin: 5px 0;
            font-size: 0.95rem;
        }

        .social-box {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .social-box a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 45px;
            height: 45px;
            background: rgba(255, 215, 0, 0.2);
            color: #ffd700;
            border-radius: 50%;
            font-size: 1.2rem;
            transition: all 0.3s ease;
            text-decoration: none;
        }

        .social-box a:hover {
            background: #ffd700;
            color: #0f172a;
            transform: translateY(-3px);
        }

        .footer-bottom {
            text-align: center;
            margin-top: 50px;
            padding-top: 20px;
            border-top: 1px solid rgba(255,255,255,0.1);
            font-size: 0.85rem;
            color: #64748b;
        }
    </style>
</head>
<body>

<div class="overlay">

<nav>
    <div class="nav-left">
        <a onclick="showMenu('dashboard', this)" class="active">Dashboard</a>
        <a onclick="showMenu('katalog', this)">Katalog</a>
        <a onclick="showMenu('kegiatan', this)">Kegiatan</a>
        <a onclick="showMenu('contact', this)">Contact</a>
    </div>
    <div class="nav-right">
        <a onclick="showMenu('login', this)">Login</a>
        <a onclick="showMenu('daftar', this)">Daftar</a>
    </div>
</nav>

<div class="container">
    
    <!-- DASHBOARD -->
    <div id="dashboard" class="section active">
        <h1>Library Panji</h1>
        <p class="tagline">Welcome to my profile</p>
        
        <div class="link-box">
            <a href="https://www.facebook.com/panji.erlangga.77" target="_blank">
                📘 Look at Me
            </a>
            <a href="https://drive.google.com/drive/folders/1KyE7ubNtW2E0yUoDRS_2pGuJB3SHfi4f" target="_blank">
                📁 Profile
            </a>
        </div>

        <div class="video-box">
            <h3>Best Video</h3>
            <iframe 
                width="560" 
                height="315" 
                src="https://www.youtube.com/embed/NWQ13Y4G0fw"
                title="YouTube Video" 
                frameborder="0" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen>
            </iframe>
        </div>
    </div>

    <!-- KATALOG -->
    <div id="katalog" class="section">
        <h2>Daftar Buku Perpustakaan</h2>
        <div class="search-box">
            <input type="text" id="searchInput" onkeyup="searchBooks()" placeholder="Cari buku perpustakaan...">
        </div>
        <ul id="bookList">
            <li>Pengantar Ilmu Perpustakaan</li>
            <li>Dasar-dasar Perpustakaan</li>
            <li>Manajemen Perpustakaan</li>
            <li>Pengembangan Koleksi Perpustakaan</li>
            <li>Layanan Perpustakaan</li>
        </ul>
    </div>

    <!-- KEGIATAN LITERASI -->
     <div id="kegiatan" class="section">
    <h2>Kegiatan/Event</h2>
    <p style="text-align: center; color: #cbd5e1; margin-bottom: 40px; font-size: 1.1rem;">
        Ikuti berbagai kegiatan menarik seputar perpustakaan
    </p>
    
    <div class="activities-list">
        
        
        <div class="activity-item" onclick="openModal(https://i.pinimg.com/736x/58/cd/c0/58cdc0f47523bdbf78768f8fa019377a.jpg), 'Seminar perkembangan perpustakaan', 'Selasa, 26 Agustus 2025 | 08.30-Selesai', 'Foto seminar perkembangan perpustakaan bertema "perkembangan">
            <img src="https://i.pinimg.com/736x/58/cd/c0/58cdc0f47523bdbf78768f8fa019377a.jpg" 
                 alt="Seminar perkembangan perpustakaan" class="activity-image">
            <div class="activity-content">
                <div class="activity-icon">📚</div>
                <div class="activity-title">Seminar perkembangan perpustakaan</div>
                <div class="activity-date">
                    <i class="fas fa-calendar-alt"></i> Selasa, 26 Agustus 2025 | 08.30-Selesai
                </div>
                <p class="activity-desc">
                    Dalam rangka pengembangan koleksi fisik menjadi koleksi digital dan menambah koleksi buku menjadi lebih banyak lagi.
                </p>
                <a href="#" class="activity-btn">
                    <i class="fas fa-arrow-right"></i> Info Lengkap
                </a>
            </div>
        </div>
        
        
        <div class="activity-item" onclick="openModal(https://i.pinimg.com/736x/74/e6/a9/74e6a93a7d2bd32b5c611131e51f1fd7.jpg', 'workshop - Pworkshop literasi 2026', '9-10 Februari 2026 | 10:00 - 14:00 WIB', 'Poster kegiatan workshop 2026 bertema "workshop literasi)">
            <img src="https://i.pinimg.com/736x/74/e6/a9/74e6a93a7d2bd32b5c611131e51f1fd7.jpg" 
                 alt="workshop literasi" class="activity-image">
            <div class="activity-content">
                <div class="activity-icon">👥</div>
                <div class="activity-title">workshop literasi</div>
                <div class="activity-date">
                    <i class="fas fa-calendar-alt"></i> 9-10 Februari 2026 | 10:00 - 14:00 WIB
                </div>
                <p class="activity-desc">
                    Dalam rangka penjelasan materi mengenai literasi di perpustakaan yang di mana pemateri memberikan penjelasan bagaimana anggota perpustakaan harus literasi dalam kebutuhan pengguna".
                </p>
                <a href="#" class="activity-btn">
                    <i class="fas fa-info-circle"></i> Info Lengkap
                </a>
            </div>
        </div>
        
        
        <div class="activity-item" onclick="openModal(https://i.pinimg.com/1200x/15/da/4c/15da4c9fe120269a5632098d6bd0e8f2.jpg, 'dies natalis perpustakaan', 'Senin, 30 Maret 2026 | 10:00 - 15:00 WIB', 'Foto dies natalis perpustakaan)">
            <img src="https://i.pinimg.com/1200x/15/da/4c/15da4c9fe120269a5632098d6bd0e8f2.jpg" 
                 alt="Simulasi Peradilan" class="activity-image">
            <div class="activity-content">
                <div class="activity-icon">⚖️</div>
                <div class="activity-title">dies natalis perpustakaan</div>
                <div class="activity-date">
                    <i class="fas fa-calendar-alt"></i> Senin, 30 Maret 2026 | 10:00 - 15:00 WIB
                </div>
                <p class="activity-desc">
                    Memeperingati hari terdirinya perpustakaan yang di mana hari tersebutlah berperosesnya perpustakaan menjadi sebaik mungkin 
                </p>
                <a href="#" class="activity-btn">
                    <i class="fas fa-arrow-right"></i> Info Lengkap
                </a>
            </div>
        </div>
    </div>

<!-- LOGIN -->
    <div id="login" class="section">
        <h2>Login Anggota</h2>
        <div class="form-container">
            <form onsubmit="event.preventDefault(); alert('Login berhasil! Selamat datang di Library Panji.'); showMenu('dashboard', document.querySelector('.nav-left a'));">
                <label>Username</label>
                <input type="text" placeholder="Masukkan username" required>
                <label>Password</label>
                <input type="password" placeholder="Masukkan kata sandi" required>
                <label>Status Pengguna</label>
                <select required>
                    <option value="">Pilih status</option>
                    <option value="anggota">Anggota</option>
                    <option value="admin">Admin</option>
                </select>
                <button type="submit">MASUK</button>
            </form>
        </div>
    </div>

        <h2>Kirim Pesan</h2>
        <div class="form-container">
            <form onsubmit="event.preventDefault(); alert('Pesan berhasil dikirim! Terima kasih Panji Erlangga.'); this.reset();">
                <label>Nama</label>
                <input type="text" placeholder="Masukkan nama Anda" required>
                <label>Email</label>
                <input type="email" placeholder="Masukkan email Anda" required>
                <label>Pesan</label>
                <textarea rows="5" placeholder="Tulis pesan Anda di sini..." required></textarea>
                <button type="submit">KIRIM PESAN</button>
            </form>
        </div>
    </div>

</div>

<!-- FOOTER -->
<footer class="main-footer">
    <div class="footer-container">
        <div class="footer-column">
            <h3>Library Panji</h3>
            <p>Perpustakaan Digital - Katalog Perpustakaan</p>
            <div style="margin-top: 15px;">
                <p><strong><i class="fas fa-clock"></i> Jam Operasional:</strong></p>
                <p>Senin - Jumat: 08:00 - 17:00 WIB</p>
                <p>Sabtu: 09:00 - 14:00 WIB</p>
                <p>Minggu: Tutup</p>
            </div>
        </div>

        <div class="footer-column">
            <h3>Hubungi Kami</h3>
            <p><i class="fas fa-envelope"></i> panjierlangga202005@gmail.com</p>
            <p><i class="fas fa-phone"></i> 082267523213</p>
            <p><i class="fas fa-map-marker-alt"></i> Medan, Sumatera Utara, Indonesia</p>
            <div style="margin-top: 15px; display: flex; gap: 15px; justify-content: center;">
                <a href="https://www.facebook.com/panji.erlangga.77" target="_blank" style="width: 45px; height: 45px; background: rgba(255, 215, 0, 0.2); color: #ffd700; border-radius: 50%; display: flex; align-items: center; justify-content: center; text-decoration: none; font-size: 1.2rem; transition: all 0.3s;">
                    <i class="fab fa-facebook-f"></i>
                </a>
                <a href="#" style="width: 45px; height: 45px; background: rgba(255, 215, 0, 0.2); color: #ffd700; border-radius: 50%; display: flex; align-items: center; justify-content: center; text-decoration: none; font-size: 1.2rem; transition: all 0.3s;">
                    <i class="fab fa-whatsapp"></i>
                </a>
            </div>
        </div>
    </div>
    <div class="footer-bottom">
        <p>&copy; 2026 PanjiErlangga. All Rights Reserved.</p>
    </div>
</footer>

</div> 

<script>
functionshowMenu(menuId, clickedElement) {
    document.querySelectorAll('.section').forEach(section => {
        section.classList.remove('active');
    });
    constselectedSection = document.getElementById(menuId);
    if (selectedSection) selectedSection.classList.add('active');
    
    if (clickedElement && clickedElement.tagName === 'A') {
        document.querySelectorAll('nav a').forEach(a => a.classList.remove('active'));
        clickedElement.classList.add('active');
    }
    window.scrollTo({ top: 0, behavior: 'smooth' });
}

functionsearchBooks() {
    letinput = document.getElementById('searchInput').value.toLowerCase();
    letli = document.getElementById('bookList').getElementsByTagName('li');
    for (let i = 0; i < li.length; i++) {
        lettextValue = li[i].textContent || li[i].innerText;
        li[i].style.display = textValue.toLowerCase().indexOf(input) > -1 ? "" : "none";
    }
}

functionopenModal(imageSrc, title, date, description) {
    document.getElementById('modalImage').src = imageSrc;
    document.getElementById('modalTitle').textContent = title;
    document.getElementById('modalDate').textContent = date;
    document.getElementById('modalDescription').textContent = description;
    
    document.getElementById('eventModal').style.display = 'block';
    document.body.style.overflow = 'hidden'; 
}

functioncloseModal() {
    document.getElementById('eventModal').style.display = 'none';
    document.body.style.overflow = 'auto'; 
}

window.onclick = function(event) {
    constmodal = document.getElementById('eventModal');
    if (event.target === modal) 
        closeModal();
    
}

document.addEventListener('keydown', function(event) {
    if (event.key === 'Escape') {
        closeModal();
    }
});
</script>

</body>
</html>
