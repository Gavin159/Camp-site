<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Campamento IBB</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            scroll-behavior: smooth;
        }

        header {
            background-color: #5e5e5e;
            color: white;
            padding: 10px 0;
            text-align: center;
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        header h1 {
            margin: 0;
        }

        nav ul {
            list-style: none;
            padding: 0;
        }

        nav ul li {
            display: inline;
            margin: 0 10px;
        }

        nav ul li a {
            color: white;
            text-decoration: none;
        }

        section {
            padding: 20px;
            margin: 20px;
            background-color: white;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }

        #countdown {
            text-align: center;
            font-size: 2em;
            margin-top: 20px;
        }

        footer {
            text-align: center;
            padding: 10px 0;
            background-color: #5c5c5c;
            color: white;
            position: fixed;
            bottom: 0;
            width: 100%;
        }

        form label {
            display: block;
            margin: 10px 0 5px;
        }

        form input, form select, form textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
        }

        form button {
            padding: 10px 20px;
            background-color: #555555;
            color: white;
            border: none;
            cursor: pointer;
        }

        form button:hover {
            background-color: #575757;
        }

        #registrationSection {
            display: none;
        }

        .signature-pad {
            border: 1px solid #ccc;
            width: 400px;
            height: 200px;
        }

        .controls {
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Bienvenido a Campamento IBB Tarija</h1>
        <nav>
            <ul>
                <li><a href="#home" onclick="showHomeSection()">Inicio</a></li>
                <li><a href="#about" onclick="showRegistrationSection()">Registracion</a></li>
                <li><a href="#contact" onclick="showHomeSection()">Contactanos</a></li>
            </ul>
        </nav>
    </header>

    <section id="home">
        <h2>Inicio</h2>
        <p>Tenemos campamento juvenil cada año en Enero, durando más o menos una semana de puro diversión, y también tienen oportunidad de aprender de la palabra de Dios.</p>
        <div id="countdown">
            Tiempo restante para el campamento: <span id="time"></span>
        </div>
    </section>

    <section id="about">
        <h2>Registracion</h2>
        <p>Aquí pueden llenar un formulario digital para registrar para campamento. Si quieres registrar, haz clic en el botón registrar ahora.</p>
        <button onclick="showRegistrationSection()">Registrar Ahora</button>
    </section>

    <section id="registrationSection">
        <h2>Registracion por Campamento IBB Tarija</h2>
        <form id="registrationForm">
            <h4>Nombre Completo</h4>
            <label for="firstName">Nombre:</label>
            <input type="text" id="firstName" name="firstName" required>
            <label for="lastName">Apellido:</label>
            <input type="text" id="lastName" name="lastName" required>
    
            <label for="age">Edad:</label>
            <input type="number" id="age" name="age" required oninput="checkAge(this.value)">
    
            <script>
                function checkAge(age) {
                    var ageInput = document.getElementById('age');
                    if (age >= 18) {
                        ageInput.setAttribute('min', 18);
                        ageInput.setAttribute('max', age);
                    } else {
                        ageInput.setAttribute('min', 0);
                        ageInput.removeAttribute('max');
                    }
                }
            </script>
    
            <label for="birthdate">Fecha de Nacimiento:</label>
            <input type="text" id="birthdate" name="birthdate" pattern="\d{1,2}/\d{1,2}/\d{4}" placeholder="DD/MM/AAAA" required>

            <div class="radio-group">
                <label>Genero:</label>
                <input type="radio" name="genero" id="hombre" value="Hombre"><label for="hombre">Hombre</label>
                <input type="radio" name="genero" id="mujer" value="Mujer"><label for="mujer">Mujer</label>
            </div>
    
            <label for="phone">Numero de Celular:</label>
            <input type="tel" id="phone" name="phone" required>
           
            <label for="parentNameFather">Nombre de Padre:</label>
            <input type="text" id="parentNameFather" name="parentNameFather" required>
    
            <label for="parentPhoneFather">Numero de Padre:</label>
            <input type="tel" id="parentPhoneFather" name="parentPhoneFather" required>

            <label for="parentNameMother">Nombre de Madre:</label>
            <input type="text" id="parentNameMother" name="parentNameMother" required>
    
            <label for="parentPhoneMother">Numero de Madre:</label>
            <input type="tel" id="parentPhoneMother" name="parentPhoneMother" required>
    
            <label for="allergies">Alergias o condiciones (si hay):</label>
            <textarea id="allergies" name="allergies" rows="3"></textarea>
    
            <label for="camppermission">Doy permiso para que mi hijo(a) puede asistir el Campamento IBB Tarija</label>
            <input type="checkbox" id="camppermission" name="camppermission" value="yes" required>
    
            <label for="pastorCode">Código de Pastor (6 dígitos):</label>
            <input type="text" id="pastorCode" name="pastorCode" pattern="\d{6}" placeholder="Ej. 123456" required>
    
            <h2>Firma Padre/Madre</h2>
            <div class="signature-container">
                <canvas id="signature-pad" class="signature-pad"></canvas>
                <div class="controls">
                    <button type="button" id="clear-btn">Borrar</button>
                    <button type="submit">Listo!</button>
                </div>
            </div>
            <input type="hidden" id="signature-data" name="signature-data">
        </form>

        <div class="back-to-home">
            <button onclick="showHomeSection()">Home</button>
        </div>
    </section>

    <section id="contact">
        <h2>Contactanos</h2>
        <p>Numero de Celular: 55555555</p>
    </section>

    <footer>
        <p>&copy; 2024 Campamento IBB Tarija. Todos los derechos reservados.</p>
    </footer>

    <script>
        // Set the date for the upcoming camp (adjust the date and time as needed)
        const campDate = new Date("January 6, 2025 03:00:00").getTime();

        // Update the countdown every second
        const countdownInterval = setInterval(function() {
            const now = new Date().getTime();
            const timeRemaining = campDate - now;

            // Calculate days, hours, minutes, and seconds
            const days = Math.floor(timeRemaining / (1000 * 60 * 60 * 24));
            const hours = Math.floor((timeRemaining % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
            const minutes = Math.floor((timeRemaining % (1000 * 60 * 60)) / (1000 * 60));
            const seconds = Math.floor((timeRemaining % (1000 * 60)) / 1000);

            // Display the countdown
            document.getElementById("time").innerHTML = `${days}d ${hours}h ${minutes}m ${seconds}s`;

            // If the countdown is finished, display a message
            if (timeRemaining < 0) {
                clearInterval(countdownInterval);
                document.getElementById("time").innerHTML = "¡El campamento ha comenzado!";
            }
        }, 1000);

        function showHomeSection() {
            document.getElementById('home').style.display = 'block';
            document.getElementById('about').style.display = 'none';
            document.getElementById('registrationSection').style.display = 'none';
        }

        function showRegistrationSection() {
            document.getElementById('home').style.display = 'none';
            document.getElementById('about').style.display = 'block';
            document.getElementById('registrationSection').style.display = 'block';
        }
    </script>
    
</body>
</html>
