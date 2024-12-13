<script>
  import Character from "./lib/Character.svelte";
</script>

<main>
  <div class="container">
    <!-- Sección de la pantalla -->
    <div class="screen">
      <Character />
    </div>

    <!-- Sección de los botones -->
    <div class="buttons">
      <button class="left">Turn Left</button>
      <button class="up">Walk</button>
      <button class="down">Shoot</button>
      <button class="right">Turn Right</button>
    </div>
  </div>
</main>

<style>
  /* Contenedor principal centrado */
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100vh;
    width: 100vw;
    text-align: center;
  }

  /* Sección de la pantalla */
  .screen {
    width: 320px; /* Ancho de la pantalla */
    height: 320px; /* Alto de la pantalla */
    margin-bottom: 20px; /* Separación entre la pantalla y los botones */
  }

  /* Sección de los botones */
  .buttons {
    display: grid;
    grid-template-rows: repeat(3, 1fr); /* Tres filas */
    grid-template-columns: repeat(3, 1fr); /* Tres columnas */
    gap: 10px;
    width: 180px; /* Ancho total de los botones */
  }

  /* Estilo de los botones */
  .buttons button {
    padding: 10px;
    font-size: 14px;
    cursor: pointer;
    border-radius: 5px;
    border: 1px solid #333;
    background-color: #f0f0f0;
  }

  /* Posicionamiento de los botones en forma de cruceta */
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
