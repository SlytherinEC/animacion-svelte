<script>
  import Character from "./lib/Character.svelte";

  let frame = 0; // Fotograma actual del personaje
  const frameCount = 17; // Total de fotogramas en el eje horizontal

  // Función para mover el personaje a la izquierda
  const moveLeft = () => {
    frame = (frame - 1 + frameCount) % frameCount;
  };

  // Función para mover el personaje a la derecha
  const moveRight = () => {
    frame = (frame + 1) % frameCount;
  };
</script>

<main>
  <div class="container">
    <!-- Sección de la pantalla -->
    <div class="screen">
      <Character {frame} />
    </div>

    <!-- Sección de los botones -->
    <div class="buttons">
      <button class="left" on:click={moveLeft}>Turn Left</button>
      <button class="up">Walk</button>
      <button class="down">Shoot</button>
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
  }

  .buttons {
    display: grid;
    grid-template-rows: repeat(3, 1fr);
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
    grid-row: 3;
    grid-column: 2;
  }
  .right {
    grid-row: 2;
    grid-column: 3;
  }
</style>
