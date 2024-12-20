<script>
  import { onMount } from 'svelte';
  export let items;

  let enableBubbles = false;
  let curX = 0, curY = 0, tgX = 0, tgY = 0;

  onMount(() => {
    enableBubbles = true;

    // Initialize animation for bubble movement
    moveBubble();
    window.addEventListener('mousemove', handleMouseMove);
  });

  function handleMouseMove(event) {
    const { clientX, clientY } = event;
    tgX = clientX - window.innerWidth / 2; // Center-based movement
    tgY = clientY - window.innerHeight / 2;
  }

  function moveBubble() {
    curX += (tgX - curX) * 0.1; // Smooth interpolation
    curY += (tgY - curY) * 0.1;

    const bubble = document.querySelector('.interactive');
    if (bubble) {
      bubble.style.transform = `translate(${curX}px, ${curY}px)`;
    }

    requestAnimationFrame(moveBubble);
  }
</script>

<section>
  <div class="futuristic-bg">
    {#if enableBubbles}
      <svg xmlns="http://www.w3.org/2000/svg">
        <defs>
          <filter id="goo">
            <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
            <feColorMatrix in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -8" result="goo" />
            <feBlend in="SourceGraphic" in2="goo" />
          </filter>
        </defs>
      </svg>
      <div class="gradients-container" style="filter: url(#goo);">
        <div class="g1"></div>
        <div class="g2"></div>
        <div class="g3"></div>
        <div class="g4"></div>
        <div class="g5"></div>
        <div class="interactive"></div>
      </div>
    {/if}
  </div>
  <div class="hero-content">
    <h1>
      {items[0]?.title}
    </h1>
  </div>
</section>

<style>
  section {
    display: grid;
    place-items: center;
    position: relative;
    height: 75vh;
    overflow: hidden;
  }

  .futuristic-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      135deg, 
      rgba(255, 0, 255, 0.9), 
      rgba(0, 255, 255, 0.8), 
      rgba(0, 255, 0, 0.7),
      rgba(255, 255, 0, 0.6), 
      rgba(255, 105, 180, 0.7), 
      rgba(0, 0, 255, 0.8)
    );
    background-size: 400% 400%;
    animation: holographic-animation 12s linear infinite; /* Increased duration for slower movement */
    filter: brightness(1.3) contrast(1.5) saturate(1.8);
    z-index: -1;
  }

  .gradients-container {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: -1;
  }

  .gradients-container > div {
    position: absolute;
    background: radial-gradient(circle, rgba(255, 255, 255, 0.8) 0%, rgba(255, 255, 255, 0) 70%);
    mix-blend-mode: screen;
    animation: float 10s ease-in-out infinite;
  }

  .g1 {
    width: 400px;
    height: 400px;
    top: 10%;
    left: 20%;
  }

  .g2 {
    width: 300px;
    height: 300px;
    top: 50%;
    left: 70%;
  }

  .g3 {
    width: 500px;
    height: 500px;
    top: 30%;
    left: 50%;
  }

  .interactive {
    position: absolute;
    background: radial-gradient(circle, rgba(255, 0, 255, 0.8), rgba(255, 255, 255, 0) 50%);
    width: 150px;
    height: 150px;
    border-radius: 50%;
    pointer-events: none;
    transition: transform 0.1s linear;
  }

  h1 {
    font-size: clamp(2.648rem, 6vw, 4.241rem);
    color: #fff;
    text-shadow: 0 0 20px rgba(166, 58, 58, 0.8), 0 0 30px rgba(0, 212, 255, 0.6);
    animation: heading 3s forwards;
    padding: 4rem;
    text-align: center;
  }

  p {
    font-size: 1.5rem;
    font-weight: 700;
    letter-spacing: 0.2rem;
    padding: 0.5rem;
    text-transform: lowercase;
    text-shadow: 0 0 15px rgba(255, 255, 255, 0.8), 0 0 25px rgba(255, 0, 255, 0.6);
    position: relative;
    animation: content 3s forwards;
  }

  @keyframes holographic-animation {
    0% {
      background-position: 0% 0%;
    }
    50% {
      background-position: 100% 100%;
    }
    100% {
      background-position: 0% 0%;
    }
  }

  @keyframes heading {
    0% {
      top: -200px;
    }
    100% {
      top: -2px;
    }
  }

  @keyframes content {
    0% {
      left: -1000px;
    }
    100% {
      left: 0px;
    }
  }

  @keyframes float {
    0%, 100% {
      transform: translate(0, 0);
    }
    50% {
      transform: translate(10px, -10px);
    }
  }
</style>
