<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>É VÍRUS IRM</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html,
    body {
      width: 100%;
      height: 100%;
      background: #000000;
      overflow: hidden;
      font-family: Arial, Helvetica, sans-serif;
    }

    /* Tela de entrada */
    #entrada {
      position: fixed;
      inset: 0;
      width: 100%;
      height: 100%;
      background: #000000;
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 9999;
      cursor: pointer;
      opacity: 1;
      transition: opacity 0.6s ease;
    }

    #entrada.escondida {
      opacity: 0;
      pointer-events: none;
    }

    #mensagem {
      color: #ffffff;
      font-size: 1rem;
      font-weight: 400;
      text-align: center;
      letter-spacing: 0.5px;
    }

    /* Tela principal */
    #principal {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: #000000;
    }

    #texto {
      color: #ff0000;
      font-size: clamp(3rem, 8vw, 4rem);
      font-weight: 900;
      text-transform: uppercase;
      text-align: center;
      letter-spacing: 2px;
      user-select: none;
    }
  </style>
</head>

<body>

  <!-- Tela que pede o clique para liberar o áudio -->
  <div id="entrada">
    <div id="mensagem">Clique em qualquer lugar para entrar</div>
  </div>

  <!-- Conteúdo principal -->
  <main id="principal">
    <div id="texto">É VIRUS IRM</div>
  </main>

  <!-- Áudio em loop -->
  <audio id="audio" loop preload="auto">
    <source src="audio.mp3" type="audio/mpeg">

    <!--
      Para usar outro áudio, troque "audio.mp3" pela URL direta
      do arquivo de áudio, por exemplo:
      <source src="https://exemplo.com/audio.mp3" type="audio/mpeg">
    -->
  </audio>

  <script>
    const entrada = document.getElementById("entrada");
    const audio = document.getElementById("audio");

    entrada.addEventListener("click", async () => {
      try {
        // O clique do usuário libera a reprodução do áudio.
        audio.currentTime = 0;
        await audio.play();

        // Esconde a tela inicial suavemente.
        entrada.classList.add("escondida");

      } catch (erro) {
        console.error("Não foi possível iniciar o áudio:", erro);
      }
    }, { once: true });
  </script>

</body>
</html>
