

<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>El Tianguis - Audio Tienda Pro</title>
    <style>
        body {
            font-family: 'Arial Black', Impact, sans-serif;
            background-color: #f4f6f9;
            color: #1a2536;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 15px;
            box-sizing: border-box;
        }
        .container {
            text-align: center;
            background-color: #ffffff;
            padding: 25px 20px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            max-width: 400px;
            width: 100%;
        }
        
        /* --- DISEÑO DE LOGO VECTORIAL --- */
        .logo-container {
            width: 130px;
            height: 130px;
            margin: 0 auto 10px auto;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .logo-svg {
            width: 100%;
            height: 100%;
        }

        /* --- TEXTOS PRINCIPALES --- */
        .brand-title {
            font-size: 38px;
            color: #1a2536;
            margin: 0;
            text-transform: uppercase;
            letter-spacing: -1px;
        }
        .brand-subtitle {
            font-size: 26px;
            color: #2b7a43;
            margin: 0 0 15px 0;
            text-transform: uppercase;
            letter-spacing: -0.5px;
        }
        .description {
            font-family: 'Segoe UI', Roboto, sans-serif;
            color: #55637a;
            font-size: 14px;
            line-height: 1.5;
            margin-bottom: 25px;
            font-weight: 500;
        }

        /* --- SECCIONES Y CONTROLES --- */
        .seccion {
            font-family: 'Segoe UI', Roboto, sans-serif;
            background-color: #f8fafc;
            border: 1px solid #e2e8f0;
            padding: 15px;
            border-radius: 14px;
            margin-bottom: 15px;
            text-align: left;
        }
        .seccion-titulo {
            font-size: 15px;
            color: #64748b;
            margin-bottom: 12px;
            font-weight: 600;
        }

        /* --- SELECTOR DE TIEMPO MANUAL --- */
        .input-tiempo-container {
            display: flex;
            align-items: center;
            justify-content: space-between;
            background-color: #ffffff;
            border: 1px solid #cbd5e1;
            padding: 10px 15px;
            border-radius: 10px;
            margin-bottom: 12px;
        }
        .input-tiempo-container label {
            font-size: 14px;
            color: #1a2536;
            font-weight: bold;
        }
        .input-tiempo-container input {
            width: 70px;
            padding: 8px;
            font-size: 16px;
            font-weight: bold;
            text-align: center;
            border: 2px solid #1a2536;
            border-radius: 6px;
            color: #1a2536;
        }

        /* --- BOTONES --- */
        button {
            font-family: 'Segoe UI', Roboto, sans-serif;
            color: white;
            border: none;
            padding: 12px 18px;
            font-size: 15px;
            font-weight: bold;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.2s ease;
            width: 100%;
            margin: 4px 0;
        }
        button:active { transform: scale(0.99); }
        
        .btn-grabar { background-color: #007bff; }
        .btn-grabar.grabando { background-color: #dc3545; animation: parpadeo 1s infinite; }
        .btn-play { background-color: #1a2536; }
        .btn-play.stop { background-color: #dc3545; }
        button:disabled { background-color: #cbd5e1; color: #94a3b8; cursor: not-allowed; }

        /* --- DISPLAY DE ESTADO Y TIEMPO --- */
        .display-box {
            display: flex;
            border: 1px solid #1a2536;
            border-radius: 8px;
            overflow: hidden;
            margin-top: 10px;
            background: #ffffff;
        }
        .display-left, .display-right {
            flex: 1;
            padding: 12px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }
        .display-left {
            border-right: 1px solid #1a2536;
            background-color: #f8fafc;
        }
        .display-label {
            font-size: 11px;
            color: #64748b;
            font-weight: bold;
            text-transform: uppercase;
            margin-bottom: 4px;
        }
        .status-text {
            font-size: 14px;
            color: #1a2536;
            font-weight: bold;
        }
        .timer {
            font-size: 34px;
            font-weight: 800;
            color: #2b7a43;
            font-variant-numeric: tabular-nums;
            line-height: 1;
        }

        /* --- CINTILLO MARCAS INFERIOR --- */
        .cintillo-saldos {
            background-color: #ff7d52;
            color: #ffffff;
            font-size: 18px;
            padding: 8px;
            border-radius: 6px;
            margin-top: 25px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        .marcas-grid {
            font-family: 'Segoe UI', Roboto, sans-serif;
            display: flex;
            justify-content: space-around;
            align-items: center;
            margin-top: 12px;
            padding: 0 5px;
        }
        .marca {
            font-size: 13px;
            font-weight: 800;
            color: #475569;
        }
        .marca-cvs { color: #cc0000; display: flex; align-items: center; gap: 2px;}
        .marca-amazon { color: #232f3e; font-style: italic; }
        .marca-target { color: #cc0000; font-weight: 900; }
        .marca-walmart { color: #0071dc; }

        @keyframes parpadeo {
            0% { opacity: 1; }
            50% { opacity: 0.6; }
            100% { opacity: 1; }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="logo-container">
        <svg class="logo-svg" viewBox="0 0 512 512" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M166 210V140C166 90.3 206.3 50 256 50C305.7 50 346 90.3 346 140V210" stroke="#f07e54" stroke-width="32" stroke-linecap="round"/>
            <path d="M166 210H380C410 210 426 235 422 265L392 435C388 455 370 470 350 470H256C254 415 210 370 155 370C155 340 140 290 150 265C155 240 146 210 166 210Z" fill="#f07e54"/>
            <path d="M155 370C210 370 254 415 256 470H115C95 470 80 452 83 432L93 376C98 346 125 370 155 370Z" fill="#ffffff"/>
            <path d="M165 345L70 425C62 432 50 424 54 414L102 300C107 288 123 286 130 297L164 328C171 334 171 340 165 345Z" fill="#1a2536"/>
        </svg>
    </div>
    
    <div class="brand-title">El Tianguis</div>
    <div class="brand-subtitle">Audio Tienda Pro</div>
    
    <p class="description">
        Graba tus anuncios de ofertas. Define los minutos de espera y sonarán interrumpiendo sutilmente la música de streaming.
    </p>
    
    <div class="seccion">
        <div class="seccion-titulo">1. Grabar Anuncio</div>
        <button id="btnGrabar" class="btn-grabar" onclick="toglearGrabacion()">Grabar Micrófono</button>
        <div id="estadoGrabacion" style="font-size: 12px; color: #64748b; margin-top: 5px; font-weight: 500; text-align: center;">Sin audio grabado</div>
    </div>

    <div class="seccion">
        <div class="seccion-titulo">2. Ajuste de Tiempo y Control</div>
        
        <div class="input-tiempo-container">
            <label for="inputMinutos">Repetir cada (minutos):</label>
            <input type="number" id="inputMinutos" value="30" min="1" max="120">
        </div>

        <button id="btnSistema" class="btn-play" onclick="toglearSistema()" disabled>Iniciar Sistema</button>
        
        <div class="display-box">
            <div class="display-left">
                <span class="display-label">Estado</span>
                <span id="estadoSistema" class="status-text">Apagado</span>
            </div>
            <div class="display-right">
                <span class="display-label">Próximo Audio</span>
                <div class="timer" id="cuentaRegresiva">00:00</div>
            </div>
        </div>
    </div>

    <div class="cintillo-saldos">Saldos Americanos</div>
    <div class="marcas-grid">
        <span class="marca marca-cvs">❤️CVS</span>
        <span class="marca marca-amazon">amazon</span>
        <span class="marca marca-target">🎯TARGET</span>
        <span class="marca marca-walmart">Walmart☀️</span>
    </div>
</div>

<script>
    let mediaRecorder;
    let audioBlobs = [];
    let audioUrl = null;
    let audioAnuncio = new Audio();
    
    let sistemaActivo = false;
    let intervalo;
    let tiempoRestante = 0;
    let wakeLock = null;

    const btnGrabar = document.getElementById('btnGrabar');
    const estadoGrabacion = document.getElementById('estadoGrabacion');
    const btnSistema = document.getElementById('btnSistema');
    const estadoSistema = document.getElementById('estadoSistema');
    const cuentaRegresivaTxt = document.getElementById('cuentaRegresiva');
    const inputMinutos = document.getElementById('inputMinutos');

    actualizarRelojVisual(inputMinutos.value * 60);

    inputMinutos.addEventListener('input', () => {
        if (!sistemaActivo) {
            let mins = parseInt(inputMinutos.value) || 0;
            actualizarRelojVisual(mins * 60);
        }
    });

    async function toglearGrabacion() {
        if (!mediaRecorder || mediaRecorder.state === "inactive") {
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
                mediaRecorder = new MediaRecorder(stream);
                audioBlobs = [];

                mediaRecorder.ondataavailable = event => { audioBlobs.push(event.data); };

                mediaRecorder.onstop = () => {
                    const audioBlob = new Blob(audioBlobs, { type: 'audio/mp3' });
                    audioUrl = URL.createObjectURL(audioBlob);
                    audioAnuncio.src = audioUrl;
                    
                    estadoGrabacion.textContent = "¡Audio guardado correctamente!";
                    btnSistema.disabled = false;
                };

                mediaRecorder.start();
                btnGrabar.textContent = "🛑 Detener Grabación";
                btnGrabar.className = "btn-grabar grabando";
                estadoGrabacion.textContent = "Grabando desde el micrófono...";
                
                if(sistemaActivo) toglearSistema();
                
            } catch (err) {
                alert("Por favor concede permisos para usar el micrófono.");
                console.error(err);
            }
        } else {
            mediaRecorder.stop();
            mediaRecorder.stream.getTracks().forEach(track => track.stop());
            btnGrabar.textContent = "Grabar Nuevo Audio";
            btnGrabar.className = "btn-grabar";
        }
    }

    async function activarMantenerPantalla() {
        try { if ('wakeLock' in navigator) { wakeLock = await navigator.wakeLock.request('screen'); } } catch (err) {}
    }
    function desactivarMantenerPantalla() { if (wakeLock !== null) { wakeLock.release(); wakeLock = null; } }

    function toglearSistema() {
        if (!sistemaActivo) {
            if (!audioUrl) return;
            
            sistemaActivo = true;
            btnSistema.textContent = "Detener Sistema";
            btnSistema.className = "btn-play stop";
            estadoSistema.textContent = "Activo";
            btnGrabar.disabled = true;
            inputMinutos.disabled = true; 
            
            activarMantenerPantalla();
            reproducirAnuncio(); 
        } else {
            sistemaActivo = false;
            clearInterval(intervalo);
            audioAnuncio.pause();
            audioAnuncio.currentTime = 0;
            btnSistema.textContent = "Iniciar Sistema";
            btnSistema.className = "btn-play";
            estadoSistema.textContent = "Apagado";
            btnGrabar.disabled = false;
            inputMinutos.disabled = false;
            
            let mins = parseInt(inputMinutos.value) || 30;
            actualizarRelojVisual(mins * 60);
            
            desactivarMantenerPantalla();
        }
    }

    function reproducirAnuncio() {
        estadoSistema.textContent = "Sonando...";
        
        audioAnuncio.play().catch(error => {
            console.log("Error de reproducción: ", error);
        });

        audioAnuncio.onended = function() {
            estadoSistema.textContent = "Esperando";
            reiniciarTemporizador();
        };
    }

    function reiniciarTemporizador() {
        clearInterval(intervalo);
        
        let minutosManuales = parseInt(inputMinutos.value) || 30;
        tiempoRestante = minutosManuales * 60; 
        
        actualizarRelojVisual(tiempoRestante);
        
        intervalo = setInterval(() => {
            tiempoRestante--;
            actualizarRelojVisual(tiempoRestante);
            if (tiempoRestante <= 0) {
                clearInterval(intervalo);
                reproducirAnuncio();
            }
        }, 1000);
    }

    function actualizarRelojVisual(segundosTotales) {
        let minutos = Math.floor(segundosTotales / 60);
        let segundos = segundosTotales % 60;
        minutos = minutos < 10 ? "0" + minutos : minutes;
        segundos = segundos < 10 ? "0" + segundos : segundos;
        cuentaRegresivaTxt.textContent = `${minutos}:${segundos}`;
    }
</script>

</body>
</html>


