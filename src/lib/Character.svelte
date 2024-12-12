<script>
  let frame = 0; // Controla el fotograma actual
  const frameCount = 17; // Cambia según la cantidad total de fotogramas que desees usar
  const frameWidth = 64; // Ajusta según el ancho de cada fotograma en píxeles
  const frameHeight = 64; // Ajusta según la altura de cada fotograma en píxeles
  const animationSpeed = 100; // Velocidad en ms por fotograma

  // Cambiar fotogramas automáticamente
  setInterval(() => {
    frame = (frame + 1) % frameCount;
  }, animationSpeed);
</script>

<div
  class="character"
  style="
--frame: {frame};
--frame-width: {frameWidth}px;
--frame-height: {frameHeight}px;
"
></div>

<style>
  .character {
    width: var(--frame-width, 64px); /* Ancho del contenedor */
    height: var(--frame-height, 64px); /* Altura del contenedor */
    background-image: url("./src/assets/starcraft-marine.png"); /* Ruta de la imagen */
    /* background-position: 0px 0px; Ajusta para centrar la porción deseada */
    /* background-size: auto; Mantén el tamaño original */
    background-position: calc(var(--frame) * -1 * var(--frame-width, 64px)) 0px;
    background-repeat: no-repeat; /* Evita que se repita la imagen */
    background-color: tomato;
  }
</style>
