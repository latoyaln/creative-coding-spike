<script>
  export let isSnowing = false
</script>

<div class="snow-overlay" style="display: {isSnowing ? 'block' : 'none'};">
  {#each Array(100) as _, i}
    <div
      class="snowflake"
      style="left: {Math.random() * 100}%; font-size: {Math.random() * 2 +
        0.5}em; animation-delay: {Math.random() * 5}s;"
    >
      ❄
    </div>
  {/each}
</div>

<style>
  .snow-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 1000;
    overflow: hidden;
  }

  .snowflake {
    position: absolute;
    top: -10px;
    color: white;
    font-size: 1em;
    animation: fall linear infinite;
    opacity: 0.8;
  }

  @keyframes fall {
    0% {
      transform: translateY(0);
    }
    100% {
      transform: translateY(100vh);
    }
  }
</style>
