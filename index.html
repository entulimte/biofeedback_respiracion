<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Entrenamiento de Coherencia Cardíaca y Pulso</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #0f172a;
            color: #ffffff;
            padding: 15px;
        }
        .container {
            text-align: center;
            max-width: 450px;
            width: 100%;
            background: #1e293b;
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.6);
        }
        h1 { font-size: 1.5rem; color: #ff4757; margin-bottom: 4px; }
        .subtitle { font-size: 0.85rem; color: #94a3b8; margin-bottom: 15px; }

        /* Panel de Configuración */
        .config-panel {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 15px;
            background: #0f172a;
            padding: 12px;
            border-radius: 12px;
        }
        .config-group { text-align: left; }
        .config-group label { display: block; font-size: 0.75rem; color: #94a3b8; margin-bottom: 4px; }
        .config-group select {
            width: 100%;
            padding: 8px;
            background: #1e293b;
            color: #fff;
            border: 1px solid #334155;
            border-radius: 6px;
            font-size: 0.9rem;
        }

        /* Guía Respiratoria (Pelota) */
        .pacer-wrapper {
            position: relative;
            width: 110px;
            height: 110px;
            margin: 0 auto 15px;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .pacer-circle {
            width: 40px;
            height: 40px;
            background: radial-gradient(circle, #38bdf8 0%, #0284c7 100%);
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(56, 189, 248, 0.6);
            transition: transform 0.1s linear;
        }
        .pacer-text {
            position: absolute;
            font-weight: bold;
            font-size: 0.85rem;
            color: #fff;
            text-shadow: 0 2px 4px rgba(0,0,0,0.8);
            pointer-events: none;
        }

        /* Gráfica ECG */
        .ecg-container {
            position: relative;
            width: 100%;
            height: 120px;
            background: #090d16;
            border-radius: 10px;
            border: 1px solid #334155;
            margin-bottom: 15px;
            overflow: hidden;
        }
        canvas#ecgCanvas {
            width: 100%;
            height: 100%;
            display: block;
        }

        /* Indicadores y Timer */
        .timer { font-size: 1.1rem; color: #ffa502; font-weight: bold; margin-bottom: 6px; }
        .progress-bar-container {
            width: 100%; background: #334155; height: 6px; border-radius: 3px; margin-bottom: 15px; overflow: hidden;
        }
        .progress-bar { width: 0%; height: 100%; background: #ffa502; transition: width 1s linear; }

        .bpm-display { font-size: 3.5rem; font-weight: bold; color: #ff4757; line-height: 1; }
        .bpm-unit { font-size: 0.8rem; color: #94a3b8; text-transform: uppercase; margin-bottom: 15px; }

        .btn {
            background-color: #ff4757; color: white; border: none; padding: 14px;
            font-size: 1rem; font-weight: bold; border-radius: 50px; cursor: pointer;
            width: 100%; box-shadow: 0 4px 15px rgba(255, 71, 87, 0.4);
        }
        .btn:disabled { background-color: #475569; box-shadow: none; cursor: not-allowed; }

        #status { margin-top: 10px; font-size: 0.8rem; color: #94a3b8; min-height: 25px; }

        /* Tabla Comparativa */
        .results-box {
            background: #0f172a; padding: 15px; border-radius: 12px; margin-top: 15px; display: none;
        }
        .results-title { color: #2ed573; font-weight: bold; margin-bottom: 10px; }
        table { width: 100%; border-collapse: collapse; margin-top: 10px; font-size: 0.8rem; }
        th, td { padding: 8px; border: 1px solid #334155; text-align: center; }
        th { background: #1e293b; color: #38bdf8; }

        #webcam { display: none; }
        #analyzer-canvas { display: none; }
    </style>
</head>
<body>

<div class="container">
    <h1>Control de Pulso & Coherencia</h1>
    <div class="subtitle">Entrenamiento Respiratorio Personalizado</div>

    <!-- Panel de Ajustes -->
    <div class="config-panel" id="configPanel">
        <div class="config-group">
            <label for="durationSelect">Duración (Minutos):</label>
            <select id="durationSelect"></select>
        </div>
        <div class="config-group">
            <label for="rpmSelect">Respiraciones / Minuto:</label>
            <select id="rpmSelect"></select>
        </div>
    </div>

    <!-- Guía de Respiración (Pelota) -->
    <div class="pacer-wrapper">
        <div class="pacer-circle" id="pacerCircle"></div>
        <div class="pacer-text" id="pacerText">Listos</div>
    </div>

    <!-- Pantalla ECG (3 Zonas de Color) -->
    <div class="ecg-container">
        <canvas id="ecgCanvas" width="400" height="120"></canvas>
    </div>

    <div class="timer" id="timer-txt">Tiempo restante: 00:00</div>
    <div class="progress-bar-container">
        <div class="progress-bar" id="p-bar"></div>
    </div>

    <div class="bpm-display" id="bpm-val">--</div>
    <div class="bpm-unit">BPM Actual</div>

    <button class="btn" id="start-btn">INICIAR ENTRENAMIENTO</button>
    <div id="status">Ubica la cámara trasera con buena luz ambiental o coloca el dedo en el lente.</div>

    <!-- Resultados y Cuadro Comparativo -->
    <div class="results-box" id="results-panel">
        <div class="results-title">✓ EJERCICIO FINALIZADO</div>
        <table id="summaryTable">
            <thead>
                <tr>
                    <th>Sesión</th>
                    <th>Tiempo</th>
                    <th>RPM</th>
                    <th>Prom. BPM</th>
                </tr>
            </thead>
            <tbody></tbody>
        </table>
    </div>
</div>

<video id="webcam" autoplay playsinline muted></video>
<canvas id="analyzer-canvas" width="100" height="100"></canvas>

<script>
    // Referencias DOM
    const video = document.getElementById('webcam');
    const analyzerCanvas = document.getElementById('analyzer-canvas');
    const actx = analyzerCanvas.getContext('2d');
    const ecgCanvas = document.getElementById('ecgCanvas');
    const ectx = ecgCanvas.getContext('2d');

    const durationSelect = document.getElementById('durationSelect');
    const rpmSelect = document.getElementById('rpmSelect');
    const startBtn = document.getElementById('start-btn');
    const bpmVal = document.getElementById('bpm-val');
    const statusText = document.getElementById('status');
    const timerTxt = document.getElementById('timer-txt');
    const progressBar = document.getElementById('p-bar');
    const pacerCircle = document.getElementById('pacerCircle');
    const pacerText = document.getElementById('pacerText');
    const resultsPanel = document.getElementById('results-panel');
    const summaryTableBody = document.querySelector('#summaryTable tbody');

    // Poblar Selects
    for (let i = 1; i <= 30; i++) {
        let opt = document.createElement('option');
        opt.value = i; opt.textContent = `${i} min`;
        if (i === 1) opt.selected = true;
        durationSelect.appendChild(opt);
    }

    for (let i = 1; i <= 15; i++) {
        let opt = document.createElement('option');
        opt.value = i; opt.textContent = `${i} RPM`;
        if (i === 6) opt.selected = true; // 6 RPM por defecto (ritmo óptimo de coherencia)
        rpmSelect.appendChild(opt);
    }

    // Variables de Estado
    let stream = null, track = null, isRunning = false;
    let frameInterval = null, countdownInterval = null, pacerInterval = null;
    let rValues = [], times = [], allValidBpms = [];
    let sessionHistory = [];
    let sessionCount = 0;
    
    // Paleta de colores para sesiones comparativas
    const sessionColors = ['#38bdf8', '#e879f9', '#4ade80', '#fbbf24', '#f43f5e'];

    let totalDurationSec = 60;
    let timeLeft = 60;
    let lastBpm = 0;

    // Dibujar Zonas de Fondo en ECG
    function drawEcgBackground() {
        ectx.fillStyle = '#090d16';
        ectx.fillRect(0, 0, ecgCanvas.width, ecgCanvas.height);

        // Zona < 70 BPM (Verde)
        ectx.fillStyle = 'rgba(46, 213, 115, 0.1)';
        ectx.fillRect(0, ecgCanvas.height * 0.6, ecgCanvas.width, ecgCanvas.height * 0.4);

        // Zona 70 - 100 BPM (Amarillo)
        ectx.fillStyle = 'rgba(255, 165, 2, 0.1)';
        ectx.fillRect(0, ecgCanvas.height * 0.3, ecgCanvas.width, ecgCanvas.height * 0.3);

        // Zona > 100 BPM (Rojo)
        ectx.fillStyle = 'rgba(255, 71, 87, 0.1)';
        ectx.fillRect(0, 0, ecgCanvas.width, ecgCanvas.height * 0.3);

        // Líneas divisoras
        ectx.strokeStyle = '#334155';
        ectx.lineWidth = 1;
        ectx.beginPath();
        ectx.moveTo(0, ecgCanvas.height * 0.3); ectx.lineTo(ecgCanvas.width, ecgCanvas.height * 0.3);
        ectx.moveTo(0, ecgCanvas.height * 0.6); ectx.lineTo(ecgCanvas.width, ecgCanvas.height * 0.6);
        ectx.stroke();
    }

    drawEcgBackground();

    // Lógica del Pacer (Respiración)
    function startPacer(rpm) {
        const cycleDuration = 60 / rpm; // segundos por ciclo
        const inhaleTime = cycleDuration * 0.4;
        const holdTime = cycleDuration * 0.2;
        const exhaleTime = cycleDuration * 0.4;

        let startTime = performance.now();

        pacerInterval = setInterval(() => {
            if (!isRunning) return;
            let elapsed = ((performance.now() - startTime) / 1000) % cycleDuration;

            if (elapsed < inhaleTime) {
                let progress = elapsed / inhaleTime;
                let scale = 1 + progress * 1.2; // Inflar
                pacerCircle.style.transform = `scale(${scale})`;
                pacerText.textContent = "Inhala";
            } else if (elapsed < inhaleTime + holdTime) {
                pacerCircle.style.transform = `scale(2.2)`;
                pacerText.textContent = "Retén";
            } else {
                let progress = (elapsed - (inhaleTime + holdTime)) / exhaleTime;
                let scale = 2.2 - progress * 1.2; // Desinflar
                pacerCircle.style.transform = `scale(${scale})`;
                pacerText.textContent = "Exhala";
            }
        }, 50);
    }

    // Dibujar ECG
    function drawEcgPoint(bpm) {
        let color = sessionColors[sessionCount % sessionColors.length];
        
        // Mapear BPM (40-140) a la altura del Canvas
        let y = ecgCanvas.height - ((bpm - 40) / 100) * ecgCanvas.height;
        y = Math.max(5, Math.min(ecgCanvas.height - 5, y));

        let x = ((totalDurationSec - timeLeft) / totalDurationSec) * ecgCanvas.width;

        ectx.strokeStyle = color;
        ectx.lineWidth = 2;
        if (allValidBpms.length === 1) {
            ectx.beginPath();
            ectx.moveTo(x, y);
        } else {
            ectx.lineTo(x, y);
            ectx.stroke();
        }
    }

    startBtn.addEventListener('click', async () => {
        if (isRunning) { stopMeasurement(false); return; }

        totalDurationSec = parseInt(durationSelect.value) * 60;
        timeLeft = totalDurationSec;
        let selectedRpm = parseInt(rpmSelect.value);

        startBtn.disabled = true;
        statusText.textContent = "Iniciando cámara...";
        allValidBpms = [];
        rValues = []; times = []; lastBpm = 0;

        try {
            stream = await navigator.mediaDevices.getUserMedia({
                video: { facingMode: "environment", width: { ideal: 300 }, height: { ideal: 300 } }
            });

            video.srcObject = stream;
            track = stream.getVideoTracks()[0];

            try { await track.applyConstraints({ advanced: [{ torch: true }] }); } catch (e) {}

            startBtn.textContent = "DETENER / ABORTAR";
            startBtn.disabled = false;
            isRunning = true;

            drawEcgBackground(); // Limpiar previo pero mantener fondo
            startPacer(selectedRpm);

            frameInterval = setInterval(processFrame, 1000 / 30);
            
            countdownInterval = setInterval(() => {
                timeLeft--;
                let m = Math.floor(timeLeft / 60).toString().padStart(2, '0');
                let s = (timeLeft % 60).toString().padStart(2, '0');
                timerTxt.textContent = `Tiempo restante: ${m}:${s}`;
                progressBar.style.width = `${((totalDurationSec - timeLeft) / totalDurationSec) * 100}%`;

                if (timeLeft <= 0) stopMeasurement(true);
            }, 1000);

            statusText.textContent = "Coloca firmemente tu dedo cubriendo el lente.";

        } catch (error) {
            statusText.textContent = "Error al acceder a la cámara trasera.";
            startBtn.disabled = false;
        }
    });

    function stopMeasurement(isCompleted = false) {
        isRunning = false;
        clearInterval(frameInterval);
        clearInterval(countdownInterval);
        clearInterval(pacerInterval);

        pacerCircle.style.transform = `scale(1)`;
        pacerText.textContent = "Listo";

        if (track) { try { track.stop(); } catch(e){} }
        if (stream) { stream.getTracks().forEach(t => t.stop()); }

        startBtn.textContent = "INICIAR ENTRENAMIENTO";
        bpmVal.textContent = "--";

        if (isCompleted) {
            statusText.textContent = "Sesión completada con éxito.";
            let avg = allValidBpms.length > 0 ? Math.round(allValidBpms.reduce((a, b) => a + b, 0) / allValidBpms.length) : '--';
            
            sessionCount++;
            sessionHistory.push({
                session: sessionCount,
                duration: `${durationSelect.value} min`,
                rpm: rpmSelect.value,
                avgBpm: avg,
                color: sessionColors[(sessionCount - 1) % sessionColors.length]
            });

            renderSummaryTable();
            resultsPanel.style.display = "block";
        } else {
            statusText.textContent = "Sesión abortada por el usuario.";
        }
    }

    function renderSummaryTable() {
        summaryTableBody.innerHTML = '';
        sessionHistory.forEach(s => {
            let tr = document.createElement('tr');
            tr.innerHTML = `
                <td style="color:${s.color}; font-weight:bold;">#${s.session}</td>
                <td>${s.duration}</td>
                <td>${s.rpm} RPM</td>
                <td style="font-weight:bold; color:#38bdf8;">${s.avgBpm} BPM</td>
            `;
            summaryTableBody.appendChild(tr);
        });
    }

    function processFrame() {
        if (!isRunning || video.paused || video.ended) return;

        actx.drawImage(video, 0, 0, analyzerCanvas.width, analyzerCanvas.height);
        const imgData = actx.getImageData(0, 0, analyzerCanvas.width, analyzerCanvas.height);
        const data = imgData.data;

        let totalRed = 0;
        for (let i = 0; i < data.length; i += 4) totalRed += data[i];

        const avgRed = totalRed / (data.length / 4);
        rValues.push(avgRed);
        times.push(performance.now());

        if (rValues.length > 120) { rValues.shift(); times.shift(); }
        if (rValues.length >= 80) calculateBPM();
    }

    function calculateBPM() {
        let peaks = [], smoothValues = [];
        for (let i = 3; i < rValues.length - 3; i++) {
            let val = (rValues[i-3] + rValues[i-2] + rValues[i-1] + rValues[i] + rValues[i+1] + rValues[i+2] + rValues[i+3]) / 7;
            smoothValues.push({val: val, time: times[i]});
        }

        for (let i = 1; i < smoothValues.length - 1; i++) {
            if (smoothValues[i].val > smoothValues[i-1].val && smoothValues[i].val > smoothValues[i+1].val) {
                peaks.push(smoothValues[i].time);
            }
        }

        if (peaks.length >= 3) {
            let intervals = [];
            for (let i = 1; i < peaks.length; i++) intervals.push(peaks[i] - peaks[i-1]);
            const avgInterval = intervals.reduce((a, b) => a + b, 0) / intervals.length;
            let bpm = Math.round(60000 / avgInterval);

            if (bpm >= 40 && bpm <= 140) {
                if (lastBpm === 0) lastBpm = bpm;
                lastBpm = Math.round(lastBpm * 0.85 + bpm * 0.15);
                bpmVal.textContent = lastBpm;
                allValidBpms.push(lastBpm);
                drawEcgPoint(lastBpm);
            }
        }
    }
</script>
</body>
</html>
