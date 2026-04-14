# Ma-piscine-
Mon calcul de propreté d’eau 
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>🏊 Aqua Pool</title>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&display=swap" rel="stylesheet"> <style>
  :root {
    --blue-deep: #0a1628;
    --blue-mid: #0d2847;
    --blue-water: #0e7fc5;
    --blue-light: #38bdf8;
    --cyan: #06d6c4;
    --green: #22c55e;
    --orange: #f97316;
    --red: #ef4444;
    --yellow: #eab308;
    --white: #f0f9ff;
    --glass: rgba(255,255,255,0.07);
    --glass-border: rgba(255,255,255,0.13);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; -webkit-tap-highlight-color: transparent; }

  body {
    font-family: 'Outfit', sans-serif;
    background: var(--blue-deep);
    color: var(--white);
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* Animated water background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 50% at 20% 20%, rgba(14,127,197,0.18) 0%, transparent 60%),
      radial-gradient(ellipse 60% 40% at 80% 70%, rgba(6,214,196,0.12) 0%, transparent 60%),
      radial-gradient(ellipse 100% 60% at 50% 100%, rgba(56,189,248,0.08) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
  }

  /* Wave animation */
  .wave-bg {
    position: fixed;
    bottom: 0;
    left: 0;
    width: 200%;
    height: 120px;
    background: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 1440 120'%3E%3Cpath fill='rgba(14,127,197,0.08)' d='M0,60 C360,120 720,0 1080,60 C1260,90 1380,45 1440,60 L1440,120 L0,120 Z'/%3E%3C/svg%3E") repeat-x;
    animation: wave 8s linear infinite;
    pointer-events: none;
    z-index: 0;
  }
  .wave-bg:nth-child(2) { animation-delay: -4s; opacity: 0.5; }

  @keyframes wave {
    0% { transform: translateX(0); }
    100% { transform: translateX(-50%); }
  }

  .app {
    position: relative;
    z-index: 1;
    max-width: 430px;
    margin: 0 auto;
    padding: 0 0 40px;
    min-height: 100vh;
  }

  /* Header */
  .header {
    padding: 50px 24px 24px;
    text-align: center;
  }

  .header-icon {
    font-size: 2.5rem;
    display: block;
    margin-bottom: 8px;
    filter: drop-shadow(0 0 20px rgba(6,214,196,0.5));
    animation: float 3s ease-in-out infinite;
  }

  @keyframes float {
    0%, 100% { transform: translateY(0); }
    50% { transform: translateY(-6px); }
  }

  .header h1 {
    font-size: 1.9rem;
    font-weight: 800;
    letter-spacing: -0.5px;
    background: linear-gradient(135deg, #fff 0%, var(--cyan) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .header p {
    font-size: 0.85rem;
    color: rgba(255,255,255,0.45);
    margin-top: 4px;
    font-weight: 300;
    letter-spacing: 0.5px;
  }

  /* Cards grid */
  .cards-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    padding: 0 16px;
    margin-bottom: 16px;
  }

  .card {
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 20px;
    padding: 18px 16px;
    backdrop-filter: blur(12px);
    position: relative;
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .card:active { transform: scale(0.97); }

  .card::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--card-accent, var(--blue-light));
    border-radius: 20px 20px 0 0;
  }

  .card-icon {
    font-size: 1.5rem;
    margin-bottom: 10px;
    display: block;
    filter: drop-shadow(0 0 8px var(--card-accent, var(--blue-light)));
  }

  .card-label {
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    color: rgba(255,255,255,0.4);
    font-weight: 600;
    margin-bottom: 6px;
  }

  .card-unit {
    font-size: 0.65rem;
    color: rgba(255,255,255,0.3);
    margin-bottom: 8px;
    font-weight: 400;
  }

  .card-input {
    background: rgba(0,0,0,0.25);
    border: 1.5px solid rgba(255,255,255,0.1);
    border-radius: 10px;
    color: white;
    font-family: 'Outfit', sans-serif;
    font-size: 1.3rem;
    font-weight: 700;
    width: 100%;
    padding: 8px 10px;
    text-align: center;
    transition: border-color 0.2s, box-shadow 0.2s;
    -moz-appearance: textfield;
  }

  .card-input::-webkit-outer-spin-button,
  .card-input::-webkit-inner-spin-button { -webkit-appearance: none; }

  .card-input:focus {
    outline: none;
    border-color: var(--card-accent, var(--blue-light));
    box-shadow: 0 0 0 3px rgba(56,189,248,0.15);
  }

  .card-range {
    font-size: 0.62rem;
    color: rgba(255,255,255,0.3);
    margin-top: 6px;
    text-align: center;
    font-weight: 300;
  }

  /* Status indicator dot */
  .card-status {
    position: absolute;
    top: 14px;
    right: 14px;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: rgba(255,255,255,0.2);
    transition: background 0.3s, box-shadow 0.3s;
  }

  .card-status.ok { background: var(--green); box-shadow: 0 0 8px var(--green); }
  .card-status.warn { background: var(--orange); box-shadow: 0 0 8px var(--orange); }
  .card-status.bad { background: var(--red); box-shadow: 0 0 8px var(--red); }

  /* Analyze button */
  .btn-wrap { padding: 0 16px; margin-bottom: 20px; }

  .btn-analyze {
    width: 100%;
    padding: 18px;
    background: linear-gradient(135deg, var(--blue-water), var(--cyan));
    border: none;
    border-radius: 18px;
    color: white;
    font-family: 'Outfit', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    letter-spacing: 0.5px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
    box-shadow: 0 8px 32px rgba(14,127,197,0.4), 0 0 0 1px rgba(255,255,255,0.1);
  }

  .btn-analyze::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, rgba(255,255,255,0.15), transparent);
    border-radius: 18px;
  }

  .btn-analyze:active { transform: scale(0.98); box-shadow: 0 4px 16px rgba(14,127,197,0.3); }

  /* Results panel */
  .results {
    margin: 0 16px;
    background: var(--glass);
    border: 1px solid var(--glass-border);
    border-radius: 24px;
    overflow: hidden;
    backdrop-filter: blur(12px);
    display: none;
    animation: slideUp 0.4s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
  }

  .results.show { display: block; }

  @keyframes slideUp {
    from { transform: translateY(30px); opacity: 0; }
    to { transform: translateY(0); opacity: 1; }
  }

  .results-header {
    padding: 20px 20px 16px;
    border-bottom: 1px solid var(--glass-border);
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .results-title {
    font-size: 0.8rem;
    text-transform: uppercase;
    letter-spacing: 2px;
    color: rgba(255,255,255,0.5);
    font-weight: 600;
  }

  .overall-status {
    margin-left: auto;
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 0.75rem;
    font-weight: 700;
    letter-spacing: 0.5px;
  }

  .overall-status.parfait { background: rgba(34,197,94,0.2); color: var(--green); border: 1px solid rgba(34,197,94,0.3); }
  .overall-status.attention { background: rgba(249,115,22,0.2); color: var(--orange); border: 1px solid rgba(249,115,22,0.3); }
  .overall-status.danger { background: rgba(239,68,68,0.2); color: var(--red); border: 1px solid rgba(239,68,68,0.3); }

  .result-item {
    padding: 16px 20px;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    display: flex;
    gap: 14px;
    align-items: flex-start;
  }

  .result-item:last-child { border-bottom: none; }

  .result-icon-wrap {
    width: 38px;
    height: 38px;
    border-radius: 12px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.1rem;
    flex-shrink: 0;
  }

  .result-icon-wrap.ok { background: rgba(34,197,94,0.15); }
  .result-icon-wrap.warn { background: rgba(249,115,22,0.15); }
  .result-icon-wrap.bad { background: rgba(239,68,68,0.15); }

  .result-body { flex: 1; }

  .result-param {
    font-size: 0.75rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 1px;
    color: rgba(255,255,255,0.5);
    margin-bottom: 3px;
  }

  .result-value-row {
    display: flex;
    align-items: baseline;
    gap: 6px;
    margin-bottom: 5px;
  }

  .result-val {
    font-size: 1.3rem;
    font-weight: 800;
  }
  .result-val.ok { color: var(--green); }
  .result-val.warn { color: var(--orange); }
  .result-val.bad { color: var(--red); }

  .result-target {
    font-size: 0.72rem;
    color: rgba(255,255,255,0.3);
    font-weight: 300;
  }

  .result-advice {
    font-size: 0.82rem;
    color: rgba(255,255,255,0.75);
    line-height: 1.45;
    font-weight: 300;
  }

  .result-advice strong {
    color: white;
    font-weight: 600;
  }

  /* No data state */
  .empty-msg {
    text-align: center;
    padding: 30px 20px;
    color: rgba(255,255,255,0.3);
    font-size: 0.85rem;
    font-weight: 300;
  }

  /* Footer */
  .footer {
    text-align: center;
    padding: 30px 16px 10px;
    font-size: 0.7rem;
    color: rgba(255,255,255,0.2);
    font-weight: 300;
    letter-spacing: 0.5px;
  }

  /* Bubble decorations */
  .bubble {
    position: fixed;
    border-radius: 50%;
    background: rgba(56,189,248,0.05);
    border: 1px solid rgba(56,189,248,0.08);
    pointer-events: none;
    z-index: 0;
    animation: rise linear infinite;
  }
  .bubble:nth-child(1) { width: 60px; height: 60px; left: 10%; animation-duration: 12s; animation-delay: 0s; }
  .bubble:nth-child(2) { width: 30px; height: 30px; left: 30%; animation-duration: 9s; animation-delay: -3s; }
  .bubble:nth-child(3) { width: 80px; height: 80px; left: 65%; animation-duration: 15s; animation-delay: -6s; }
  .bubble:nth-child(4) { width: 20px; height: 20px; left: 85%; animation-duration: 8s; animation-delay: -2s; }

  @keyframes rise {
    0% { transform: translateY(110vh) scale(1); opacity: 0; }
    10% { opacity: 1; }
    90% { opacity: 0.5; }
    100% { transform: translateY(-10vh) scale(1.2); opacity: 0; }
  }
</style>
</head>
<body>

<div class="bubble"></div>
<div class="bubble"></div>
<div class="bubble"></div>
<div class="bubble"></div>
<div class="wave-bg"></div>
<div class="wave-bg"></div>

<div class="app">
  <div class="header">
    <span class="header-icon">🏊</span>
    <h1>Aqua Pool</h1>
    <p>Analyse de l'eau en temps réel</p>
  </div>

  <div class="cards-grid">
    <!-- pH -->
    <div class="card" style="--card-accent: #38bdf8;">
      <div class="card-status" id="status-ph"></div>
      <span class="card-icon">⚗️</span>
      <div class="card-label">pH</div>
      <div class="card-unit">Sans unité</div>
      <input class="card-input" type="number" id="val-ph" placeholder="7.2" step="0.1" min="0" max="14">
      <div class="card-range">Idéal : 7,2 – 7,6</div>
    </div>

    <!-- Température -->
    <div class="card" style="--card-accent: #f97316;">
      <div class="card-status" id="status-temp"></div>
      <span class="card-icon">🌡️</span>
      <div class="card-label">Température</div>
      <div class="card-unit">°C</div>
      <input class="card-input" type="number" id="val-temp" placeholder="28" step="0.5" min="0" max="50">
      <div class="card-range">Idéal : 24 – 30 °C</div>
    </div>

    <!-- Chlore libre -->
    <div class="card" style="--card-accent: #06d6c4;">
      <div class="card-status" id="status-chlore"></div>
      <span class="card-icon">🧪</span>
      <div class="card-label">Chlore libre</div>
      <div class="card-unit">mg/L (ppm)</div>
      <input class="card-input" type="number" id="val-chlore" placeholder="1.2" step="0.1" min="0" max="20">
      <div class="card-range">Idéal : 1,0 – 3,0</div>
    </div>

    <!-- TAC -->
    <div class="card" style="--card-accent: #a78bfa;">
      <div class="card-status" id="status-tac"></div>
      <span class="card-icon">🔬</span>
      <div class="card-label">TAC</div>
      <div class="card-unit">mg/L (°f)</div>
      <input class="card-input" type="number" id="val-tac" placeholder="120" step="5" min="0" max="500">
      <div class="card-range">Idéal : 80 – 160 mg/L</div>
    </div>

    <!-- TH (Dureté) -->
    <div class="card" style="--card-accent: #ec4899;">
      <div class="card-status" id="status-th"></div>
      <span class="card-icon">💎</span>
      <div class="card-label">TH (Dureté)</div>
      <div class="card-unit">mg/L</div>
      <input class="card-input" type="number" id="val-th" placeholder="200" step="5" min="0" max="800">
      <div class="card-range">Idéal : 150 – 300 mg/L</div>
    </div>

    <!-- Chlore combiné -->
    <div class="card" style="--card-accent: #eab308;">
      <div class="card-status" id="status-chlorec"></div>
      <span class="card-icon">⚡</span>
      <div class="card-label">Chlore combiné</div>
      <div class="card-unit">mg/L (ppm)</div>
      <input class="card-input" type="number" id="val-chlorec" placeholder="0.2" step="0.1" min="0" max="10">
      <div class="card-range">Max : &lt; 0,6 mg/L</div>
    </div>
  </div>

  <div class="btn-wrap">
    <button class="btn-analyze" onclick="analyzePool()">
      🔍 &nbsp;Analyser mon eau
    </button>
  </div>

  <div class="results" id="results">
    <div class="results-header">
      <span>📋</span>
      <span class="results-title">Résultats</span>
      <span class="overall-status" id="overall-status">—</span>
    </div>
    <div id="results-list"></div>
  </div>

  <div class="footer">Valeurs basées sur les normes NF EN piscine • Usage personnel</div> </div>

<script>
const params = {
  ph: {
    label: 'pH', icon: '⚗️', unit: '',
    ideal: [7.2, 7.6], warn: [6.8, 7.9], bad: [0, 14],
    adviceLow: '<strong>pH trop bas (eau acide) :</strong> Ajoutez du <strong>pH+ (soude) ou pH Up</strong>. Dose ~50g/10m³ pour +0,2 de pH. Attendez 4h avant de re-tester.',
    adviceHigh: '<strong>pH trop élevé (eau basique) :</strong> Ajoutez du <strong>pH- (acide sulfurique) ou pH Down</strong>. Dose ~40g/10m³ pour -0,2 de pH. Attendez 4h avant de re-tester.',
    adviceOk: 'Votre pH est parfait. Eau équilibrée et confortable pour la baignade.',
  },
  temp: {
    label: 'Température', icon: '🌡️', unit: '°C',
    ideal: [24, 30], warn: [18, 34], bad: [0, 50],
    adviceLow: '<strong>Eau froide :</strong> Baignade déconseillée. Si vous avez une pompe à chaleur, augmentez la consigne. Temps de chauffage estimé : +1°C/h selon équipement.',
    adviceHigh: '<strong>Eau trop chaude :</strong> Risque de prolifération bactérienne. Augmentez la fréquence de filtration et la dose de chlore. Évitez la baignade au-dessus de 34°C.',
    adviceOk: 'Température idéale pour la baignade et l\'efficacité du chlore.',
  },
  chlore: {
    label: 'Chlore libre', icon: '🧪', unit: ' mg/L',
    ideal: [1.0, 3.0], warn: [0.5, 5.0], bad: [0, 20],
    adviceLow: '<strong>Chlore insuffisant :</strong> Risque d\'algues et bactéries. Ajoutez des <strong>galets de chlore lent</strong> dans le skimmer ou du <strong>chlore choc granulé</strong> si c\'est urgent (250g/10m³). Vérifiez que la filtration tourne au moins 8h/jour.',
    adviceHigh: '<strong>Chlore trop élevé :</strong> Ne pas se baigner. Arrêtez l\'ajout de chlore et laissez la filtration tourner. Le soleil dégrade naturellement le chlore. Vérifiez votre pH (un pH élevé bloque le chlore).',
    adviceOk: 'Taux de désinfection efficace. L\'eau est saine pour la baignade.',
  },
  tac: {
    label: 'TAC (Alcalinité)', icon: '🔬', unit: ' mg/L',
    ideal: [80, 160], warn: [60, 200], bad: [0, 500],
    adviceLow: '<strong>TAC trop bas :</strong> Eau peu tamponée, le pH va varier brutalement. Ajoutez du <strong>bicarbonate de soude</strong> : environ 100g/10m³ pour +10 mg/L. Mélangez avant d\'ajouter au bassin.',
    adviceHigh: '<strong>TAC trop élevé :</strong> Le pH sera difficile à faire baisser. Utilisez du <strong>pH-</strong> pour corriger progressivement. Diluer l\'eau du bassin avec de l\'eau douce peut aussi aider.',
    adviceOk: 'Alcalinité équilibrée. Le pH sera stable et facile à maintenir.',
  },
  th: {
    label: 'TH (Dureté)', icon: '💎', unit: ' mg/L',
    ideal: [150, 300], warn: [100, 400], bad: [0, 800],
    adviceLow: '<strong>Eau trop douce :</strong> Risque de corrosion des équipements. Ajoutez du <strong>chlorure de calcium</strong> (réhausseur de dureté) : 100g/10m³ pour +10 mg/L.',
    adviceHigh: '<strong>Eau trop dure :</strong> Risque de dépôts calcaires sur les parois et équipements. Utilisez un <strong>anti-calcaire</strong> liquide. En cas extrême, renouveler une partie de l\'eau.',
    adviceOk: 'Dureté de l\'eau correcte. Pas de risque de corrosion ni de calcaire.',
  },
  chlorec: {
    label: 'Chlore combiné', icon: '⚡', unit: ' mg/L',
    ideal: [0, 0.6], warn: [0, 1.5], bad: [0, 10],
    adviceLow: null, // not applicable
    adviceHigh: '<strong>Chlore combiné trop élevé :</strong> Responsable des yeux qui piquent et de l\'odeur de chlore. Effectuez un <strong>choc chloré</strong> (chlore choc 250g/10m³) de préférence le soir. Fermez la piscine 12h. Vérifiez aussi le pH.',
    adviceOk: 'Peu de chloramines présentes. L\'eau ne devrait pas irriter les yeux.',
  },
};

function getStatus(param, value) {
  const p = params[param];
  if (value === null || isNaN(value)) return 'empty';
  if (value >= p.ideal[0] && value <= p.ideal[1]) return 'ok';
  if (value >= p.warn[0] && value <= p.warn[1]) return 'warn';
  return 'bad';
}

function updateDot(param, status) {
  const el = document.getElementById('status-' + param);
  if (!el) return;
  el.className = 'card-status';
  if (status !== 'empty') el.classList.add(status); }

// Live dot update
['ph','temp','chlore','tac','th','chlorec'].forEach(p => {
  document.getElementById('val-' + p).addEventListener('input', function() {
    const v = parseFloat(this.value);
    const s = getStatus(p, v);
    updateDot(p, s);
  });
});

function analyzePool() {
  const values = {};
  let hasAny = false;
  ['ph','temp','chlore','tac','th','chlorec'].forEach(p => {
    const v = parseFloat(document.getElementById('val-' + p).value);
    values[p] = isNaN(v) ? null : v;
    if (!isNaN(v)) hasAny = true;
  });

  const resultsEl = document.getElementById('results');
  const listEl = document.getElementById('results-list');
  const overallEl = document.getElementById('overall-status');

  if (!hasAny) {
    listEl.innerHTML = '<div class="empty-msg">💧 Entrez au moins une valeur pour analyser votre eau</div>';
    resultsEl.classList.add('show');
    return;
  }

  let html = '';
  let statuses = [];

  Object.entries(values).forEach(([key, val]) => {
    if (val === null) return;
    const p = params[key];
    const status = getStatus(key, val);
    statuses.push(status);

    let advice = '';
    if (status === 'ok') {
      advice = p.adviceOk;
    } else if (val < p.ideal[0]) {
      advice = p.adviceLow || p.adviceOk;
    } else {
      advice = p.adviceHigh || p.adviceOk;
    }

    const displayVal = val + p.unit;

    html += `
      <div class="result-item">
        <div class="result-icon-wrap ${status}">${p.icon}</div>
        <div class="result-body">
          <div class="result-param">${p.label}</div>
          <div class="result-value-row">
            <span class="result-val ${status}">${displayVal}</span>
            <span class="result-target">/ idéal : ${p.ideal[0]}–${p.ideal[1]}${p.unit}</span>
          </div>
          <div class="result-advice">${advice}</div>
        </div>
      </div>
    `;
  });

  listEl.innerHTML = html;

  // Overall status
  const hasBad = statuses.includes('bad');
  const hasWarn = statuses.includes('warn');
  if (hasBad) {
    overallEl.textContent = '🔴 Danger';
    overallEl.className = 'overall-status danger';
  } else if (hasWarn) {
    overallEl.textContent = '🟠 Attention';
    overallEl.className = 'overall-status attention';
  } else {
    overallEl.textContent = '🟢 Parfait';
    overallEl.className = 'overall-status parfait';
  }

  resultsEl.classList.remove('show');
  void resultsEl.offsetWidth; // force reflow for animation
  resultsEl.classList.add('show');

  resultsEl.scrollIntoView({ behavior: 'smooth', block: 'start' }); } </script> </body> </html>
