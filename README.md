<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inicio de Sesión</title>
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
        .login-container {
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
        .forgot-password {
            text-align: center;
            margin-top: 10px;
        }
        .forgot-password a {
            color: #007BFF;
            text-decoration: none;
        }
        .forgot-password a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <div class="login-container">
        <h1>Iniciar Sesión</h1>
        <form action="/login" method="post">
            <label for="username">Usuario</label>
            <input type="text" id="username" name="username" placeholder="Ingresa tu usuario" required>
            
            <label for="password">Contraseña</label>
            <input type="password" id="password" name="password" placeholder="Ingresa tu contraseña" required>
            
            <button type="submit">Ingresar</button>
        </form>
        <div class="forgot-password">
            <a href="#">¿Olvidaste tu contraseña?</a>
        </div>
    </div>
</body>
</html>
