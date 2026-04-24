<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Profil 3D Bootstrap | Alex Alredo Sinaga</title>
    
    <!-- Link Bootstrap 5 CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;800&display=swap" rel="stylesheet">

    <style>
        /* --- ANIMASI CUSTOM (Tetap Murni CSS) --- */
        @keyframes gradientBG {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        @keyframes typing {
            0% { width: 0; }
            70% { width: 100%; }
            100% { width: 100%; }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: #ff7675; }
        }

        /* --- STYLING UTAMA --- */
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(-45deg, #ee7752, #e73c7e, #23a6d5, #23d5ab);
            background-size: 400% 400%;
            animation: gradientBG 12s ease infinite;
            overflow-x: hidden;
            perspective: 1000px;
        }

        /* Container Card Menggunakan Glassmorphism */
        .custom-card {
            background: rgba(255, 255, 255, 0.9);
            border: none;
            border-radius: 30px;
            box-shadow: 0 25px 50px rgba(0,0,0,0.2);
            transition: transform 0.1s ease;
            transform-style: preserve-3d;
            max-width: 450px;
            overflow: hidden;
        }

        .profile-img {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 6px solid #fff;
            object-fit: cover;
            animation: float 4s ease-in-out infinite;
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
        }

        /* Animasi Ketik (Bootstrap membantu alignment dengan d-flex) */
        .typing-text {
            font-size: 1.7rem;
            font-weight: 800;
            color: #2d3436;
            white-space: nowrap;
            overflow: hidden;
            border-right: 4px solid #ff7675;
            width: 0;
            animation: 
                typing 3s steps(18) forwards infinite,
                blink-caret 0.75s infinite;
        }

        .feature-box {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 15px 5px;
            transition: all 0.3s ease;
            border: 1px solid #eee;
        }

        .feature-box:hover {
            transform: scale(1.05);
            background: #fff;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .reason-box {
            background: linear-gradient(135deg, #fdfbfb 0%, #ebedee 100%);
            border-radius: 20px;
            border-left: 5px solid #23a6d5;
        }
    </style>
</head>
<body>

    <div class="container d-flex justify-content-center align-items-center">
        <!-- Card Bootstrap -->
        <div class="card custom-card p-4 p-md-5" id="card">
            
            <!-- Foto Profil (Bootstrap class: mx-auto d-block) -->
            <img src="foto-alex.png" alt="Alex Alredo Sinaga" class="profile-img mx-auto d-block mb-4">

            <!-- Nama dengan Wrapper Flex Bootstrap -->
            <div class="d-flex justify-content-center mb-2">
                <div class="typing-text">Alex Alredo Sinaga</div>
            </div>

            <p class="text-secondary fw-bold text-center mb-4">NIM: 7243250012</p>

            <!-- Grid System Bootstrap untuk Ikon -->
            <div class="row g-2 mb-4 text-center">
                <div class="col-4">
                    <div class="feature-box">
                        <span class="fs-3">🚀</span><br>
                        <small class="fw-bold">Startup</small>
                    </div>
                </div>
                <div class="col-4">
                    <div class="feature-box">
                        <span class="fs-3">💻</span><br>
                        <small class="fw-bold">Digital</small>
                    </div>
                </div>
                <div class="col-4">
                    <div class="feature-box">
                        <span class="fs-3">📊</span><br>
                        <small class="fw-bold">Bisnis</small>
                    </div>
                </div>
            </div>

            <!-- Bagian Alasan dengan Spasi Bootstrap -->
            <div class="reason-box p-3 shadow-sm">
                <h6 class="fw-bold text-primary mb-2">Alasan Memilih Bisnis Digital:</h6>
                <p class="small text-muted mb-0 text-start">
                    "Saya ingin membuka bisnis dan menyediakan lapangan pekerjaan. Di era yang dipenuhi dunia digital ini, jurusan ini adalah fondasi yang paling meyakinkan untuk masa depan."
                </p>
            </div>

            <footer class="mt-4 text-center text-muted" style="font-size: 0.7rem;">
                Bisnis Digital C24 &bull; Bootstrap Edition
            </footer>
        </div>
    </div>

    <!-- Bootstrap Bundle JS -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>

    <!-- JavaScript untuk Efek 3D -->
    <script>
        const card = document.getElementById('card');
        
        card.addEventListener('mousemove', (e) => {
            const rect = card.getBoundingClientRect();
            const x = e.clientX - rect.left;
            const y = e.clientY - rect.top;
            
            const centerX = rect.width / 2;
            const centerY = rect.height / 2;
            
            const rotateX = (y - centerY) / 10;
            const rotateY = (centerX - x) / 10;
            
            card.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg)`;
        });

        card.addEventListener('mouseleave', () => {
            card.style.transform = `rotateX(0deg) rotateY(0deg)`;
        });
    </script>

</body>
</html>
