<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Data Analysis Tool</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", system-ui, sans-serif;
    }

    body {
      background: #050816;
      color: #e5e7eb;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 24px;
    }

    .app {
      width: 100%;
      max-width: 960px;
      background: radial-gradient(circle at top left, #1f2937, #020617);
      border-radius: 18px;
      box-shadow: 0 22px 45px rgba(15, 23, 42, 0.9);
      padding: 24px 24px 16px;
      border: 1px solid rgba(148, 163, 184, 0.35);
    }

    .header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
      gap: 16px;
      flex-wrap: wrap;
    }

    .title-wrap h1 {
      font-size: 1.5rem;
      font-weight: 600;
      letter-spacing: 0.02em;
    }

    .title-wrap p {
      font-size: 0.9rem;
      color: #9ca3af;
      margin-top: 4px;
    }

    .badge {
      font-size: 0.75rem;
      padding: 4px 10px;
      border-radius: 999px;
      border: 1px solid rgba(96, 165, 250, 0.6);
      background: rgba(15, 23, 42, 0.7);
      color: #bfdbfe;
      white-space: nowrap;
    }

    .layout {
      display: grid;
      grid-template-columns: 3fr 2fr;
      gap: 18px;
    }

    @media (max-width: 768px) {
      .layout {
        grid-template-columns: 1fr;
      }
    }

    .card {
      background: rgba(15, 23, 42, 0.75);
      border-radius: 14px;
      border: 1px solid rgba(55, 65, 81, 0.9);
      padding: 14px 14px 10px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .card-header {
      display: flex;
      justify-content: space-between;
      align-items: baseline;
      gap: 8px;
    }

    .card-header h2 {
      font-size: 0.95rem;
      font-weight: 600;
    }

    .card-header span {
      font-size: 0.75rem;
      color: #9ca3af;
    }

    label {
      font-size: 0.8rem;
      color: #d1d5db;
      display: block;
      margin-bottom: 4px;
    }

    textarea,
    input {
      width: 100%;
      background: rgba(15, 23, 42, 0.9);
      border-radius: 10px;
      border: 1px solid rgba(55, 65, 81, 0.9);
      color: #e5e7eb;
      padding: 8px 10px;
      font-size: 0.85rem;
      outline: none;
      resize: vertical;
      min-height: 90px;
    }

    textarea:focus,
    input:focus {
      border-color: #60a5fa;
      box-shadow: 0 0 0 1px rgba(37, 99, 235, 0.6);
    }

    .hint {
      font-size: 0.75rem;
      color: #9ca3af;
      margin-top: 2px;
    }

    .controls {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 4px;
    }

    button {
      border: none;
      cursor: pointer;
      border-radius: 999px;
      padding: 6px 14px;
      font-size: 0.8rem;
      font-weight: 500;
      display: inline-flex;
      align-items: center;
      gap: 6px;
      transition: transform 0.08s ease, box-shadow 0.08s ease, background 0.1s ease;
    }

    .btn-primary {
      background: linear-gradient(to right, #2563eb, #4f46e5);
      color: #e5e7eb;
      box-shadow: 0 9px 20px rgba(37, 99, 235, 0.55);
    }

    .btn-primary:hover {
      transform: translateY(-1px);
      box-shadow: 0 12px 26px rgba(37, 99, 235, 0.7);
    }

    .btn-secondary {
      background: rgba(15, 23, 42, 0.95);
      border: 1px solid rgba(75, 85, 99, 0.9);
      color: #d1d5db;
    }

    .btn-secondary:hover {
      background: rgba(31, 41, 55, 0.9);
    }

    .stats-grid {
      display: grid;
      grid-template-columns: repeat(2, minmax(0, 1fr));
      gap: 8px;
      margin-top: 4px;
    }

    .stat {
      background: radial-gradient(circle at top, rgba(37, 99, 235, 0.17), rgba(17, 24, 39, 0.9));
      border-radius: 10px;
      padding: 8px 9px;
      border: 1px solid rgba(55, 65, 81, 0.9);
    }

    .stat-label {
      font-size: 0.7rem;
      color: #9ca3af;
      margin-bottom: 2px;
    }

    .stat-value {
      font-size: 0.95rem;
      font-weight: 600;
    }

    .stat-secondary {
      font-size: 0.7rem;
      color: #9ca3af;
      margin-top: 2px;
    }

    .log {
      max-height: 160px;
      overflow-y: auto;
      font-size: 0.78rem;
      padding-right: 4px;
    }

    .log-entry {
      padding: 4px 0;
      border-bottom: 1px solid rgba(31, 41, 55, 0.9);
      display: flex;
      justify-content: space-between;
      gap: 6px;
    }

    .log-entry span {
      white-space: nowrap;
    }

    .log-entry small {
      color: #9ca3af;
      white-space: nowrap;
    }

    .pill {
      display: inline-flex;
      align-items: center;
      gap: 4px;
      padding: 2px 8px;
      border-radius: 999px;
      font-size: 0.7rem;
      background: rgba(15, 23, 42, 0.9);
      border: 1px solid rgba(75, 85, 99, 0.9);
    }

    .chart {
      width: 100%;
      height: 140px;
      border-radius: 10px;
      background: radial-gradient(circle at top, rgba(6, 182, 212, 0.18), rgba(15, 23, 42, 0.95));
      border: 1px solid rgba(55, 65, 81, 0.9);
      padding: 8px;
    }

    canvas {
      width: 100%;
      height: 100%;
    }

    .footer {
      margin-top: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      font-size: 0.75rem;
      color: #6b7280;
    }

    .footer span {
      white-space: nowrap;
    }

    .footer small {
      color: #9ca3af;
    }
  </style>
</head>
<body>
  <div class="app">
    <div class="header">
      <div class="title-wrap">
        <h1>СБОР И АНАЛИЗ ДАННЫХ</h1>
        <p>Вставьте свои цифры, мгновенно проанализируйте их и сохраните историю запусков.</p>
      </div>
      <div class="badge">Client-side · no server needed</div>
    </div>

    <div class="layout">
      <!-- Left: Input & controls -->
      <div class="card">
        <div class="card-header">
          <h2>Числа</h2>
          <span>число,запятая,пробел 
          </span>
        </div>

        <div>
          <label for="data-input">Значения</label>
          <textarea id="data-input" placeholder="Пример: 10, 20, 20, 35, 40  50&#10;или одно значение для одной линии"></textarea>
          <div class="hint">Только цифры, дргуие символы и пробелмы не принимаю.</div>
        </div>

        <div class="controls">
          <button class="btn-primary" id="analyze-btn">
            ▶ Анализ 
          </button>
          <button class="btn-secondary" id="random-btn">
            ✦ Рандомные цифры
          </button>
          <button class="btn-secondary" id="clear-btn">
            ⌫ Чистка
          </button>
        </div>
      </div>

      <!-- Right: Stats & history -->
      <div class="card">
        <div class="card-header">
          <h2>Результат</h2>
          <span id="status-label">Ожидание данных…</span>
        </div>

        <div class="stats-grid" id="stats-grid">
          <div class="stat">
            <div class="stat-label">Сумма</div>
            <div class="stat-value" id="stat-count">0</div>
          </div>
          <div class="stat">
            <div class="stat-label">Средне арифметическое</div>
            <div class="stat-value" id="stat-mean">–</div>
          </div>
          <div class="stat">
            <div class="stat-label">Медиан</div>
            <div class="stat-value" id="stat-median">–</div>
          </div>
          <div class="stat">
            <div class="stat-label">Стандарт. отклонение</div>
            <div class="stat-value" id="stat-std">–</div>
          </div>
        </div>

        <div class="stat-secondary" id="extra-info"></div>

        <div class="chart">
          <canvas id="chart-canvas"></canvas>
        </div>

        <div style="margin-top: 6px;">
          <div class="card-header" style="margin-bottom: 4px;">
            <h2>Captured runs</h2>
            <span>Последние анализ</span>
          </div>
          <div class="log" id="runs-log"></div>
        </div>
      </div>
    </div>

    <div class="footer">
      <small id="footer-meta">Нету данных для анализа</small>
    </div>
  </div>

  <script>
    const inputEl = document.getElementById("data-input");
    const analyzeBtn = document.getElementById("analyze-btn");
    const randomBtn = document.getElementById("random-btn");
    const clearBtn = document.getElementById("clear-btn");

    const statCount = document.getElementById("stat-count");
    const statMean = document.getElementById("stat-mean");
    const statMedian = document.getElementById("stat-median");
    const statStd = document.getElementById("stat-std");
    const extraInfo = document.getElementById("extra-info");
    const statusLabel = document.getElementById("status-label");
    const runsLog = document.getElementById("runs-log");
    const footerMeta = document.getElementById("footer-meta");

    const canvas = document.getElementById("chart-canvas");
    const ctx = canvas.getContext("2d");

    function getNumericValues(raw) {
      const tokens = raw
        .split(/[\s,;]+/)
        .map(t => t.trim())
        .filter(Boolean);

      const numbers = [];
      for (const t of tokens) {
        const value = Number(t.replace(",", "."));
        if (!Number.isNaN(value) && Number.isFinite(value)) {
          numbers.push(value);
        }
      }
      return numbers;
    }

    function computeStats(values) {
      if (!values.length) return null;

      const sorted = [...values].sort((a, b) => a - b);
      const n = values.length;
      const sum = values.reduce((acc, v) => acc + v, 0);
      const mean = sum / n;
      const median =
        n % 2 === 1
          ? sorted[(n - 1) / 2]
          : (sorted[n / 2 - 1] + sorted[n / 2]) / 2;

      const variance =
        n > 1
          ? values.reduce((acc, v) => acc + (v - mean) ** 2, 0) / (n - 1)
          : 0;
      const std = Math.sqrt(variance);

      const min = sorted[0];
      const max = sorted[sorted.length - 1];

      return { n, mean, median, std, min, max };
    }

    function drawChart(values) {
      const width = canvas.clientWidth;
      const height = canvas.clientHeight;
      const ratio = window.devicePixelRatio || 1;
      canvas.width = width * ratio;
      canvas.height = height * ratio;
      ctx.setTransform(ratio, 0, 0, ratio, 0, 0);

      ctx.clearRect(0, 0, width, height);

      if (!values.length) {
        ctx.fillStyle = "#6b7280";
        ctx.font = "11px system-ui, -apple-system, BlinkMacSystemFont";
        ctx.fillText("Chart will show your values as a line.", 10, height / 2);
        return;
      }

      const minVal = Math.min(...values);
      const maxVal = Math.max(...values);
      const span = maxVal - minVal || 1;

      const paddingX = 12;
      const paddingY = 10;
      const chartW = width - paddingX * 2;
      const chartH = height - paddingY * 2;

      ctx.strokeStyle = "rgba(55,65,81,0.7)";
      ctx.lineWidth = 1;
      ctx.beginPath();
      ctx.moveTo(paddingX, paddingY + chartH);
      ctx.lineTo(paddingX, paddingY);
      ctx.lineTo(paddingX + chartW, paddingY);
      ctx.stroke();

      if (values.length === 1) {
        const x = paddingX + chartW / 2;
        const y = paddingY + chartH - ((values[0] - minVal) / span) * chartH;
        ctx.fillStyle = "#60a5fa";
        ctx.beginPath();
        ctx.arc(x, y, 4, 0, Math.PI * 2);
        ctx.fill();
        return;
      }

      ctx.strokeStyle = "#38bdf8";
      ctx.lineWidth = 1.3;
      ctx.beginPath();

      values.forEach((v, i) => {
        const t = values.length === 1 ? 0 : i / (values.length - 1);
        const x = paddingX + t * chartW;
        const y = paddingY + chartH - ((v - minVal) / span) * chartH;

        if (i === 0) {
          ctx.moveTo(x, y);
        } else {
          ctx.lineTo(x, y);
        }
      });
      ctx.stroke();

      ctx.fillStyle = "#60a5fa";
      values.forEach((v, i) => {
        const t = values.length === 1 ? 0 : i / (values.length - 1);
        const x = paddingX + t * chartW;
        const y = paddingY + chartH - ((v - minVal) / span) * chartH;
        ctx.beginPath();
        ctx.arc(x, y, 2.4, 0, Math.PI * 2);
        ctx.fill();
      });
    }

    function formatNumber(value) {
      if (value === null || value === undefined || Number.isNaN(value)) {
        return "–";
      }
      const abs = Math.abs(value);
      const digits = abs >= 1000 || abs === 0 ? 2 : 3;
      return value.toFixed(digits).replace(/\.?0+$/, "");
    }

    function addRunToLog(stats) {
      const timestamp = new Date().toLocaleTimeString();
      const div = document.createElement("div");
      div.className = "log-entry";
      div.innerHTML = `
        <span>${stats.n} values · μ=${formatNumber(stats.mean)}</span>
        <small>${timestamp}</small>
      `;
      runsLog.prepend(div);
    }

    function analyze() {
      const raw = inputEl.value || "";
      const values = getNumericValues(raw);

      if (!values.length) {
        statusLabel.textContent = "No valid numeric values found.";
        statCount.textContent = "0";
        statMean.textContent = "–";
        statMedian.textContent = "–";
        statStd.textContent = "–";
        extraInfo.textContent = "";
        drawChart([]);
        footerMeta.textContent = "Waiting for valid data…";
        return;
      }

      const stats = computeStats(values);
      statCount.textContent = String(stats.n);
      statMean.textContent = formatNumber(stats.mean);
      statMedian.textContent = formatNumber(stats.median);
      statStd.textContent = formatNumber(stats.std);

      extraInfo.textContent = `Min: ${formatNumber(
        stats.min
      )} · Max: ${formatNumber(stats.max)} · Range: ${formatNumber(
        stats.max - stats.min
      )}`;

      statusLabel.textContent = "Analysis complete.";
      drawChart(values);
      addRunToLog(stats);
      footerMeta.textContent = `Last run: ${stats.n} values analyzed`;
    }

    function fillRandomSample() {
      const n = 20 + Math.floor(Math.random() * 30);
      const values = Array.from({ length: n }, () =>
        (Math.random() * 100).toFixed(1)
      );
      inputEl.value = values.join(", ");
      statusLabel.textContent = "Random sample generated. Press Analyze.";
    }

    function clearAll() {
      inputEl.value = "";
      statCount.textContent = "0";
      statMean.textContent = "–";
      statMedian.textContent = "–";
      statStd.textContent = "–";
      extraInfo.textContent = "";
      statusLabel.textContent = "Waiting for data…";
      drawChart([]);
      footerMeta.textContent = "No data analyzed yet";
    }

    analyzeBtn.addEventListener("click", analyze);
    randomBtn.addEventListener("click", fillRandomSample);
    clearBtn.addEventListener("click", clearAll);
    inputEl.addEventListener("keydown", (event) => {
      if ((event.metaKey || event.ctrlKey) && event.key === "Enter") {
        event.preventDefault();
        analyze();
      }
    });

    drawChart([]);
  </script>
</body>
</html>
