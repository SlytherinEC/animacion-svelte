<script>
  export let frameX = 0; // Fotograma actual en el eje horizontal
  export let frameY = 0; // Fotograma actual en el eje vertical
  const frameWidth = 64; // Ancho de cada fotograma en píxeles
  const frameHeight = 64; // Alto de cada fotograma en píxeles
</script>

<div class="character-container">
  <div
    class="character"
    style="background-position: {-(frameX * frameWidth)}px {-(frameY * frameHeight)}px;"
  ></div>
</div>

<style>
  .character-container {
    position: relative;
    width: 60px; /* Ancho de un frame del sprite */
    height: 60px; /* Alto de un frame del sprite */
    margin: 128px 0 0 128px; /* Margen para centrar el sprite en la pantalla */
    overflow: hidden;
  }

  .character {
    width: 1051px; /* Ancho total del sprite */
    height: 866px; /* Alto total del sprite */
    background-image: url('/src/assets/starcraft-marine.png');
    background-repeat: no-repeat;
  }
</style>
