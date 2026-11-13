<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MIC CHECK! – My Speaking Identity</title>
  <!-- Load Google Fonts for bold, child-friendly TV talent-show typography -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@500;600;700&family=Nunito:wght@600;700;800;900&display=swap" rel="stylesheet" />

  <style>
    /* ==========================================================================
       1. CSS VARIABLES & TV TALENT SHOW PALETTE
       ========================================================================== */
    :root {
      --studio-deep: #15092e;
      --studio-purple: #2c1359;
      --studio-indigo: #3e1d80;
      --curtain-red: #b91c1c;
      --curtain-bright: #ef4444;
      --gold-bright: #fde047;
      --gold-warm: #f59e0b;
      --gold-dark: #92400e;
      --cyan-neon: #38bdf8;
      --cyan-dark: #0284c7;
      --emerald-ok: #22c55e;
      --emerald-dark: #15803d;
      --coral-rec: #f43f5e;
      --coral-dark: #be123c;
      --card-cream: #fffdf7;
      --text-ink: #1e1b4b;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      font-family: 'Nunito', sans-serif;
      background: radial-gradient(circle at top, #3b1e7a 0%, #14082b 75%, #090317 100%);
      color: var(--text-ink);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 12px;
      overflow-x: hidden;
    }

    h1, h2, h3, .show-font {
      font-family: 'Fredoka', sans-serif;
      letter-spacing: 0.4px;
    }

    /* ==========================================================================
       2. MAIN TV STUDIO STAGE CONTAINER & ANIMATED LIGHTING
       ========================================================================== */
    #tv-stage-container {
      width: 100%;
      max-width: 980px;
      min-height: 680px;
      background: linear-gradient(180deg, #24104d 0%, #32186b 55%, #1d0c3d 100%);
      border-radius: 30px;
      border: 6px solid var(--gold-warm);
      box-shadow:
        0 24px 60px rgba(0, 0, 0, 0.72),
        0 0 36px rgba(251, 191, 36, 0.35),
        inset 0 0 0 4px #78350f;
      position: relative;
      overflow: hidden;
      display: flex;
      flex-direction: column;
    }

    /* Sweeping Animated TV Stage Spotlights */
    .spotlight {
      position: absolute;
      top: -40px;
      width: 340px;
      height: 540px;
      background: linear-gradient(180deg, rgba(253, 224, 71, 0.24) 0%, rgba(253, 224, 71, 0) 90%);
      clip-path: polygon(42% 0%, 58% 0%, 100% 100%, 0% 100%);
      pointer-events: none;
      z-index: 1;
      transform-origin: top center;
    }

    .spotlight.left {
      left: 6%;
      animation: swayLeft 5.5s ease-in-out infinite;
    }

    .spotlight.right {
      right: 6%;
      background: linear-gradient(180deg, rgba(56, 189, 248, 0.22) 0%, rgba(56, 189, 248, 0) 90%);
      animation: swayRight 6s ease-in-out infinite;
    }

    .spotlight.center-onair {
      left: 50%;
      width: 490px;
      transform: translateX(-50%);
      background: linear-gradient(180deg, rgba(253, 224, 71, 0.42) 0%, rgba(244, 63, 94, 0.08) 85%, transparent 100%);
      opacity: 0;
      transition: opacity 0.35s ease;
    }

    .spotlight.center-onair.active {
      opacity: 1;
    }

    @keyframes swayLeft {
      0%, 100% { transform: rotate(-14deg); }
      50% { transform: rotate(10deg); }
    }

    @keyframes swayRight {
      0%, 100% { transform: rotate(14deg); }
      50% { transform: rotate(-10deg); }
    }

    /* Decorative Red Theater Curtains on Left & Right Edges */
    .stage-curtain {
      position: absolute;
      top: 0;
      bottom: 0;
      width: 34px;
      background: repeating-linear-gradient(
        90deg,
        #991b1b 0px,
        #dc2626 10px,
        #7f1d1d 18px
      );
      z-index: 15;
      pointer-events: none;
      box-shadow: 0 0 18px rgba(0, 0, 0, 0.6);
    }

    .stage-curtain.left { left: 0; border-right: 3px solid #fbbf24; }
    .stage-curtain.right { right: 0; border-left: 3px solid #fbbf24; }

    /* ==========================================================================
       3. TOP TV SHOW HUD BAR (ROUND TRACKER, STARS & SFX TOGGLE)
       ========================================================================== */
    #show-hud {
      display: none;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 10px;
      background: linear-gradient(90deg, #160933, #2e1463, #160933);
      border-bottom: 4px solid var(--gold-warm);
      padding: 12px 44px;
      color: #ffffff;
      z-index: 20;
      position: relative;
    }

    .hud-pill {
      background: rgba(255, 255, 255, 0.12);
      border: 2px solid rgba(253, 224, 71, 0.5);
      border-radius: 999px;
      padding: 6px 14px;
      font-weight: 800;
      font-size: 0.95rem;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .round-tracker {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .round-badge {
      padding: 5px 12px;
      border-radius: 999px;
      font-family: 'Fredoka', sans-serif;
      font-size: 0.85rem;
      font-weight: 600;
      background: rgba(255, 255, 255, 0.14);
      color: #cbd5e1;
      border: 2px solid transparent;
      transition: all 0.25s;
    }

    .round-badge.active {
      background: var(--gold-bright);
      color: #451a03;
      border-color: #ffffff;
      transform: scale(1.06);
      box-shadow: 0 0 12px rgba(253, 224, 71, 0.65);
    }

    .round-badge.done {
      background: var(--emerald-ok);
      color: #ffffff;
    }

    .sfx-toggle-btn {
      background: #38bdf8;
      color: #082f49;
      border: 2px solid #ffffff;
      border-radius: 12px;
      padding: 5px 12px;
      font-family: 'Fredoka', sans-serif;
      font-weight: 700;
      font-size: 0.85rem;
      cursor: pointer;
    }

    /* ==========================================================================
       4. SCREENS & TRANSITIONS
       ========================================================================== */
    .screen {
      display: none;
      flex: 1;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px 46px 68px; /* Bottom padding leaves room for audience silhouette */
      position: relative;
      z-index: 10;
      animation: popStageIn 0.4s cubic-bezier(0.22, 1, 0.36, 1);
    }

    .screen.active {
      display: flex;
    }

    @keyframes popStageIn {
      from { opacity: 0; transform: translateY(14px) scale(0.98); }
      to { opacity: 1; transform: translateY(0) scale(1); }
    }

    /* ==========================================================================
       5. 3D TV SHOW BUTTONS (LARGE & TOUCH-FRIENDLY)
       ========================================================================== */
    .btn-tv {
      font-family: 'Fredoka', sans-serif;
      font-size: 1.2rem;
      font-weight: 700;
      color: #451a03;
      background: linear-gradient(180deg, #fef08a 0%, #f59e0b 100%);
      border: 4px solid #78350f;
      border-radius: 20px;
      padding: 13px 28px;
      cursor: pointer;
      box-shadow: 0 6px 0 #78350f, 0 12px 24px rgba(0, 0, 0, 0.35);
      transition: transform 0.12s ease, filter 0.12s ease;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      text-transform: uppercase;
    }

    .btn-tv:hover:not(:disabled) {
      transform: translateY(-2px);
      filter: brightness(1.06);
    }

    .btn-tv:active:not(:disabled) {
      transform: translateY(4px);
      box-shadow: 0 2px 0 #78350f;
    }

    .btn-cyan {
      background: linear-gradient(180deg, #7dd3fc 0%, #0284c7 100%);
      color: #ffffff;
      border-color: #0c4a6e;
      box-shadow: 0 6px 0 #0c4a6e, 0 10px 20px rgba(0, 0, 0, 0.25);
    }

    .btn-cyan:active:not(:disabled) {
      box-shadow: 0 2px 0 #0c4a6e;
    }

    .btn-emerald {
      background: linear-gradient(180deg, #4ade80 0%, #16a34a 100%);
      color: #ffffff;
      border-color: #14532d;
      box-shadow: 0 6px 0 #14532d, 0 10px 20px rgba(0, 0, 0, 0.25);
    }

    .btn-emerald:active:not(:disabled) {
      box-shadow: 0 2px 0 #14532d;
    }

    .btn-emerald:disabled {
      background: #94a3b8;
      border-color: #475569;
      box-shadow: 0 4px 0 #475569;
      cursor: not-allowed;
      opacity: 0.75;
    }

    .btn-coral {
      background: linear-gradient(180deg, #fb7185 0%, #e11d48 100%);
      color: #ffffff;
      border-color: #881337;
      box-shadow: 0 6px 0 #881337, 0 10px 20px rgba(225, 29, 72, 0.35);
    }

    .btn-coral:active:not(:disabled) {
      box-shadow: 0 2px 0 #881337;
    }

    .btn-slate {
      background: linear-gradient(180deg, #e2e8f0 0%, #cbd5e1 100%);
      color: #1e293b;
      border-color: #475569;
      box-shadow: 0 5px 0 #475569;
      font-size: 0.95rem;
      padding: 9px 16px;
    }

    /* ==========================================================================
       6. WELCOME SCREEN & MIC PERMISSION INSTRUCTIONS
       ========================================================================== */
    .tv-logo-sign {
      background: linear-gradient(180deg, #4c1d95 0%, #2e1065 100%);
      border: 6px solid var(--gold-bright);
      border-radius: 30px;
      padding: 16px 34px;
      text-align: center;
      box-shadow:
        0 10px 0 #78350f,
        0 0 30px rgba(253, 224, 71, 0.5);
      margin-bottom: 16px;
      position: relative;
    }

    .on-air-pill {
      display: inline-block;
      background: #ef4444;
      color: #ffffff;
      font-family: 'Fredoka', sans-serif;
      font-size: 0.85rem;
      font-weight: 700;
      padding: 3px 14px;
      border-radius: 999px;
      border: 2px solid #ffffff;
      letter-spacing: 1.5px;
      margin-bottom: 6px;
      animation: blinkOnAir 1.4s infinite;
    }

    @keyframes blinkOnAir {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.55; }
    }

    .tv-logo-sign h1 {
      font-size: clamp(1.9rem, 4.5vw, 3.1rem);
      color: var(--gold-bright);
      text-shadow: 3px 3px 0 #78350f, 0 0 16px rgba(253, 224, 71, 0.6);
      line-height: 1.08;
    }

    .tv-logo-sub {
      color: #bae6fd;
      font-size: clamp(1rem, 2.2vw, 1.25rem);
      font-weight: 800;
      margin-top: 4px;
    }

    .welcome-card {
      background: var(--card-cream);
      border: 4px solid var(--gold-warm);
      border-radius: 26px;
      padding: 20px 26px;
      max-width: 740px;
      width: 100%;
      text-align: center;
      box-shadow: 0 12px 28px rgba(0, 0, 0, 0.35);
      margin-bottom: 18px;
    }

    .welcome-card p {
      font-size: 1.08rem;
      font-weight: 800;
      color: #1e1b4b;
      line-height: 1.55;
      margin-bottom: 14px;
    }

    .mic-permission-box {
      background: #eff6ff;
      border: 3px solid #38bdf8;
      color: #0c4a6e;
      border-radius: 18px;
      padding: 12px 16px;
      font-size: 0.96rem;
      font-weight: 800;
      line-height: 1.45;
      text-align: left;
      display: flex;
      align-items: flex-start;
      gap: 12px;
    }

    .mic-permission-icon {
      font-size: 1.8rem;
      line-height: 1;
      flex-shrink: 0;
    }

    .tv-text-input {
      width: 100%;
      max-width: 380px;
      padding: 12px 18px;
      font-family: 'Fredoka', sans-serif;
      font-size: 1.2rem;
      color: #1e1b4b;
      background: #fefce8;
      border: 3px solid #f59e0b;
      border-radius: 16px;
      text-align: center;
      outline: none;
      transition: border-color 0.2s, box-shadow 0.2s;
    }

    .tv-text-input:focus {
      border-color: #0284c7;
      box-shadow: 0 0 0 4px rgba(56, 189, 248, 0.3);
    }

    /* ==========================================================================
       7. STAGE CHALLENGE SCREEN (4 SPEAKING ROUNDS)
       ========================================================================== */
    #stage-screen {
      justify-content: flex-start;
      padding-top: 14px;
      gap: 12px;
    }

    .round-header-bar {
      width: 100%;
      max-width: 820px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 8px;
    }

    .round-title-tag {
      background: linear-gradient(90deg, #f59e0b, #fbbf24);
      color: #451a03;
      border: 3px solid #ffffff;
      border-radius: 999px;
      padding: 6px 20px;
      font-family: 'Fredoka', sans-serif;
      font-size: 1.15rem;
      font-weight: 700;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
    }

    .prompt-counter-tag {
      background: rgba(255, 255, 255, 0.16);
      color: #fde047;
      border: 2px solid #fde047;
      border-radius: 999px;
      padding: 5px 16px;
      font-weight: 800;
      font-size: 0.95rem;
    }

    /* Main Teleprompter & Interaction Card */
    .teleprompter-card {
      width: 100%;
      max-width: 820px;
      background: var(--card-cream);
      border: 5px solid var(--gold-warm);
      border-radius: 26px;
      padding: 18px 24px;
      box-shadow: 0 14px 30px rgba(0, 0, 0, 0.4);
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      gap: 12px;
    }

    .prompt-instruction {
      background: #e0f2fe;
      color: #0369a1;
      border: 2px solid #38bdf8;
      border-radius: 999px;
      padding: 4px 16px;
      font-size: 0.92rem;
      font-weight: 800;
    }

    /* Live Sentence Teleprompter Display */
    .sentence-teleprompter {
      width: 100%;
      background: #1e1b4b;
      color: #ffffff;
      border: 4px solid #38bdf8;
      border-radius: 20px;
      padding: 14px 20px;
      font-family: 'Fredoka', sans-serif;
      font-size: clamp(1.3rem, 3vw, 1.85rem);
      line-height: 1.4;
      box-shadow: inset 0 4px 12px rgba(0, 0, 0, 0.5);
    }

    .sentence-fill-word {
      color: #fde047;
      text-decoration: underline;
      text-decoration-style: wavy;
      text-underline-offset: 5px;
    }

    /* Interactive Answer Helper Controls */
    .interactive-answer-area {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }

    .idea-chips-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 8px;
    }

    .idea-chip {
      background: #fef3c7;
      color: #78350f;
      border: 2px solid #f59e0b;
      border-radius: 999px;
      padding: 7px 15px;
      font-family: 'Nunito', sans-serif;
      font-weight: 800;
      font-size: 0.94rem;
      cursor: pointer;
      transition: all 0.15s;
    }

    .idea-chip:hover, .idea-chip.selected {
      background: #f59e0b;
      color: #ffffff;
      transform: translateY(-1px);
    }

    /* Round 3 Hobby Cards Grid */
    .hobbies-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(125px, 1fr));
      gap: 10px;
      width: 100%;
    }

    .hobby-card {
      background: #f8fafc;
      border: 3px solid #cbd5e1;
      border-radius: 18px;
      padding: 10px 8px;
      cursor: pointer;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      transition: all 0.18s;
    }

    .hobby-card:hover {
      border-color: #38bdf8;
      transform: translateY(-2px);
    }

    .hobby-card.selected {
      background: #fef9c3;
      border-color: #f59e0b;
      box-shadow: 0 4px 12px rgba(245, 158, 11, 0.35);
      transform: scale(1.03);
    }

    .hobby-emoji {
      font-size: 2.2rem;
    }

    .hobby-label {
      font-family: 'Fredoka', sans-serif;
      font-size: 0.98rem;
      color: #1e1b4b;
    }

    /* Round 4 Editable Big Speech Box */
    .speech-textarea {
      width: 100%;
      min-height: 112px;
      padding: 12px 16px;
      font-family: 'Nunito', sans-serif;
      font-size: 1.06rem;
      font-weight: 800;
      color: #1e1b4b;
      background: #fefce8;
      border: 3px solid #f59e0b;
      border-radius: 16px;
      resize: vertical;
      line-height: 1.5;
    }

    .sentence-count-badge {
      font-size: 0.88rem;
      font-weight: 800;
      padding: 4px 14px;
      border-radius: 999px;
      background: #dcfce7;
      color: #15803d;
      border: 2px solid #22c55e;
    }

    .sentence-count-badge.warning {
      background: #fef3c7;
      color: #b45309;
      border-color: #f59e0b;
    }

    /* ==========================================================================
       8. STUDIO MICROPHONE, REAL-TIME EQUALIZER & AUDIO PLAYBACK STATION
       ========================================================================== */
    .studio-mic-station {
      width: 100%;
      background: linear-gradient(180deg, #f1f5f9 0%, #e2e8f0 100%);
      border: 3px solid #cbd5e1;
      border-radius: 22px;
      padding: 14px 18px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      transition: all 0.3s;
    }

    .studio-mic-station.on-air {
      background: linear-gradient(180deg, #fff1f2 0%, #ffe4e6 100%);
      border-color: #f43f5e;
      box-shadow: 0 0 22px rgba(244, 63, 94, 0.35);
    }

    .mic-visual-row {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 18px;
    }

    /* Real Audio-Reactive Equalizer Wave Bars */
    .eq-bars {
      display: flex;
      align-items: center;
      gap: 6px;
      height: 46px;
    }

    .eq-bar {
      width: 8px;
      height: 12px;
      background: #94a3b8;
      border-radius: 999px;
      transition: height 0.08s ease-out, background 0.2s;
    }

    .studio-mic-station.on-air .eq-bar {
      background: #f43f5e;
    }

    .studio-mic-station.on-air .eq-bar:nth-child(2) { background: #f59e0b; }
    .studio-mic-station.on-air .eq-bar:nth-child(3) { background: #10b981; }
    .studio-mic-station.on-air .eq-bar:nth-child(4) { background: #0284c7; }
    .studio-mic-station.on-air .eq-bar:nth-child(5) { background: #8b5cf6; }

    /* Cartoon Studio Microphone SVG */
    .cartoon-mic-icon {
      width: 64px;
      height: 76px;
      filter: drop-shadow(0 4px 6px rgba(0, 0, 0, 0.25));
      transition: transform 0.25s;
    }

    .studio-mic-station.on-air .cartoon-mic-icon {
      animation: micRock 0.65s ease-in-out infinite alternate;
    }

    @keyframes micRock {
      0% { transform: rotate(-6deg) scale(1.06); }
      100% { transform: rotate(6deg) scale(1.06); }
    }

    .stage-buttons-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 12px;
    }

    .on-air-status-text {
      font-weight: 800;
      font-size: 1rem;
      color: #334155;
      max-width: 650px;
    }

    .studio-mic-station.on-air .on-air-status-text {
      color: #be123c;
    }

    /* Playback Review Box (Appears after recording stops) */
    .playback-box {
      display: none;
      width: 100%;
      max-width: 640px;
      background: #ffffff;
      border: 3px solid #38bdf8;
      border-radius: 18px;
      padding: 12px 16px;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      animation: popStageIn 0.3s ease;
    }

    .playback-box.visible {
      display: flex;
    }

    .playback-controls-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 10px;
      width: 100%;
    }

    #pupil-audio-player {
      height: 40px;
      max-width: 280px;
      border-radius: 999px;
    }

    /* ==========================================================================
       9. SELF-ASSESSMENT SPEAKING CHECKLIST
       ========================================================================== */
    .checklist-panel {
      display: none;
      width: 100%;
      background: #fefce8;
      border: 3px solid #eab308;
      border-radius: 20px;
      padding: 14px 18px;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      animation: popStageIn 0.35s ease;
    }

    .checklist-panel.visible {
      display: flex;
    }

    .checklist-title {
      font-family: 'Fredoka', sans-serif;
      font-size: 1.15rem;
      color: #854d0e;
    }

    .checklist-items {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      width: 100%;
    }

    .check-item-label {
      background: #ffffff;
      border: 3px solid #cbd5e1;
      border-radius: 14px;
      padding: 10px 14px;
      display: flex;
      align-items: center;
      gap: 8px;
      font-weight: 800;
      font-size: 0.98rem;
      color: #1e293b;
      cursor: pointer;
      transition: all 0.15s;
      user-select: none;
    }

    .check-item-label:hover {
      border-color: #38bdf8;
    }

    .check-item-label.checked {
      background: #dcfce7;
      border-color: #16a34a;
      color: #14532d;
    }

    .check-item-label input[type="checkbox"] {
      width: 20px;
      height: 20px;
      accent-color: #16a34a;
      cursor: pointer;
    }

    /* ==========================================================================
       10. STAR SPEAKER CERTIFICATE (GRAND FINALE SCREEN)
       ========================================================================== */
    #confetti-canvas {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 30;
    }

    .certificate-frame {
      width: 100%;
      max-width: 780px;
      background: linear-gradient(180deg, #fffbeb 0%, #fef3c7 100%);
      border: 8px double #b45309;
      border-radius: 26px;
      padding: 22px 28px;
      text-align: center;
      box-shadow: 0 18px 40px rgba(0, 0, 0, 0.5);
      position: relative;
      margin-bottom: 16px;
    }

    .cert-badge {
      font-size: 2.6rem;
      margin-bottom: 4px;
    }

    .cert-heading {
      font-size: clamp(1.5rem, 3.8vw, 2.4rem);
      color: #78350f;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .cert-sub {
      font-weight: 800;
      color: #92400e;
      font-size: 1rem;
      margin: 4px 0 10px;
    }

    .cert-pupil-name {
      font-family: 'Fredoka', sans-serif;
      font-size: clamp(1.7rem, 4vw, 2.5rem);
      color: #1e1b4b;
      border-bottom: 4px solid #f59e0b;
      display: inline-block;
      padding: 2px 28px;
      margin-bottom: 10px;
    }

    .cert-stars-row {
      font-family: 'Fredoka', sans-serif;
      font-size: 1.3rem;
      color: #15803d;
      background: #dcfce7;
      border: 2px solid #22c55e;
      border-radius: 999px;
      padding: 5px 20px;
      display: inline-block;
      margin-bottom: 12px;
    }

    .cert-speech-summary {
      background: #ffffff;
      border: 2px dashed #d97706;
      border-radius: 16px;
      padding: 12px 16px;
      font-size: 0.98rem;
      font-weight: 700;
      color: #334155;
      line-height: 1.5;
      text-align: left;
    }

    .cert-actions-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 14px;
    }

    /* ==========================================================================
       11. CHEERING TV AUDIENCE SILHOUETTE FOOTER
       ========================================================================== */
    .audience-footer {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 54px;
      pointer-events: none;
      z-index: 12;
    }

    .audience-footer.cheering {
      animation: audienceCheer 0.45s ease-in-out 4;
    }

    @keyframes audienceCheer {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-9px); }
    }

    /* ==========================================================================
       12. RESPONSIVE & PRINT STYLES
       ========================================================================== */
    @media (max-width: 680px) {
      #tv-stage-container {
        border-radius: 20px;
        border-width: 4px;
      }
      .stage-curtain {
        width: 16px;
      }
      #show-hud {
        padding: 10px 22px;
      }
      .screen {
        padding: 14px 22px 62px;
      }
      .round-tracker {
        display: none;
      }
      .btn-tv {
        font-size: 1.05rem;
        padding: 11px 20px;
      }
    }

    @media print {
      body {
        background: #ffffff;
        padding: 0;
      }
      #tv-stage-container {
        border: none;
        box-shadow: none;
        background: #ffffff;
      }
      .spotlight, .stage-curtain, .audience-footer, .cert-actions-row, #confetti-canvas {
        display: none !important;
      }
      .certificate-frame {
        box-shadow: none;
        margin: 0 auto;
      }
    }
  </style>
</head>
<body>

  <div id="tv-stage-container">
    <!-- Animated TV Spotlights -->
    <div class="spotlight left"></div>
    <div class="spotlight right"></div>
    <div class="spotlight center-onair" id="center-spotlight"></div>

    <!-- Stage Curtains -->
    <div class="stage-curtain left"></div>
    <div class="stage-curtain right"></div>

    <!-- ======================================================================
         TOP TV SHOW HUD BAR
         ====================================================================== -->
    <header id="show-hud">
      <div class="hud-pill">
        <span>🎤</span>
        <span id="hud-contestant-name">Star Contestant</span>
      </div>

      <div class="round-tracker" id="hud-round-badges">
        <span class="round-badge active" data-round="0">R1: Intro</span>
        <span class="round-badge" data-round="1">R2: Favourites</span>
        <span class="round-badge" data-round="2">R3: Hobbies</span>
        <span class="round-badge" data-round="3">R4: Big Speech</span>
      </div>

      <div style="display: flex; align-items: center; gap: 8px;">
        <div class="hud-pill" style="background: rgba(253, 224, 71, 0.2);">
          <span>⭐</span>
          <span id="hud-stars">0</span> / <span id="hud-total-stars">10</span>
        </div>
        <button type="button" class="sfx-toggle-btn" id="btn-sfx">🔊 SFX</button>
      </div>
    </header>

    <!-- ======================================================================
         SCREEN 1: WELCOME SCREEN & MICROPHONE PERMISSION GUIDE
         ====================================================================== -->
    <section id="welcome-screen" class="screen active">
      <div class="tv-logo-sign">
        <div class="on-air-pill">● LIVE TV TALENT SHOW</div>
        <h1>🎤 MIC CHECK! 🎤</h1>
        <div class="tv-logo-sub">My Speaking Identity – Year 4 Star Speaker Challenge</div>
      </div>

      <div class="welcome-card">
        <p>
          Welcome to <strong>“MIC CHECK!”</strong> — the exciting children’s television show where YOU are the newest contestant! Complete <strong>4 Speaking Rounds</strong> on stage, record and listen to your own voice, and earn stars to become our next <strong>STAR SPEAKER</strong>!
        </p>

        <div class="mic-permission-box">
          <div class="mic-permission-icon">🎙️</div>
          <div>
            <strong>How Your Microphone Works:</strong><br />
            When your browser asks to use your microphone, click <strong>Allow</strong> so you can record and hear your own voice! All recordings stay safely on your device and are never uploaded anywhere.
          </div>
        </div>
      </div>

      <button type="button" class="btn-tv" id="btn-start-show">
        🎬 STEP ONTO THE STAGE!
      </button>
    </section>

    <!-- ======================================================================
         SCREEN 2: STAGE SPEAKING ROUND SCREEN
         ====================================================================== -->
    <section id="stage-screen" class="screen">
      <div class="round-header-bar">
        <div class="round-title-tag" id="round-title-display">Round 1: Introduce Yourself</div>
        <div class="prompt-counter-tag" id="prompt-counter-display">Challenge 1 of 4</div>
      </div>

      <div class="teleprompter-card">
        <div class="prompt-instruction" id="prompt-instruction-display">
          Complete the sentence below, then record yourself speaking it aloud!
        </div>

        <!-- Live Teleprompter Sentence -->
        <div class="sentence-teleprompter" id="teleprompter-display">
          “My name is <span class="sentence-fill-word">______</span>.”
        </div>

        <!-- Dynamic Answer Controls (Input / Chips / Hobby Cards / Round 4 Speech Editor) -->
        <div class="interactive-answer-area" id="answer-controls-container"></div>

        <!-- Cartoon Studio Microphone, Real Voice Recorder & Playback Station -->
        <div class="studio-mic-station" id="mic-station">
          <div class="mic-visual-row">
            <div class="eq-bars" id="eq-left">
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
            </div>

            <!-- Cartoon Retro TV Studio Microphone SVG -->
            <svg class="cartoon-mic-icon" viewBox="0 0 80 96" xmlns="http://www.w3.org/2000/svg">
              <rect x="22" y="6" width="36" height="48" rx="18" fill="#cbd5e1" stroke="#1e293b" stroke-width="3.5"/>
              <line x1="22" y1="22" x2="58" y2="22" stroke="#475569" stroke-width="2.5"/>
              <line x1="22" y1="30" x2="58" y2="30" stroke="#475569" stroke-width="2.5"/>
              <line x1="22" y1="38" x2="58" y2="38" stroke="#475569" stroke-width="2.5"/>
              <rect x="20" y="27" width="40" height="7" rx="3" fill="#f59e0b" stroke="#78350f" stroke-width="2"/>
              <path d="M14,34 Q14,64 40,64 Q66,64 66,34" fill="none" stroke="#f59e0b" stroke-width="5" stroke-linecap="round"/>
              <rect x="36" y="64" width="8" height="20" fill="#475569" stroke="#1e293b" stroke-width="2.5"/>
              <ellipse cx="40" cy="86" rx="22" ry="6" fill="#1e293b"/>
            </svg>

            <div class="eq-bars" id="eq-right">
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
            </div>
          </div>

          <div class="on-air-status-text" id="stage-status-text">
            Tap <strong>🔴 RECORD MY VOICE</strong> and speak your sentence clearly!
          </div>

          <div class="stage-buttons-row">
            <button type="button" class="btn-tv btn-coral" id="btn-record-voice">
              🔴 RECORD MY VOICE
            </button>

            <button type="button" class="btn-tv btn-slate" id="btn-practice-no-mic" style="display: none;">
              🗣️ Practice Without Mic
            </button>
          </div>

          <!-- Voice Playback & Re-Record Panel -->
          <div class="playback-box" id="playback-box">
            <div style="font-weight: 800; color: #0369a1; font-size: 0.95rem;">
              🎧 Listen back to check your speaking!
            </div>
            <div class="playback-controls-row">
              <button type="button" class="btn-tv btn-cyan" id="btn-play-recording" style="font-size: 1rem; padding: 10px 18px;">
                ▶️ PLAY MY RECORDING
              </button>
              <audio id="pupil-audio-player" controls></audio>
              <button type="button" class="btn-tv" id="btn-record-again" style="font-size: 1rem; padding: 10px 18px;">
                🔄 Record Again
              </button>
            </div>
          </div>
        </div>

        <!-- 3-Point Speaking Self-Assessment Checklist -->
        <div class="checklist-panel" id="speaking-checklist">
          <div class="checklist-title">📋 Star Speaker Self-Check — Tick all 3 to earn your Star!</div>
          <div class="checklist-items">
            <label class="check-item-label">
              <input type="checkbox" class="speaker-chk" id="chk-1" />
              <span>1. Did I speak clearly?</span>
            </label>
            <label class="check-item-label">
              <input type="checkbox" class="speaker-chk" id="chk-2" />
              <span>2. Did I use complete sentences?</span>
            </label>
            <label class="check-item-label">
              <input type="checkbox" class="speaker-chk" id="chk-3" />
              <span>3. Did I speak confidently?</span>
            </label>
          </div>
        </div>

        <!-- Next Challenge / Finish Round Button -->
        <button type="button" class="btn-tv btn-emerald" id="btn-next-challenge" disabled style="display: none;">
          ⭐ COLLECT STAR & CONTINUE ➡️
        </button>
      </div>
    </section>

    <!-- ======================================================================
         SCREEN 3: GRAND FINALE STAR SPEAKER CERTIFICATE
         ====================================================================== -->
    <section id="certificate-screen" class="screen">
      <canvas id="confetti-canvas"></canvas>

      <div class="certificate-frame">
        <div class="cert-badge">🏆🌟🎤🌟🏆</div>
        <h1 class="cert-heading">Star Speaker Certificate</h1>
        <div class="cert-sub">Presented by the “MIC CHECK!” Television Talent Show to</div>

        <div class="cert-pupil-name" id="cert-name-display">Star Speaker</div>
        <br />
        <div class="cert-stars-row" id="cert-stars-display">
          ⭐ 10 / 10 Stars Earned – Official Star Speaker!
        </div>

        <div class="cert-speech-summary" id="cert-speech-display">
          <!-- Populated with the pupil's complete Big Introduction -->
        </div>
      </div>

      <div class="cert-actions-row">
        <button type="button" class="btn-tv btn-cyan" id="btn-print-cert">
          🖨️ PRINT / SAVE CERTIFICATE
        </button>
        <button type="button" class="btn-tv" id="btn-play-again">
          🔄 PLAY AGAIN
        </button>
      </div>
    </section>

    <!-- Cheering TV Audience Silhouette Footer -->
    <svg class="audience-footer" id="audience-svg" viewBox="0 0 1000 60" preserveAspectRatio="none">
      <path d="M0,60 L0,40 Q25,22 50,40 Q75,20 100,40 Q130,24 160,40 Q190,18 220,40 Q255,25 290,40 Q325,20 360,40 Q395,22 430,40 Q465,18 500,40 Q535,24 570,40 Q605,20 640,40 Q675,22 710,40 Q745,18 780,40 Q815,24 850,40 Q885,20 920,40 Q960,22 1000,40 L1000,60 Z" fill="#0f0524"/>
      <circle cx="50" cy="24" r="11" fill="#0f0524"/>
      <circle cx="130" cy="22" r="12" fill="#0f0524"/>
      <circle cx="220" cy="21" r="11" fill="#0f0524"/>
      <circle cx="310" cy="24" r="12" fill="#0f0524"/>
      <circle cx="400" cy="20" r="11" fill="#0f0524"/>
      <circle cx="500" cy="22" r="13" fill="#0f0524"/>
      <circle cx="600" cy="20" r="11" fill="#0f0524"/>
      <circle cx="690" cy="24" r="12" fill="#0f0524"/>
      <circle cx="780" cy="21" r="11" fill="#0f0524"/>
      <circle cx="870" cy="23" r="12" fill="#0f0524"/>
      <circle cx="950" cy="22" r="11" fill="#0f0524"/>
    </svg>
  </div>

  <!-- ========================================================================
       JAVASCRIPT: GAME ROUNDS, MEDIARECORDER API, EQUALIZER & CERTIFICATE
       ======================================================================== -->
  <script>
    /**
     * ========================================================================
     * 1. FOUR SPEAKING ROUNDS CURRICULUM DATA (YEAR 4 ESL)
     * ========================================================================
     */
    const HOBBY_OPTIONS = [
      {
        id: "reading",
        label: "Reading",
        emoji: "📚",
        sentence: "My hobby is reading storybooks because it is fun and helps me learn new words."
      },
      {
        id: "swimming",
        label: "Swimming",
        emoji: "🏊",
        sentence: "My hobby is swimming because it is fun and keeps me healthy."
      },
      {
        id: "drawing",
        label: "Drawing",
        emoji: "🎨",
        sentence: "My hobby is drawing colourful pictures because I love art."
      },
      {
        id: "singing",
        label: "Singing",
        emoji: "🎶",
        sentence: "My hobby is singing English songs because music makes me happy."
      },
      {
        id: "football",
        label: "Playing Football",
        emoji: "⚽",
        sentence: "My hobby is playing football with my friends because it is exciting."
      }
    ];

    const ROUNDS = [
      {
        id: 1,
        title: "Round 1: Introduce Yourself",
        prompts: [
          {
            key: "name",
            type: "fill",
            instruction: "Type your name below, then record yourself saying the full sentence!",
            prefix: "My name is ",
            suffix: ".",
            placeholder: "your name",
            chips: []
          },
          {
            key: "age",
            type: "fixed",
            instruction: "Record yourself saying this sentence proudly to the studio audience!",
            fixedSentence: "I am ten years old."
          },
          {
            key: "town",
            type: "fill",
            instruction: "Type or tap where you live, then record the full sentence!",
            prefix: "I live in ",
            suffix: ".",
            placeholder: "your town or city",
            chips: ["Alor Setar", "Pokok Sena", "Kuala Lumpur", "Penang", "London"]
          },
          {
            key: "school",
            type: "fill",
            instruction: "Type or tap your school name, then record the full sentence!",
            prefix: "I am a pupil at ",
            suffix: ".",
            placeholder: "your school name",
            chips: ["SK Taman Indah", "SK Seri Mutiara", "SK Pokok Sena", "Year 4"]
          }
        ]
      },
      {
        id: 2,
        title: "Round 2: My Favourite Things",
        prompts: [
          {
            key: "colour",
            type: "fill",
            instruction: "Choose or type your favourite colour, then record your voice!",
            prefix: "My favourite colour is ",
            suffix: ".",
            placeholder: "colour",
            chips: ["blue", "red", "green", "yellow", "purple", "pink"]
          },
          {
            key: "food",
            type: "fill",
            instruction: "Choose or type your favourite food, then record your voice!",
            prefix: "My favourite food is ",
            suffix: ".",
            placeholder: "food",
            chips: ["nasi lemak", "fried chicken", "pizza", "noodles", "ice cream"]
          },
          {
            key: "subject",
            type: "fill",
            instruction: "Choose or type your favourite school subject, then record!",
            prefix: "My favourite subject is ",
            suffix: ".",
            placeholder: "subject",
            chips: ["English", "Mathematics", "Science", "Art", "Physical Education"]
          },
          {
            key: "enjoy",
            type: "fill",
            instruction: "Choose or type something you enjoy doing, then record!",
            prefix: "I enjoy ",
            suffix: ".",
            placeholder: "activity",
            chips: ["playing games", "helping my parents", "learning English", "riding my bicycle"]
          }
        ]
      },
      {
        id: 3,
        title: "Round 3: My Hobbies",
        prompts: [
          {
            key: "hobby",
            type: "hobby",
            instruction: "Tap a hobby card below and edit or speak a complete sentence explaining it!"
          }
        ]
      },
      {
        id: 4,
        title: "Round 4: The Big Introduction",
        prompts: [
          {
            key: "bigIntro",
            type: "finale",
            instruction: "GRAND FINALE! Record your complete self-introduction (at least 4 sentences) to become the Star Speaker!"
          }
        ]
      }
    ];

    /**
     * ========================================================================
     * 2. GAME STATE & AUDIO STREAM REFERENCES
     * ========================================================================
     */
    const totalStarsAvailable = ROUNDS.reduce((total, r) => total + r.prompts.length, 0);

    const gameState = {
      roundIdx: 0,
      promptIdx: 0,
      stars: 0,
      isRecording: false,
      recordSeconds: 0,
      recordTimerId: null,
      mediaRecorder: null,
      audioChunks: [],
      currentAudioUrl: null,
      micStream: null,
      analyserNode: null,
      eqAnimFrameId: null,
      soundEnabled: true,
      answers: {
        name: "",
        age: "I am ten years old.",
        town: "",
        school: "",
        colour: "",
        food: "",
        subject: "",
        enjoy: "",
        selectedHobbyId: "reading",
        hobbySentence: HOBBY_OPTIONS[0].sentence,
        bigIntro: ""
      }
    };

    /**
     * ========================================================================
     * 3. WEB AUDIO API SOUND EFFECTS (NO EXTERNAL SOUND URLS NEEDED)
     * ========================================================================
     */
    let audioCtx = null;

    function getAudioContext() {
      if (!audioCtx) {
        const Ctx = window.AudioContext || window.webkitAudioContext;
        if (Ctx) audioCtx = new Ctx();
      }
      if (audioCtx && audioCtx.state === "suspended") {
        audioCtx.resume();
      }
      return audioCtx;
    }

    function playTone(type) {
      if (!gameState.soundEnabled) return;
      try {
        const ctx = getAudioContext();
        if (!ctx) return;

        const now = ctx.currentTime;
        if (type === "click") {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = "triangle";
          osc.frequency.setValueAtTime(540, now);
          osc.frequency.exponentialRampToValueAtTime(760, now + 0.08);
          gain.gain.setValueAtTime(0.14, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + 0.09);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now);
          osc.stop(now + 0.09);
        } else if (type === "recStart") {
          const osc = ctx.createOscillator();
          const gain = ctx.createGain();
          osc.type = "sine";
          osc.frequency.setValueAtTime(880, now);
          gain.gain.setValueAtTime(0.14, now);
          gain.gain.exponentialRampToValueAtTime(0.001, now + 0.16);
          osc.connect(gain);
          gain.connect(ctx.destination);
          osc.start(now);
          osc.stop(now + 0.16);
        } else if (type === "star") {
          const chord = [523.25, 659.25, 783.99, 1046.5];
          chord.forEach((freq, idx) => {
            const osc = ctx.createOscillator();
            const gain = ctx.createGain();
            osc.type = "triangle";
            osc.frequency.setValueAtTime(freq, now + idx * 0.08);
            gain.gain.setValueAtTime(0.16, now + idx * 0.08);
            gain.gain.exponentialRampToValueAtTime(0.001, now + idx * 0.08 + 0.35);
            osc.connect(gain);
            gain.connect(ctx.destination);
            osc.start(now + idx * 0.08);
            osc.stop(now + idx * 0.08 + 0.35);
          });
        }
      } catch (e) {
        // Ignore audio context errors gracefully
      }
    }

    /**
     * ========================================================================
     * 4. BROWSER MEDIARECORDER API (LOCAL DEVICE VOICE RECORDING & PLAYBACK)
     * ========================================================================
     */
    function getSupportedAudioMimeType() {
      if (typeof MediaRecorder === "undefined") return "";
      const candidates = [
        "audio/webm;codecs=opus",
        "audio/webm",
        "audio/mp4",
        "audio/ogg;codecs=opus"
      ];
      for (const mime of candidates) {
        if (MediaRecorder.isTypeSupported && MediaRecorder.isTypeSupported(mime)) {
          return mime;
        }
      }
      return "";
    }

    function revokeCurrentRecordingUrl() {
      const player = document.getElementById("pupil-audio-player");
      player.pause();
      player.removeAttribute("src");
      player.load();
      if (gameState.currentAudioUrl) {
        URL.revokeObjectURL(gameState.currentAudioUrl);
        gameState.currentAudioUrl = null;
      }
    }

    async function startVoiceRecording() {
      if (!navigator.mediaDevices || !navigator.mediaDevices.getUserMedia || typeof MediaRecorder === "undefined") {
        document.getElementById("stage-status-text").innerHTML =
          "⚠️ Voice recording is not supported in this browser. Use <strong>Chrome, Edge, or Safari</strong>, or tap <strong>Practice Without Mic</strong> below!";
        document.getElementById("btn-practice-no-mic").style.display = "inline-flex";
        return;
      }

      try {
        // Request microphone permission if stream isn't already active
        if (!gameState.micStream || !gameState.micStream.active) {
          gameState.micStream = await navigator.mediaDevices.getUserMedia({
            audio: {
              echoCancellation: true,
              noiseSuppression: true,
              autoGainControl: true
            }
          });
        }

        // Connect Web Audio API AnalyserNode for real-time equalizer bar animation
        const ctx = getAudioContext();
        if (ctx && !gameState.analyserNode) {
          const source = ctx.createMediaStreamSource(gameState.micStream);
          gameState.analyserNode = ctx.createAnalyser();
          gameState.analyserNode.fftSize = 64;
          source.connect(gameState.analyserNode);
        }

        revokeCurrentRecordingUrl();
        gameState.audioChunks = [];

        const mimeType = getSupportedAudioMimeType();
        const options = mimeType ? { mimeType } : undefined;
        gameState.mediaRecorder = new MediaRecorder(gameState.micStream, options);

        gameState.mediaRecorder.ondataavailable = (event) => {
          if (event.data && event.data.size > 0) {
            gameState.audioChunks.push(event.data);
          }
        };

        gameState.mediaRecorder.onstop = () => {
          const blobType = mimeType || "audio/webm";
          const audioBlob = new Blob(gameState.audioChunks, { type: blobType });
          gameState.currentAudioUrl = URL.createObjectURL(audioBlob);

          const player = document.getElementById("pupil-audio-player");
          player.src = gameState.currentAudioUrl;

          finishRecordingUI();
        };

        playTone("recStart");
        gameState.mediaRecorder.start();
        gameState.isRecording = true;
        gameState.recordSeconds = 0;

        // Update UI to ON AIR Recording state
        const station = document.getElementById("mic-station");
        station.classList.add("on-air");
        document.getElementById("center-spotlight").classList.add("active");
        document.getElementById("playback-box").classList.remove("visible");
        document.getElementById("btn-practice-no-mic").style.display = "none";

        const recBtn = document.getElementById("btn-record-voice");
        recBtn.innerHTML = "⏹️ STOP RECORDING";
        recBtn.classList.remove("btn-coral");
        recBtn.classList.add("btn-emerald");

        document.getElementById("stage-status-text").innerHTML =
          "🔴 <strong>RECORDING (0s)...</strong> Speak clearly into your microphone, then tap <strong>STOP RECORDING</strong>!";

        clearInterval(gameState.recordTimerId);
        gameState.recordTimerId = setInterval(() => {
          gameState.recordSeconds += 1;
          document.getElementById("stage-status-text").innerHTML =
            `🔴 <strong>RECORDING (${gameState.recordSeconds}s)...</strong> Speak clearly, then tap <strong>STOP RECORDING</strong>!`;
        }, 1000);

        animateLiveEqualizer();
      } catch (err) {
        document.getElementById("stage-status-text").innerHTML =
          "🚫 <strong>Microphone Permission Needed!</strong> Click <strong>Allow</strong> in your browser address bar to record your voice, or use <strong>Practice Without Mic</strong> below.";
        document.getElementById("btn-practice-no-mic").style.display = "inline-flex";
      }
    }

    function stopVoiceRecording() {
      clearInterval(gameState.recordTimerId);
      cancelAnimationFrame(gameState.eqAnimFrameId);
      resetEqualizerBars();

      if (gameState.mediaRecorder && gameState.mediaRecorder.state !== "inactive") {
        gameState.mediaRecorder.stop();
      }
      gameState.isRecording = false;
    }

    function finishRecordingUI() {
      const station = document.getElementById("mic-station");
      station.classList.remove("on-air");
      document.getElementById("center-spotlight").classList.remove("active");

      const recBtn = document.getElementById("btn-record-voice");
      recBtn.innerHTML = "🔴 RECORD MY VOICE";
      recBtn.classList.remove("btn-emerald");
      recBtn.classList.add("btn-coral");

      // Trigger cheering audience animation
      const audience = document.getElementById("audience-svg");
      audience.classList.remove("cheering");
      void audience.offsetWidth;
      audience.classList.add("cheering");

      document.getElementById("stage-status-text").innerHTML =
        "🎉 <strong>Recording saved on your device!</strong> Listen to your voice below, then tick your checklist!";
      document.getElementById("playback-box").classList.add("visible");
      document.getElementById("speaking-checklist").classList.add("visible");

      const nextBtn = document.getElementById("btn-next-challenge");
      nextBtn.style.display = "inline-flex";
      validateChecklist();
    }

    function handlePracticeWithoutMic() {
      playTone("click");
      const audience = document.getElementById("audience-svg");
      audience.classList.remove("cheering");
      void audience.offsetWidth;
      audience.classList.add("cheering");

      document.getElementById("stage-status-text").innerHTML =
        "👏 <strong>Great speaking practice!</strong> Tick all 3 items in your Star Speaker checklist below!";
      document.getElementById("speaking-checklist").classList.add("visible");

      const nextBtn = document.getElementById("btn-next-challenge");
      nextBtn.style.display = "inline-flex";
      validateChecklist();
    }

    function animateLiveEqualizer() {
      if (!gameState.analyserNode || !gameState.isRecording) return;
      const dataArray = new Uint8Array(gameState.analyserNode.frequencyBinCount);
      const bars = document.querySelectorAll(".eq-bar");

      function step() {
        if (!gameState.isRecording) return;
        gameState.analyserNode.getByteFrequencyData(dataArray);

        bars.forEach((bar, i) => {
          const val = dataArray[(i * 2) % dataArray.length] || 0;
          const heightPx = Math.max(10, Math.min(44, Math.round((val / 255) * 44) + 8));
          bar.style.height = `${heightPx}px`;
        });

        gameState.eqAnimFrameId = requestAnimationFrame(step);
      }
      step();
    }

    function resetEqualizerBars() {
      document.querySelectorAll(".eq-bar").forEach(bar => {
        bar.style.height = "12px";
      });
    }

    /**
     * ========================================================================
     * 5. SCREEN NAVIGATION & HUD UPDATES
     * ========================================================================
     */
    function switchScreen(id) {
      document.querySelectorAll(".screen").forEach(s => s.classList.remove("active"));
      document.getElementById(id).classList.add("active");

      const hud = document.getElementById("show-hud");
      hud.style.display = id === "stage-screen" ? "flex" : "none";
    }

    function updateShowHUD() {
      const displayName = gameState.answers.name.trim() || "Star Contestant";
      document.getElementById("hud-contestant-name").textContent = displayName;
      document.getElementById("hud-stars").textContent = gameState.stars;
      document.getElementById("hud-total-stars").textContent = totalStarsAvailable;

      document.querySelectorAll(".round-badge").forEach((badge, idx) => {
        badge.classList.remove("active", "done");
        if (idx < gameState.roundIdx) {
          badge.classList.add("done");
        } else if (idx === gameState.roundIdx) {
          badge.classList.add("active");
        }
      });
    }

    /**
     * ========================================================================
     * 6. RENDERING CURRENT PROMPT & INTERACTIVE CONTROLS
     * ========================================================================
     */
    function escapeHTML(str) {
      return str
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;");
    }

    function countSentences(text) {
      const matches = text
        .trim()
        .split(/[.!?]+/)
        .map(s => s.trim())
        .filter(s => s.length > 2);
      return matches.length;
    }

    function updateTeleprompterDisplay() {
      const round = ROUNDS[gameState.roundIdx];
      const prompt = round.prompts[gameState.promptIdx];
      const el = document.getElementById("teleprompter-display");

      if (prompt.type === "fixed") {
        el.innerHTML = `“${prompt.fixedSentence}”`;
      } else if (prompt.type === "fill") {
        const val = (gameState.answers[prompt.key] || "").trim() || "______";
        el.innerHTML = `“${prompt.prefix}<span class="sentence-fill-word">${escapeHTML(val)}</span>${prompt.suffix}”`;
      } else if (prompt.type === "hobby") {
        const text = (gameState.answers.hobbySentence || "").trim() || "Choose a hobby card below!";
        el.innerHTML = `“<span class="sentence-fill-word">${escapeHTML(text)}</span>”`;
      } else if (prompt.type === "finale") {
        const speech = (gameState.answers.bigIntro || "").trim();
        el.innerHTML = `<div style="font-size: clamp(1.02rem, 2.1vw, 1.3rem); text-align: left;">“${escapeHTML(speech)}”</div>`;
      }
    }

    function buildDefaultBigIntro() {
      const name = gameState.answers.name.trim() || "a Year 4 pupil";
      const town = gameState.answers.town.trim() || "Malaysia";
      const school = gameState.answers.school.trim() || "my primary school";
      const colour = gameState.answers.colour.trim() || "blue";
      const food = gameState.answers.food.trim() || "nasi lemak";
      const subject = gameState.answers.subject.trim() || "English";
      const hobby = gameState.answers.hobbySentence.trim() || "My hobby is reading storybooks because it is fun.";

      return (
        `Hello everyone! My name is ${name}. ` +
        `I am ten years old and I live in ${town}. ` +
        `I am a pupil at ${school}. ` +
        `My favourite colour is ${colour}, my favourite food is ${food}, and my favourite subject is ${subject}. ` +
        `${hobby} Thank you!`
      );
    }

    function loadPrompt() {
      if (gameState.isRecording) stopVoiceRecording();
      revokeCurrentRecordingUrl();

      const round = ROUNDS[gameState.roundIdx];
      const prompt = round.prompts[gameState.promptIdx];

      updateShowHUD();

      document.getElementById("round-title-display").textContent = round.title;
      document.getElementById("prompt-counter-display").textContent =
        `Challenge ${gameState.promptIdx + 1} of ${round.prompts.length}`;
      document.getElementById("prompt-instruction-display").textContent = prompt.instruction;

      // Reset Recorder, Playback, Checklist & Next Button
      const station = document.getElementById("mic-station");
      station.classList.remove("on-air");
      document.getElementById("center-spotlight").classList.remove("active");

      const recBtn = document.getElementById("btn-record-voice");
      recBtn.innerHTML = "🔴 RECORD MY VOICE";
      recBtn.classList.remove("btn-emerald");
      recBtn.classList.add("btn-coral");

      document.getElementById("playback-box").classList.remove("visible");
      document.getElementById("speaking-checklist").classList.remove("visible");
      document.getElementById("btn-practice-no-mic").style.display = "none";

      document.querySelectorAll(".speaker-chk").forEach(chk => {
        chk.checked = false;
        chk.parentElement.classList.remove("checked");
      });

      const nextBtn = document.getElementById("btn-next-challenge");
      nextBtn.style.display = "none";
      nextBtn.disabled = true;

      document.getElementById("stage-status-text").innerHTML =
        "Tap <strong>🔴 RECORD MY VOICE</strong> and speak your sentence clearly!";

      // Build interactive controls for the current prompt type
      const controlsBox = document.getElementById("answer-controls-container");
      controlsBox.innerHTML = "";

      if (prompt.type === "fill") {
        const input = document.createElement("input");
        input.type = "text";
        input.className = "tv-text-input";
        input.placeholder = `Type ${prompt.placeholder} here...`;
        input.value = gameState.answers[prompt.key] || "";
        input.maxLength = 40;

        input.addEventListener("input", (e) => {
          gameState.answers[prompt.key] = e.target.value;
          if (prompt.key === "name") updateShowHUD();
          updateTeleprompterDisplay();
        });

        controlsBox.appendChild(input);

        if (prompt.chips && prompt.chips.length > 0) {
          const chipsRow = document.createElement("div");
          chipsRow.className = "idea-chips-row";
          prompt.chips.forEach(chipText => {
            const chip = document.createElement("button");
            chip.type = "button";
            chip.className = "idea-chip";
            chip.textContent = chipText;
            chip.addEventListener("click", () => {
              playTone("click");
              gameState.answers[prompt.key] = chipText;
              input.value = chipText;
              updateTeleprompterDisplay();
            });
            chipsRow.appendChild(chip);
          });
          controlsBox.appendChild(chipsRow);
        }
      } else if (prompt.type === "hobby") {
        const grid = document.createElement("div");
        grid.className = "hobbies-grid";

        HOBBY_OPTIONS.forEach(hobby => {
          const card = document.createElement("div");
          card.className = "hobby-card" + (gameState.answers.selectedHobbyId === hobby.id ? " selected" : "");
          card.innerHTML = `
            <div class="hobby-emoji">${hobby.emoji}</div>
            <div class="hobby-label">${hobby.label}</div>
          `;
          card.addEventListener("click", () => {
            playTone("click");
            gameState.answers.selectedHobbyId = hobby.id;
            gameState.answers.hobbySentence = hobby.sentence;
            hobbyInput.value = hobby.sentence;
            document.querySelectorAll(".hobby-card").forEach(c => c.classList.remove("selected"));
            card.classList.add("selected");
            updateTeleprompterDisplay();
          });
          grid.appendChild(card);
        });

        controlsBox.appendChild(grid);

        const hobbyInput = document.createElement("input");
        hobbyInput.type = "text";
        hobbyInput.className = "tv-text-input";
        hobbyInput.style.maxWidth = "680px";
        hobbyInput.style.fontSize = "1.02rem";
        hobbyInput.value = gameState.answers.hobbySentence;
        hobbyInput.placeholder = "Write or edit your hobby explanation sentence...";
        hobbyInput.addEventListener("input", (e) => {
          gameState.answers.hobbySentence = e.target.value;
          updateTeleprompterDisplay();
        });
        controlsBox.appendChild(hobbyInput);
      } else if (prompt.type === "finale") {
        if (!gameState.answers.bigIntro) {
          gameState.answers.bigIntro = buildDefaultBigIntro();
        }

        const countBadge = document.createElement("div");
        countBadge.className = "sentence-count-badge";

        const updateCountBadge = (txt) => {
          const count = countSentences(txt);
          if (count >= 4) {
            countBadge.className = "sentence-count-badge";
            countBadge.textContent = `✅ ${count} sentences ready (Goal: at least 4 sentences)`;
          } else {
            countBadge.className = "sentence-count-badge warning";
            countBadge.textContent = `✍️ ${count} of 4 sentences written — add ${4 - count} more!`;
          }
        };

        const area = document.createElement("textarea");
        area.className = "speech-textarea";
        area.value = gameState.answers.bigIntro;
        area.placeholder = "Write at least 4 sentences to introduce yourself...";
        area.addEventListener("input", (e) => {
          gameState.answers.bigIntro = e.target.value;
          updateCountBadge(e.target.value);
          updateTeleprompterDisplay();
        });

        updateCountBadge(area.value);
        controlsBox.appendChild(countBadge);
        controlsBox.appendChild(area);
      }

      updateTeleprompterDisplay();
    }

    function validateChecklist() {
      const checks = Array.from(document.querySelectorAll(".speaker-chk"));
      const allChecked = checks.every(c => c.checked);
      const nextBtn = document.getElementById("btn-next-challenge");

      nextBtn.disabled = !allChecked;

      const isFinalPrompt =
        gameState.roundIdx === ROUNDS.length - 1 &&
        gameState.promptIdx === ROUNDS[gameState.roundIdx].prompts.length - 1;

      if (isFinalPrompt) {
        nextBtn.innerHTML = "🏆 CLAIM STAR SPEAKER CERTIFICATE! ➡️";
      } else {
        nextBtn.innerHTML = "⭐ COLLECT STAR & CONTINUE ➡️";
      }
    }

    /**
     * ========================================================================
     * 7. PROGRESSION & GRAND FINALE STAR SPEAKER CERTIFICATE
     * ========================================================================
     */
    function handleNextChallenge() {
      playTone("star");
      gameState.stars += 1;
      updateShowHUD();

      const round = ROUNDS[gameState.roundIdx];
      if (gameState.promptIdx < round.prompts.length - 1) {
        gameState.promptIdx += 1;
        loadPrompt();
      } else if (gameState.roundIdx < ROUNDS.length - 1) {
        gameState.roundIdx += 1;
        gameState.promptIdx = 0;
        loadPrompt();
      } else {
        showCertificateScreen();
      }
    }

    function showCertificateScreen() {
      playTone("star");
      const pupilName = gameState.answers.name.trim() || "Star Speaker";

      document.getElementById("cert-name-display").textContent = pupilName;
      document.getElementById("cert-stars-display").textContent =
        `⭐ ${gameState.stars} / ${totalStarsAvailable} Stars Earned – Official Star Speaker!`;
      document.getElementById("cert-speech-display").innerHTML =
        `<strong>🎤 My Star Speaker Introduction:</strong><br/>“${escapeHTML(gameState.answers.bigIntro || buildDefaultBigIntro())}”`;

      switchScreen("certificate-screen");
      launchVictoryConfetti();
    }

    function launchVictoryConfetti() {
      const canvas = document.getElementById("confetti-canvas");
      const ctx = canvas.getContext("2d");
      canvas.width = canvas.parentElement.clientWidth;
      canvas.height = canvas.parentElement.clientHeight;

      const colors = ["#fde047", "#38bdf8", "#f43f5e", "#4ade80", "#c084fc", "#fb923c"];
      const particles = Array.from({ length: 95 }, () => ({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height - canvas.height,
        w: Math.random() * 10 + 6,
        h: Math.random() * 6 + 4,
        color: colors[Math.floor(Math.random() * colors.length)],
        vy: Math.random() * 3 + 2,
        vx: Math.random() * 2 - 1,
        rot: Math.random() * 360
      }));

      let frame = 0;
      function draw() {
        if (!document.getElementById("certificate-screen").classList.contains("active")) return;
        ctx.clearRect(0, 0, canvas.width, canvas.height);

        particles.forEach(p => {
          p.y += p.vy;
          p.x += p.vx;
          p.rot += 4;
          if (p.y > canvas.height) p.y = -12;

          ctx.save();
          ctx.translate(p.x, p.y);
          ctx.rotate((p.rot * Math.PI) / 180);
          ctx.fillStyle = p.color;
          ctx.fillRect(-p.w / 2, -p.h / 2, p.w, p.h);
          ctx.restore();
        });

        frame++;
        if (frame < 460) requestAnimationFrame(draw);
      }
      draw();
    }

    function resetGame() {
      playTone("click");
      if (gameState.isRecording) stopVoiceRecording();
      revokeCurrentRecordingUrl();

      gameState.roundIdx = 0;
      gameState.promptIdx = 0;
      gameState.stars = 0;
      gameState.answers = {
        name: "",
        age: "I am ten years old.",
        town: "",
        school: "",
        colour: "",
        food: "",
        subject: "",
        enjoy: "",
        selectedHobbyId: "reading",
        hobbySentence: HOBBY_OPTIONS[0].sentence,
        bigIntro: ""
      };
      switchScreen("welcome-screen");
    }

    /**
     * ========================================================================
     * 8. EVENT LISTENERS
     * ========================================================================
     */
    document.getElementById("btn-start-show").addEventListener("click", () => {
      playTone("star");
      switchScreen("stage-screen");
      loadPrompt();
    });

    document.getElementById("btn-record-voice").addEventListener("click", () => {
      if (!gameState.isRecording) {
        startVoiceRecording();
      } else {
        stopVoiceRecording();
      }
    });

    document.getElementById("btn-play-recording").addEventListener("click", () => {
      const player = document.getElementById("pupil-audio-player");
      if (player.src) {
        player.currentTime = 0;
        player.play();
      }
    });

    document.getElementById("btn-record-again").addEventListener("click", () => {
      document.getElementById("speaking-checklist").classList.remove("visible");
      document.getElementById("btn-next-challenge").style.display = "none";
      document.querySelectorAll(".speaker-chk").forEach(chk => {
        chk.checked = false;
        chk.parentElement.classList.remove("checked");
      });
      startVoiceRecording();
    });

    document.getElementById("btn-practice-no-mic").addEventListener("click", () => {
      handlePracticeWithoutMic();
    });

    document.querySelectorAll(".speaker-chk").forEach(chk => {
      chk.addEventListener("change", (e) => {
        playTone("click");
        e.target.parentElement.classList.toggle("checked", e.target.checked);
        validateChecklist();
      });
    });

    document.getElementById("btn-next-challenge").addEventListener("click", () => {
      handleNextChallenge();
    });

    document.getElementById("btn-print-cert").addEventListener("click", () => {
      window.print();
    });

    document.getElementById("btn-play-again").addEventListener("click", () => {
      resetGame();
    });

    document.getElementById("btn-sfx").addEventListener("click", (e) => {
      gameState.soundEnabled = !gameState.soundEnabled;
      e.target.textContent = gameState.soundEnabled ? "🔊 SFX" : "🔇 Muted";
    });
  </script>
</body>
</html>
