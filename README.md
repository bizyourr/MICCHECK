<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>MIC CHECK! – My Speaking Identity</title>
  <!-- Load Google Fonts for friendly, rounded TV talent-show typography -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@500;600;700&family=Nunito:wght@600;700;800;900&display=swap" rel="stylesheet" />

  <style>
    /* ==========================================================================
       1. AESTHETIC SOFT PASTEL BLUE & BUTTER-YELLOW DESIGN TOKENS
       ========================================================================== */
    :root {
      --blue-ice: #EBF6FF;
      --blue-sky: #BAE0FF;
      --blue-bright: #7CC4FA;
      --blue-deep: #2B6CB0;
      --blue-ink: #1E3A5F;

      --yellow-cream: #FFFBE6;
      --yellow-butter: #FFF1A8;
      --yellow-sun: #FFE066;
      --yellow-amber: #D97706;
      --yellow-bronze: #92400E;

      --coral-rec: #F43F5E;
      --coral-dark: #BE123C;
      --mint-ok: #22C55E;
      --mint-dark: #15803D;

      --glass-white: rgba(255, 255, 255, 0.86);
      --glass-border: rgba(255, 255, 255, 0.95);
      --shadow-soft: 0 18px 45px rgba(43, 108, 176, 0.16);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
    }

    body {
      font-family: 'Nunito', sans-serif;
      background: linear-gradient(135deg, var(--blue-ice) 0%, var(--yellow-cream) 50%, var(--blue-sky) 100%);
      color: var(--blue-ink);
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
       2. MAIN TV STUDIO STAGE CONTAINER, CLOUDS, SPOTLIGHTS & SPARKLES
       ========================================================================== */
    #tv-stage-container {
      width: 100%;
      max-width: 980px;
      min-height: 690px;
      background: linear-gradient(180deg, #D8EEFF 0%, var(--blue-ice) 45%, var(--yellow-cream) 100%);
      border-radius: 32px;
      border: 6px solid var(--yellow-sun);
      box-shadow:
        0 22px 55px rgba(43, 108, 176, 0.24),
        0 0 0 4px var(--blue-bright),
        inset 0 0 30px rgba(255, 255, 255, 0.7);
      position: relative;
      overflow: hidden;
      display: flex;
      flex-direction: column;
    }

    /* Soft Pastel Studio Spotlight Beams */
    .studio-beam {
      position: absolute;
      top: -30px;
      width: 340px;
      height: 540px;
      background: linear-gradient(180deg, rgba(255, 224, 102, 0.48) 0%, rgba(255, 251, 230, 0) 90%);
      clip-path: polygon(42% 0%, 58% 0%, 100% 100%, 0% 100%);
      pointer-events: none;
      z-index: 1;
      transform-origin: top center;
    }

    .studio-beam.left {
      left: 6%;
      animation: beamSwayLeft 6s ease-in-out infinite;
    }

    .studio-beam.right {
      right: 6%;
      background: linear-gradient(180deg, rgba(124, 196, 250, 0.42) 0%, rgba(235, 246, 255, 0) 90%);
      animation: beamSwayRight 6.5s ease-in-out infinite;
    }

    .studio-beam.center-onair {
      left: 50%;
      width: 500px;
      transform: translateX(-50%);
      background: linear-gradient(180deg, rgba(255, 224, 102, 0.72) 0%, rgba(244, 63, 94, 0.1) 85%, transparent 100%);
      opacity: 0;
      transition: opacity 0.35s ease;
    }

    .studio-beam.center-onair.active {
      opacity: 1;
    }

    @keyframes beamSwayLeft {
      0%, 100% { transform: rotate(-13deg); }
      50% { transform: rotate(9deg); }
    }

    @keyframes beamSwayRight {
      0%, 100% { transform: rotate(13deg); }
      50% { transform: rotate(-9deg); }
    }

    /* Floating Pastel Studio Clouds */
    .pastel-cloud {
      position: absolute;
      background: rgba(255, 255, 255, 0.78);
      border-radius: 999px;
      pointer-events: none;
      z-index: 2;
      box-shadow: 0 8px 20px rgba(124, 196, 250, 0.22);
    }

    .pastel-cloud::before,
    .pastel-cloud::after {
      content: "";
      position: absolute;
      background: rgba(255, 255, 255, 0.85);
      border-radius: 50%;
    }

    .cloud-1 {
      width: 120px;
      height: 38px;
      top: 68px;
      left: 5%;
      animation: driftCloud 14s ease-in-out infinite;
    }
    .cloud-1::before { width: 52px; height: 52px; top: -24px; left: 18px; }
    .cloud-1::after { width: 40px; height: 40px; top: -16px; left: 58px; }

    .cloud-2 {
      width: 135px;
      height: 42px;
      top: 82px;
      right: 6%;
      animation: driftCloud 16s ease-in-out infinite reverse;
    }
    .cloud-2::before { width: 56px; height: 56px; top: -26px; left: 22px; }
    .cloud-2::after { width: 44px; height: 44px; top: -18px; left: 66px; }

    @keyframes driftCloud {
      0%, 100% { transform: translateX(0px); }
      50% { transform: translateX(18px); }
    }

    /* Decorative Floating Butter-Yellow Stars */
    .sparkle-star {
      position: absolute;
      color: var(--yellow-amber);
      font-size: 1.35rem;
      pointer-events: none;
      z-index: 3;
      animation: twinkleStar 2.8s ease-in-out infinite;
    }

    @keyframes twinkleStar {
      0%, 100% { transform: scale(0.9) rotate(0deg); opacity: 0.65; }
      50% { transform: scale(1.2) rotate(12deg); opacity: 1; }
    }

    /* ==========================================================================
       3. TOP TV SHOW HUD BAR (PROGRESS, STARS, FULL-TAB LAUNCHER & SFX)
       ========================================================================== */
    #show-hud {
      display: none;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 8px;
      background: rgba(255, 255, 255, 0.88);
      backdrop-filter: blur(10px);
      border-bottom: 4px solid var(--yellow-sun);
      padding: 10px 20px;
      color: var(--blue-ink);
      z-index: 25;
      position: relative;
      box-shadow: 0 4px 16px rgba(43, 108, 176, 0.12);
    }

    .hud-group {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 8px;
    }

    .hud-pill {
      background: var(--blue-ice);
      border: 2px solid var(--blue-bright);
      border-radius: 999px;
      padding: 5px 14px;
      font-weight: 800;
      font-size: 0.92rem;
      color: var(--blue-deep);
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .hud-pill.star-pill {
      background: var(--yellow-butter);
      border-color: var(--yellow-sun);
      color: var(--yellow-bronze);
    }

    .round-tracker {
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .round-badge {
      padding: 5px 11px;
      border-radius: 999px;
      font-family: 'Fredoka', sans-serif;
      font-size: 0.82rem;
      font-weight: 600;
      background: #F1F5F9;
      color: #64748B;
      border: 2px solid #CBD5E1;
      transition: all 0.25s;
    }

    .round-badge.active {
      background: var(--yellow-sun);
      color: var(--yellow-bronze);
      border-color: var(--yellow-amber);
      transform: scale(1.05);
      box-shadow: 0 3px 10px rgba(217, 119, 6, 0.25);
    }

    .round-badge.done {
      background: #DCFCE7;
      color: var(--mint-dark);
      border-color: var(--mint-ok);
    }

    .hud-mini-btn {
      background: linear-gradient(180deg, #E0F2FE 0%, var(--blue-sky) 100%);
      color: var(--blue-deep);
      border: 2px solid var(--blue-bright);
      border-radius: 12px;
      padding: 5px 11px;
      font-family: 'Fredoka', sans-serif;
      font-weight: 600;
      font-size: 0.84rem;
      cursor: pointer;
      box-shadow: 0 2px 0 var(--blue-bright);
      transition: transform 0.1s;
    }

    .hud-mini-btn:active {
      transform: translateY(2px);
      box-shadow: none;
    }

    .hud-mini-btn.yellow-btn {
      background: linear-gradient(180deg, var(--yellow-cream) 0%, var(--yellow-sun) 100%);
      color: var(--yellow-bronze);
      border-color: var(--yellow-amber);
      box-shadow: 0 2px 0 var(--yellow-amber);
    }

    /* ==========================================================================
       4. SCREENS & SMOOTH ENTRANCE TRANSITIONS
       ========================================================================== */
    .screen {
      display: none;
      flex: 1;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px 24px 66px;
      position: relative;
      z-index: 10;
      animation: floatStageIn 0.42s cubic-bezier(0.22, 1, 0.36, 1);
    }

    .screen.active {
      display: flex;
    }

    @keyframes floatStageIn {
      from { opacity: 0; transform: translateY(14px) scale(0.98); }
      to { opacity: 1; transform: translateY(0) scale(1); }
    }

    /* ==========================================================================
       5. PASTEL 3D STUDIO BUTTONS
       ========================================================================== */
    .btn-studio {
      font-family: 'Fredoka', sans-serif;
      font-size: 1.16rem;
      font-weight: 700;
      color: var(--yellow-bronze);
      background: linear-gradient(180deg, var(--yellow-butter) 0%, var(--yellow-sun) 100%);
      border: 4px solid var(--yellow-amber);
      border-radius: 22px;
      padding: 13px 28px;
      cursor: pointer;
      box-shadow: 0 6px 0 var(--yellow-amber), 0 10px 22px rgba(217, 119, 6, 0.22);
      transition: transform 0.12s ease, filter 0.12s ease;
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 9px;
      text-transform: uppercase;
    }

    .btn-studio:hover:not(:disabled) {
      transform: translateY(-2px);
      filter: brightness(1.04);
    }

    .btn-studio:active:not(:disabled) {
      transform: translateY(4px);
      box-shadow: 0 2px 0 var(--yellow-amber);
    }

    .btn-sky {
      background: linear-gradient(180deg, #E0F2FE 0%, var(--blue-bright) 100%);
      color: var(--blue-ink);
      border-color: var(--blue-deep);
      box-shadow: 0 6px 0 var(--blue-deep), 0 10px 20px rgba(43, 108, 176, 0.2);
    }

    .btn-sky:active:not(:disabled) {
      box-shadow: 0 2px 0 var(--blue-deep);
    }

    .btn-mint {
      background: linear-gradient(180deg, #86EFAC 0%, #22C55E 100%);
      color: #FFFFFF;
      border-color: var(--mint-dark);
      box-shadow: 0 6px 0 var(--mint-dark), 0 10px 20px rgba(21, 128, 61, 0.22);
    }

    .btn-mint:active:not(:disabled) {
      box-shadow: 0 2px 0 var(--mint-dark);
    }

    .btn-mint:disabled {
      background: #CBD5E1;
      border-color: #94A3B8;
      box-shadow: 0 4px 0 #94A3B8;
      color: #64748B;
      cursor: not-allowed;
    }

    .btn-coral {
      background: linear-gradient(180deg, #FDA4AF 0%, var(--coral-rec) 100%);
      color: #FFFFFF;
      border-color: var(--coral-dark);
      box-shadow: 0 6px 0 var(--coral-dark), 0 10px 22px rgba(244, 63, 94, 0.28);
    }

    .btn-coral:active:not(:disabled) {
      box-shadow: 0 2px 0 var(--coral-dark);
    }

    .btn-soft-neutral {
      background: #F8FAFC;
      color: #475569;
      border-color: #94A3B8;
      box-shadow: 0 4px 0 #94A3B8;
      font-size: 0.96rem;
      padding: 9px 18px;
    }

    /* ==========================================================================
       6. WELCOME SCREEN & FULL-TAB LAUNCHER
       ========================================================================== */
    .tv-marquee-card {
      background: linear-gradient(180deg, var(--yellow-cream) 0%, var(--yellow-butter) 100%);
      border: 5px solid var(--yellow-sun);
      border-radius: 30px;
      padding: 16px 34px;
      text-align: center;
      box-shadow:
        0 10px 0 var(--yellow-amber),
        0 16px 30px rgba(43, 108, 176, 0.18);
      margin-bottom: 16px;
    }

    .on-air-pill {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: #FFF1F2;
      color: var(--coral-dark);
      font-family: 'Fredoka', sans-serif;
      font-size: 0.85rem;
      font-weight: 700;
      padding: 4px 15px;
      border-radius: 999px;
      border: 2px solid #FDA4AF;
      letter-spacing: 1.2px;
      margin-bottom: 6px;
      animation: softPulseOnAir 1.5s infinite;
    }

    @keyframes softPulseOnAir {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.04); }
    }

    .tv-marquee-card h1 {
      font-size: clamp(1.9rem, 4.5vw, 3.1rem);
      color: var(--blue-deep);
      text-shadow: 2px 2px 0 #FFFFFF;
      line-height: 1.08;
    }

    .tv-marquee-sub {
      color: var(--yellow-bronze);
      font-size: clamp(1rem, 2.2vw, 1.22rem);
      font-weight: 800;
      margin-top: 4px;
    }

    .glass-welcome-panel {
      background: var(--glass-white);
      backdrop-filter: blur(12px);
      border: 4px solid var(--glass-border);
      border-radius: 28px;
      padding: 20px 26px;
      max-width: 750px;
      width: 100%;
      text-align: center;
      box-shadow: var(--shadow-soft);
      margin-bottom: 18px;
      display: flex;
      flex-direction: column;
      gap: 14px;
    }

    .welcome-story-text {
      font-size: 1.08rem;
      font-weight: 800;
      color: var(--blue-ink);
      line-height: 1.55;
    }

    .mic-guide-box {
      background: var(--blue-ice);
      border: 3px solid var(--blue-bright);
      color: var(--blue-ink);
      border-radius: 20px;
      padding: 13px 16px;
      font-size: 0.95rem;
      font-weight: 800;
      line-height: 1.45;
      text-align: left;
      display: flex;
      align-items: flex-start;
      gap: 12px;
    }

    .welcome-actions-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 14px;
    }

    /* ==========================================================================
       7. STAGE SPEAKING ROUND SCREEN (FROSTED GLASS CARDS)
       ========================================================================== */
    #stage-screen {
      justify-content: flex-start;
      padding-top: 14px;
      gap: 12px;
    }

    .stage-topbar {
      width: 100%;
      max-width: 830px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 8px;
    }

    .round-title-pill {
      background: linear-gradient(90deg, var(--yellow-butter), var(--yellow-sun));
      color: var(--yellow-bronze);
      border: 3px solid #FFFFFF;
      border-radius: 999px;
      padding: 6px 20px;
      font-family: 'Fredoka', sans-serif;
      font-size: 1.15rem;
      font-weight: 700;
      box-shadow: 0 4px 14px rgba(43, 108, 176, 0.15);
    }

    .challenge-count-pill {
      background: rgba(255, 255, 255, 0.9);
      color: var(--blue-deep);
      border: 2px solid var(--blue-bright);
      border-radius: 999px;
      padding: 5px 16px;
      font-weight: 800;
      font-size: 0.95rem;
    }

    .glass-stage-card {
      width: 100%;
      max-width: 830px;
      background: var(--glass-white);
      backdrop-filter: blur(12px);
      border: 4px solid #FFFFFF;
      border-radius: 28px;
      padding: 18px 24px;
      box-shadow: var(--shadow-soft);
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      gap: 12px;
    }

    .prompt-hint-badge {
      background: var(--blue-ice);
      color: var(--blue-deep);
      border: 2px solid var(--blue-bright);
      border-radius: 999px;
      padding: 4px 16px;
      font-size: 0.92rem;
      font-weight: 800;
    }

    /* Pastel Sky-Blue & Butter-Yellow Teleprompter Display */
    .teleprompter-box {
      width: 100%;
      background: linear-gradient(135deg, #F0F8FF 0%, var(--yellow-cream) 100%);
      color: var(--blue-ink);
      border: 4px solid var(--blue-bright);
      border-radius: 22px;
      padding: 14px 20px;
      font-family: 'Fredoka', sans-serif;
      font-size: clamp(1.3rem, 3vw, 1.85rem);
      line-height: 1.4;
      box-shadow: inset 0 2px 8px rgba(124, 196, 250, 0.25);
    }

    .blank-word-highlight {
      color: var(--blue-deep);
      background: var(--yellow-butter);
      padding: 1px 12px;
      border-radius: 12px;
      border-bottom: 3px solid var(--yellow-amber);
    }

    /* Interactive Answer Controls */
    .answer-builder-area {
      width: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }

    .pastel-text-input {
      width: 100%;
      max-width: 400px;
      padding: 11px 18px;
      font-family: 'Fredoka', sans-serif;
      font-size: 1.18rem;
      color: var(--blue-ink);
      background: #FFFFFF;
      border: 3px solid var(--blue-bright);
      border-radius: 18px;
      text-align: center;
      outline: none;
      transition: border-color 0.2s, box-shadow 0.2s;
    }

    .pastel-text-input:focus {
      border-color: var(--yellow-amber);
      box-shadow: 0 0 0 4px rgba(255, 224, 102, 0.45);
    }

    .chips-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 8px;
    }

    .pastel-chip {
      background: var(--yellow-cream);
      color: var(--yellow-bronze);
      border: 2px solid var(--yellow-sun);
      border-radius: 999px;
      padding: 7px 15px;
      font-family: 'Nunito', sans-serif;
      font-weight: 800;
      font-size: 0.94rem;
      cursor: pointer;
      transition: all 0.15s;
    }

    .pastel-chip:hover {
      background: var(--yellow-sun);
      transform: translateY(-1px);
    }

    /* Round 3 Hobby Cards */
    .hobbies-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(125px, 1fr));
      gap: 10px;
      width: 100%;
    }

    .hobby-card {
      background: var(--blue-ice);
      border: 3px solid var(--blue-sky);
      border-radius: 20px;
      padding: 10px 8px;
      cursor: pointer;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 4px;
      transition: all 0.18s;
    }

    .hobby-card:hover {
      border-color: var(--blue-bright);
      transform: translateY(-2px);
    }

    .hobby-card.selected {
      background: var(--yellow-butter);
      border-color: var(--yellow-amber);
      box-shadow: 0 6px 14px rgba(217, 119, 6, 0.2);
      transform: scale(1.03);
    }

    .hobby-emoji {
      font-size: 2.2rem;
    }

    .hobby-label {
      font-family: 'Fredoka', sans-serif;
      font-size: 0.98rem;
      color: var(--blue-ink);
    }

    /* Round 4 Editable Big Speech Box */
    .speech-editor-box {
      width: 100%;
      min-height: 112px;
      padding: 12px 16px;
      font-family: 'Nunito', sans-serif;
      font-size: 1.05rem;
      font-weight: 800;
      color: var(--blue-ink);
      background: #FFFFFF;
      border: 3px solid var(--blue-bright);
      border-radius: 18px;
      resize: vertical;
      line-height: 1.5;
    }

    .sentence-counter-pill {
      font-size: 0.88rem;
      font-weight: 800;
      padding: 4px 14px;
      border-radius: 999px;
      background: #DCFCE7;
      color: var(--mint-dark);
      border: 2px solid var(--mint-ok);
    }

    .sentence-counter-pill.needs-more {
      background: var(--yellow-butter);
      color: var(--yellow-bronze);
      border-color: var(--yellow-amber);
    }

    /* ==========================================================================
       8. STUDIO MICROPHONE, LIVE EQUALIZER & AUDIO PLAYBACK STATION
       ========================================================================== */
    .mic-studio-station {
      width: 100%;
      background: linear-gradient(180deg, rgba(235, 246, 255, 0.9) 0%, rgba(255, 251, 230, 0.9) 100%);
      border: 3px solid var(--blue-sky);
      border-radius: 24px;
      padding: 14px 18px;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      transition: all 0.3s;
    }

    .mic-studio-station.recording {
      background: linear-gradient(180deg, #FFF1F2 0%, var(--yellow-cream) 100%);
      border-color: var(--coral-rec);
      box-shadow: 0 0 22px rgba(244, 63, 94, 0.22);
    }

    .mic-visual-row {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 18px;
    }

    /* Real-Time Volume Equalizer Wave Bars */
    .eq-wave-group {
      display: flex;
      align-items: center;
      gap: 6px;
      height: 46px;
    }

    .eq-bar {
      width: 8px;
      height: 12px;
      background: var(--blue-bright);
      border-radius: 999px;
      transition: height 0.08s ease-out, background 0.2s;
    }

    .eq-bar:nth-child(even) {
      background: var(--yellow-sun);
    }

    .mic-studio-station.recording .eq-bar {
      background: var(--coral-rec);
    }

    .mic-studio-station.recording .eq-bar:nth-child(2) { background: var(--yellow-amber); }
    .mic-studio-station.recording .eq-bar:nth-child(3) { background: var(--mint-ok); }
    .mic-studio-station.recording .eq-bar:nth-child(4) { background: var(--blue-deep); }

    /* Cartoon Studio Microphone SVG */
    .cartoon-mic-svg {
      width: 64px;
      height: 76px;
      filter: drop-shadow(0 4px 8px rgba(43, 108, 176, 0.22));
    }

    .mic-studio-station.recording .cartoon-mic-svg {
      animation: micBounce 0.6s ease-in-out infinite alternate;
    }

    @keyframes micBounce {
      0% { transform: rotate(-6deg) scale(1.06); }
      100% { transform: rotate(6deg) scale(1.06); }
    }

    .studio-status-msg {
      font-weight: 800;
      font-size: 0.98rem;
      color: var(--blue-ink);
      max-width: 680px;
      line-height: 1.45;
    }

    .mic-studio-station.recording .studio-status-msg {
      color: var(--coral-dark);
    }

    .mic-controls-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 10px;
    }

    /* Playback Review Box */
    .playback-review-box {
      display: none;
      width: 100%;
      max-width: 660px;
      background: #FFFFFF;
      border: 3px solid var(--blue-bright);
      border-radius: 20px;
      padding: 12px 16px;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      animation: floatStageIn 0.3s ease;
    }

    .playback-review-box.visible {
      display: flex;
    }

    .playback-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      gap: 10px;
      width: 100%;
    }

    #pupil-audio-player {
      height: 40px;
      max-width: 270px;
      border-radius: 999px;
    }

    /* ==========================================================================
       9. SELF-ASSESSMENT SPEAKING CHECKLIST
       ========================================================================== */
    .checklist-card {
      display: none;
      width: 100%;
      background: var(--yellow-cream);
      border: 3px solid var(--yellow-sun);
      border-radius: 22px;
      padding: 14px 18px;
      flex-direction: column;
      align-items: center;
      gap: 10px;
      animation: floatStageIn 0.35s ease;
    }

    .checklist-card.visible {
      display: flex;
    }

    .checklist-heading {
      font-family: 'Fredoka', sans-serif;
      font-size: 1.12rem;
      color: var(--yellow-bronze);
    }

    .checklist-grid {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 10px;
      width: 100%;
    }

    .chk-pill-label {
      background: #FFFFFF;
      border: 3px solid var(--blue-sky);
      border-radius: 16px;
      padding: 9px 14px;
      display: flex;
      align-items: center;
      gap: 8px;
      font-weight: 800;
      font-size: 0.96rem;
      color: var(--blue-ink);
      cursor: pointer;
      transition: all 0.15s;
      user-select: none;
    }

    .chk-pill-label:hover {
      border-color: var(--blue-bright);
    }

    .chk-pill-label.checked {
      background: #DCFCE7;
      border-color: var(--mint-ok);
      color: var(--mint-dark);
    }

    .chk-pill-label input[type="checkbox"] {
      width: 20px;
      height: 20px;
      accent-color: var(--mint-ok);
      cursor: pointer;
    }

    /* ==========================================================================
       10. STAR SPEAKER CERTIFICATE SCREEN
       ========================================================================== */
    #confetti-canvas {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 30;
    }

    .certificate-card {
      width: 100%;
      max-width: 780px;
      background: linear-gradient(180deg, #FFFFFF 0%, var(--yellow-cream) 60%, var(--blue-ice) 100%);
      border: 8px double var(--yellow-amber);
      border-radius: 28px;
      padding: 24px 28px;
      text-align: center;
      box-shadow: var(--shadow-soft);
      position: relative;
      margin-bottom: 16px;
    }

    .cert-top-icons {
      font-size: 2.5rem;
      margin-bottom: 4px;
    }

    .cert-title {
      font-size: clamp(1.5rem, 3.8vw, 2.4rem);
      color: var(--blue-deep);
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .cert-subtitle {
      font-weight: 800;
      color: var(--yellow-bronze);
      font-size: 1rem;
      margin: 4px 0 10px;
    }

    .cert-pupil-name {
      font-family: 'Fredoka', sans-serif;
      font-size: clamp(1.7rem, 4vw, 2.5rem);
      color: var(--blue-ink);
      border-bottom: 4px solid var(--yellow-sun);
      display: inline-block;
      padding: 2px 28px;
      margin-bottom: 10px;
    }

    .cert-stars-badge {
      font-family: 'Fredoka', sans-serif;
      font-size: 1.25rem;
      color: var(--mint-dark);
      background: #DCFCE7;
      border: 2px solid var(--mint-ok);
      border-radius: 999px;
      padding: 5px 20px;
      display: inline-block;
      margin-bottom: 12px;
    }

    .cert-speech-box {
      background: rgba(255, 255, 255, 0.92);
      border: 2px dashed var(--blue-bright);
      border-radius: 18px;
      padding: 12px 16px;
      font-size: 0.98rem;
      font-weight: 700;
      color: var(--blue-ink);
      line-height: 1.5;
      text-align: left;
    }

    .cert-buttons-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 14px;
    }

    /* ==========================================================================
       11. SOFT PASTEL AUDIENCE SILHOUETTE FOOTER
       ========================================================================== */
    .audience-wave-footer {
      position: absolute;
      bottom: 0;
      left: 0;
      width: 100%;
      height: 52px;
      pointer-events: none;
      z-index: 12;
    }

    .audience-wave-footer.cheering {
      animation: audienceJump 0.45s ease-in-out 4;
    }

    @keyframes audienceJump {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-9px); }
    }

    /* ==========================================================================
       12. RESPONSIVE & PRINT STYLES
       ========================================================================== */
    @media (max-width: 680px) {
      #tv-stage-container {
        border-radius: 22px;
        border-width: 4px;
      }
      .screen {
        padding: 14px 14px 60px;
      }
      .round-tracker {
        display: none;
      }
      .btn-studio {
        font-size: 1.04rem;
        padding: 11px 20px;
      }
    }

    @media print {
      body {
        background: #FFFFFF;
        padding: 0;
      }
      #tv-stage-container {
        border: none;
        box-shadow: none;
        background: #FFFFFF;
      }
      .studio-beam, .pastel-cloud, .sparkle-star, .audience-wave-footer, .cert-buttons-row, #confetti-canvas {
        display: none !important;
      }
      .certificate-card {
        box-shadow: none;
        margin: 0 auto;
      }
    }
  </style>
