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
    <div class="container" id="main-interface">
        <h2>Bienvenido</h2>
        <p>Elige una sección para continuar.</p>
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

                <label for="q3">3. ¿Has eliminado criaderos de mosquitos en tu hogar?</label>
                <textarea id="q3" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q4">4. ¿Usas insecticidas o repelentes regularmente?</label>
                <textarea id="q4" placeholder="Escribe tu respuesta aquí..."></textarea>

                <label for="q5">5. ¿Consideras importante informar a la comunidad sobre el dengue?</label>
                <textarea id="q5" placeholder="Escribe tu respuesta aquí..."></textarea>

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
            const responses = [];
            for (let i = 1; i <= 5; i++) {
                const answer = document.getElementById(`q${i}`).value.trim();
                if (!answer) {
                    alert("Por favor, responde todas las preguntas.");
                    return;
                }
                responses.push(answer);
            }

            const results = `
                <h4>Respuestas Guardadas:</h4>
                ${responses.map((res, idx) => `<p><strong>${idx + 1}:</strong> ${res}</p>`).join("")}
            `;
            document.getElementById("survey-results").innerHTML = results;
            document.getElementById("survey-form").reset();
        }
    </script>
</body>
</html>
