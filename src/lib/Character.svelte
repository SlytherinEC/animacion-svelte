<script>
  let frame = 0; // Controla el fotograma actual
  const frameCount = 17; // Número total de fotogramas
  const frameWidth = 64; // Ancho de cada fotograma en píxeles
  const frameHeight = 64; // Altura de cada fotograma en píxeles
  const animationSpeed = 200; // Velocidad de la animación en milisegundos

  // Cambiar fotogramas automáticamente
  const interval = setInterval(() => {
    frame = (frame + 1) % frameCount;
    console.log(frame);
  }, animationSpeed);

  // Limpieza del intervalo cuando el componente se destruya
  import { onDestroy } from "svelte";
  onDestroy(() => {
    clearInterval(interval);
  });
</script>

<!-- Aquí se usan las variables directamente en el atributo style -->
<div
  class="character"
  style="
    width: {frameWidth}px;
    height: {frameHeight}px;
    background-image: url('/src/assets/starcraft-marine.png');
    background-position: {-(frame * frameWidth)}px 0px;
    background-repeat: no-repeat;
  "
></div>

<style>
  .character {
    background-color: tomato;
    margin: 128px auto;
  }
</style>