</head>
<body>

  <div id="tv-stage-container">
    <!-- Soft Pastel Studio Spotlights -->
    <div class="studio-beam left"></div>
    <div class="studio-beam right"></div>
    <div class="studio-beam center-onair" id="center-spotlight"></div>

    <!-- Floating Pastel Clouds & Stars -->
    <div class="pastel-cloud cloud-1"></div>
    <div class="pastel-cloud cloud-2"></div>
    <div class="sparkle-star" style="top: 56px; left: 22%;">✦</div>
    <div class="sparkle-star" style="top: 96px; right: 24%; animation-delay: 0.9s;">★</div>
    <div class="sparkle-star" style="bottom: 84px; left: 8%; animation-delay: 1.5s;">✦</div>
    <div class="sparkle-star" style="bottom: 92px; right: 9%; animation-delay: 0.4s;">★</div>

    <!-- ======================================================================
         TOP TV SHOW HUD BAR
         ====================================================================== -->
    <header id="show-hud">
      <div class="hud-group">
        <div class="hud-pill">
          <span>🎤</span>
          <span id="hud-contestant-name">Star Contestant</span>
        </div>
        <div class="hud-pill star-pill">
          <span>⭐</span>
          <span id="hud-stars">0</span> / <span id="hud-total-stars">10</span>
        </div>
      </div>

      <div class="round-tracker" id="hud-round-badges">
        <span class="round-badge active" data-round="0">R1: Intro</span>
        <span class="round-badge" data-round="1">R2: Favourites</span>
        <span class="round-badge" data-round="2">R3: Hobbies</span>
        <span class="round-badge" data-round="3">R4: Big Speech</span>
      </div>

      <div class="hud-group">
        <button type="button" class="hud-mini-btn yellow-btn" id="btn-hud-full-tab" title="Open in a full browser tab for microphone access">
          🚀 Full Tab (Mic)
        </button>
        <button type="button" class="hud-mini-btn" id="btn-sfx">🔊 SFX</button>
      </div>
    </header>

    <!-- ======================================================================
         SCREEN 1: WELCOME SCREEN & DIRECT FULL-TAB MIC LAUNCHER
         ====================================================================== -->
    <section id="welcome-screen" class="screen active">
      <div class="tv-marquee-card">
        <div class="on-air-pill">● LIVE CHILDREN'S TV SHOW</div>
        <h1>🎤 MIC CHECK! 🎤</h1>
        <div class="tv-marquee-sub">My Speaking Identity – Year 4 Star Speaker Show</div>
      </div>

      <div class="glass-welcome-panel">
        <p class="welcome-story-text">
          Welcome to <strong>“MIC CHECK!”</strong> — the fun television show where YOU are the newest contestant! Complete <strong>4 Speaking Rounds</strong> on stage, record and listen to your own voice, and earn stars to win your official <strong>Star Speaker Certificate</strong>!
        </p>

        <div class="mic-guide-box">
          <div style="font-size: 1.85rem; line-height: 1;">🎙️</div>
          <div>
            <strong>Microphone &amp; Full-Tab Tip:</strong><br />
            If you are viewing this inside a small preview box, tap <strong>🚀 OPEN IN FULL TAB (ENABLE MIC)</strong> first so your browser can ask for microphone permission. When prompted, click <strong>Allow</strong>!
          </div>
        </div>
      </div>

      <div class="welcome-actions-row">
        <button type="button" class="btn-studio btn-sky" id="btn-welcome-full-tab">
          🚀 OPEN IN FULL TAB (ENABLE MIC)
        </button>
        <button type="button" class="btn-studio" id="btn-start-show">
          🎬 STEP ONTO THE STAGE!
        </button>
      </div>
    </section>

    <!-- ======================================================================
         SCREEN 2: STAGE SPEAKING ROUND SCREEN
         ====================================================================== -->
    <section id="stage-screen" class="screen">
      <div class="stage-topbar">
        <div class="round-title-pill" id="round-title-display">Round 1: Introduce Yourself</div>
        <div class="challenge-count-pill" id="prompt-counter-display">Challenge 1 of 4</div>
      </div>

      <div class="glass-stage-card">
        <div class="prompt-hint-badge" id="prompt-instruction-display">
          Complete the sentence below, then record yourself speaking aloud!
        </div>

        <!-- Live Teleprompter Sentence -->
        <div class="teleprompter-box" id="teleprompter-display">
          “My name is <span class="blank-word-highlight">______</span>.”
        </div>

        <!-- Dynamic Answer Controls -->
        <div class="answer-builder-area" id="answer-controls-container"></div>

        <!-- Studio Microphone, Live Equalizer & Playback Station -->
        <div class="mic-studio-station" id="mic-station">
          <div class="mic-visual-row">
            <div class="eq-wave-group">
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
            </div>

            <!-- Cute Pastel Studio Microphone SVG -->
            <svg class="cartoon-mic-svg" viewBox="0 0 80 96" xmlns="http://www.w3.org/2000/svg">
              <rect x="22" y="6" width="36" height="48" rx="18" fill="#E0F2FE" stroke="#2B6CB0" stroke-width="3.5"/>
              <line x1="22" y1="22" x2="58" y2="22" stroke="#7CC4FA" stroke-width="2.5"/>
              <line x1="22" y1="30" x2="58" y2="30" stroke="#7CC4FA" stroke-width="2.5"/>
              <line x1="22" y1="38" x2="58" y2="38" stroke="#7CC4FA" stroke-width="2.5"/>
              <rect x="20" y="27" width="40" height="7" rx="3.5" fill="#FFE066" stroke="#D97706" stroke-width="2"/>
              <path d="M14,34 Q14,64 40,64 Q66,64 66,34" fill="none" stroke="#FFE066" stroke-width="5" stroke-linecap="round"/>
              <rect x="36" y="64" width="8" height="20" fill="#7CC4FA" stroke="#2B6CB0" stroke-width="2.5"/>
              <ellipse cx="40" cy="86" rx="22" ry="6" fill="#2B6CB0"/>
            </svg>

            <div class="eq-wave-group">
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
              <div class="eq-bar"></div>
            </div>
          </div>

          <div class="studio-status-msg" id="stage-status-text">
            Tap <strong>🔴 RECORD MY VOICE</strong> and speak your sentence clearly!
          </div>

          <div class="mic-controls-row">
            <button type="button" class="btn-studio btn-coral" id="btn-record-voice">
              🔴 RECORD MY VOICE
            </button>

            <button type="button" class="btn-studio btn-sky" id="btn-stage-full-tab" style="display: none; font-size: 0.96rem; padding: 9px 18px;">
              🚀 Open in Full Tab (Enable Mic)
            </button>

            <button type="button" class="btn-studio btn-soft-neutral" id="btn-practice-no-mic" style="display: none;">
              🗣️ Practice Without Mic
            </button>
          </div>

          <!-- Voice Playback & Re-Record Panel -->
          <div class="playback-review-box" id="playback-box">
            <div style="font-weight: 800; color: var(--blue-deep); font-size: 0.95rem;">
              🎧 Listen back to check your speaking!
            </div>
            <div class="playback-row">
              <button type="button" class="btn-studio btn-sky" id="btn-play-recording" style="font-size: 1rem; padding: 10px 18px;">
                ▶️ PLAY MY RECORDING
              </button>
              <audio id="pupil-audio-player" controls></audio>
              <button type="button" class="btn-studio" id="btn-record-again" style="font-size: 1rem; padding: 10px 18px;">
                🔄 Record Again
              </button>
            </div>
          </div>
        </div>

        <!-- 3-Point Speaking Self-Assessment Checklist -->
        <div class="checklist-card" id="speaking-checklist">
          <div class="checklist-heading">📋 Star Speaker Self-Check — Tick all 3 to collect your Star!</div>
          <div class="checklist-grid">
            <label class="chk-pill-label">
              <input type="checkbox" class="speaker-chk" id="chk-1" />
              <span>1. Did I speak clearly?</span>
            </label>
            <label class="chk-pill-label">
              <input type="checkbox" class="speaker-chk" id="chk-2" />
              <span>2. Did I use complete sentences?</span>
            </label>
            <label class="chk-pill-label">
              <input type="checkbox" class="speaker-chk" id="chk-3" />
              <span>3. Did I speak confidently?</span>
            </label>
          </div>
        </div>

        <!-- Claim Star & Continue Button -->
        <button type="button" class="btn-studio btn-mint" id="btn-next-challenge" disabled style="display: none;">
          ⭐ CLAIM STAR &amp; NEXT ➡️
        </button>
      </div>
    </section>

    <!-- ======================================================================
         SCREEN 3: GRAND FINALE STAR SPEAKER CERTIFICATE
         ====================================================================== -->
    <section id="certificate-screen" class="screen">
      <canvas id="confetti-canvas"></canvas>

      <div class="certificate-card">
        <div class="cert-top-icons">🏆🌟🎤🌟🏆</div>
        <h1 class="cert-title">Star Speaker Certificate</h1>
        <div class="cert-subtitle">Presented by the “MIC CHECK!” Television Talent Show to</div>

        <div class="cert-pupil-name" id="cert-name-display">Star Speaker</div>
        <br />
        <div class="cert-stars-badge" id="cert-stars-display">
          ⭐ 10 / 10 Stars Earned – Official Star Speaker!
        </div>

        <div class="cert-speech-box" id="cert-speech-display">
          <!-- Populated with pupil's Big Introduction -->
        </div>
      </div>

      <div class="cert-buttons-row">
        <button type="button" class="btn-studio btn-sky" id="btn-print-cert">
          🖨️ PRINT / SAVE CERTIFICATE
        </button>
        <button type="button" class="btn-studio" id="btn-play-again">
          🔄 PLAY AGAIN
        </button>
      </div>
    </section>

    <!-- Soft Pastel Audience Silhouette Footer -->
    <svg class="audience-wave-footer" id="audience-svg" viewBox="0 0 1000 60" preserveAspectRatio="none">
      <path d="M0,60 L0,40 Q25,22 50,40 Q75,20 100,40 Q130,24 160,40 Q190,18 220,40 Q255,25 290,40 Q325,20 360,40 Q395,22 430,40 Q465,18 500,40 Q535,24 570,40 Q605,20 640,40 Q675,22 710,40 Q745,18 780,40 Q815,24 850,40 Q885,20 920,40 Q960,22 1000,40 L1000,60 Z" fill="#93C5FD" opacity="0.65"/>
      <circle cx="50" cy="24" r="11" fill="#93C5FD" opacity="0.65"/>
      <circle cx="130" cy="22" r="12" fill="#93C5FD" opacity="0.65"/>
      <circle cx="220" cy="21" r="11" fill="#93C5FD" opacity="0.65"/>
      <circle cx="310" cy="24" r="12" fill="#93C5FD" opacity="0.65"/>
      <circle cx="400" cy="20" r="11" fill="#93C5FD" opacity="0.65"/>
      <circle cx="500" cy="22" r="13" fill="#93C5FD" opacity="0.65"/>
      <circle cx="600" cy="20" r="11" fill="#93C5FD" opacity="0.65"/>
      <circle cx="690" cy="24" r="12" fill="#93C5FD" opacity="0.65"/>
      <circle cx="780" cy="21" r="11" fill="#93C5FD" opacity="0.65"/>
      <circle cx="870" cy="23" r="12" fill="#93C5FD" opacity="0.65"/>
      <circle cx="950" cy="22" r="11" fill="#93C5FD" opacity="0.65"/>
    </svg>
  </div>

  <!-- ========================================================================
       JAVASCRIPT: FULL-TAB LAUNCHER, MEDIARECORDER API, ROUNDS & CERTIFICATE
       ======================================================================== -->
  <script>
    /**
     * ========================================================================
     * 1. DIRECT FULL-TAB MICROPHONE LAUNCHER (PREVENTS BLANK TABS)
     * ========================================================================
     */
    function openInFullTab() {
      playTone("click");
      const currentHref = window.location.href || "";

      // If hosted on a live http/https URL (e.g., Netlify, GitHub Pages, Google Sites), open it directly
      if (currentHref.startsWith("http://") || currentHref.startsWith("https://")) {
        const win = window.open(currentHref, "_blank", "noopener,noreferrer");
        if (win) return;
      }

      // If running inside a sandboxed preview (srcdoc / about:blank / blob), build a clean standalone Blob tab
      try {
        const docClone = document.documentElement.cloneNode(true);
        const fullHTML = "<!DOCTYPE html>\n" + docClone.outerHTML;
        const blob = new Blob([fullHTML], { type: "text/html;charset=utf-8" });
        const blobUrl = URL.createObjectURL(blob);
        window.open(blobUrl, "_blank");
      } catch (err) {
        document.getElementById("stage-status-text").innerHTML =
          "⚠️ Your browser blocked opening a new tab. Please allow pop-ups or save this page (`Ctrl+S` / `Cmd+S`) and open it in Chrome or Edge.";
      }
    }

    /**
     * ========================================================================
     * 2. FOUR SPEAKING ROUNDS CURRICULUM DATA (YEAR 4 ESL)
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
            chips: ["blue", "yellow", "green", "pink", "purple", "red"]
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
            instruction: "Tap a hobby card below and edit or speak a simple sentence explaining it!"
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
     * 3. GAME STATE & AUDIO STREAM REFERENCES
     * ========================================================================
     */
    const totalStarsAvailable = ROUNDS.reduce((sum, r) => sum + r.prompts.length, 0);

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
     * 4. WEB AUDIO API SOUND EFFECTS (NO EXTERNAL SOUND URLS NEEDED)
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
          gain.gain.setValueAtTime(0.13, now);
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
          gain.gain.setValueAtTime(0.13, now);
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
            gain.gain.setValueAtTime(0.15, now + idx * 0.08);
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
     * 5. BROWSER MEDIARECORDER API (LOCAL DEVICE VOICE RECORDING & PLAYBACK)
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
          "⚠️ Voice recording is not supported in this browser. Open in <strong>Chrome, Edge, or Safari</strong>, or tap <strong>Practice Without Mic</strong> below!";
        document.getElementById("btn-stage-full-tab").style.display = "inline-flex";
        document.getElementById("btn-practice-no-mic").style.display = "inline-flex";
        return;
      }

      try {
        if (!gameState.micStream || !gameState.micStream.active) {
          gameState.micStream = await navigator.mediaDevices.getUserMedia({
            audio: {
              echoCancellation: true,
              noiseSuppression: true,
              autoGainControl: true
            }
          });
        }

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

        const station = document.getElementById("mic-station");
        station.classList.add("recording");
        document.getElementById("center-spotlight").classList.add("active");
        document.getElementById("playback-box").classList.remove("visible");
        document.getElementById("btn-stage-full-tab").style.display = "none";
        document.getElementById("btn-practice-no-mic").style.display = "none";

        const recBtn = document.getElementById("btn-record-voice");
        recBtn.innerHTML = "⏹️ STOP RECORDING";
        recBtn.classList.remove("btn-coral");
        recBtn.classList.add("btn-mint");

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
          "🚫 <strong>Microphone Blocked or Permission Needed!</strong> Tap <strong>🚀 Open in Full Tab (Enable Mic)</strong> or click <strong>Allow</strong> in your browser address bar.";
        document.getElementById("btn-stage-full-tab").style.display = "inline-flex";
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
      station.classList.remove("recording");
      document.getElementById("center-spotlight").classList.remove("active");

      const recBtn = document.getElementById("btn-record-voice");
      recBtn.innerHTML = "🔴 RECORD MY VOICE";
      recBtn.classList.remove("btn-mint");
      recBtn.classList.add("btn-coral");

      const audience = document.getElementById("audience-svg");
      audience.classList.remove("cheering");
      void audience.offsetWidth;
      audience.classList.add("cheering");

      document.getElementById("stage-status-text").innerHTML =
        "🎉 <strong>Recording saved on your device!</strong> Listen back below to check your voice, then tick your checklist!";
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
     * 6. SCREEN NAVIGATION, HUD & TELEPROMPTER RENDERING
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

    function escapeHTML(str) {
      return str
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;");
    }

    function countSentences(text) {
      return text
        .trim()
        .split(/[.!?]+/)
        .map(s => s.trim())
        .filter(s => s.length > 2).length;
    }

    function updateTeleprompterDisplay() {
      const round = ROUNDS[gameState.roundIdx];
      const prompt = round.prompts[gameState.promptIdx];
      const el = document.getElementById("teleprompter-display");

      if (prompt.type === "fixed") {
        el.innerHTML = `“${prompt.fixedSentence}”`;
      } else if (prompt.type === "fill") {
        const val = (gameState.answers[prompt.key] || "").trim() || "______";
        el.innerHTML = `“${prompt.prefix}<span class="blank-word-highlight">${escapeHTML(val)}</span>${prompt.suffix}”`;
      } else if (prompt.type === "hobby") {
        const text = (gameState.answers.hobbySentence || "").trim() || "Choose a hobby card below!";
        el.innerHTML = `“<span class="blank-word-highlight">${escapeHTML(text)}</span>”`;
      } else if (prompt.type === "finale") {
        const speech = (gameState.answers.bigIntro || "").trim();
        el.innerHTML = `<div style="font-size: clamp(1.02rem, 2.1vw, 1.28rem); text-align: left;">“${escapeHTML(speech)}”</div>`;
      }
    }

    function buildDefaultBigIntro() {
      const name = gameState.answers.name.trim() || "a Year 4 pupil";
      const town = gameState.answers.town.trim() || "Malaysia";
      const school = gameState.answers.school.trim() || "my primary school";
      const colour = gameState.answers.colour.trim() || "soft blue";
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

      const station = document.getElementById("mic-station");
      station.classList.remove("recording");
      document.getElementById("center-spotlight").classList.remove("active");

      const recBtn = document.getElementById("btn-record-voice");
      recBtn.innerHTML = "🔴 RECORD MY VOICE";
      recBtn.classList.remove("btn-mint");
      recBtn.classList.add("btn-coral");

      document.getElementById("playback-box").classList.remove("visible");
      document.getElementById("speaking-checklist").classList.remove("visible");
      document.getElementById("btn-stage-full-tab").style.display = "none";
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

      const controlsBox = document.getElementById("answer-controls-container");
      controlsBox.innerHTML = "";

      if (prompt.type === "fill") {
        const input = document.createElement("input");
        input.type = "text";
        input.className = "pastel-text-input";
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
          chipsRow.className = "chips-row";
          prompt.chips.forEach(chipText => {
            const chip = document.createElement("button");
            chip.type = "button";
            chip.className = "pastel-chip";
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
        hobbyInput.className = "pastel-text-input";
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
        countBadge.className = "sentence-counter-pill";

        const updateCountBadge = (txt) => {
          const count = countSentences(txt);
          if (count >= 4) {
            countBadge.className = "sentence-counter-pill";
            countBadge.textContent = `✅ ${count} sentences ready (Goal: at least 4 sentences)`;
          } else {
            countBadge.className = "sentence-counter-pill needs-more";
            countBadge.textContent = `✍️ ${count} of 4 sentences written — add ${4 - count} more!`;
          }
        };

        const area = document.createElement("textarea");
        area.className = "speech-editor-box";
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
        nextBtn.innerHTML = "⭐ CLAIM STAR & NEXT ➡️";
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

      const colors = ["#7CC4FA", "#FFE066", "#2B6CB0", "#F43F5E", "#22C55E", "#F59E0B"];
      const particles = Array.from({ length: 90 }, () => ({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height - canvas.height,
        w: Math.random() * 10 + 6,
        h: Math.random() * 6 + 4,
        color: colors[Math.floor(Math.random() * colors.length)],
        vy: Math.random() * 2.8 + 1.8,
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
    document.getElementById("btn-welcome-full-tab").addEventListener("click", openInFullTab);
    document.getElementById("btn-hud-full-tab").addEventListener("click", openInFullTab);
    document.getElementById("btn-stage-full-tab").addEventListener("click", openInFullTab);

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
