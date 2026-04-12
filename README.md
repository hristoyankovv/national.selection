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
            background: linear-gradient(90deg, transparent, rgba(0,200,255,0.8), rgba(2
