<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registro Torneo Futbol 7 - Elyon Yireh</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background: #667eea;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            background: white;
            padding: 30px;
            border-radius: 8px;
            width: 100%;
            max-width: 500px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
        }

        h1 {
            text-align: center;
            color: #333;
            margin-bottom: 10px;
            font-size: 24px;
        }

        .subtitle {
            text-align: center;
            color: #666;
            margin-bottom: 25px;
            font-size: 14px;
        }

        .section-title {
            background: #667eea;
            color: white;
            padding: 10px;
            margin: 20px 0 15px 0;
            border-radius: 5px;
            font-size: 14px;
            font-weight: bold;
        }

        .form-group {
            margin-bottom: 12px;
        }

        label {
            display: block;
            margin-bottom: 4px;
            color: #333;
            font-size: 13px;
            font-weight: bold;
        }

        input, select {
            width: 100%;
            padding: 8px;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 13px;
            font-family: Arial, sans-serif;
        }

        input:focus, select:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 5px rgba(102, 126, 234, 0.3);
        }

        .two-columns {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
        }

        .player {
            background: #f5f5f5;
            padding: 12px;
            margin-bottom: 10px;
            border-radius: 4px;
            border-left: 4px solid #667eea;
        }

        .player-title {
            font-weight: bold;
            color: #333;
            margin-bottom: 8px;
            font-size: 12px;
        }

        .checkbox-group {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-top: 10px;
        }

        .checkbox-group input[type="checkbox"] {
            width: auto;
        }

        .checkbox-group label {
            margin: 0;
            font-weight: normal;
        }

        .btn-group {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-top: 25px;
        }

        button {
            padding: 10px;
            border: none;
            border-radius: 4px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }

        .btn-submit {
            background: #667eea;
            color: white;
        }

        .btn-submit:hover {
            background: #5568d3;
        }

        .btn-reset {
            background: #ddd;
            color: #333;
        }

        .btn-reset:hover {
            background: #ccc;
        }

        .btn-add {
            background: #28a745;
            color: white;
            width: 100%;
            margin-top: 10px;
        }

        .btn-add:hover {
            background: #218838;
        }

        .btn-remove {
            background: #dc3545;
            color: white;
            padding: 5px 10px;
            font-size: 12px;
            width: 100%;
            margin-top: 8px;
        }

        .btn-remove:hover {
            background: #c82333;
        }

        .message {
            padding: 12px;
            margin-bottom: 15px;
            border-radius: 4px;
            text-align: center;
            font-size: 13px;
            display: none;
        }

        .success {
            background: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }

        .error {
            background: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }

        @media (max-width: 600px) {
            .two-columns {
                grid-template-columns: 1fr;
            }
            .btn-group {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>⚽ Torneo Futbol 7</h1>
        <p class="subtitle">Elyon Yireh</p>

        <div id="mensaje" class="message"></div>

        <form id="form">
            <!-- EQUIPO -->
            <div class="section-title">📌 DATOS DEL EQUIPO</div>

            <div class="form-group">
                <label>Nombre del Equipo *</label>
                <input type="text" name="nombreEquipo" required>
            </div>

            <div class="two-columns">
                <div class="form-group">
                    <label>Ciudad *</label>
                    <select name="ciudad" required>
                        <option value="">Seleccionar</option>
                        <option value="Bogotá">Bogotá</option>
                        <option value="Medellín">Medellín</option>
                        <option value="Cali">Cali</option>
                        <option value="Barranquilla">Barranquilla</option>
                        <option value="Cartagena">Cartagena</option>
                        <option value="Otra">Otra</option>
                    </select>
                </div>
                <div class="form-group">
                    <label>Estado *</label>
                    <select name="estado" required>
                        <option value="activo">Activo</option>
                        <option value="inactivo">Inactivo</option>
                    </select>
                </div>
            </div>

            <!-- ENCARGADO -->
            <div class="section-title">👤 RESPONSABLE DEL EQUIPO</div>

            <div class="form-group">
                <label>Nombre Completo *</label>
                <input type="text" name="encargadoNombre" required>
            </div>

            <!-- JUGADORES -->
            <div class="section-title">⚽ JUGADORES (7 REQUERIDOS)</div>

            <div id="jugadores"></div>

            <button type="button" class="btn-add" onclick="agregarJugador()">+ Agregar Jugador</button>

            <!-- BOTONES -->
            <div class="btn-group">
                <button type="submit" class="btn-submit">Registrar</button>
                <button type="reset" class="btn-reset">Limpiar</button>
            </div>
        </form>
    </div>

    <script>
        let numJugadores = 0;

        function agregarJugador() {
            if (numJugadores >= 7) {
                mostrarMensaje('Máximo 7 jugadores', 'error');
                return;
            }

            numJugadores++;
            const div = document.createElement('div');
            div.className = 'player';
            div.id = jugador-${numJugadores};
            div.innerHTML = `
                <div class="player-title">Jugador #${numJugadores}</div>
                
                <input type="text" name="nombreJugador_${numJugadores}" placeholder="Nombre" required>
                
                <div class="two-columns">
                    <input type="number" name="numero_${numJugadores}" placeholder="Número" min="1" max="99" required>
                    <select name="posicion_${numJugadores}" required>
                        <option value="">Posición</option>
                        <option value="Portero">Portero</option>
                        <option value="Defensa">Defensa</option>
                        <option value="Centrocampista">Centrocampista</option>
                        <option value="Delantero">Delantero</option>
                    </select>
                </div>

                <div class="checkbox-group">
                    <input type="checkbox" name="capitan_${numJugadores}" id="cap_${numJugadores}">
                    <label for="cap_${numJugadores}">Capitán</label>
                </div>

                ${numJugadores > 1 ? <button type="button" class="btn-remove" onclick="eliminarJugador(${numJugadores})">Eliminar</button> : ''}
            `;

            document.getElementById('jugadores').appendChild(div);
        }

        function eliminarJugador(id) {
            document.getElementById(jugador-${id}).remove();
            numJugadores--;
        }

        function mostrarMensaje(texto, tipo) {
            const msg = document.getElementById('mensaje');
            msg.textContent = texto;
            msg.className = message ${tipo};
            msg.style.display = 'block';
            setTimeout(() => msg.style.display = 'none', 4000);
        }

        document.getElementById('form').addEventListener('submit', async function(e) {
            e.preventDefault();

            if (numJugadores !== 7) {
                mostrarMensaje('Debes agregar exactamente 7 jugadores', 'error');
                return;
            }

            const capitanes = document.querySelectorAll('input[name^="capitan_"]:checked');
            if (capitanes.length === 0) {
                mostrarMensaje('Debes designar un capitán', 'error');
                return;
            }

            const datos = {
                nombreEquipo: this.nombreEquipo.value,
                ciudad: this.ciudad.value,
                estado: this.estado.value,
                encargadoNombre: this.encargadoNombre.value,
                jugadores: []
            };

            for (let i = 1; i <= 7; i++) {
                datos.jugadores.push({
                    nombre: document.querySelector(input[name="nombreJugador_${i}"]).value,
                    numero: document.querySelector(input[name="numero_${i}"]).value,
                    posicion: document.querySelector(select[name="posicion_${i}"]).value,
                    esCapitan: document.querySelector(input[name="capitan_${i}"]).checked ? 1 : 0
                });
            }

            try {
                const response = await fetch('registrar.php', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify(datos)
                });

                const resultado = await response.json();

                if (resultado.success) {
                    mostrarMensaje('✓ Equipo registrado correctamente', 'success');
                    setTimeout(() => {
                        this.reset();
                        document.getElementById('jugadores').innerHTML = '';
                        numJugadores = 0;
                        agregarJugador();
                    }, 2000);
                } else {
                    mostrarMensaje('Error: ' + resultado.mensaje, 'error');
                }
            } catch (error) {
                mostrarMensaje('Error de conexión', 'error');
                console.error(error);
            }
        });

        // Agregar primer jugador al cargar
        agregarJugador();
    </script>
</body>
</html>
