<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PanjiErlangga</title>

<style>
body {
    margin:0;
    font-family: Arial, sans-serif;
    background-image: url("https://i.pinimg.com/1200x/55/c6/e6/55c6e6b947eeda67b1bfa761c1013663.jpg");
    background-size: cover;
    background-position: center;
    color:white;
}

.overlay{
    background-color: rgba(0,0,0,0.65);
    min-height:100vh;
}

nav{
    background-color: rgba(0,0,0,0.8);
    padding:15px;
    text-align:center;
    position: sticky;
    top: 0;
    z-index: 1000;
}

nav a{
    color:white;
    margin:0 15px;
    text-decoration:none;
    font-weight:bold;
    cursor: pointer;
}

nav a:hover{
    color: #ffd700;
}

.container{
    padding:40px;
    max-width:900px;
    margin:auto;
}

/* Bagian Menu (Section) */
.section{
    display:none; /* Semua bagian disembunyikan dulu */
    transition: opacity 0.3s ease;
    animation: fadeIn 0.5s;
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.active{
    display:block;
}

h1,h2{
    text-align:center;
    color: #ffd700; /* Warna Emas */
}

.link-box{
    text-align:center;
    margin-top:25px;
}

.link-box a{
    display:block;
    margin:10px;
    color:#ffd700;
    font-size:18px;
    text-decoration:none;
    padding: 10px;
    border: 1px solid #ffd700;
    border-radius: 5px;
    transition: background0.3s;
}

.link-box a:hover{
    background-color: rgba(255, 215, 0, 0.2);
}

.video-box{
    text-align:center;
    margin-top:30px;
}

/* Styling untuk form login (Bagian Atas) */
.login-form {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: rgba(0,0,0,0.8);
    border-radius: 8px;
    border: 1px solid #ffd700;
}

.login-form input {
    width: 100%;
    padding: 10px;
    margin: 10px 0;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    box-sizing: border-box; /* Agar padding tidak memecah lebar */
}

.login-form button, .button {
    width: 100%;
    padding: 10px;
    background-color: #ffd700;
    border: none;
    border-radius: 4px;
    font-size: 16px;
    cursor: pointer;
    color: black;
    font-weight: bold;
    margin-top: 10px;
}

.login-form button:hover, .button:hover {
    background-color: #e6c200;
}

/* Styling untuk Bagian Daftar & Contact (Yang belum ada stylenya) */
.card {
    background-color: rgba(0, 0, 0, 0.8);
    padding: 20px;
    border-radius: 8px;
    margin-bottom: 20px;
    border: 1px solid #555;
}

.card label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

.card input, .card textarea {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: none;
    border-radius: 4px;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

/* Footer */
footer {
    text-align: center;
    padding: 20px;
    margin-top: 40px;
    font-size: 12px;
    opacity: 0.7;
}
</style>

<script>
function showMenu(menu){
    // 1. Sembunyikan semua bagian dengan class 'section'
    document.querySelectorAll('.section').forEach(sec => {
        sec.classList.remove('active');
    });
    
    // 2. Tampilkan bagian yang dipilih (ID-nya sesuai parameter)
    const selectedSection = document.getElementById(menu);
    if (selectedSection) {
        selectedSection.classList.add('active');
    }
    
    // Gulir ke atas saat pindah menu (untuk tampilan mobile)
    window.scrollTo(0, 0);
}
</script>

</head>

<body>
<div class="overlay">

<nav>
    <a onclick="showMenu('dashboard')">Dashboard</a>
    <a onclick="showMenu('katalog')">Katalog</a>
    <a onclick="showMenu('kegiatan')">Literasi</a>
    <a onclick="showMenu('event')">Event</a>
    <a onclick="showMenu('login')">Login</a>
    <a onclick="showMenu('daftar')">Daftar</a> <!-- Link Baru -->
    <a onclick="showMenu('contact')">Contact</a> <!-- Link Baru -->
</nav>

<div class="container">

<!-- DASHBOARD -->
<div id="dashboard" class="section active">
    <h1>Library Panji</h1>
    <p style="text-align:center;">Welcome to my profile.</p>

    <div class="link-box">
        <a href="https://www.facebook.com/panji.erlangga.77" target="_blank">
        Look at Me
        </a>
        <a href="https://drive.google.com/drive/folders/1KyE7ubNtW2E0yUoDRS_2pGuJB3SHfi4f" target="_blank">
        Profile
        </a>
    </div>

    <div class="video-box">
        <h3>Best Video</h3>
        <!-- Link YouTube sudah diperbaiki ke format Embed -->
        <iframe width="560" height="315"
        src="https://www.youtube.com/embed/NWQ13Y4G0fw"
        title="YouTube video"
        frameborder="0"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen
        loading="lazy">
        </iframe>
    </div>
</div>

<!-- KATALOG BUKU -->
<div id="katalog" class="section">
    <h2>Daftar Buku</h2>
    <ul style="line-height: 1.8;">
        <li>Pengantar Ilmu Perpustakaan </li>
        <li>Dasar-dasar Perpustakaan</li>
        <li>Manajemen Perpustakaan</li>
        <li>Pengembangan Koleksi Perpustakaan</li>
        <li>Layanan Perpustakaan</li>
    </ul>
</div>

<!-- KEGIATAN -->
<div id="kegiatan" class="section">
    <h2> Kegiatan Literasi</h2>
    <ul style="line-height: 1.8;">
        <li>Karya Tulis Ilmiah</li>
        <li>Workshop</li>
        <li>Praktik</li>
    </ul>
</div>

<!-- EVENT -->
<div id="event" class="section">
    <h2>Event</h2>

    <div class="card">
        <h3>Galeri Event</h3>

        <form>
            <label>Sosialisasi</label>
            <input type="text" id="Sosialisasi" placeholder="SosialisasiPemberdayaan UMKM Untuk Mengatasi Kemiskinan di Kota Medan Dinas Koperasi dan UMKM Prrov.Sumut" required>

            <label>Upload Foto</label>
            <input type="file" id="fotoEvent" accept="image/*" required>

            <button type="button" class="button" onclick="uploadEvent()">Upload</button>
        </form>
    </div>

    <div class="card">
        <h3>Galeri Event</h3>
        <div id="galeriEvent"></div>
    </div>
</div>

<!-- LOGIN -->
<div id="login" class="section">
    <h2>Login Anggota</h2>
    <div class="login-form">
        <form>
            <label>Username</label>
            <input type="username" required>
            <label>Password</label>
            <input type="password" required>
            <label>Status Pengguna</label>
            <input type="Status Pengguna" required>
            <button type="submit">Masuk</button>
        </form>
    </div>
</div>

<!-- DAFTAR (REGISTER) -->
<div id="daftar" class="section">
    <h2>Pendaftaran Anggota</h2>
    <div class="card">
        <form>
            <label>Nama Lengkap</label>
            <input type="text" required>
            
            <label>Email</label>
            <input type="email" required>
            
            <label>Password</label>
            <input type="password" required>
            
            <button type="submit" class="button">Daftar Sekarang</button>
        </form>
    </div>
</div>

<!-- CONTACT -->
<div id="contact" class="section">
    <h2>Contact Pemilik</h2>
    <div class="card">
        <p><strong>Nama:</strong> Panji Erlangga</p>
        <p><strong>Email:</strong> panjierlangga202005@gmail.com</p>
        <p><strong>WhatsApp:</strong> 082267523213</p>
        <p><strong>Lokasi:</strong> Medan, Indonesia</p>
    </div>

    <h2>Kirim Pesan</h2>
    <div class="card">
        <form>
            <label>Nama</label>
            <input type="text" placeholder="Masukkan nama Anda" required>
            
            <label>Email</label>
            <input type="email" placeholder="Masukkan email Anda" required>
            
            <label>Pesan</label>
            <textarea rows="5" placeholder="Tulis pesan Anda di sini..." required></textarea>
            
            <button type="submit" class="button">Kirim Pesan</button>
        </form>
    </div>
</div>

<!-- FOOTER -->
<footer>
    &copy; 2026 PanjiErlangga. All Rights Reserved.
</footer>

</div>

</div>

</body>
</html>

