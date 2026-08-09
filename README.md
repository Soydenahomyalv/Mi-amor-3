<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Para ti 💗</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      min-height: 100vh;
      background: radial-gradient(circle at top, #30204f, #120d20 70%);
      color: white;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
    }

    .stars {
      position: fixed;
      inset: 0;
      pointer-events: none;
      background-image:
        radial-gradient(white 1px, transparent 1px),
        radial-gradient(white 1px, transparent 1px);
      background-size: 80px 80px, 120px 120px;
      opacity: 0.35;
    }

    .container {
      position: relative;
      z-index: 2;
      width: min(90%, 600px);
      text-align: center;
    }

    .screen {
      display: none;
      animation: aparecer 0.8s ease;
    }

    .screen.active {
      display: block;
    }

    h1 {
      font-size: 2.3rem;
      margin-bottom: 18px;
    }

    p {
      font-size: 1.1rem;
      line-height: 1.7;
      color: #eee;
      margin-bottom: 25px;
    }

    /* SOBRE */

    .envelope {
      width: 230px;
      height: 150px;
      margin: 35px auto;
      background: #d9a7ff;
      position: relative;
      cursor: pointer;
      border-radius: 8px;
      box-shadow: 0 15px 40px rgba(0,0,0,.4);
      transition: transform .3s;
    }

    .envelope:hover {
      transform: scale(1.05);
    }

    .envelope::before {
      content: "";
      position: absolute;
      inset: 0;
      background: #c38af0;
      clip-path: polygon(0 0, 50% 55%, 100% 0);
    }

    .heart {
      position: absolute;
      left: 50%;
      top: 52%;
      transform: translate(-50%, -50%);
      font-size: 45px;
      z-index: 2;
    }

    button {
      border: none;
      padding: 13px 25px;
      border-radius: 30px;
      background: #d9a7ff;
      color: #21122e;
      font-size: 1rem;
      font-weight: bold;
      cursor: pointer;
      transition: .3s;
    }

    button:hover {
      transform: scale(1.05);
      box-shadow: 0 0 20px rgba(217,167,255,.5);
    }

    .letter {
      background: rgba(255,255,255,.08);
      border: 1px solid rgba(255,255,255,.15);
      padding: 30px;
      border-radius: 20px;
      backdrop-filter: blur(10px);
      box-shadow: 0 15px 50px rgba(0,0,0,.35);
    }

    .final {
      font-size: 1.25rem;
    }

    .floating-heart {
      position: fixed;
      bottom: -30px;
      animation: subir 5s linear forwards;
      pointer-events: none;
      z-index: 5;
    }

    @keyframes aparecer {
      from {
        opacity: 0;
        transform: translateY(20px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    @keyframes subir {
      from {
        transform: translateY(0) rotate(0deg);
        opacity: 1;
      }

      to {
        transform: translateY(-110vh) rotate(360deg);
        opacity: 0;
      }
    }
  </style>
</head>

<body>

  <div class="stars"></div>

  <main class="container">

    <!-- PANTALLA 1 -->
    <section id="inicio" class="screen active">

      <h1>Hola, tú... 👀</h1>

      <p>
        Tengo algo preparado para ti.<br>
        Pero tendrás que abrirlo para descubrirlo. :3
      </p>

      <div class="envelope" onclick="abrirCarta()">
        <div class="heart">💌</div>
      </div>

      <p>Haz clic en el sobre ✨</p>

    </section>


    <!-- PANTALLA 2 -->
    <section id="carta" class="screen">

      <div class="letter">

        <h1>Para ti 💗</h1>

        <p>
          Puede que estemos separados por una pantalla,
          pero eso nunca ha impedido que una persona
          pueda convertirse en alguien realmente especial.
        </p>

        <p>
          Gracias por cada conversación, cada momento,
          cada risa y cada pequeño recuerdo que hemos creado.
        </p>

        <p>
          Y aunque esto sea solamente una pequeña página,
          la hice pensando especialmente en ti.
        </p>

        <button onclick="mostrarFinal()">
          Hay algo más... 🌙
        </button>

      </div>

    </section>


    <!-- PANTALLA 3 -->
    <section id="final" class="screen">

      <div class="letter">

        <h1>Encontraste el final 💗</h1>

        <p class="final">
          Si llegaste hasta aquí, solamente quería decirte
          que eres alguien muy especial para mí.
        </p>

        <p class="final">
          Gracias por existir en mi pequeño universo. 🌌
        </p>

        <p class="final">
          Con cariño,<br>
          <strong>Joss :3</strong>
        </p>

        <button onclick="lluviaDeCorazones()">
          ✨ Una última sorpresa
        </button>

      </div>

    </section>

  </main>


  <script>

    function cambiarPantalla(actual, siguiente) {
      document.getElementById(actual).classList.remove("active");
      document.getElementById(siguiente).classList.add("active");
    }

    function abrirCarta() {
      cambiarPantalla("inicio", "carta");
    }

    function mostrarFinal() {
      cambiarPantalla("carta", "final");
      lluviaDeCorazones();
    }

    function lluviaDeCorazones() {

      for (let i = 0; i < 25; i++) {

        const heart = document.createElement("div");

        heart.className = "floating-heart";

        heart.innerHTML =
          ["💗", "💖", "💕", "❤️", "✨"][Math.floor(Math.random() * 5)];

        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize = (15 + Math.random() * 25) + "px";
        heart.style.animationDuration = (3 + Math.random() * 4) + "s";

        document.body.appendChild(heart);

        setTimeout(() => {
          heart.remove();
        }, 7000);
      }
    }

  </script>

</body>
</html>
