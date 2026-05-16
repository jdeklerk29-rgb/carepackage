<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Care Package</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html,
    body {
      width: 100%;
      min-height: 100%;
      overflow-x: hidden;
    }

    body {
      font-family: 'Poppins', sans-serif;
      color: #fff7ef;
      background: #1d2443;
    }

    .beach-page {
      position: relative;
      min-height: 100svh;
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      padding: clamp(22px, 4vw, 44px) 16px 78px;
      isolation: isolate;
      overflow: hidden;
      background-image:
        linear-gradient(to bottom, rgba(15, 17, 36, 0.12), rgba(15, 17, 36, 0.58)),
        url('https://images.unsplash.com/photo-1507525428034-b723cf961d3e?q=90&w=2200&auto=format&fit=crop');
      background-size: cover;
      background-position: center center;
      background-repeat: no-repeat;
    }

    .beach-page::before {
      content: "";
      position: absolute;
      inset: 0;
      z-index: -1;
      background:
        radial-gradient(circle at 50% 34%, rgba(255, 198, 118, 0.24), transparent 28%),
        linear-gradient(to bottom, rgba(255,255,255,0.06), rgba(0,0,0,0.22));
      pointer-events: none;
    }

    .message-card {
      width: min(820px, calc(100% - 12px));
      padding: clamp(24px, 5vw, 56px);
      border-radius: clamp(24px, 4vw, 38px);
      border: 1px solid rgba(255, 255, 255, 0.26);
      background: rgba(14, 18, 39, 0.38);
      box-shadow: 0 28px 85px rgba(0, 0, 0, 0.32);
      backdrop-filter: blur(18px) saturate(1.15);
      -webkit-backdrop-filter: blur(18px) saturate(1.15);
      text-align: center;
      animation: floatCard 5.5s ease-in-out infinite;
    }

    .sweet-button {
      width: 62px;
      height: 62px;
      margin: 0 auto 20px;
      display: grid;
      place-items: center;
      border: 1px solid rgba(255, 255, 255, 0.34);
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.22);
      color: #fff;
      font-size: 30px;
      cursor: pointer;
      box-shadow:
        inset 0 0 20px rgba(255,255,255,0.18),
        0 12px 32px rgba(0,0,0,0.2);
      touch-action: manipulation;
      transition: transform 220ms ease, background 220ms ease, box-shadow 220ms ease;
    }

    .sweet-button:hover,
    .sweet-button:focus-visible {
      transform: translateY(-3px) scale(1.06) rotate(-4deg);
      background: rgba(255, 255, 255, 0.32);
      box-shadow:
        inset 0 0 24px rgba(255,255,255,0.22),
        0 16px 42px rgba(0,0,0,0.28);
      outline: none;
    }

    .message-text {
      max-width: 720px;
      margin: 0 auto;
      font-family: 'Playfair Display', serif;
      font-size: clamp(24px, 5vw, 44px);
      line-height: 1.24;
      letter-spacing: -0.03em;
      color: #fffaf2;
      text-shadow: 0 4px 24px rgba(0, 0, 0, 0.62);
      text-wrap: balance;
    }

    .tap-note {
      margin-top: 18px;
      font-size: clamp(12px, 2.7vw, 14px);
      letter-spacing: 0.03em;
      color: rgba(255, 250, 242, 0.9);
      text-shadow: 0 2px 14px rgba(0,0,0,0.45);
    }

    .signature {
      position: fixed;
      left: 50%;
      bottom: max(16px, env(safe-area-inset-bottom));
      transform: translateX(-50%);
      width: calc(100% - 32px);
      text-align: center;
      z-index: 3;
      font-size: clamp(11px, 3vw, 14px);
      font-weight: 500;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: rgba(255, 250, 242, 0.92);
      text-shadow: 0 3px 18px rgba(0, 0, 0, 0.7);
      pointer-events: none;
    }

    .sparkle {
      position: fixed;
      pointer-events: none;
      z-index: 20;
      font-size: 22px;
      animation: sparklePop 850ms ease forwards;
      will-change: transform, opacity;
    }

    @keyframes floatCard {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }

    @keyframes sparklePop {
      0% {
        opacity: 0;
        transform: translate(-50%, -50%) scale(0.5) rotate(0deg);
      }
      45% { opacity: 1; }
      100% {
        opacity: 0;
        transform: translate(-50%, -95px) scale(1.25) rotate(24deg);
      }
    }

    @media (max-width: 680px) {
      .beach-page {
        align-items: center;
        padding: 22px 12px 72px;
        background-position: center center;
      }

      .message-card {
        width: 100%;
        padding: 24px 18px;
        background: rgba(14, 18, 39, 0.46);
        backdrop-filter: blur(14px) saturate(1.1);
        -webkit-backdrop-filter: blur(14px) saturate(1.1);
      }

      .sweet-button {
        width: 56px;
        height: 56px;
        font-size: 27px;
        margin-bottom: 16px;
      }

      .message-text {
        font-size: clamp(23px, 7.3vw, 34px);
        line-height: 1.22;
      }
    }

    @media (prefers-reduced-motion: reduce) {
      .message-card,
      .sparkle {
        animation: none;
      }

      .sweet-button {
        transition: none;
      }
    }
  </style>
</head>
<body>
  <main class="beach-page" aria-label="Sunset beach care package message">
    <section class="message-card">
      <button class="sweet-button" type="button" aria-label="Send sweetness">🍬</button>

      <p class="message-text">
        I know you're in need of some sweetness (bec I'm not there), so here's a care package for you for whenever you get that infamous, rare, random and HARDCORE craving. Think of me when you're enjoying a delicious treat. I miss you and love you my angel. Love, Your Fiancé. PS. These treats are only meant to be enjoyed during times of craving, you will be penalised for breaking the rules.
      </p>

      <p class="tap-note">Tap the sweet above for a tiny sunset surprise.</p>
    </section>
  </main>

  <footer class="signature">Designed by Xena's Fiancé</footer>

  <script>
    (function () {
      const button = document.querySelector('.sweet-button');
      const treats = ['🍫', '🍓', '🍬', '🍪', '✨', '🌅', '💛'];

      function createSparkle(x, y) {
        const sparkle = document.createElement('span');
        sparkle.className = 'sparkle';
        sparkle.textContent = treats[Math.floor(Math.random() * treats.length)];
        sparkle.style.left = x + 'px';
        sparkle.style.top = y + 'px';
        document.body.appendChild(sparkle);

        window.setTimeout(function () {
          sparkle.remove();
        }, 900);
      }

      function burst() {
        const rect = button.getBoundingClientRect();
        const centerX = rect.left + rect.width / 2;
        const centerY = rect.top + rect.height / 2;

        for (let i = 0; i < 12; i += 1) {
          window.setTimeout(function () {
            createSparkle(
              centerX + Math.random() * 140 - 70,
              centerY + Math.random() * 60 - 30
            );
          }, i * 42);
        }
      }

      button.addEventListener('click', burst);
    })();
  </script>
</body>
</html>
