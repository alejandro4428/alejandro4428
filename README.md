<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salud - Encuesta</title>
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
            background: linear-gradient(135deg, #56CCF2, #2F80ED);
            color: #333;
        }

        h1, h2, h3 {
            color: #ffffff;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
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
            max-width: 600px;
            margin: 20px auto;
            background: #ffffff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
        }

        .section-container h3 {
            color: #2F80ED;
            margin-bottom: 15px;
        }

        p {
            font-size: 1em;
            margin-bottom: 10px;
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
            background-color: #2F80ED;
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

        /* Inputs y Textareas */
        input, textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1em;
        }

        textarea {
            height: 80px;
        }

        label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
        }

        /* Encabezados */
        .header {
            text-align: center;
            padding: 20px;
        }

        .header img {
            width: 100px;
        }

        .header p {
            color: white;
            font-size: 1.2em;
        }
    </style>
</head>
<body>
    <!-- Encabezado -->
    <div class="header">
        <img src="https://via.placeholder.com/100" alt="Logo">
        <h1>Tu Salud es Nuestra Prioridad</h1>
        <p>Protegemos tu salud y te ayudamos a prevenir enfermedades.</p>
    </div>

    <!-- Página principal -->
    <div class="container" id="main-interface">
        <h2>Bienvenido</h2>
        <p>Elige una sección para continuar.</p>
        <button class="primary" onclick="showSurvey()">Encuestas</button>
        <button class="secondary" onclick="showMonitoring()">Monitoreo</button>
    </div>

    <!-- Encuesta -->
    <div class="interface-container hidden" id="survey-section">
        <div class="section-container">
            <h3>Encuesta de Prevención</h3>
            <form id="survey-form">
                <label for="q1">1. ¿Qué medidas tomas para prevenir el dengue?</label>
                <textarea id="q1" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q2">2. ¿Sabes identificar los síntomas del dengue?</label>
                <textarea id="q2" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q3">3. ¿Qué acciones realizarías para educar a tu comunidad sobre el dengue?</label>
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

    <script>
        // Navegación
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

        // Guardar encuesta
        function saveSurvey() {
            const q1 = document.getElementById("q1").value.trim();
            const q2 = document.getElementById("q2").value.trim();
            const q3 = document.getElementById("q3").value.trim();

            if (q1 && q2 && q3) {
                const results = `
                    <h4>Respuestas Guardadas:</h4>
                    <p><strong>1:</strong> ${q1}</p>
                    <p><strong>2:</strong> ${q2}</p>
                    <p><strong>3:</strong> ${q3}</p>
                `;
                document.getElementById("survey-results").innerHTML = results;
                document.getElementById("survey-form").reset();
            } else {
                alert("Por favor, responde todas las preguntas.");
            }
        }
    </script>
</body>
</html>
