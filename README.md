# HeartGuard-AI
Heat Guard AI
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>HeatGuard AI – Advanced Visual Prototype</title>
  <style>
    * {
      box-sizing: border-box;
    }

    :root {
      --bg-ios: #f2f2f7;
      --card-ios: #ffffff;
      --accent-ios: #0a84ff;
      --accent-ios-soft: rgba(10, 132, 255, 0.12);
      --text-primary: #111827;
      --text-secondary: #6b7280;
    }

    body {
      margin: 0;
      font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text", system-ui,
        "Segoe UI", sans-serif;
      background: var(--bg-ios);
      color: var(--text-primary);
    }

    .app {
      max-width: 430px;
      margin: 0 auto;
      padding: 16px 14px 28px;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
    }

    .status-spacer {
      height: 10px;
    }

    header {
      margin-bottom: 10px;
    }

    .header-bar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 4px 4px 0;
    }

    .header-title-group {
      display: flex;
      flex-direction: column;
      gap: 3px;
    }

    .app-name-chip {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 3px 9px;
      border-radius: 999px;
      background: var(--accent-ios-soft);
      color: var(--accent-ios);
      font-size: 0.7rem;
      font-weight: 600;
      letter-spacing: 0.08em;
      text-transform: uppercase;
    }

    .app-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: var(--accent-ios);
    }

    .large-title {
      font-size: 1.7rem;
      font-weight: 700;
      color: var(--text-primary);
    }

    .subtitle {
      font-size: 0.85rem;
      color: var(--text-secondary);
    }

    .avatar-circle {
      width: 32px;
      height: 32px;
      border-radius: 999px;
      background: #e5e7eb;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.8rem;
      font-weight: 600;
      color: #4b5563;
    }

    main {
      flex: 1;
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: 8px;
    }

    /* Card base */
    .card {
      position: relative;
      background: var(--card-ios);
      border-radius: 22px;
      padding: 16px 16px 18px;
      border: 1px solid rgba(0, 0, 0, 0.04);
      box-shadow: 0 8px 18px rgba(15, 23, 42, 0.06);
      overflow: hidden;
      opacity: 0;
      transform: translateY(10px);
      animation: cardIn 0.3s ease forwards;
    }

    .card-inner {
      position: relative;
      z-index: 1;
    }

    .card-fade-in {
      animation: cardIn 0.3s ease forwards;
    }

    @keyframes cardIn {
      from {
        opacity: 0;
        transform: translateY(10px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .section-title {
      font-size: 0.96rem;
      font-weight: 600;
      margin-bottom: 4px;
      color: var(--text-primary);
    }

    label {
      display: block;
      font-size: 0.85rem;
      margin-bottom: 4px;
      color: var(--text-secondary);
    }

    select {
      width: 100%;
      padding: 10px;
      border-radius: 12px;
      border: 1px solid #d1d5db;
      font-size: 0.95rem;
      background: #f9fafb;
      color: var(--text-primary);
      appearance: none;
      -webkit-appearance: none;
      background-image:
        linear-gradient(45deg, transparent 50%, #9ca3af 50%),
        linear-gradient(135deg, #9ca3af 50%, transparent 50%);
      background-position: calc(100% - 14px) calc(50% - 3px),
        calc(100% - 10px) calc(50% - 3px);
      background-size: 6px 6px, 6px 6px;
      background-repeat: no-repeat;
    }

    .field {
      margin-bottom: 12px;
    }

    button {
      border: none;
      border-radius: 999px;
      padding: 10px 18px;
      font-size: 0.95rem;
      cursor: pointer;
      transition: transform 0.08s ease, box-shadow 0.08s ease,
        background 0.12s ease, opacity 0.12s ease;
    }

    button:active {
      transform: scale(0.97);
      box-shadow: 0 5px 15px rgba(15, 23, 42, 0.18);
      opacity: 0.9;
    }

    .btn-primary {
      background: var(--accent-ios);
      color: white;
      width: 100%;
      margin-top: 4px;
      box-shadow: 0 10px 22px rgba(0, 122, 255, 0.35);
    }

    .btn-secondary {
      background: #e5e7eb;
      color: var(--text-primary);
    }

    .btn-ghost {
      background: transparent;
      color: var(--accent-ios);
      padding-inline: 0;
      box-shadow: none;
    }

    .btn-row {
      display: flex;
      justify-content: space-between;
      gap: 8px;
      margin-top: 16px;
    }

    .hidden {
      display: none;
    }

    .pill-row {
      display: flex;
      flex-wrap: wrap;
      gap: 6px;
      margin-top: 10px;
    }

    .pill {
      padding: 4px 10px;
      border-radius: 999px;
      background: #e5e7eb;
      font-size: 0.75rem;
      color: #4b5563;
    }

    .pill.primary {
      background: #dbeafe;
      color: #1d4ed8;
    }

    /* Risk badge + icon */
    .risk-row {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 8px;
    }

    .risk-icon {
      width: 28px;
      height: 28px;
      border-radius: 999px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.1rem;
      background: #fee2e2;
    }

    .risk-badge {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      padding: 5px 14px;
      border-radius: 999px;
      font-size: 0.78rem;
      font-weight: 650;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      background: #f3f4f6;
      color: var(--text-primary);
    }

    .risk-safe {
      background: #dcfce7;
      color: #166534;
    }

    .risk-caution {
      background: #fef9c3;
      color: #854d0e;
    }

    .risk-high {
      background: #ffedd5;
      color: #9a3412;
    }

    .risk-extreme {
      background: #fee2e2;
      color: #b91c1c;
    }

    .metrics {
      display: flex;
      justify-content: space-between;
      gap: 8px;
      margin-bottom: 8px;
      flex-wrap: wrap;
    }

    .metric {
      flex: 1;
      min-width: 100px;
      background: #f9fafb;
      border-radius: 14px;
      padding: 8px 10px;
      font-size: 0.8rem;
      border: 1px solid #e5e7eb;
    }

    .metric span {
      display: block;
      font-weight: 600;
      font-size: 1.05rem;
      color: var(--text-primary);
    }

    .small-text {
      font-size: 0.8rem;
      color: var(--text-secondary);
    }

    ul.recommendations {
      padding-left: 18px;
      margin: 8px 0 0;
      font-size: 0.9rem;
      color: #374151;
    }

    ul.recommendations li + li {
      margin-top: 4px;
    }

    .note {
      margin-top: 8px;
      font-size: 0.85rem;
      color: #b91c1c;
    }

    .forecast-grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 8px;
      margin-top: 8px;
    }

    .forecast-card {
      background: #f9fafb;
      border-radius: 12px;
      padding: 8px;
      text-align: center;
      font-size: 0.85rem;
      border: 1px solid #e5e7eb;
      color: var(--text-primary);
    }

    .forecast-time {
      font-weight: 600;
      margin-bottom: 4px;
    }

    .forecast-level {
      font-weight: 500;
      margin-bottom: 2px;
    }

    /* Chart section (more advanced) */
    .chart-section {
      margin-top: 12px;
      border-top: 1px solid #e5e7eb;
      padding-top: 10px;
    }

    .chart-title-row {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 4px;
    }

    .chart-title {
      font-size: 0.9rem;
      font-weight: 600;
    }

    .chart-legend {
      display: flex;
      gap: 6px;
      align-items: center;
      font-size: 0.7rem;
      color: #6b7280;
    }

    .legend-dot {
      width: 8px;
      height: 8px;
      border-radius: 999px;
      background: #ff453a;
    }

    .chart {
      display: flex;
      align-items: flex-end;
      gap: 12px;
      height: 120px;
      margin-top: 4px;
    }

    .chart-bar {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      align-items: center;
      gap: 4px;
      font-size: 0.75rem;
      color: #6b7280;
      position: relative;
    }

    .bar {
      width: 26px;
      border-radius: 999px 999px 0 0;
      background: #d1d5db;
      height: 25%;
      transition: height 0.35s ease, background 0.2s ease,
        transform 0.15s ease, box-shadow 0.15s ease;
      box-shadow: 0 6px 12px rgba(15, 23, 42, 0.18);
      position: relative;
    }

    .chart-bar:hover .bar {
      transform: translateY(-2px) scale(1.03);
      box-shadow: 0 10px 16px rgba(15, 23, 42, 0.22);
    }

    .bar-label {
      position: absolute;
      top: -18px;
      font-size: 0.7rem;
      color: #4b5563;
    }

    .bar-safe {
      background: #34c759;
    }

    .bar-caution {
      background: #ffd60a;
    }

    .bar-high {
      background: #ff9f0a;
    }

    .bar-extreme {
      background: #ff453a;
    }

    .segmented {
      display: inline-flex;
      padding: 2px;
      border-radius: 999px;
      background: #e5e7eb;
      margin-top: 6px;
    }

    .segment {
      padding: 4px 12px;
      font-size: 0.78rem;
      border-radius: 999px;
      cursor: pointer;
      color: #4b5563;
      user-select: none;
    }

    .segment.active {
      background: #ffffff;
      color: #111827;
      box-shadow: 0 2px 6px rgba(15, 23, 42, 0.18);
    }

    .footer-note {
      font-size: 0.75rem;
      color: var(--text-secondary);
      text-align: center;
      margin-top: 12px;
    }

    .bottom-info {
      margin-top: 6px;
      text-align: center;
    }
  </style>
</head>
<body>
  <div class="app">
    <div class="status-spacer"></div>

    <header>
      <div class="header-bar">
        <div class="header-title-group">
          <div class="app-name-chip">
            <div class="app-dot"></div>
            HeatGuard AI
          </div>
          <div class="large-title">Heat safety</div>
          <div class="subtitle">Personalised alerts for hot climates</div>
        </div>
        <div class="avatar-circle">FG</div>
      </div>
    </header>

    <main>
      <!-- Screen 0: Onboarding -->
      <section id="screen0" class="card">
        <div class="card-inner">
          <div class="section-title">Stay safe under extreme heat</div>
          <p class="small-text">
            HeatGuard AI turns weather and humidity into simple, clear guidance for
            workers, students, and coaches in the UAE.
          </p>

          <div class="pill-row">
            <div class="pill primary">Real-feel risk levels</div>
            <div class="pill">Smart break planning</div>
            <div class="pill">Hydration reminders</div>
          </div>

          <div class="pill-row" style="margin-top: 6px;">
            <div class="pill">Schools</div>
            <div class="pill">Construction sites</div>
            <div class="pill">Sports fields</div>
          </div>

          <div class="btn-row" style="margin-top: 18px;">
            <button id="startBtn" class="btn-primary">Get started</button>
          </div>

          <div class="bottom-info">
            <button id="aboutBtn" class="btn-ghost small-text">
              Learn how this prototype works →
            </button>
          </div>
        </div>
      </section>

      <!-- Screen 1: User Selection -->
      <section id="screen1" class="card hidden">
        <div class="card-inner">
          <div class="section-title">Set up your profile</div>
          <p class="small-text" style="margin-bottom: 10px;">
            Tell us who you are and where you are. We estimate your heat stress risk
            for today.
          </p>
          <div class="field">
            <label for="userType">User type</label>
            <select id="userType">
              <option>Construction Worker</option>
              <option>Outdoor Student</option>
              <option>Sports Coach</option>
            </select>
          </div>
          <div class="field">
            <label for="location">Location</label>
            <select id="location">
              <option>Abu Dhabi</option>
              <option>Dubai</option>
              <option>Al Ain</option>
            </select>
          </div>
          <button id="continueBtn" class="btn-primary">Show my heat risk</button>
        </div>
      </section>

      <!-- Screen 2: Today Overview -->
      <section id="screen2" class="card hidden">
        <div class="card-inner">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px;">
            <button id="backToSetup" class="btn-ghost small-text">← Profile</button>
            <div class="segmented">
              <div id="segToday" class="segment active">Today</div>
              <div id="segTomorrow" class="segment">Tomorrow</div>
            </div>
          </div>

          <div class="small-text" id="selectedProfile"></div>

          <h2 style="margin: 6px 0 6px; font-size: 1.05rem;">Today's heat risk</h2>
          <p class="small-text" id="todayLocation"></p>

          <div class="risk-row">
            <div id="riskIcon" class="risk-icon">☀️</div>
            <div id="riskBadge" class="risk-badge risk-extreme">Extreme</div>
          </div>

          <div class="metrics">
            <div class="metric">
              Temperature
              <span><span id="tempValue">46</span>°C</span>
            </div>
            <div class="metric">
              Humidity
              <span><span id="humidityValue">60</span>%</span>
            </div>
            <div class="metric">
              Feels like
              <span><span id="feelsLikeValue">53</span>°C</span>
            </div>
          </div>

          <p class="note" id="riskNote">High danger of heat exhaustion and heat stroke.</p>

          <h3 style="font-size: 0.95rem; margin-top: 10px;">Recommended actions</h3>
          <ul id="recommendationList" class="recommendations"></ul>

          <div class="chart-section">
            <div class="chart-title-row">
              <div class="chart-title">Today's heat risk by time of day</div>
              <div class="chart-legend">
                <span class="legend-dot"></span>
                <span>Higher bar = higher risk</span>
              </div>
            </div>
            <div class="chart">
              <div class="chart-bar">
                <div class="bar" id="chartMorning">
                  <div class="bar-label" id="labelMorning">–</div>
                </div>
                <span class="chart-label">Morning</span>
              </div>
              <div class="chart-bar">
                <div class="bar" id="chartAfternoon">
                  <div class="bar-label" id="labelAfternoon">–</div>
                </div>
                <span class="chart-label">Afternoon</span>
              </div>
              <div class="chart-bar">
                <div class="bar" id="chartEvening">
                  <div class="bar-label" id="labelEvening">–</div>
                </div>
                <span class="chart-label">Evening</span>
              </div>
            </div>
            <p class="small-text">Tap different profiles or locations to see how the pattern changes.</p>
          </div>

          <div class="btn-row">
            <button id="viewTomorrow" class="btn-secondary" style="flex: 1;">Open forecast</button>
          </div>
        </div>
      </section>

      <!-- Screen 3: Tomorrow's Forecast -->
      <section id="screen3" class="card hidden">
        <div class="card-inner">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px;">
            <button id="backToToday" class="btn-ghost small-text">← Today</button>
            <span class="small-text" id="selectedProfile2"></span>
          </div>

          <h2 style="margin: 4px 0 6px; font-size: 1.05rem;">Tomorrow's heat outlook</h2>
          <p class="small-text" id="tomorrowLocation"></p>

          <div class="forecast-grid">
            <div class="forecast-card">
              <div class="forecast-time">Morning</div>
              <div class="forecast-level" id="forecastMorningLevel">High</div>
              <div class="small-text" id="forecastMorningDetails"></div>
            </div>
            <div class="forecast-card">
              <div class="forecast-time">Afternoon</div>
              <div class="forecast-level" id="forecastAfternoonLevel">Extreme</div>
              <div class="small-text" id="forecastAfternoonDetails"></div>
            </div>
            <div class="forecast-card">
              <div class="forecast-time">Evening</div>
              <div class="forecast-level" id="forecastEveningLevel">Moderate</div>
              <div class="small-text" id="forecastEveningDetails"></div>
            </div>
          </div>

          <h3 style="font-size: 0.95rem; margin-top: 12px;">How HeatGuard AI thinks</h3>
          <p class="small-text">
            For this prototype, the heat index is a simple rule-based model:<br />
            <strong>Heat Index = Temperature + (Humidity ÷ 5)</strong><br />
            &lt; 35 = Safe · 35–40 = Caution · 40–45 = High · &gt; 45 = Extreme.
          </p>
        </div>
      </section>

      <!-- Screen 4: About -->
      <section id="screen4" class="card hidden">
        <div class="card-inner">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px;">
            <button id="backFromAbout" class="btn-ghost small-text">← Back</button>
            <span class="small-text">About HeatGuard AI</span>
          </div>

          <div class="section-title">Prototype details</div>
          <p class="small-text">
            This is an early software prototype built for the Youth 4 Sustainability
            "Out of Labs" program. It simulates how an AI assistant could support
            safer outdoor work and learning during extreme heat.
          </p>

          <ul class="small-text" style="margin-top: 8px; padding-left: 18px;">
            <li>Uses rule-based "AI" logic for the demo.</li>
            <li>Inputs: location, temperature, humidity, user type.</li>
            <li>Outputs: risk level, tailored actions, and a visual risk chart.</li>
          </ul>

          <p class="small-text" style="margin-top: 10px;">
            Future versions could connect to live weather APIs, school timetables, and
            site schedules to send real-time push notifications and dashboards.
          </p>
        </div>
      </section>
    </main>

    <div class="footer-note">
      Prototype for Youth 4 Sustainability – Out of Labs
    </div>
  </div>

  <script>
    const WEATHER = {
      "Abu Dhabi": { temperature: 46, humidity: 60 },
      Dubai: { temperature: 44, humidity: 55 },
      "Al Ain": { temperature: 45, humidity: 50 },
    };

    const RECOMMENDATIONS = {
      "Construction Worker": {
        Extreme: [
          "Take 10-minute breaks every 20 minutes of work.",
          "Drink water at least every 15 minutes.",
          "Avoid outdoor work between 12:00–15:00.",
          "Move heavy tasks to early morning or evening.",
        ],
        High: [
          "Schedule regular shade breaks every 30 minutes.",
          "Ensure all workers carry water bottles.",
          "Monitor workers for signs of dizziness or headache.",
        ],
        Caution: [
          "Plan short breaks each hour.",
          "Encourage workers to start the day well hydrated.",
        ],
        Safe: ["Normal work schedule. Keep drinking water regularly."],
      },
      "Outdoor Student": {
        Extreme: [
          "Move PE classes indoors or under full shade.",
          "Limit continuous activity to max 10–15 minutes.",
          "Mandatory water breaks before and after activity.",
        ],
        High: [
          "Shorten outdoor activities and add extra breaks.",
          "Avoid intense exercise during midday.",
        ],
        Caution: [
          "Encourage hats and light clothing.",
          "Plan more activities in early morning.",
        ],
        Safe: ["Normal schedule with regular water breaks."],
      },
      "Sports Coach": {
        Extreme: [
          "Reschedule training to early morning or late evening.",
          "Provide shade and cooling towels where possible.",
          "Check athletes frequently for signs of heat stress.",
        ],
        High: [
          "Reduce training intensity and add extra breaks.",
          "Ensure each athlete has their own water bottle.",
        ],
        Caution: [
          "Monitor players closely and give optional rests.",
          "Remind athletes to hydrate before and after sessions.",
        ],
        Safe: ["Regular training with standard water breaks."],
      },
    };

    const state = {
      userType: "Construction Worker",
      location: "Abu Dhabi",
    };

    const screen0 = document.getElementById("screen0");
    const screen1 = document.getElementById("screen1");
    const screen2 = document.getElementById("screen2");
    const screen3 = document.getElementById("screen3");
    const screen4 = document.getElementById("screen4");

    const userTypeSelect = document.getElementById("userType");
    const locationSelect = document.getElementById("location");

    const tempValue = document.getElementById("tempValue");
    const humidityValue = document.getElementById("humidityValue");
    const feelsLikeValue = document.getElementById("feelsLikeValue");
    const riskBadge = document.getElementById("riskBadge");
    const riskIcon = document.getElementById("riskIcon");
    const riskNote = document.getElementById("riskNote");
    const recommendationList = document.getElementById("recommendationList");
    const selectedProfile = document.getElementById("selectedProfile");
    const todayLocation = document.getElementById("todayLocation");

    const selectedProfile2 = document.getElementById("selectedProfile2");
    const tomorrowLocation = document.getElementById("tomorrowLocation");
    const forecastMorningLevel = document.getElementById("forecastMorningLevel");
    const forecastAfternoonLevel = document.getElementById("forecastAfternoonLevel");
    const forecastEveningLevel = document.getElementById("forecastEveningLevel");
    const forecastMorningDetails = document.getElementById("forecastMorningDetails");
    const forecastAfternoonDetails = document.getElementById("forecastAfternoonDetails");
    const forecastEveningDetails = document.getElementById("forecastEveningDetails");

    const chartMorning = document.getElementById("chartMorning");
    const chartAfternoon = document.getElementById("chartAfternoon");
    const chartEvening = document.getElementById("chartEvening");
    const labelMorning = document.getElementById("labelMorning");
    const labelAfternoon = document.getElementById("labelAfternoon");
    const labelEvening = document.getElementById("labelEvening");

    const segToday = document.getElementById("segToday");
    const segTomorrow = document.getElementById("segTomorrow");
    const aboutBtn = document.getElementById("aboutBtn");
    const backFromAbout = document.getElementById("backFromAbout");

    function calculateRisk(temperature, humidity) {
      const heatIndex = temperature + humidity / 5;
      let level;
      if (heatIndex < 35) level = "Safe";
      else if (heatIndex < 40) level = "Caution";
      else if (heatIndex < 45) level = "High";
      else level = "Extreme";
      return { heatIndex, level };
    }

    // Simple sanity tests for calculateRisk
    (function runTests() {
      const t1 = calculateRisk(30, 20); // 30 + 4 = 34 -> Safe
      console.assert(t1.level === "Safe", "Expected Safe for low heat index");
      const t2 = calculateRisk(38, 10); // 38 + 2 = 40 -> High
      console.assert(t2.level === "High", "Expected High for heat index 40");
      const t3 = calculateRisk(45, 50); // 45 + 10 = 55 -> Extreme
      console.assert(
        t3.level === "Extreme",
        "Expected Extreme for very high heat index"
      );
    })();

    function setRiskBadge(level) {
      riskBadge.classList.remove(
        "risk-safe",
        "risk-caution",
        "risk-high",
        "risk-extreme"
      );
      if (level === "Safe") riskBadge.classList.add("risk-safe");
      if (level === "Caution") riskBadge.classList.add("risk-caution");
      if (level === "High") riskBadge.classList.add("risk-high");
      if (level === "Extreme") riskBadge.classList.add("risk-extreme");
      riskBadge.textContent = level;

      const icons = {
        Safe: "😊",
        Caution: "😅",
        High: "🥵",
        Extreme: "⚠️",
      };
      riskIcon.textContent = icons[level] || "☀️";
    }

    function setRiskNote(level) {
      const notes = {
        Safe: "Low heat risk. Continue normal activities with regular hydration.",
        Caution:
          "Conditions are warm. Plan short breaks and remind everyone to drink water.",
        High:
          "High risk of heat stress. Shorten outdoor exposure and increase breaks.",
        Extreme:
          "Very high risk of heat exhaustion and heat stroke. Avoid midday heat.",
      };
      riskNote.textContent = notes[level] || "Heat risk information unavailable.";
    }

    function buildDayProfile(temperature, humidity) {
      const morningTemp = temperature - 3;
      const afternoonTemp = temperature + 1;
      const eveningTemp = temperature - 5;

      const morning = calculateRisk(morningTemp, humidity);
      const afternoon = calculateRisk(afternoonTemp, humidity);
      const evening = calculateRisk(eveningTemp, humidity);

      return [
        {
          label: "Morning",
          temp: morningTemp,
          humidity,
          heatIndex: morning.heatIndex,
          level: morning.level,
        },
        {
          label: "Afternoon",
          temp: afternoonTemp,
          humidity,
          heatIndex: afternoon.heatIndex,
          level: afternoon.level,
        },
        {
          label: "Evening",
          temp: eveningTemp,
          humidity,
          heatIndex: evening.heatIndex,
          level: evening.level,
        },
      ];
    }

    function levelShort(level) {
      return level === "Caution" ? "Caut." : level;
    }

    function updateBars(profile) {
      const heatIndexes = profile.map((p) => p.heatIndex);
      const min = Math.min(...heatIndexes);
      const max = Math.max(...heatIndexes);
      const span = Math.max(1, max - min);
      const base = 30; // minimum height %
      const range = 70; // additional % range

      const mapping = [
        { bar: chartMorning, labelEl: labelMorning, data: profile[0] },
        { bar: chartAfternoon, labelEl: labelAfternoon, data: profile[1] },
        { bar: chartEvening, labelEl: labelEvening, data: profile[2] },
      ];

      mapping.forEach(({ bar, labelEl, data }) => {
        bar.classList.remove("bar-safe", "bar-caution", "bar-high", "bar-extreme");
        const level = data.level;
        const cls =
          level === "Safe"
            ? "bar-safe"
            : level === "Caution"
            ? "bar-caution"
            : level === "High"
            ? "bar-high"
            : "bar-extreme";
        bar.classList.add(cls);

        const normalized = (data.heatIndex - min) / span;
        const heightPercent = base + range * normalized;
        bar.style.height = heightPercent + "%";

        labelEl.textContent = `${Math.round(data.heatIndex)}°`;
        bar.title = `${data.label}: ${Math.round(
          data.temp
        )}°C, HI ${Math.round(data.heatIndex)} (${data.level})`;
      });
    }

    function renderToday() {
      const weather = WEATHER[state.location];
      const { temperature, humidity } = weather;
      const { heatIndex, level } = calculateRisk(temperature, humidity);

      tempValue.textContent = temperature;
      humidityValue.textContent = humidity;
      feelsLikeValue.textContent = Math.round(heatIndex);
      todayLocation.textContent = `Location: ${state.location}`;
      selectedProfile.textContent = `${state.userType} · ${state.location}`;

      setRiskBadge(level);
      setRiskNote(level);

      recommendationList.innerHTML = "";
      const recsByUser = RECOMMENDATIONS[state.userType] || {};
      const recs = recsByUser[level] || [];
      recs.forEach((text) => {
        const li = document.createElement("li");
        li.textContent = text;
        recommendationList.appendChild(li);
      });

      const profile = buildDayProfile(temperature, humidity);
      updateBars(profile);
    }

    function describeForecast(level) {
      const map = {
        Safe: "Good time for most activities.",
        Caution: "Plan lighter activities and add breaks.",
        High: "Limit time in direct sun and keep water nearby.",
        Extreme: "Avoid intense outdoor activity; reschedule if possible.",
      };
      return map[level] || "Check conditions before planning activities.";
    }

    function renderTomorrow() {
      const base = WEATHER[state.location];
      const profile = buildDayProfile(base.temperature, base.humidity);

      const [morning, afternoon, evening] = profile;

      forecastMorningLevel.textContent = morning.level;
      forecastAfternoonLevel.textContent = afternoon.level;
      forecastEveningLevel.textContent = evening.level;

      forecastMorningDetails.textContent = describeForecast(morning.level);
      forecastAfternoonDetails.textContent = describeForecast(afternoon.level);
      forecastEveningDetails.textContent = describeForecast(evening.level);

      tomorrowLocation.textContent = `Location: ${state.location}`;
      selectedProfile2.textContent = `${state.userType} · ${state.location}`;
    }

    function showScreen(id) {
      [screen0, screen1, screen2, screen3, screen4].forEach((el) => {
        if (!el) return;
        el.classList.add("hidden");
      });
      const target = document.getElementById(id);
      if (target) {
        target.classList.remove("hidden");
      }
    }

    function activateSegment(which) {
      if (which === "today") {
        segToday.classList.add("active");
        segTomorrow.classList.remove("active");
        showScreen("screen2");
      } else {
        segTomorrow.classList.add("active");
        segToday.classList.remove("active");
        renderTomorrow();
        showScreen("screen3");
      }
    }

    // Event listeners
    document.getElementById("startBtn").addEventListener("click", () => {
      showScreen("screen1");
    });

    userTypeSelect.addEventListener("change", () => {
      state.userType = userTypeSelect.value;
      renderToday();
    });

    locationSelect.addEventListener("change", () => {
      state.location = locationSelect.value;
      renderToday();
    });

    document.getElementById("continueBtn").addEventListener("click", () => {
      renderToday();
      activateSegment("today");
    });

    document.getElementById("backToSetup").addEventListener("click", () => {
      showScreen("screen1");
    });

    document.getElementById("viewTomorrow").addEventListener("click", () => {
      activateSegment("tomorrow");
    });

    document.getElementById("backToToday").addEventListener("click", () => {
      activateSegment("today");
    });

    segToday.addEventListener("click", () => activateSegment("today"));
    segTomorrow.addEventListener("click", () => activateSegment("tomorrow"));

    aboutBtn.addEventListener("click", () => {
      showScreen("screen4");
    });

    backFromAbout.addEventListener("click", () => {
      showScreen("screen0");
    });
  </script>
</body>
</html>
