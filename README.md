<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salud - Tu Salud es Nuestra Prioridad</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }

        .container {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            text-align: center;
            flex-direction: column;
        }

        h1 {
            color: #007BFF;
        }

        p {
            font-size: 1.2em;
            margin-bottom: 20px;
        }

        img {
            width: 300px;
            margin-bottom: 20px;
        }

        button {
            padding: 10px 20px;
            font-size: 1em;
            border: none;
            border-radius: 5px;
            margin: 5px;
            cursor: pointer;
        }

        button.primary {
            background-color: #007BFF;
            color: white;
        }

        button.secondary {
            background-color: #6c757d;
            color: white;
        }

        .hidden {
            display: none;
        }

        .form-container {
            padding: 20px;
            background: white;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            margin: auto;
        }

        .form-container h2 {
            margin-bottom: 20px;
        }

        label {
            display: block;
            margin: 10px 0 5px;
            font-weight: bold;
        }

        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .interface-section {
            padding: 20px;
        }

        .interface-section h3 {
            color: #007BFF;
        }

        .monitoring-section, .survey-section {
            margin-top: 20px;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
        }

        .survey-section textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }

        .survey-section button {
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container" id="home">
        <h1>Tu Salud es Nuestra Prioridad</h1>
        <img src="https://via.placeholder.com/300" alt="Salud">
        <p>Proteger tu salud y prevenir enfermedades es nuestra misión.</p>
        <button class="primary" onclick="showRegister()">Registrarme</button>
        <button class="secondary" onclick="showLogin()">Iniciar Sesión</button>
    </div>

    <!-- Formulario de Registro -->
    <div class="form-container hidden" id="register-form">
        <h2>Registro</h2>
        <label for="register-email">Correo Electrónico</label>
        <input type="email" id="register-email" placeholder="Ingresa tu correo" required>
        <label for="register-password">Contraseña</label>
        <input type="password" id="register-password" placeholder="Crea tu contraseña" required>
        <button class="primary" onclick="register()">Registrarse</button>
        <button class="secondary" onclick="showHome()">Cancelar</button>
    </div>

    <!-- Formulario de Inicio de Sesión -->
    <div class="form-container hidden" id="login-form">
        <h2>Iniciar Sesión</h2>
        <label for="login-email">Correo Electrónico</label>
        <input type="email" id="login-email" placeholder="Ingresa tu correo" required>
        <label for="login-password">Contraseña</label>
        <input type="password" id="login-password" placeholder="Ingresa tu contraseña" required>
        <button class="primary" onclick="login()">Ingresar</button>
        <button class="secondary" onclick="showHome()">Cancelar</button>
        <div style="margin-top: 10px;">
            <a href="#" onclick="showForgotPassword()">¿Olvidaste tu contraseña?</a>
        </div>
    </div>

    <!-- Recuperación de Contraseña -->
    <div class="form-container hidden" id="forgot-password-form">
        <h2>Recuperar Contraseña</h2>
        <label for="forgot-email">Correo Electrónico</label>
        <input type="email" id="forgot-email" placeholder="Ingresa tu correo" required>
        <button class="primary" onclick="recoverPassword()">Recuperar</button>
        <button class="secondary" onclick="showLogin()">Cancelar</button>
    </div>

    <!-- Interfaz Principal -->
    <div class="hidden" id="main-interface">
        <div class="interface-section">
            <h3>Monitoreo</h3>
            <div class="monitoring-section">
                <h4>Cómo prevenirlo:</h4>
                <p>- Eliminar criaderos</p>
                <p>- Uso de insecticidas</p>
                <p>- Protección personal</p>
            </div>
            <div class="monitoring-section">
                <h4>Síntomas:</h4>
                <p>- Fiebre</p>
                <p>- Erupciones cutáneas</p>
                <p>- Dolores musculares y articulares</p>
                <p>- Conjuntivitis</p>
            </div>
            <div class="monitoring-section">
                <h4>Cómo se contagia:</h4>
                <p>Un mosquito infectado pica a una persona sana y transmite el virus.</p>
            </div>
        </div>

        <div class="interface-section">
            <h3>Encuesta</h3>
            <div class="survey-section">
                <textarea id="survey-response" placeholder="¿Qué acciones tomas para prevenir el dengue?"></textarea>
                <button class="primary" onclick="saveSurvey()">Guardar Encuesta</button>
                <div id="survey-results" style="margin-top: 10px;"></div>
            </div>
        </div>
    </div>

    <script>
        // Simulación de base de datos
        const users = {};

        // Funciones para mostrar formularios
        function showHome() {
            toggleVisibility("home");
        }

        function showRegister() {
            toggleVisibility("register-form");
        }

        function showLogin() {
            toggleVisibility("login-form");
        }

        function showForgotPassword() {
            toggleVisibility("forgot-password-form");
        }

        function toggleVisibility(id) {
            document.querySelectorAll(".container, .form-container, #main-interface").forEach(el => el.classList.add("hidden"));
            document.getElementById(id).classList.remove("hidden");
        }

        // Registro
        function register() {
            const email = document.getElementById("register-email").value;
            const password = document.getElementById("register-password").value;
            if (users[email]) {
                alert("Este correo ya está registrado.");
            } else {
                users[email] = password;
                alert("Registro exitoso. Ahora inicia sesión.");
                showLogin();
            }
        }

        // Inicio de sesión
        function login() {
            const email = document.getElementById("login-email").value;
            const password = document.getElementById("login-password").value;
            if (users[email] === password) {
                alert("Inicio de sesión exitoso.");
                toggleVisibility("main-interface");
            } else {
                alert("Correo o contraseña incorrectos.");
            }
        }

        // Recuperar contraseña
        function recoverPassword() {
            const email = document.getElementById("forgot-email").value;
            if (users[email]) {
                alert(`Tu contraseña es: ${users[email]}`);
                showLogin();
            } else {
                alert("Correo no registrado.");
            }
        }

        // Guardar encuesta
        function saveSurvey() {
            const response = document.getElementById("survey-response").value;
            if (response.trim()) {
                document.getElementById("survey-results").innerText = `Respuesta guardada: ${response}`;
                document.getElementById("survey-response").value = "";
            } else {
                alert("Por favor, escribe una respuesta.");
            }
        }
    </script>
</body>
</html>
