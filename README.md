<!DOCTYPE html>
<html lang="bg">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MLBB National Team Registration</title>
    <link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@500;600;700&family=Exo+2:wght@300;400;600;800&display=swap" rel="stylesheet">
    <style>
        :root {
            --gold: #FFD700;
            --gold2: #FFA500;
            --bg: #080c14;
            --panel: #0d1520;
            --panel2: #111c2e;
            --border: #1e3050;
            --accent: #00c8ff;
            --accent2: #0077ff;
            --red: #ff3c3c;
            --green: #00e676;
            --text: #c8daf0;
            --muted: #4a6080;
        }

        * { box-sizing: border-box; margin: 0; padding: 0; }

        body {
            font-family: 'Exo 2', sans-serif;
            background: var(--bg);
            color: var(--text);
            min-height: 100vh;
        }

        body::before {
            content: '';
            position: fixed; inset: 0;
            background:
                radial-gradient(ellipse 80% 40% at 50% -10%, rgba(0,120,255,0.10) 0%, transparent 70%),
                radial-gradient(ellipse 40% 60% at 90% 50%, rgba(255,160,0,0.05) 0%, transparent 60%);
            pointer-events: none; z-index: 0;
        }

        .grid-bg {
            position: fixed; inset: 0; z-index: 0;
            background-image:
                linear-gradient(rgba(0,200,255,0.025) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0,200,255,0.025) 1px, transparent 1px);
            background-size: 40px 40px;
            pointer-events: none;
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 20px 60px;
            position: relative; z-index: 1;
        }

        /* ── HEADER ── */
        header {
            text-align: center;
            padding: 44px 20px 28px;
            border-bottom: 1px solid var(--border);
            margin-bottom: 28px;
        }

        .flag-line {
            display: inline-flex; align-items: center; gap: 8px;
            background: rgba(255,255,255,0.03);
            border: 1px solid var(--border);
            border-radius: 40px;
            padding: 5px 18px;
            font-size: 11px;
            color: var(--muted);
            margin-bottom: 16px;
            letter-spacing: 3px;
            text-transform: uppercase;
        }

        header h1 {
            font-family: 'Rajdhani', sans-serif;
            font-size: clamp(28px, 6vw, 52px);
            font-weight: 700;
            letter-spacing: 3px;
            text-transform: uppercase;
            background: linear-gradient(135deg, #fff 20%, var(--gold) 60%, var(--gold2));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            line-height: 1.1;
            margin-bottom: 10px;
        }

        header p {
            color: var(--muted);
            font-size: 13px;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        /* ── COUNTDOWN ── */
        .countdown-section {
            margin-bottom: 28px;
            text-align: center;
            position: relative;
        }
        .countdown-label-top {
            font-size: 11px; font-weight: 700; letter-spacing: 4px;
            text-transform: uppercase; color: var(--muted); margin-bottom: 10px;
        }
        .countdown-deadline {
            font-family: 'Rajdhani', sans-serif; font-size: 13px; font-weight: 600;
            color: var(--gold2); letter-spacing: 2px; text-transform: uppercase;
            margin-bottom: 20px; opacity: 0.8;
        }
        .countdown-wrap {
            display: inline-flex; gap: 0; align-items: center; justify-content: center;
            background: rgba(0,0,0,0.4);
            border: 1px solid rgba(0,200,255,0.15);
            border-radius: 18px; padding: 28px 36px;
            position: relative; overflow: hidden;
        }
        .countdown-wrap::before {
            content: ''; position: absolute; inset: 0;
            background: radial-gradient(ellipse 100% 80% at 50% 50%, rgba(0,120,255,0.07) 0%, transparent 70%);
            pointer-events: none;
        }
        .countdown-wrap::after {
            content: ''; position: absolute; top: 0; left: 10%; right: 10%; height: 1px;
            background: linear-gradient(90deg, transparent, rgba(0,200,255,0.8), rgba(255,215,0,0.6), rgba(0,200,255,0.8), transparent);
            animation: scanLine 3s linear infinite;
        }
        @keyframes scanLine { 0%{opacity:.4} 50%{opacity:1} 100%{opacity:.4} }
        .cd-unit { display: flex; flex-direction: column; align-items: center; min-width: 90px; }
        .cd-num {
            font-family: 'Rajdhani', sans-serif;
            font-size: clamp(52px, 8vw, 88px); font-weight: 700; line-height: 1; color: #fff;
            text-shadow: 0 0 20px rgba(0,200,255,0.9), 0 0 40px rgba(0,200,255,0.5), 0 0 80px rgba(0,150,255,0.3);
            letter-spacing: -2px; transition: color 0.3s;
        }
        .cd-num.tick { animation: digitTick 0.25s ease-out; }
        @keyframes digitTick { 0%{transform:translateY(-6px);opacity:.4} 100%{transform:translateY(0);opacity:1} }
        .cd-label { font-size: 10px; font-weight: 700; letter-spacing: 3px; text-transform: uppercase; color: var(--muted); margin-top: 6px; }
        .cd-sep {
            font-family: 'Rajdhani', sans-serif; font-size: clamp(40px, 6vw, 72px); font-weight: 700;
            color: rgba(0,200,255,0.3); margin: 0 4px; margin-bottom: 20px;
            animation: blink 1s step-start infinite; line-height: 1;
        }
        @keyframes blink { 0%,100%{opacity:1} 50%{opacity:.15} }
        .countdown-wrap.urgent .cd-num {
            color: #ff6b6b;
            text-shadow: 0 0 20px rgba(255,60,60,0.9), 0 0 40px rgba(255,60,60,0.5), 0 0 80px rgba(255,0,0,0.3);
        }
        .countdown-wrap.urgent::after {
            background: linear-gradient(90deg, transparent, rgba(255,60,60,0.8), rgba(255,150,0,0.6), rgba(255,60,60,0.8), transparent);
        }
        .cd-expired {
            font-family: 'Rajdhani', sans-serif; font-size: 28px; font-weight: 700;
            color: var(--red); letter-spacing: 3px; text-shadow: 0 0 20px rgba(255,60,60,0.6); padding: 28px 40px;
        }
        .countdown-particles { position: absolute; inset: 0; pointer-events: none; overflow: hidden; border-radius: 18px; }
        .particle {
            position: absolute; width: 2px; height: 2px; border-radius: 50%;
            background: rgba(0,200,255,0.6); animation: particleFloat linear infinite;
        }
        @keyframes particleFloat {
            0%{transform:translateY(100%) translateX(0);opacity:0}
            10%{opacity:1} 90%{opacity:.6}
            100%{transform:translateY(-100px) translateX(var(--drift));opacity:0}
        }
        .countdown-bottom {
            margin-top: 14px; display: flex; align-items: center; justify-content: center;
            gap: 8px; font-size: 12px; color: var(--muted); letter-spacing: 1px;
        }
        .live-dot {
            width: 7px; height: 7px; border-radius: 50%; background: var(--green);
            box-shadow: 0 0 8px var(--green); animation: pulse 1.5s ease-in-out infinite; flex-shrink: 0;
        }
        @keyframes pulse { 0%,100%{transform:scale(1);opacity:1} 50%{transform:scale(1.5);opacity:.5} }

        /* ── TABS ── */
        .tabs {
            display: flex; gap: 6px;
            background: var(--panel);
            border: 1px solid var(--border);
            border-radius: 10px;
            padding: 5px;
            margin-bottom: 22px;
            overflow-x: auto;
        }

        .tab-btn {
            flex: 1; min-width: 100px;
            padding: 10px 14px;
            background: transparent;
            border: none; border-radius: 7px;
            color: var(--muted);
            font-family: 'Exo 2', sans-serif;
            font-size: 12px; font-weight: 600;
            cursor: pointer; transition: all .2s;
            white-space: nowrap;
            text-transform: uppercase; letter-spacing: .5px;
        }

        .tab-btn.active {
            background: linear-gradient(135deg, var(--accent2), #0050cc);
            color: #fff;
        }

        .tab-btn:hover:not(.active) {
            background: rgba(255,255,255,0.05);
            color: var(--text);
        }

        .tab-content { display: none; }
        .tab-content.active { display: block; }

        /* ── FORM CARD ── */
        .form-card {
            background: var(--panel);
            border: 1px solid var(--border);
            border-radius: 14px;
            padding: 28px;
            margin-bottom: 20px;
        }

        .card-title {
            font-family: 'Rajdhani', sans-serif;
            font-size: 20px; font-weight: 700;
            color: var(--gold);
            text-transform: uppercase; letter-spacing: 2px;
            margin-bottom: 20px;
            padding-bottom: 14px;
            border-bottom: 1px solid var(--border);
        }

        .form-grid {
            display: grid; grid-template-columns: 1fr 1fr;
            gap: 16px; margin-bottom: 16px;
        }

        .form-group { display: flex; flex-direction: column; gap: 7px; }
        .form-group.full { grid-column: 1 / -1; }

        label {
            font-size: 11px; font-weight: 600;
            color: var(--muted);
            text-transform: uppercase; letter-spacing: 1px;
        }

        input, select, textarea {
            background: var(--panel2);
            border: 1px solid var(--border);
            border-radius: 8px;
            color: var(--text);
            font-family: 'Exo 2', sans-serif;
            font-size: 13px;
            padding: 11px 13px;
            outline: none;
            transition: border-color .2s, box-shadow .2s;
        }

        input:focus, select:focus, textarea:focus {
            border-color: var(--accent2);
            box-shadow: 0 0 0 3px rgba(0,119,255,0.12);
        }

        select option { background: var(--panel2); }
        textarea { resize: vertical; min-height: 80px; }

        /* ── ROLES ── */
        .roles-grid {
            display: grid; grid-template-columns: repeat(5, 1fr);
            gap: 8px;
        }

        .role-checkbox {
            display: flex; align-items: center; gap: 7px;
            padding: 10px 8px;
            background: var(--panel2);
            border: 1px solid var(--border);
            border-radius: 8px;
            cursor: pointer; transition: all .2s;
        }

        .role-checkbox:hover { border-color: var(--accent2); background: rgba(0,119,255,0.07); }
        .role-checkbox:has(input:checked) { border-color: var(--gold); background: rgba(255,215,0,0.06); }

        .role-checkbox input[type="checkbox"] {
            width: 15px; height: 15px;
            accent-color: var(--gold);
            padding: 0; border: none; background: none;
        }

        .role-checkbox label {
            cursor: pointer; font-size: 11px; font-weight: 600;
            color: var(--text); margin: 0;
            letter-spacing: 0; text-transform: none;
        }

        /* ── BUTTONS ── */
        .btn-group {
            display: flex; gap: 10px;
            justify-content: flex-end; margin-top: 20px;
        }

        button {
            padding: 11px 22px;
            border: none; border-radius: 8px;
            font-family: 'Exo 2', sans-serif;
            font-size: 12px; font-weight: 700;
            text-transform: uppercase; letter-spacing: 1px;
            cursor: pointer; transition: all .2s;
        }

        .btn-gold {
            background: linear-gradient(135deg, var(--gold), var(--gold2));
            color: #000;
        }

        .btn-gold:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(255,165,0,0.35); }
        .btn-gold:disabled { opacity: .5; cursor: not-allowed; transform: none; box-shadow: none; }

        .btn-blue {
            background: linear-gradient(135deg, var(--accent2), #004fcc);
            color: #fff;
        }

        .btn-blue:hover { transform: translateY(-2px); box-shadow: 0 6px 20px rgba(0,119,255,0.35); }

        .btn-ghost {
            background: transparent;
            border: 1px solid var(--border);
            color: var(--muted);
        }

        .btn-ghost:hover { border-color: var(--accent); color: var(--text); }

        .btn-red {
            background: rgba(255,60,60,0.08);
            border: 1px solid var(--red);
            color: var(--red);
            padding: 5px 10px; font-size: 11px;
        }

        .btn-red:hover { background: rgba(255,60,60,0.18); }

        /* ── MESSAGES ── */
        .message {
            padding: 14px 16px;
            border-radius: 9px;
            margin-bottom: 18px;
            font-size: 13px;
            display: none;
            line-height: 1.5;
        }

        .message.show { display: block; }

        .message.success {
            background: rgba(0,230,118,0.08);
            border: 1px solid rgba(0,230,118,0.3);
            color: var(--green);
        }

        .message.error {
            background: rgba(255,60,60,0.08);
            border: 1px solid rgba(255,60,60,0.3);
            color: var(--red);
        }

        /* ── SUCCESS STATE ── */
        .success-state {
            text-align: center;
            padding: 50px 20px;
            display: none;
        }

        .success-state.show { display: block; }
        .success-icon { font-size: 56px; margin-bottom: 16px; }

        .success-state h3 {
            font-family: 'Rajdhani', sans-serif;
            font-size: 26px; font-weight: 700;
            color: var(--gold); margin-bottom: 10px;
        }

        .success-state p { color: var(--muted); font-size: 14px; line-height: 1.6; }

        /* ── TABLE ── */
        .filter-bar {
            display: flex; gap: 10px; flex-wrap: wrap;
            margin-bottom: 16px;
        }

        .filter-bar input, .filter-bar select { flex: 1; min-width: 140px; }

        table { width: 100%; border-collapse: collapse; }

        thead { background: var(--panel2); }

        th {
            padding: 11px 12px;
            text-align: left;
            font-size: 10px; font-weight: 700;
            text-transform: uppercase; letter-spacing: 1px;
            color: var(--muted);
            border-bottom: 1px solid var(--border);
        }

        td {
            padding: 12px;
            border-bottom: 1px solid rgba(30,48,80,0.45);
            font-size: 12px; vertical-align: middle;
        }

        tr:hover td { background: rgba(0,119,255,0.04); }

        .rank-badge {
            display: inline-block; padding: 3px 9px; border-radius: 5px;
            font-size: 10px; font-weight: 700;
            background: rgba(255,165,0,0.13); color: var(--gold);
            border: 1px solid rgba(255,165,0,0.3);
        }

        .role-badge {
            display: inline-block; padding: 2px 7px; border-radius: 4px;
            font-size: 10px; font-weight: 600; margin: 1px;
            background: rgba(0,200,255,0.08); color: var(--accent);
            border: 1px solid rgba(0,200,255,0.2);
        }

        .status-badge {
            display: inline-block; padding: 3px 9px; border-radius: 5px;
            font-size: 10px; font-weight: 700;
        }

        .status-pending  { background: rgba(255,200,0,0.1);  color: #ffcc00; }
        .status-approved { background: rgba(0,230,118,0.1);  color: var(--green); }
        .status-national { background: rgba(255,165,0,0.15); color: var(--gold); border: 1px solid rgba(255,165,0,0.3); }
        .status-reserve  { background: rgba(0,119,255,0.12); color: var(--accent); border: 1px solid rgba(0,119,255,0.3); }

        .empty-state { text-align: center; padding: 50px 20px; color: var(--muted); }
        .empty-state .ico { font-size: 44px; margin-bottom: 12px; }

        @media (max-width: 768px) {
            .form-grid { grid-template-columns: 1fr; }
            .roles-grid { grid-template-columns: repeat(2, 1fr); }
            .countdown-wrap { padding: 18px 12px; }
            .cd-unit { min-width: 60px; }
            .cd-num { font-size: 42px; letter-spacing: -1px; }
            .cd-sep { font-size: 32px; }
            .cd-label { font-size: 9px; letter-spacing: 1px; }
            .tabs { gap: 4px; }
            .tab-btn { padding: 8px 8px; font-size: 11px; min-width: 80px; }
            .form-card { padding: 18px 14px; }
            header h1 { font-size: 28px; letter-spacing: 1px; }
            .container { padding: 0 12px 40px; }
            header { padding: 28px 12px 20px; }
            .btn-group { flex-direction: column; }
            .btn-group button { width: 100%; }
        }

        @media (max-width: 480px) {
            .roles-grid { grid-template-columns: 1fr 1fr; }
            .cd-num { font-size: 34px; }
            .cd-unit { min-width: 46px; }
            .cd-sep { font-size: 26px; margin: 0 2px; }
            header h1 { font-size: 22px; }
        }
    </style>
</head>
<body>
<div class="grid-bg"></div>

<div class="container">
    <header>
        <div class="flag-line">🇧🇬 Bulgaria Esports · Official Selection</div>
        <h1>🎮 MLBB National Team</h1>
        <p>Български национален отбор - официална регистрация</p>
    </header>

    <!-- COUNTDOWN -->
    <div class="countdown-section">
        <div class="countdown-label-top">⏰ Краен срок за регистрация</div>
        <div class="countdown-deadline">Петък, 17 Април 2026 · 23:59</div>
        <div class="countdown-wrap" id="cdWrap">
            <div class="countdown-particles" id="cdParticles"></div>
            <div class="cd-unit">
                <div class="cd-num" id="cdDays">00</div>
                <div class="cd-label">Дни</div>
            </div>
            <div class="cd-sep">:</div>
            <div class="cd-unit">
                <div class="cd-num" id="cdHours">00</div>
                <div class="cd-label">Часа</div>
            </div>
            <div class="cd-sep">:</div>
            <div class="cd-unit">
                <div class="cd-num" id="cdMins">00</div>
                <div class="cd-label">Минути</div>
            </div>
            <div class="cd-sep">:</div>
            <div class="cd-unit">
                <div class="cd-num" id="cdSecs">00</div>
                <div class="cd-label">Секунди</div>
            </div>
        </div>
        <div class="countdown-bottom">
            <div class="live-dot"></div>
            <span>Обновява се в реално време</span>
        </div>
    </div>

    <!-- TABS — Admin tab is hidden, accessible only via secret URL hash -->
    <div class="tabs">
        <button class="tab-btn active" onclick="switchTab(event,'register')">📝 Регистрация</button>
        <button class="tab-btn" id="adminTabBtn" onclick="switchTab(event,'admin')" style="display:none;">⚙️ Администрация</button>
    </div>

    <!-- ══════════════ TAB: РЕГИСТРАЦИЯ ══════════════ -->
    <div id="register" class="tab-content active">
        <div class="form-card">
            <div class="card-title">📝 Регистрирай се за Национален Отбор</div>

            <!-- Success state (shown after Formspree submit) -->
            <div class="success-state" id="successState">
                <div class="success-icon">🎉</div>
                <h3>Регистрацията е изпратена!</h3>
                <p>Получихме твоята кандидатура.<br>
                Ще бъдеш уведомен чрез Facebook и Discord за резултата.<br><br>
                Очаквай съобщение от организаторите!</p>
                <br>
                <button class="btn-gold" onclick="showFormAgain()">➕ Нова Регистрация</button>
            </div>

            <!-- The actual form -->
            <div id="formWrapper">
                <div id="regMessage" class="message"></div>

                <!-- ▼▼▼ Formspree AJAX integration ▼▼▼ -->
                <form id="registrationForm" onsubmit="handleSubmit(event)">
                    <div class="form-grid">
                        <div class="form-group">
                            <label for="ign">IGN (In-Game Name) *</label>
                            <input type="text" id="ign" name="IGN" placeholder="Твоят игрален прякор" required>
                        </div>

                        <div class="form-group">
                            <label for="discord">Discord *</label>
                            <input type="text" id="discord" name="Discord" placeholder="username или username#1234" required>
                        </div>

                        <div class="form-group">
                            <label for="facebook">Facebook (за обратна връзка)</label>
                            <input type="text" id="facebook" name="Facebook" placeholder="Твоя Facebook профил или линк">
                        </div>

                        <div class="form-group">
                            <label for="rank">Игрален Ранг *</label>
                            <select id="rank" name="Ранг" required>
                                <option value="">— Избери ранг —</option>
                                <option value="Mythical Immortal">Mythical Immortal</option>
                                <option value="Mythical Glory">Mythical Glory</option>
                                <option value="Mythical Honor">Mythical Honor</option>
                                <option value="Legend">Legend</option>
                                <option value="Epic">Epic</option>
                            </select>
                        </div>

                        <div class="form-group">
                            <label for="winrate">Win Rate (%) *</label>
                            <input type="number" id="winrate" name="Win Rate" placeholder="напр. 58" min="0" max="100" required>
                        </div>

                        <div class="form-group">
                            <label for="experience">Опит в Турнири</label>
                            <input type="text" id="experience" name="Турнирен Опит" placeholder="напр. участие в турнир 2x, scrims">
                        </div>
                    </div>

                    <div class="form-group full" style="margin-bottom:16px;">
                        <label>Предпочитани Роли * (поне 1)</label>
                        <div class="roles-grid">
                            <div class="role-checkbox">
                                <input type="checkbox" id="role_mid" name="Роля: Mid laner" value="Mid laner">
                                <label for="role_mid">⚡ Mid laner</label>
                            </div>
                            <div class="role-checkbox">
                                <input type="checkbox" id="role_marksman" name="Роля: Marksman" value="Marksman">
                                <label for="role_marksman">🏹 Marksman</label>
                            </div>
                            <div class="role-checkbox">
                                <input type="checkbox" id="role_roamer" name="Роля: Roamer" value="Roamer">
                                <label for="role_roamer">🌊 Roamer</label>
                            </div>
                            <div class="role-checkbox">
                                <input type="checkbox" id="role_exp" name="Роля: Exp laner" value="Exp laner">
                                <label for="role_exp">🛡️ Exp laner</label>
                            </div>
                            <div class="role-checkbox">
                                <input type="checkbox" id="role_jungle" name="Роля: Jungle" value="Jungle">
                                <label for="role_jungle">🌿 Jungle</label>
                            </div>
                        </div>
                    </div>


                    <div class="form-group full" style="margin-bottom:16px;">
                        <label for="heroes">Любими Герои (топ 3-5)</label>
                        <textarea id="heroes" name="Любими Герои" placeholder="напр. Lancelot, Ling, Fanny, Beatrix"></textarea>
                    </div>

                    <div class="form-group full">
                        <label for="extra">Защо искаш да представляваш България?</label>
                        <textarea id="extra" name="Мотивация" placeholder="Разкажи за мотивацията си..."></textarea>
                    </div>

                    <div class="btn-group">
                        <button type="button" class="btn-ghost" onclick="clearForm()">Изчисти</button>
                        <button type="submit" class="btn-gold" id="submitBtn">✔ Изпрати Регистрация</button>
                    </div>
                </form>
            </div>
        </div>
    </div>

    <!-- ══════════════ TAB: АДМИНИСТРАЦИЯ ══════════════ -->
    <div id="admin" class="tab-content">
        <div class="form-card">
            <div class="card-title">⚙️ Административен Панел</div>
            <div style="display:flex; gap:10px; flex-wrap:wrap; margin-bottom:20px;">
                <button class="btn-blue" onclick="approveAllPending()">✔ Одобри Всички Чакащи</button>
                <button class="btn-ghost" onclick="resetAllData()">🔄 Изтрий Всички Данни</button>
            </div>
            <div style="overflow-x:auto;">
                <table>
                    <thead>
                        <tr>
                            <th>IGN</th>
                            <th>Discord</th>
                            <th>Facebook</th>
                            <th>Ранг</th>
                            <th>WR%</th>
                            <th>Роли</th>
                            <th>Статус</th>
                            <th>Действия</th>
                        </tr>
                    </thead>
                    <tbody id="adminBody"></tbody>
                </table>
            </div>
            <div id="emptyAdmin" class="empty-state" style="display:none;">
                <div class="ico">📋</div>
                <p>Няма участници за управление</p>
            </div>
        </div>
    </div>
</div>

<script>
// ══════════════════════════════════════════════
//  STATE
// ══════════════════════════════════════════════
let participants = JSON.parse(localStorage.getItem('mlbb_participants') || '[]');

// ══════════════════════════════════════════════
//  SECRET ADMIN HASH
//  Достъп до админ панела: yoursite.com/index.html#admin-mlbb2025bg
//  Смени тайната дума по-долу — пази я само за себе си!
// ══════════════════════════════════════════════
const ADMIN_SECRET = 'mlbb2025bg';

function checkAdminAccess() {
    const params = new URLSearchParams(window.location.search);
    const hash   = window.location.hash;
    // Works on CodePen (?admin=secret) and Netlify/other sites (#secret)
    if (params.get('admin') === ADMIN_SECRET || hash.includes(ADMIN_SECRET)) {
        document.getElementById('adminTabBtn').style.display = '';
        document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
        document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
        document.getElementById('admin').classList.add('active');
        document.getElementById('adminTabBtn').classList.add('active');
        renderAdminPanel();
    }
}

window.addEventListener('hashchange', checkAdminAccess);

// ══════════════════════════════════════════════
//  INIT
// ══════════════════════════════════════════════
updateStats();
renderAdminPanel();
checkAdminAccess();

// ══════════════════════════════════════════════
//  TABS
// ══════════════════════════════════════════════
function switchTab(e, tabName) {
    document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
    document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
    document.getElementById(tabName).classList.add('active');
    e.target.classList.add('active');
    if (tabName === 'participants') renderParticipants();
    if (tabName === 'admin') renderAdminPanel();
}

// ══════════════════════════════════════════════
//  FORMSPREE AJAX SUBMIT
// ══════════════════════════════════════════════
async function handleSubmit(e) {
    e.preventDefault();

    const ign     = document.getElementById('ign').value.trim();
    const discord = document.getElementById('discord').value.trim();
    const rank    = document.getElementById('rank').value;
    const winrate = document.getElementById('winrate').value;
    const roles   = getSelectedRoles();

    // Client-side validation — show specific error for each missing field
    const errors = [];
    if (!ign)              errors.push('❌ IGN е задължително');
    if (!discord)          errors.push('❌ Discord е задължително');
    if (!rank)             errors.push('❌ Избери ранг');
    if (!winrate)          errors.push('❌ Въведи Win Rate');
    if (roles.length === 0) errors.push('❌ Избери поне една роля');

    if (errors.length > 0) {
        showMessage('regMessage', errors.join('  |  '), 'error');
        // Also highlight the empty fields visually
        const fieldMap = {ign: ign, discord: discord, rank: rank, winrate: winrate};
        Object.entries(fieldMap).forEach(([id, val]) => {
            const el = document.getElementById(id);
            if (el) el.style.borderColor = val ? '' : '#ff3c3c';
        });
        return;
    }

    // Reset border colors on valid submit
    ['ign','discord','rank','winrate'].forEach(id => {
        const el = document.getElementById(id);
        if (el) el.style.borderColor = '';
    });

    if (participants.find(p => p.ign.toLowerCase() === ign.toLowerCase())) {
        showMessage('regMessage', '⚠️ Участник с този IGN вече е регистриран!', 'error');
        return;
    }

    const submitBtn = document.getElementById('submitBtn');
    submitBtn.disabled = true;
    submitBtn.textContent = '⏳ Изпращане...';

    // Re-read roles fresh at submit time to avoid stale values
    const freshRoles = getSelectedRoles();
    const payload = JSON.stringify({
        ign:        ign,
        discord:    discord,
        facebook:   document.getElementById('facebook').value.trim(),
        rank:       rank,
        winrate:    winrate,
        roles:      freshRoles.join(', '),
        heroes:     document.getElementById('heroes').value.trim(),
        experience: document.getElementById('experience').value.trim(),
        extra:      document.getElementById('extra').value.trim()
    });

    try {
        // Google Apps Script requires no-cors mode from browser
        await fetch('https://script.google.com/macros/s/AKfycbyAkclGB7MtKb_5zGun9ypbxC4DQTW5hvGzW4fRmCxm5Mnu1WOoRvmhEIYgHSFnvjGOKg/exec', {
            method: 'POST',
            body: payload,
            mode: 'no-cors'
        });

        // no-cors always returns opaque response so we assume success if no exception
        participants.push({
            id: Date.now(),
            ign,
            discord,
            facebook: document.getElementById('facebook').value.trim(),
            rank,
            winrate: parseFloat(winrate) || 0,
            roles,
            experience: document.getElementById('experience').value.trim(),
            heroes: document.getElementById('heroes').value.trim(),
            extra: document.getElementById('extra').value.trim(),
            status: 'pending',
            registeredAt: new Date().toLocaleString('bg-BG')
        });
        localStorage.setItem('mlbb_participants', JSON.stringify(participants));
        updateStats();

        // Show success screen
        document.getElementById('formWrapper').style.display = 'none';
        document.getElementById('successState').classList.add('show');

    } catch (err) {
        showMessage('regMessage', '❌ Няма връзка. Провери интернета и опитай пак.', 'error');
        submitBtn.disabled = false;
        submitBtn.textContent = '✔ Изпрати Регистрация';
    }
}

function showFormAgain() {
    document.getElementById('registrationForm').reset();
    document.getElementById('formWrapper').style.display = 'block';
    document.getElementById('successState').classList.remove('show');
    const btn = document.getElementById('submitBtn');
    btn.disabled = false;
    btn.textContent = '✔ Изпрати Регистрация';
}

// ══════════════════════════════════════════════
//  HELPERS
// ══════════════════════════════════════════════
function getSelectedRoles() {
    // Map each role to its exact checkbox id
    const roleMap = {
        'Mid laner':  'role_mid',
        'Marksman':   'role_marksman',
        'Roamer':     'role_roamer',
        'Exp laner':  'role_exp',
        'Jungle':     'role_jungle'
    };
    return Object.entries(roleMap)
        .filter(([role, id]) => {
            const el = document.getElementById(id);
            return el && el.checked;
        })
        .map(([role]) => role);
}

function showMessage(elId, msg, type) {
    const el = document.getElementById(elId);
    el.textContent = msg;
    el.className = 'message show ' + type;
    setTimeout(() => el.classList.remove('show'), 5000);
}

function clearForm() {
    document.getElementById('registrationForm').reset();
}

function updateStats() {
    // Stats display replaced by countdown timer
}

// ══════════════════════════════════════════════
//  COUNTDOWN TIMER
// ══════════════════════════════════════════════
(function initCountdown() {
    const DEADLINE = new Date('2026-04-17T23:59:59');
    const elDays  = document.getElementById('cdDays');
    const elHours = document.getElementById('cdHours');
    const elMins  = document.getElementById('cdMins');
    const elSecs  = document.getElementById('cdSecs');
    const wrap    = document.getElementById('cdWrap');
    const pContainer = document.getElementById('cdParticles');
    if (pContainer) {
        for (let i = 0; i < 18; i++) {
            const p = document.createElement('div');
            p.className = 'particle';
            const left = Math.random() * 100;
            const dur  = 4 + Math.random() * 6;
            const delay = Math.random() * 6;
            const drift = (Math.random() - 0.5) * 60;
            p.style.cssText = 'left:'+left+'%;bottom:0;animation-duration:'+dur+'s;animation-delay:'+delay+'s;--drift:'+drift+'px';
            if (i % 3 === 1) p.style.background = 'rgba(255,215,0,0.5)';
            if (i % 3 === 2) p.style.background = 'rgba(0,119,255,0.5)';
            pContainer.appendChild(p);
        }
    }
    function pad(n) { return String(n).padStart(2, '0'); }
    function tick(el, newVal) {
        if (!el || el.textContent === newVal) return;
        el.textContent = newVal;
        el.classList.remove('tick');
        void el.offsetWidth;
        el.classList.add('tick');
    }
    function update() {
        const diff = new Date('2026-04-17T23:59:59') - new Date();
        if (diff <= 0) {
            if (wrap) wrap.innerHTML = '<div class="cd-expired">🔒 РЕГИСТРАЦИЯТА Е ПРИКЛЮЧИЛА</div>';
            return;
        }
        tick(elDays,  pad(Math.floor(diff / 86400000)));
        tick(elHours, pad(Math.floor((diff % 86400000) / 3600000)));
        tick(elMins,  pad(Math.floor((diff % 3600000) / 60000)));
        tick(elSecs,  pad(Math.floor((diff % 60000) / 1000)));
        if (diff < 86400000 && wrap) wrap.classList.add('urgent');
    }
    update();
    setInterval(update, 1000);
})();

function getStatusLabel(s) {
    return { pending:'⏳ Чакащ', approved:'✔ Одобрен', national:'🇧🇬 Национален', reserve:'🔵 Резерва' }[s] || s;
}

// ══════════════════════════════════════════════
//  ADMIN PANEL
// ══════════════════════════════════════════════
function renderAdminPanel() {
    const tbody = document.getElementById('adminBody');
    const empty = document.getElementById('emptyAdmin');

    if (!participants.length) { tbody.innerHTML = ''; empty.style.display = 'block'; return; }
    empty.style.display = 'none';

    tbody.innerHTML = participants.map(p => `
        <tr>
            <td><strong>${p.ign}</strong></td>
            <td>${p.discord}</td>
            <td style="color:var(--muted)">${p.facebook || '—'}</td>
            <td><span class="rank-badge">${p.rank}</span></td>
            <td>${p.winrate}%</td>
            <td>${p.roles.map(r=>`<span class="role-badge">${r}</span>`).join('')}</td>
            <td>
                <select onchange="setStatus(${p.id},this.value)" style="padding:4px 8px;font-size:11px;background:var(--panel2);border:1px solid var(--border);color:var(--text);border-radius:5px">
                    <option value="pending"  ${p.status==='pending' ?'selected':''}>⏳ Чакащ</option>
                    <option value="approved" ${p.status==='approved'?'selected':''}>✔ Одобрен</option>
                    <option value="national" ${p.status==='national'?'selected':''}>🇧🇬 Национален</option>
                    <option value="reserve"  ${p.status==='reserve' ?'selected':''}>🔵 Резерва</option>
                </select>
            </td>
            <td>
                <button class="btn-red" onclick="deleteParticipant(${p.id})">🗑 Изтрий</button>
            </td>
        </tr>`).join('');
}

function setStatus(id, status) {
    const p = participants.find(x => x.id === id);
    if (!p) return;
    p.status = status;
    localStorage.setItem('mlbb_participants', JSON.stringify(participants));
    updateStats(); renderParticipants(); renderAdminPanel();
}

function deleteParticipant(id) {
    if (!confirm('Сигурен ли си?')) return;
    participants = participants.filter(p => p.id !== id);
    localStorage.setItem('mlbb_participants', JSON.stringify(participants));
    updateStats(); renderParticipants(); renderAdminPanel();
}

function approveAllPending() {
    participants.forEach(p => { if (p.status === 'pending') p.status = 'approved'; });
    localStorage.setItem('mlbb_participants', JSON.stringify(participants));
    updateStats(); renderAdminPanel(); renderParticipants();
    alert('✔ Всички чакащи участници са одобрени!');
}

function resetAllData() {
    if (!confirm('⚠️ Това ще изтрие ВСИЧКИ локални данни! Formspree записите остават. Сигурен ли си?')) return;
    participants = [];
    localStorage.setItem('mlbb_participants', JSON.stringify(participants));
    updateStats(); renderAdminPanel(); renderParticipants();
}

function exportToCSV() {
    const hdr = ['IGN','Discord','Facebook','Ранг','Win Rate','Роли','Опит','Герои','Мотивация','Статус','Дата'];
    const rows = participants.map(p => [
        p.ign, p.discord, p.facebook, p.rank, p.winrate,
        p.roles.join('|'), p.experience, p.heroes, p.extra, p.status, p.registeredAt
    ]);
    const csv = [hdr, ...rows].map(r => r.map(c => `"${c}"`).join(',')).join('\n');
    const a = document.createElement('a');
    a.href = 'data:text/csv;charset=utf-8,\uFEFF' + encodeURIComponent(csv);
    a.download = 'mlbb_participants_' + new Date().toISOString().slice(0,10) + '.csv';
    a.click();
}
</script>
</body>
</html>
