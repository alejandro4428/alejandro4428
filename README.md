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
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        p {
            color: #ffffff;
            font-size: 1.2em;
            margin-bottom: 10px;
        }

        /* Encabezado */
        .header {
            text-align: center;
            padding: 20px;
            background: rgba(0, 0, 0, 0.3);
            border-bottom: 5px solid #ffffff;
        }

        .header img {
            width: 80px;
            margin-bottom: 10px;
        }

        /* Contenedores */
        .container {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            text-align: center;
            padding: 20px;
        }

        .hidden {
            display: none;
        }

        .interface-container {
            padding: 20px;
            text-align: center;
        }

        .section-container {
            max-width: 700px;
            margin: 20px auto;
            background: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .section-container h3 {
            color: #185a9d;
            margin-bottom: 15px;
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
        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
        }

        /* Textarea */
        textarea {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
            margin-bottom: 20px;
            height: 100px;
        }

    </style>
</head>
<body>
    <!-- Encabezado -->
    <div class="header">
        <img src="https://via.placeholder.com/80" alt="Logo">
        <h1>Tu Salud es Nuestra Prioridad</h1>
        <p>Protegiendo tu bienestar, paso a paso.</p>
    </div>

    <!-- Página principal -->
    <div class="container" id="welcome-screen">
        <h2>Bienvenido</h2>
        <p>Elige una opción para continuar.</p>
        <button class="primary" onclick="showLogin()">Iniciar Sesión</button>
        <button class="secondary" onclick="showRegister()">Registrarse</button>
    </div>

    <!-- Registro -->
    <div class="container hidden" id="register-screen">
        <h2>Registrarse</h2>
        <form id="register-form">
            <input type="email" id="register-email" placeholder="Correo electrónico" required>
            <input type="password" id="register-password" placeholder="Contraseña" required>
            <button type="button" class="primary" onclick="registerUser()">Registrarse</button>
            <button type="button" class="secondary" onclick="showWelcome()">Volver</button>
        </form>
    </div>

    <!-- Inicio de sesión -->
    <div class="container hidden" id="login-screen">
        <h2>Iniciar Sesión</h2>
        <form id="login-form">
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
    <div class="interface-container hidden" id="survey-section">
        <div class="section-container">
            <h3>Encuesta de Prevención del Dengue</h3>
            <form id="survey-form">
                <label for="q1">1. ¿Qué medidas tomas para prevenir el dengue?</label>
                <textarea id="q1" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q2">2. ¿Conoces los síntomas más comunes del dengue?</label>
                <textarea id="q2" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q3">3. ¿Usas repelentes contra los mosquitos?</label>
                <textarea id="q3" placeholder="Escribe tu respuesta aquí..."></textarea>

                <button type="button" class="primary" onclick="saveSurvey()">Guardar Encuesta</button>
                <button type="button" class="secondary" onclick="showMainInterface()">Volver</button>
            </form>
            <div id="survey-results" style="margin-top: 20px;"></div>
        </div>
    </div>

    <!-- Sección de Monitoreo -->
    <div class="interface-container hidden" id="monitoring-section">
        <div class="section-container">
            <h3>¿Cómo prevenir el dengue?</h3>
            <p>- Eliminar criaderos</p>
            <p>- Uso de insecticidas</p>
            <p>- Protección personal</p>
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
            <p>El dengue se transmite a través de la picadura de mosquitos infectados que pican a una persona infectada y luego pueden transmitir el virus a otras personas.</p>
        </div>
        <button class="secondary" onclick="showMainInterface()">Volver</button>
    </div>

    <script>
        // Variable para almacenar usuarios registrados
        let users = [];

        // Mostrar pantallas
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
            document.querySelectorAll(".container, .interface-container").forEach(el => el.classList.add("hidden"));
            document.getElementById(id).classList.remove("hidden");
        }

        // Función de registro
        function registerUser() {
            const email = document.getElementById("register-email").value;
            const password = document.getElementById("register-password").value;

            if (email && password) {
                const existingUser = users.find(u => u.email === email);
                if (existingUser) {
                    alert("Este correo ya está registrado.");
                } else {
                    users.push({ email, password });
                    alert("Registro exitoso.");
                    showWelcome();
                }
            } else {
                alert("Por favor, complete todos los campos.");
            }
        }

        // Función de inicio de sesión
        function loginUser() {
            const email = document.getElementById("login-email").value;
            const password = document.getElementById("login-password").value;

            const user = users.find(u => u.email === email && u.password === password);
            if (user) {
                alert("Inicio de sesión exitoso.");
                showMainInterface();
            } else {
                alert("Credenciales incorrectas.");
            }
        }

        // Función de recuperación de contraseña
        function forgotPassword() {
            const email = prompt("Ingresa tu correo electrónico:");
            const user = users.find(u => u.email === email);
            if (user) {
                alert(`Tu contraseña es: ${user.password}`);
            } else {
                alert("Correo no registrado.");
            }
        }

        // Función para guardar la encuesta
        function saveSurvey() {
            const q1 = document.getElementById("q1").value;
            const q2 = document.getElementById("q2").value;
            const q3 = document.getElementById("q3").value;
            if (q1 && q2 && q3) {
                document.getElementById("survey-results").innerHTML = `
                    <h4>Resultados de la Encuesta:</h4>
                    <p><strong>Pregunta 1:</strong> ${q1}</p>
                    <p><strong>Pregunta 2:</strong> ${q2}</p>
                    <p><strong>Pregunta 3:</strong> ${q3}</p>
                `;
                alert("Encuesta guardada.");
                showMainInterface();
            } else {
                alert("Por favor, completa todas las preguntas.");
            }
        }
    </script>
</body>
</html>
