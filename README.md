<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro e Inicio de Sesión</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f4f4f4;
        }
        .container {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            width: 300px;
        }
        h1 {
            font-size: 1.5em;
            text-align: center;
            margin-bottom: 20px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: bold;
        }
        input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            width: 100%;
            padding: 10px;
            background-color: #007BFF;
            border: none;
            color: white;
            border-radius: 5px;
            font-size: 1em;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .link {
            text-align: center;
            margin-top: 10px;
        }
        .link a {
            color: #007BFF;
            text-decoration: none;
        }
        .link a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="container" id="login-form">
        <h1>Iniciar Sesión</h1>
        <form id="form-login">
            <label for="email-login">Correo Electrónico</label>
            <input type="email" id="email-login" name="email-login" placeholder="Ingresa tu correo" required>
            
            <label for="password-login">Contraseña</label>
            <input type="password" id="password-login" name="password-login" placeholder="Ingresa tu contraseña" required>
            
            <button type="button" onclick="login()">Ingresar</button>
        </form>
        <div class="link">
            <a href="#" onclick="showResetPassword()">¿Olvidaste tu contraseña?</a>
        </div>
        <div class="link">
            <a href="#" onclick="showRegister()">¿No tienes cuenta? Regístrate</a>
        </div>
    </div>

    <div class="container" id="register-form" style="display: none;">
        <h1>Registro</h1>
        <form id="form-register">
            <label for="email-register">Correo Electrónico</label>
            <input type="email" id="email-register" name="email-register" placeholder="Ingresa tu correo" required>
            
            <label for="password-register">Contraseña</label>
            <input type="password" id="password-register" name="password-register" placeholder="Crea tu contraseña" required>
            
            <button type="button" onclick="register()">Registrarse</button>
        </form>
        <div class="link">
            <a href="#" onclick="showLogin()">Ya tengo una cuenta</a>
        </div>
    </div>

    <div class="container" id="reset-form" style="display: none;">
        <h1>Recuperar Contraseña</h1>
        <form id="form-reset">
            <label for="email-reset">Correo Electrónico</label>
            <input type="email" id="email-reset" name="email-reset" placeholder="Ingresa tu correo" required>
            
            <button type="button" onclick="resetPassword()">Recuperar</button>
        </form>
        <div class="link">
            <a href="#" onclick="showLogin()">Volver al inicio de sesión</a>
        </div>
    </div>

    <script>
        // Simulación de una base de datos
        const users = {};

        // Mostrar formularios
        function showLogin() {
            document.getElementById("login-form").style.display = "block";
            document.getElementById("register-form").style.display = "none";
            document.getElementById("reset-form").style.display = "none";
        }

        function showRegister() {
            document.getElementById("login-form").style.display = "none";
            document.getElementById("register-form").style.display = "block";
            document.getElementById("reset-form").style.display = "none";
        }

        function showResetPassword() {
            document.getElementById("login-form").style.display = "none";
            document.getElementById("register-form").style.display = "none";
            document.getElementById("reset-form").style.display = "block";
        }

        // Función para registrar un usuario
        function register() {
            const email = document.getElementById("email-register").value;
            const password = document.getElementById("password-register").value;

            if (users[email]) {
                alert("Este correo ya está registrado.");
            } else {
                users[email] = password;
                alert("Registro exitoso.");
                showLogin();
            }
        }

        // Función para iniciar sesión
        function login() {
            const email = document.getElementById("email-login").value;
            const password = document.getElementById("password-login").value;

            if (users[email] && users[email] === password) {
                alert("Inicio de sesión exitoso.");
            } else {
                alert("Correo o contraseña incorrectos.");
            }
        }

        // Función para recuperar contraseña
        function resetPassword() {
            const email = document.getElementById("email-reset").value;

            if (users[email]) {
                alert(`Tu contraseña es: ${users[email]}`);
            } else {
                alert("Correo no registrado.");
            }
        }
    </script>
</body>
</html>
