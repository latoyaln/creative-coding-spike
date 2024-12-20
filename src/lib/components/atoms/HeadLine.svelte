<script>
  export let title = ''
</script>

<h2 class="glitch">{title}</h2>

<style>
  h2 {
    display: flex;
    justify-content: center;
    align-items: center;
    text-transform: uppercase;
    font-size: var(--fs-xl);
    color: var(--cs-midnight-lagoon);
    background-color: var(--cs-sky-glacier);
    padding: 1em;
    position: relative;
    overflow: hidden;
  }

  /* The base glitch effect */
  .glitch::before,
  .glitch::after {
    content: attr(data-text);
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    color: var(--cs-midnight-lagoon);
    z-index: -1;
  }

  .glitch::before {
    animation: glitch 1s infinite linear alternate-reverse;
    clip-path: polygon(0 2%, 100% 2%, 100% 14%, 0 14%);
  }

  .glitch::after {
    animation: glitch 1.2s infinite linear alternate-reverse;
    clip-path: polygon(0 85%, 100% 85%, 100% 100%, 0 100%);
    color: var(--cs-sky-glacier);
  }

  @keyframes glitch {
    0% {
      transform: translate(0);
    }
    20% {
      transform: translate(-5px, -5px);
    }
    40% {
      transform: translate(5px, 5px);
    }
    60% {
      transform: translate(-5px, 5px);
    }
    80% {
      transform: translate(5px, -5px);
    }
    100% {
      transform: translate(0);
    }
  }
</style>
