# si
si
<!DOCTYPE html>
<html lang="es">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>¿Quieres ser mi San Valentín?</title>

  <style>
    body {
      font-family: Arial, sans-serif;
      background: linear-gradient(135deg, #ff9a9e, #fecfef);
      color: white;
      margin: 0;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }

    .container {
      background: rgba(255, 255, 255, 0.2);
      padding: 30px;
      border-radius: 25px;
      text-align: center;
      width: 90%;
      max-width: 400px;
      z-index: 2;
    }

    h1 {
      font-size: 2.2em;
      margin-bottom: 25px;
    }

    .buttons {
      display: flex;
      gap: 15px;
      justify-content: center;
    }

    button {
      font-size: 1.4em;
      padding: 15px 30px;
      border-radius: 50px;
      border: none;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s;
    }

    #yes {
      background: #ff6b6b;
      color: white;
    }

    #no {
      background: #4ecdc4;
      color: white;
    }

    .hidden {
      display: none;
    }

    .congrats {
      font-size: 1.6em;
      animation: fadeIn 1.5s ease forwards;
    }

    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: scale(0.9);
      }

      to {
        opacity: 1;
        transform: scale(1);
      }
    }

    .hearts {
      position: absolute;
      inset: 0;
      pointer-events: none;
    }

    .heart {
      position: absolute;
      font-size: 2em;
      animation: float 6s linear infinite;
    }

    @keyframes float {
      from {
        transform: translateY(100vh);
      }

      to {
        transform: translateY(-100vh);
      }
    }
  </style>
</head>

<body>

  <div class="hearts" id="hearts"></div>

  <div class="container">
    <h1 id="question">¿Quieres ser mi San Valentín?</h1>

    <div class="buttons" id="buttons">
      <button id="yes">Sí 💖</button>
      <button id="no">No 🙄</button>
    </div>

    <div class="congrats hidden" id="congrats">
      Nos vemos a las 13:30 en tu puerta 🏡
      Te amo ❤️
    </div>
  </div>

  <script>
    const yes = document.getElementById("yes");
    const no = document.getElementById("no");
    const q = document.getElementById("question");
    const c = document.getElementById("congrats");
    const b = document.getElementById("buttons");
    const hearts = document.getElementById("hearts");
    let scale = 1;

    function heart() {
      const h = document.createElement("div");
      h.className = "heart";
      h.textContent = "❤️";
      h.style.left = Math.random() * 100 + "%";
      hearts.appendChild(h);
    }
    for (let i = 0; i < 15; i++) heart();
    no.addEventListener("click", () => {
      if (navigator.vibrate) navigator.vibrate(100);
      scale += 0.3;
      yes.style.transform = `scale(${scale})`;
    });
    no.addEventListener("touchstart", () => {
      const x = Math.random() * (window.innerWidth - 100);
      const y = Math.random() * (window.innerHeight - 100);
      no.style.position = "absolute";
      no.style.left = x + "px";
      no.style.top = y + "px";
    });
    yes.addEventListener("click", () => {
      if (navigator.vibrate) navigator.vibrate([200, 100, 200]);
      q.classList.add("hidden");
      b.classList.add("hidden");
      c.classList.remove("hidden");
      for (let i = 0; i < 40; i++) heart();
    });
  </script>

</body>

</html>
