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

        .interface-container {
            padding: 20px;
            text-align: center;
        }

        .section-container {
            max-width: 600px;
            margin: 20px auto;
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }

        .section-container h3 {
            color: #007BFF;
            margin-bottom: 15px;
        }

        textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <!-- Página de inicio -->
    <div class="container" id="home">
        <h1>Tu Salud es Nuestra Prioridad</h1>
        <img src="https://via.placeholder.com/300" alt="Salud">
        <p>Proteger tu salud y prevenir enfermedades es nuestra misión.</p>
        <button class="primary" onclick="showRegister()">Registrarme</button>
        <button class="secondary" onclick="showLogin()">Iniciar Sesión</button>
    </div>

    <!-- Formulario de Registro -->
    <div class="container hidden" id="register-form">
        <h2>Registro</h2>
        <input type="email" id="register-email" placeholder="Correo electrónico" required>
        <input type="password" id="register-password" placeholder="Contraseña" required>
        <button class="primary" onclick="register()">Registrarse</button>
        <button class="secondary" onclick="showHome()">Cancelar</button>
    </div>

    <!-- Formulario de Inicio de Sesión -->
    <div class="container hidden" id="login-form">
        <h2>Iniciar Sesión</h2>
        <input type="email" id="login-email" placeholder="Correo electrónico" required>
        <input type="password" id="login-password" placeholder="Contraseña" required>
        <button class="primary" onclick="login()">Ingresar</button>
        <button class="secondary" onclick="showHome()">Cancelar</button>
    </div>

    <!-- Interfaz después de iniciar sesión -->
    <div class="container hidden" id="main-interface">
        <h2>Bienvenido</h2>
        <p>Elige una sección para continuar.</p>
        <button class="primary" onclick="showMonitoring()">Monitoreo</button>
        <button class="secondary" onclick="showSurvey()">Encuestas</button>
    </div>

    <!-- Sección de Monitoreo -->
    <div class="interface-container hidden" id="monitoring-section">
        <div class="section-container">
            <h3>Cómo prevenirlo</h3>
            <p>- Eliminar criaderos</p>
            <p>- Uso de insecticidas</p>
            <p>- Protección personal</p>
        </div>
        <div class="section-container">
            <h3>Síntomas</h3>
            <p>- Fiebre</p>
            <p>- Erupciones cutáneas</p>
            <p>- Dolores musculares y articulares</p>
            <p>- Conjuntivitis</p>
        </div>
        <div class="section-container">
            <h3>Cómo se contagia</h3>
            <p>Un mosquito infectado pica a una persona sana y transmite el virus.</p>
        </div>
        <button class="secondary" onclick="showMainInterface()">Volver</button>
    </div>

    <!-- Sección de Encuestas -->
    <div class="interface-container hidden" id="survey-section">
        <div class="section-container">
            <h3>Encuesta de Prevención</h3>
            <textarea id="survey-response" placeholder="¿Qué medidas tomas para prevenir el dengue?"></textarea>
            <button class="primary" onclick="saveSurvey()">Guardar Encuesta</button>
            <button class="secondary" onclick="showMainInterface()">Volver</button>
            <div id="survey-results" style="margin-top: 20px;"></div>
        </div>
    </div>

    <script>
        // Simulación de base de datos
        const users = {};

        // Funciones de navegación
        function showHome() {
            toggleVisibility("home");
        }

        function showRegister() {
            toggleVisibility("register-form");
        }

        function showLogin() {
            toggleVisibility("login-form");
        }

        function showMainInterface() {
            toggleVisibility("main-interface");
        }

        function showMonitoring() {
            toggleVisibility("monitoring-section");
        }

        function showSurvey() {
            toggleVisibility("survey-section");
        }

        function toggleVisibility(id) {
            document.querySelectorAll(".container, .interface-container").forEach(el => el.classList.add("hidden"));
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
            if (users[email] && users[email] === password) {
                alert("Inicio de sesión exitoso.");
                showMainInterface();
            } else {
                alert("Correo o contraseña incorrectos.");
            }
        }

        // Guardar encuesta
        function saveSurvey() {
            const response = document.getElementById("survey-response").value.trim();
            if (response) {
                document.getElementById("survey-results").innerText = `Respuesta guardada: ${response}`;
                document.getElementById("survey-response").value = "";
            } else {
                alert("Por favor, escribe una respuesta.");
            }
        }
    </script>
</body>
</html>
