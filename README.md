<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tu Salud es Nuestra Prioridad</title>
    <style>
        /* General */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Arial', sans-serif;
            line-height: 1.6;
            background: linear-gradient(135deg, #43cea2, #185a9d);
            color: #333;
        }

        h1, h2, h3 {
            color: #ffffff;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.3);
        }

        p {
            color: #ffffff;
            font-size: 1em;
            margin-bottom: 10px;
        }

        /* Contenedores principales */
        .container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            text-align: center;
            padding: 20px;
        }

        .hidden {
            display: none;
        }

        /* Contenido dentro de las secciones */
        .section-container {
            width: 90%;
            max-width: 600px;
            margin: 10px auto;
            background: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            text-align: left;
        }

        .section-container h3 {
            color: #185a9d;
            margin-bottom: 10px;
        }

        label {
            font-weight: bold;
            color: #185a9d;
        }

        /* Botones */
        button {
            padding: 10px 20px;
            font-size: 1em;
            border: none;
            border-radius: 5px;
            margin: 5px;
            cursor: pointer;
            transition: all 0.3s ease-in-out;
        }

        button.primary {
            background-color: #185a9d;
            color: white;
        }

        button.secondary {
            background-color: #6c757d;
            color: white;
        }

        button:hover {
            opacity: 0.9;
            transform: translateY(-2px);
        }

        /* Inputs */
        input, textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
        }

        /* Responsividad */
        @media (max-width: 768px) {
            h1, h2 {
                font-size: 1.5em;
            }

            button {
                font-size: 0.9em;
                padding: 8px 15px;
            }

            .section-container {
                padding: 15px;
            }
        }
    </style>
</head>
<body>
    <!-- Página principal -->
    <div class="container" id="welcome-screen">
        <h1>Tu Salud es Nuestra Prioridad</h1>
        <p>Protegiendo tu bienestar, paso a paso.</p>
        <button class="primary" onclick="showLogin()">Iniciar Sesión</button>
        <button class="secondary" onclick="showRegister()">Registrarse</button>
    </div>

    <!-- Registro -->
    <div class="container hidden" id="register-screen">
        <h2>Registrarse</h2>
        <form>
            <input type="email" id="register-email" placeholder="Correo electrónico" required>
            <input type="password" id="register-password" placeholder="Contraseña" required>
            <button type="button" class="primary" onclick="registerUser()">Registrarse</button>
            <button type="button" class="secondary" onclick="showWelcome()">Volver</button>
        </form>
    </div>

    <!-- Inicio de sesión -->
    <div class="container hidden" id="login-screen">
        <h2>Iniciar Sesión</h2>
        <form>
            <input type="email" id="login-email" placeholder="Correo electrónico" required>
            <input type="password" id="login-password" placeholder="Contraseña" required>
            <button type="button" class="primary" onclick="loginUser()">Iniciar Sesión</button>
            <button type="button" class="secondary" onclick="showWelcome()">Volver</button>
        </form>
        <button class="secondary" onclick="forgotPassword()">Olvidé mi contraseña</button>
    </div>

    <!-- Página principal después de iniciar sesión -->
    <div class="container hidden" id="main-interface">
        <h2>Bienvenido a tu perfil</h2>
        <button class="primary" onclick="showSurvey()">Encuestas</button>
        <button class="secondary" onclick="showMonitoring()">Monitoreo</button>
    </div>

    <!-- Encuesta -->
    <div class="container hidden" id="survey-section">
        <div class="section-container">
            <h3>Encuesta de Prevención del Dengue</h3>
            <form>
                <label for="q1">1. ¿Qué medidas tomas para prevenir el dengue?</label>
                <textarea id="q1" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q2">2. ¿Conoces los síntomas más comunes del dengue?</label>
                <textarea id="q2" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q3">3. ¿Usas repelentes contra los mosquitos?</label>
                <textarea id="q3" placeholder="Escribe tu respuesta aquí..."></textarea>

                <button type="button" class="primary" onclick="saveSurvey()">Guardar Encuesta</button>
                <button type="button" class="secondary" onclick="showMainInterface()">Volver</button>
            </form>
        </div>
    </div>

    <!-- Monitoreo -->
    <div class="container hidden" id="monitoring-section">
        <div class="section-container">
            <h3>¿Cómo prevenir el dengue?</h3>
            <ul>
                <li>Eliminar criaderos</li>
                <li>Uso de insecticidas</li>
                <li>Protección personal</li>
            </ul>
        </div>
        <div class="section-container">
            <h3>Síntomas</h3>
            <ul>
                <li>Fiebre</li>
                <li>Erupciones cutáneas</li>
                <li>Dolores musculares y articulares</li>
                <li>Conjuntivitis</li>
            </ul>
        </div>
        <div class="section-container">
            <h3>¿Cómo se contagia?</h3>
            <p>El dengue se transmite cuando un mosquito pica a una persona infectada, adquiere el virus y posteriormente puede transmitirlo al picar a otras personas.</p>
        </div>
        <button class="secondary" onclick="showMainInterface()">Volver</button>
    </div>

    <script>
        // Variables globales
        let users = [];

        // Funciones de navegación
        function showWelcome() {
            toggleVisibility("welcome-screen");
        }

        function showRegister() {
            toggleVisibility("register-screen");
        }

        function showLogin() {
            toggleVisibility("login-screen");
        }

        function showMainInterface() {
            toggleVisibility("main-interface");
        }

        function showSurvey() {
            toggleVisibility("survey-section");
        }

        function showMonitoring() {
            toggleVisibility("monitoring-section");
        }

        function toggleVisibility(id) {
            document.querySelectorAll(".container").forEach(el => el.classList.add("hidden"));
            document.getElementById(id).classList.remove("hidden");
        }

        // Registro de usuario
        function registerUser() {
            const email = document.getElementById("register-email").value;
            const password = document.getElementById("register-password").value;
            if (users.some(u => u.email === email)) {
                alert("Este correo ya está registrado.");
            } else {
                users.push({ email, password });
                alert("Registro exitoso.");
                showWelcome();
            }
        }

        // Inicio de sesión
        function loginUser() {
            const email = document.getElementById("login-email").value;
            const password = document.getElementById("login-password").value;
            const user = users.find(u => u.email === email && u.password === password);
            if (user) {
                showMainInterface();
            } else {
                alert("Credenciales incorrectas.");
            }
        }

        // Recuperación de contraseña
        function forgotPassword() {
            const email = prompt("Ingresa tu correo:");
            const user = users.find(u => u.email === email);
            alert(user ? `Tu contraseña es: ${user.password}` : "Correo no registrado.");
        }

        // Guardar encuesta
        function saveSurvey() {
            alert("Encuesta guardada con éxito.");
            showMainInterface();
        }
    </script>
</body>
</html>
