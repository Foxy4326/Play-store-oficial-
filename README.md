<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GameStore - Plataforma de Jogos APK</title>
    <style>
        :root {
            --primary-color: #4285f4;
            --secondary-color: #34a853;
            --accent-color: #ea4335;
            --background-color: #f8f9fa;
            --card-color: #ffffff;
            --text-color: #333333;
            --text-light: #757575;
            --shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            line-height: 1.6;
        }

        header {
            background-color: var(--card-color);
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 15px;
        }

        .navbar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 0;
        }

        .logo {
            display: flex;
            align-items: center;
            font-size: 1.5rem;
            font-weight: bold;
            color: var(--primary-color);
        }

        .logo i {
            margin-right: 8px;
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin-left: 20px;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;
            transition: color 0.3s;
        }

        .nav-links a:hover {
            color: var(--primary-color);
        }

        .auth-buttons {
            display: flex;
            gap: 10px;
        }

        .btn {
            padding: 8px 16px;
            border-radius: 4px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            border: none;
        }

        .btn-primary {
            background-color: var(--primary-color);
            color: white;
        }

        .btn-outline {
            background-color: transparent;
            border: 1px solid var(--primary-color);
            color: var(--primary-color);
        }

        .btn:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }

        .hero {
            background: linear-gradient(135deg, var(--primary-color), #5c6bc0);
            color: white;
            padding: 60px 0;
            text-align: center;
        }

        .hero h1 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 30px;
        }

        .section {
            padding: 60px 0;
        }

        .section-title {
            text-align: center;
            margin-bottom: 40px;
            font-size: 2rem;
        }

        .games-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 25px;
        }

        .game-card {
            background-color: var(--card-color);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: transform 0.3s;
        }

        .game-card:hover {
            transform: translateY(-5px);
        }

        .game-image {
            height: 150px;
            background-color: #e0e0e0;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-light);
        }

        .game-info {
            padding: 15px;
        }

        .game-title {
            font-weight: bold;
            margin-bottom: 5px;
        }

        .game-developer {
            color: var(--text-light);
            font-size: 0.9rem;
            margin-bottom: 10px;
        }

        .game-rating {
            display: flex;
            align-items: center;
            color: var(--text-light);
            font-size: 0.9rem;
        }

        .rating-stars {
            color: #fbbc04;
            margin-right: 5px;
        }

        .upload-section {
            background-color: var(--card-color);
            padding: 40px;
            border-radius: 8px;
            box-shadow: var(--shadow);
            max-width: 800px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }

        .form-control {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }

        .file-upload {
            border: 2px dashed #ddd;
            padding: 20px;
            text-align: center;
            border-radius: 4px;
            cursor: pointer;
            transition: border-color 0.3s;
        }

        .file-upload:hover {
            border-color: var(--primary-color);
        }

        .file-upload i {
            font-size: 2rem;
            color: var(--text-light);
            margin-bottom: 10px;
        }

        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0,0,0,0.5);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background-color: var(--card-color);
            padding: 30px;
            border-radius: 8px;
            width: 90%;
            max-width: 400px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .modal-title {
            margin-bottom: 20px;
            text-align: center;
            font-size: 1.5rem;
        }

        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-light);
        }

        .tabs {
            display: flex;
            border-bottom: 1px solid #ddd;
            margin-bottom: 20px;
        }

        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
        }

        .tab.active {
            border-bottom: 2px solid var(--primary-color);
            color: var(--primary-color);
            font-weight: 500;
        }

        footer {
            background-color: #333;
            color: white;
            padding: 40px 0 20px;
        }

        .footer-content {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
            margin-bottom: 30px;
        }

        .footer-column h3 {
            margin-bottom: 15px;
            font-size: 1.2rem;
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
            color: white;
        }

        .copyright {
            text-align: center;
            padding-top: 20px;
            border-top: 1px solid #444;
            color: #aaa;
            font-size: 0.9rem;
        }

        @media (max-width: 768px) {
            .navbar {
                flex-direction: column;
                padding: 15px 0;
            }
            
            .nav-links {
                margin: 15px 0;
            }
            
            .auth-buttons {
                width: 100%;
                justify-content: center;
            }
            
            .hero h1 {
                font-size: 2rem;
            }
            
            .hero p {
                font-size: 1rem;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="container">
            <nav class="navbar">
                <div class="logo">
                    <i>🎮</i>
                    <span>GameStore</span>
                </div>
                <ul class="nav-links">
                    <li><a href="#home">Início</a></li>
                    <li><a href="#games">Jogos</a></li>
                    <li><a href="#upload">Publicar</a></li>
                    <li><a href="#about">Sobre</a></li>
                </ul>
                <div class="auth-buttons">
                    <button class="btn btn-outline" id="loginBtn">Entrar</button>
                    <button class="btn btn-primary" id="registerBtn">Cadastrar</button>
                </div>
            </nav>
        </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
        <div class="container">
            <h1>Descubra e Publique Jogos Incríveis</h1>
            <p>A plataforma definitiva para desenvolvedores publicarem seus jogos em APK e para jogadores descobrirem novas experiências.</p>
            <button class="btn btn-primary" id="exploreBtn">Explorar Jogos</button>
        </div>
    </section>

    <!-- Games Section -->
    <section class="section" id="games">
        <div class="container">
            <h2 class="section-title">Jogos em Destaque</h2>
            <div class="games-grid">
                <!-- Game Card 1 -->
                <div class="game-card">
                    <div class="game-image">Imagem do Jogo</div>
                    <div class="game-info">
                        <div class="game-title">Space Adventure</div>
                        <div class="game-developer">Cosmic Games</div>
                        <div class="game-rating">
                            <span class="rating-stars">★★★★☆</span>
                            <span>4.2</span>
                        </div>
                    </div>
                </div>
                
                <!-- Game Card 2 -->
                <div class="game-card">
                    <div class="game-image">Imagem do Jogo</div>
                    <div class="game-info">
                        <div class="game-title">Racing Extreme</div>
                        <div class="game-developer">SpeedDev</div>
                        <div class="game-rating">
                            <span class="rating-stars">★★★★★</span>
                            <span>4.8</span>
                        </div>
                    </div>
                </div>
                
                <!-- Game Card 3 -->
                <div class="game-card">
                    <div class="game-image">Imagem do Jogo</div>
                    <div class="game-info">
                        <div class="game-title">Puzzle Master</div>
                        <div class="game-developer">Brainy Studios</div>
                        <div class="game-rating">
                            <span class="rating-stars">★★★☆☆</span>
                            <span>3.5</span>
                        </div>
                    </div>
                </div>
                
                <!-- Game Card 4 -->
                <div class="game-card">
                    <div class="game-image">Imagem do Jogo</div>
                    <div class="game-info">
                        <div class="game-title">Zombie Survival</div>
                        <div class="game-developer">Apocalypse Games</div>
                        <div class="game-rating">
                            <span class="rating-stars">★★★★☆</span>
                            <span>4.3</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Upload Section -->
    <section class="section" id="upload">
        <div class="container">
            <h2 class="section-title">Publicar seu Jogo</h2>
            <div class="upload-section">
                <form id="uploadForm">
                    <div class="form-group">
                        <label for="gameTitle">Título do Jogo</label>
                        <input type="text" id="gameTitle" class="form-control" placeholder="Digite o título do jogo" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="gameDescription">Descrição</label>
                        <textarea id="gameDescription" class="form-control" rows="4" placeholder="Descreva seu jogo" required></textarea>
                    </div>
                    
                    <div class="form-group">
                        <label for="gameCategory">Categoria</label>
                        <select id="gameCategory" class="form-control" required>
                            <option value="">Selecione uma categoria</option>
                            <option value="action">Ação</option>
                            <option value="adventure">Aventura</option>
                            <option value="puzzle">Quebra-cabeça</option>
                            <option value="racing">Corrida</option>
                            <option value="sports">Esportes</option>
                            <option value="strategy">Estratégia</option>
                        </select>
                    </div>
                    
                    <div class="form-group">
                        <label>Arquivo APK</label>
                        <div class="file-upload" id="fileUploadArea">
                            <i>📁</i>
                            <p>Clique para selecionar ou arraste o arquivo APK</p>
                            <input type="file" id="apkFile" accept=".apk" style="display: none;">
                        </div>
                        <div id="fileName" style="margin-top: 10px;"></div>
                    </div>
                    
                    <div class="form-group">
                        <label for="gameIcon">Ícone do Jogo</label>
                        <input type="file" id="gameIcon" class="form-control" accept="image/*">
                    </div>
                    
                    <button type="submit" class="btn btn-primary" style="width: 100%;">Publicar Jogo</button>
                </form>
            </div>
        </div>
    </section>

    <!-- Login Modal -->
    <div class="modal" id="loginModal">
        <div class="modal-content">
            <span class="close-modal" id="closeLoginModal">&times;</span>
            <h3 class="modal-title">Entrar na GameStore</h3>
            <form id="loginForm">
                <div class="form-group">
                    <label for="loginEmail">E-mail</label>
                    <input type="email" id="loginEmail" class="form-control" placeholder="Seu e-mail" required>
                </div>
                
                <div class="form-group">
                    <label for="loginPassword">Senha</label>
                    <input type="password" id="loginPassword" class="form-control" placeholder="Sua senha" required>
                </div>
                
                <button type="submit" class="btn btn-primary" style="width: 100%;">Entrar</button>
            </form>
            <p style="text-align: center; margin-top: 15px;">
                Não tem uma conta? <a href="#" id="showRegisterFromLogin">Cadastre-se</a>
            </p>
        </div>
    </div>

    <!-- Register Modal -->
    <div class="modal" id="registerModal">
        <div class="modal-content">
            <span class="close-modal" id="closeRegisterModal">&times;</span>
            <h3 class="modal-title">Criar Conta</h3>
            <form id="registerForm">
                <div class="form-group">
                    <label for="registerName">Nome Completo</label>
                    <input type="text" id="registerName" class="form-control" placeholder="Seu nome completo" required>
                </div>
                
                <div class="form-group">
                    <label for="registerEmail">E-mail</label>
                    <input type="email" id="registerEmail" class="form-control" placeholder="Seu e-mail" required>
                </div>
                
                <div class="form-group">
                    <label for="registerPassword">Senha</label>
                    <input type="password" id="registerPassword" class="form-control" placeholder="Crie uma senha" required>
                </div>
                
                <div class="form-group">
                    <label for="registerConfirmPassword">Confirmar Senha</label>
                    <input type="password" id="registerConfirmPassword" class="form-control" placeholder="Confirme sua senha" required>
                </div>
                
                <button type="submit" class="btn btn-primary" style="width: 100%;">Criar Conta</button>
            </form>
            <p style="text-align: center; margin-top: 15px;">
                Já tem uma conta? <a href="#" id="showLoginFromRegister">Entrar</a>
            </p>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="container">
            <div class="footer-content">
                <div class="footer-column">
                    <h3>GameStore</h3>
                    <ul class="footer-links">
                        <li><a href="#">Sobre nós</a></li>
                        <li><a href="#">Carreiras</a></li>
                        <li><a href="#">Blog</a></li>
                        <li><a href="#">Contato</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Desenvolvedores</h3>
                    <ul class="footer-links">
                        <li><a href="#">Documentação</a></li>
                        <li><a href="#">Política de Publicação</a></li>
                        <li><a href="#">Analytics</a></li>
                        <li><a href="#">Suporte</a></li>
                    </ul>
                </div>
                
                <div class="footer-column">
                    <h3>Legal</h3>
                    <ul class="footer-links">
                        <li><a href="#">Termos de Serviço</a></li>
                        <li><a href="#">Política de Privacidade</a></li>
                        <li><a href="#">DMCA</a></li>
                        <li><a href="#">Cookies</a></li>
                    </ul>
                </div>
            </div>
            
            <div class="copyright">
                &copy; 2023 GameStore. Todos os direitos reservados.
            </div>
        </div>
    </footer>

    <script>
        // Modal functionality
        const loginBtn = document.getElementById('loginBtn');
        const registerBtn = document.getElementById('registerBtn');
        const loginModal = document.getElementById('loginModal');
        const registerModal = document.getElementById('registerModal');
        const closeLoginModal = document.getElementById('closeLoginModal');
        const closeRegisterModal = document.getElementById('closeRegisterModal');
        const showRegisterFromLogin = document.getElementById('showRegisterFromLogin');
        const showLoginFromRegister = document.getElementById('showLoginFromRegister');
        
        // Open login modal
        loginBtn.addEventListener('click', () => {
            loginModal.style.display = 'flex';
        });
        
        // Open register modal
        registerBtn.addEventListener('click', () => {
            registerModal.style.display = 'flex';
        });
        
        // Close modals
        closeLoginModal.addEventListener('click', () => {
            loginModal.style.display = 'none';
        });
        
        closeRegisterModal.addEventListener('click', () => {
            registerModal.style.display = 'none';
        });
        
        // Switch between login and register modals
        showRegisterFromLogin.addEventListener('click', (e) => {
            e.preventDefault();
            loginModal.style.display = 'none';
            registerModal.style.display = 'flex';
        });
        
        showLoginFromRegister.addEventListener('click', (e) => {
            e.preventDefault();
            registerModal.style.display = 'none';
            loginModal.style.display = 'flex';
        });
        
        // Close modals when clicking outside
        window.addEventListener('click', (e) => {
            if (e.target === loginModal) {
                loginModal.style.display = 'none';
            }
            if (e.target === registerModal) {
                registerModal.style.display = 'none';
            }
        });
        
        // File upload functionality
        const fileUploadArea = document.getElementById('fileUploadArea');
        const apkFileInput = document.getElementById('apkFile');
        const fileName = document.getElementById('fileName');
        
        fileUploadArea.addEventListener('click', () => {
            apkFileInput.click();
        });
        
        fileUploadArea.addEventListener('dragover', (e) => {
            e.preventDefault();
            fileUploadArea.style.borderColor = '#4285f4';
            fileUploadArea.style.backgroundColor = '#f0f7ff';
        });
        
        fileUploadArea.addEventListener('dragleave', () => {
            fileUploadArea.style.borderColor = '#ddd';
            fileUploadArea.style.backgroundColor = 'transparent';
        });
        
        fileUploadArea.addEventListener('drop', (e) => {
            e.preventDefault();
            fileUploadArea.style.borderColor = '#ddd';
            fileUploadArea.style.backgroundColor = 'transparent';
            
            if (e.dataTransfer.files.length) {
                apkFileInput.files = e.dataTransfer.files;
                updateFileName();
            }
        });
        
        apkFileInput.addEventListener('change', updateFileName);
        
        function updateFileName() {
            if (apkFileInput.files.length) {
                fileName.textContent = `Arquivo selecionado: ${apkFileInput.files[0].name}`;
            } else {
                fileName.textContent = '';
            }
        }
        
        // Form submissions
        document.getElementById('loginForm').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Login realizado com sucesso!');
            loginModal.style.display = 'none';
        });
        
        document.getElementById('registerForm').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Conta criada com sucesso!');
            registerModal.style.display = 'none';
        });
        
        document.getElementById('uploadForm').addEventListener('submit', (e) => {
            e.preventDefault();
            alert('Jogo publicado com sucesso!');
            document.getElementById('uploadForm').reset();
            fileName.textContent = '';
        });
        
        // Smooth scrolling
        document.getElementById('exploreBtn').addEventListener('click', () => {
            document.getElementById('games').scrollIntoView({ behavior: 'smooth' });
        });
        
        // Navigation smooth scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                
                const targetId = this.getAttribute('href');
                if (targetId === '#') return;
                
                const targetElement = document.querySelector(targetId);
                if (targetElement) {
                    targetElement.scrollIntoView({ behavior: 'smooth' });
                }
            });
        });
    </script>
</body>
</html>
