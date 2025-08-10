# Noor-surprise-
A sweet interactive surprise with html and css
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
  <title>Noor ✨ — Tap for Surprise</title>
  <link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
  <style>
    :root {
      --pink1: #fff0f6;
      --pink2: #ffd6e8;
      --accent: #ff5fa8;
      --text: #5b2130;
    }
    * { box-sizing: border-box; }
    html, body {
      height: 100%;
      margin: 0;
      padding: 0;
      font-family: Poppins, system-ui, Segoe UI, Roboto, Arial;
      background: radial-gradient(circle at 10% 20%, #ffeef6 0%, var(--pink1) 25%, var(--pink2) 100%);
      color: var(--text);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      overflow: hidden;
    }
    h1 {
      font-family: 'Great Vibes', cursive;
      font-size: 60px;
      margin: 0;
      color: #6b1230;
      text-shadow: 0 4px 14px rgba(107, 18, 48, 0.12);
    }
    .sub {
      font-size: 20px;
      font-weight: 600;
      margin: 12px 0 40px;
    }
    .tap-btn {
      padding: 14px 26px;
      background: linear-gradient(90deg, var(--accent), #ff93b7);
      color: white;
      font-size: 20px;
      border: none;
      border-radius: 999px;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(107,18,48,0.15);
      transition: transform 0.15s ease;
    }
    .tap-btn:active { transform: scale(0.96); }

    /* Hidden second screen */
    .screen { position: absolute; inset: 0; display: none; flex-direction: column; align-items: center; justify-content: center; padding: 20px; }
    .screen.active { display: flex; }
    .poem {
      background: rgba(255,255,255,0.7);
      padding: 16px;
      border-radius: 14px;
      font-size: 16px;
      text-align: center;
      max-width: 600px;
      margin-bottom: 20px;
    }
    .bubble-area {
      position: relative;
      flex: 1;
      width: 100%;
      max-width: 600px;
      background: rgba(255,255,255,0.15);
      border-radius: 14px;
      overflow: hidden;
    }
    .bubble {
      position: absolute;
      border-radius: 50%;
      pointer-events: none;
      background: radial-gradient(circle at 30% 30%, rgba(255,255,255,0.9), rgba(255,255,255,0.6));
      box-shadow: 0 4px 10px rgba(107,18,48,0.1);
      animation: floatUp linear forwards;
    }
    @keyframes floatUp {
      from { transform: translateY(0); opacity: 1; }
      to { transform: translateY(-200px); opacity: 0; }
    }
  </style>
</head>
<body>

  <!-- First screen -->
  <div id="screen1" class="screen active">
    <h1>Noor ✨</h1>
    <div class="sub">Tap to see your surprise</div>
    <button class="tap-btn" onclick="showSecondScreen()">Tap Here</button>
  </div>

  <!-- Second screen -->
  <div id="screen2" class="screen">
    <h1>Good Morning, Golu molu ✨</h1>
    <div class="poem">
      Good morning, my sweetest — every sunrise reminds me of your smile.<br>
      May your day be as soft as a lullaby, bright as your laughter,<br>
      and filled with tiny magical moments. 💖
    </div>
    <div class="bubble-area" id="bubbleArea"></div>
  </div>

  <script>
    function showSecondScreen() {
      document.getElementById('screen1').classList.remove('active');
      document.getElementById('screen2').classList.add('active');
      startBubbles();
    }

    function startBubbles() {
      const area = document.getElementById('bubbleArea');
      setInterval(() => {
        const bubble = document.createElement('div');
        const size = Math.random() * 40 + 20;
        bubble.className = 'bubble';
        bubble.style.width = size + 'px';
        bubble.style.height = size + 'px';
        bubble.style.left = Math.random() * (area.clientWidth - size) + 'px';
        bubble.style.bottom = '-50px';
        bubble.style.animationDuration = (Math.random() * 3 + 3) + 's';
        area.appendChild(bubble);
        setTimeout(() => bubble.remove(), 6000);
      }, 300);
    }
  </script>

</body>
</html>
