<script>
  import Character from "./lib/Character.svelte";

  let frameX = 0; // Fotograma actual en el eje horizontal
  let frameY = 4; // Fotograma actual en el eje vertical
  const frameCountX = 17; // Total de fotogramas en el eje horizontal
  const frameCountY = 11; // Total de fotogramas en el eje vertical (caminar)

  let backgroundX = 0; // Posición del fondo en el eje X
  let backgroundY = 0; // Posición del fondo en el eje Y
  const backgroundStep = 5; // Cantidad de píxeles que el fondo se mueve por paso
  const animationSpeed = 100; // Velocidad de animación en ms
  let intervalId = null; // Intervalo para animar

  const stopAnimation = () => {
    clearInterval(intervalId);
  };

  // Función para mover el personaje a la izquierda
  const moveLeft = () => {
    stopAnimation();
      frameX = (frameX - 1 + frameCountX) % frameCountX;
  };

  // Función para mover el personaje a la derecha
  const moveRight = () => {
    stopAnimation();

      frameX = (frameX + 1) % frameCountX;
  };

  // Función para simular caminar
  const walk = () => {
    stopAnimation();

    intervalId = setInterval(() => {
      if (frameY === 0 || frameY > frameCountY) {
        frameY = 4;
      }
      frameY = frameY + 1; // Ciclo de 9 fotogramas para caminar

      // Ajustar la posición del fondo para simular el movimiento

      switch (frameX) {
        case 0:
        case 1:
          backgroundY += backgroundStep;
          break;
        case 2:
        case 3:
          backgroundY += backgroundStep;
          backgroundX -= 3;

          break;
        case 4:
        case 5:
          backgroundY += backgroundStep;
          backgroundX -= backgroundStep;
          break;
        case 6:
        case 7:
          backgroundY += 3;
          backgroundX -= backgroundStep;
          break;
        case 8:
        case 9:
          backgroundX -= backgroundStep;
          break;
        case 10:
        case 11:
          backgroundY -= 3;
          backgroundX -= backgroundStep;
          break;
        case 12:
        case 13:
          backgroundY -= backgroundStep;
          backgroundX -= backgroundStep;
          break;
        case 14:
        case 15:
          backgroundY -= backgroundStep;
          backgroundX -= 3;
        case 16:
          backgroundY -= backgroundStep;
          break;
      }
    }, animationSpeed);
  };

  // Función para simular disparar
  const shoot = () => {
    stopAnimation();
    intervalId = setInterval(() => {
      if (frameY >= 0 && frameY < 3) {
        frameY = frameY + 1;
      } else if (frameY >= 4) {
        frameY = 3;
      } else {
        frameY = 2;
      }
    }, animationSpeed);
  };
</script>

<main>
  <div class="container">
    <!-- Sección de la pantalla -->
    <div
      class="screen"
      style="background-position: {backgroundX}px {backgroundY}px;"
    >
      <Character {frameX} {frameY} />
    </div>

    <!-- Sección de los botones -->
    <div class="buttons">
      <button class="left" on:click={moveLeft}>Turn Left</button>
      <button class="up" on:click={walk}>Walk</button>
      <button class="down" on:click={shoot}>Shoot</button>
      <button class="right" on:click={moveRight}>Turn Right</button>
    </div>
  </div>
</main>

<style>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100vw;
    text-align: center;
  }

  .screen {
    width: 320px;
    height: 320px;
    margin-bottom: 20px;
    border: 5px solid #000;
    border-radius: 5px;
    background-image: url("/src/assets/ground.gif");
  }

  .buttons {
    display: grid;
    grid-template-rows: repeat(2, 1fr);
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
    width: 180px;
  }

  .buttons button {
    padding: 10px;
    font-size: 14px;
    cursor: pointer;
    border-radius: 5px;
    border: 1px solid #333;
    background-color: #f0f0f0;
  }

  .left {
    grid-row: 2;
    grid-column: 1;
  }
  .up {
    grid-row: 1;
    grid-column: 2;
  }
  .down {
    grid-row: 2;
    grid-column: 2;
  }
  .right {
    grid-row: 2;
    grid-column: 3;
  }
</style>
