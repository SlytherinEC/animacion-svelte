<script>
  export let frame = 0; // Recibir el fotograma actual desde App.svelte
  const frameWidth = 64; // Ancho de cada fotograma en píxeles
</script>

<div class="character-container">
  <div
    class="character"
    style="background-position: {-(frame * frameWidth)}px 0px;"
  ></div>
</div>

<style>
  .character-container {
    position: relative;
    width: 64px; /* Ancho de un frame del sprite */
    height: 64px; /* Alto de un frame del sprite */
    overflow: hidden;
  }

  .character {
    width: 1051px; /* Ancho total del sprite */
    height: 866px; /* Alto total del sprite */
    background-image: url('/src/assets/starcraft-marine.png');
    background-repeat: no-repeat;
  }
</style>
