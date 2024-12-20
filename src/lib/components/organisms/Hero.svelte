<script>
  import { Button, ArrowRight } from '$lib/index'

  export let items

  let currentImageIndex = 0

  import cocktail1 from '$lib/assets/cocktail1.png'
  import cocktail2 from '$lib/assets/cocktail2.png'
  import cocktail3 from '$lib/assets/cocktail3.png'

  const images = [cocktail1, cocktail2, cocktail3]

  function nextImage() {
    currentImageIndex = (currentImageIndex + 1) % images.length
  }

  function playAudio() {
    const audio = document.getElementById('snowGlobeSound')
    audio.play()
  }

  function stopAudio() {
    const audio = document.getElementById('snowGlobeSound')
    audio.pause()
    audio.currentTime = 0 // Reset the audio playback time
  }
</script>

<section>
  <div class="hero-wrapper">
    <div class="hero-content">
      <h1>
        {items[0].title}
        <Button
          variant="primary"
          title="Book Now"
          icon={ArrowRight}
          iconColor="#000000"
          size="lg"
        />
        <Button variant="primary" title="Shake It" size="lg" on:click={nextImage} />
      </h1>
      <p>{items[0].subtitle}</p>
    </div>
    <!-- svelte-ignore a11y-mouse-events-have-key-events -->
    <div
      class="snow-ball"
      role="button"
      tabindex="0"
      on:mouseover={playAudio}
      on:mouseout={stopAudio}
    >
      <div class="snow-globe">
        <div class="ball-container">
          <img src={images[currentImageIndex]} alt="Cocktail" class="cocktail-image" />
          <div class="snowman">
            <div class="scarf"></div>
            <div class="hat"></div>
          </div>
          <div class="trees"></div>
          <div class="trees2"></div>
          <div class="reflection"></div>
          <div class="snowfall">
            <div class="snowflake"></div>
            <div class="snowflake1"></div>
            <div class="snowflake2"></div>
          </div>
        </div>
        <div class="holder"></div>
      </div>
      <div class="shadow"></div>
    </div>
  </div>
  <audio id="snowGlobeSound" src="/src/lib/assets/snowglobe.mp3"></audio>
</section>

<style>
  section {
    display: flex;
    justify-content: center;
    align-items: center;
    background: linear-gradient(180deg, var(--cs-midnight-lagoon) 0%, var(--cs-sky-glacier) 100%);
    position: relative;
    height: 55vh;
    overflow: hidden;
  }

  .hero-wrapper {
    display: flex;
    align-items: flex-start;
    gap: 2rem;
    max-width: 100%;
  }

  .hero-content {
    padding: 1rem;
    margin-top: 3rem;
    font-weight: 700;
    color: #fff;
    max-width: 60%;
  }

  .snow-ball {
    position: relative;
    top: -15px;
    max-width: 40%;
  }

  .ball-container {
    position: relative;
    width: 370px;
    height: 370px;
    border-radius: 50%;
    border: 5px solid rgba(255, 255, 255, 0.3);
    overflow: hidden;
  }

  .ball-container:before {
    content: '';
    position: absolute;
    background-color: #f2f2f2;
    width: 350px;
    height: 110px;
    top: 275px;
  }

  .ball-container:after {
    content: '';
    position: absolute;
    background-color: white;
    border-radius: 50%;
    width: 324px;
    height: 40px;
    top: 255px;
    left: 23px;
  }

  .trees {
    position: absolute;
    background-color: white;
    width: 20px;
    height: 45px;
    border-radius: 10px;
    left: 50px;
    top: 210px;
    z-index: 3;
    box-shadow: 160px -10px white;
  }

  .trees:before {
    content: '';
    position: absolute;
    background-color: #625f56;
    width: 5px;
    border-radius: 5px 5px 0 0;
    height: 30px;
    left: 7.5px;
    top: 25px;
    box-shadow: 159.5px -10px #625f56;
  }

  .trees2 {
    position: absolute;
    height: 0;
    width: 0;
    border-left: 30px solid transparent;
    border-right: 30px solid transparent;
    border-bottom: 90px solid #97b2b0;
    top: 165px;
    left: 165px;
  }

  .trees2:before {
    content: '';
    position: absolute;
    height: 0;
    width: 0;
    border-left: 20px solid transparent;
    border-right: 20px solid transparent;
    border-bottom: 70px solid #62827c;
    top: 25px;
    left: 25px;
  }

  .trees2:after {
    content: '';
    position: absolute;
    height: 0;
    width: 0;
    border-left: 30px solid transparent;
    border-right: 30px solid transparent;
    border-bottom: 90px solid #62827c;
    left: -140px;
    top: 20px;
  }

  .snowman {
    position: absolute;
    border-radius: 50%;
    background-color: rgba(0, 0, 0, 0.1);
    width: 30px;
    height: 10px;
    top: 270px;
    left: 265px;
    z-index: 4;
  }

  .snowman:before {
    content: '';
    position: absolute;
    background-color: #f2f2f2;
    width: 30px;
    height: 30px;
    border-radius: 50%;
    top: -23px;
  }

  .snowman:after {
    content: '';
    position: absolute;
    background-color: #f2f2f2;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    top: -40px;
    left: 5px;
  }

  .scarf {
    position: absolute;
    width: 20px;
    height: 5px;
    background-color: #a5a696;
    top: -23px;
    left: 5px;
    border-radius: 10px;
    z-index: 5;
  }

  .scarf:before {
    content: '';
    position: absolute;
    width: 5px;
    height: 15px;
    background-color: #a5a696;
    left: 5px;
    border-radius: 10px;
  }

  .scarf:after {
    content: '';
    position: absolute;
    height: 0;
    width: 0;
    border-top: 3px solid transparent;
    border-bottom: 3px solid transparent;
    border-right: 10px solid #ca6702;
    top: -7px;
    left: -5px;
    transform: rotate(-10deg);
  }

  .hat {
    position: absolute;
    z-index: 6;
    border-top: 12px solid #60676a;
    border-right: 2px solid transparent;
    border-left: 2px solid transparent;
    border-bottom: 5px solid transparent;
    width: 15px;
    top: -52px;
    left: 5px;
  }

  .hat:before {
    content: '';
    position: absolute;
    background-color: #60676a;
    width: 25px;
    height: 3px;
    border-radius: 10px;
    left: -5px;
  }

  .hat:after {
    content: '';
    position: absolute;
    background-color: #60676a;
    border-radius: 50%;
    width: 3px;
    height: 3px;
    top: 5px;
    box-shadow: 5px 0 #60676a;
  }

  .reflection {
    position: absolute;
    z-index: 7;
    background-color: rgba(255, 255, 255, 0.2);
    width: 370px;
    height: 370px;
    border-radius: 50%;
    box-shadow: inset 5px 10px 20px rgba(255, 255, 255, 0.4);
  }

  .holder {
    position: absolute;
    z-index: 8;
    width: 255px;
    height: 20px;
    background-color: #625f56;
    top: 335px;
    left: 63px;
  }

  .holder:before {
    content: '';
    position: absolute;
    width: 255px;
    height: 0;
    border-right: 10px solid transparent;
    border-left: 10px solid transparent;
    border-bottom: 60px solid #7d7360;
    top: 20px;
    left: -10px;
  }

  .holder:after {
    content: '';
    position: absolute;
    width: 285px;
    height: 5px;
    border-radius: 20px;
    background-color: #625f56;
    top: 75px;
    left: -15px;
  }

  .shadow {
    position: absolute;
    width: 370px;
    height: 10px;
    border-radius: 20px;
    background-color: rgba(0, 0, 0, 0.2);
    top: 410px;
    left: 4px;
    transition: 0.3s;
  }

  .snowfall {
    position: absolute;
    z-index: 6;
  }

  .snowflake,
  .snowflake1,
  .snowflake2 {
    position: absolute;
    border-radius: 50%;
    background-color: white;
    width: 7px;
    height: 7px;
    filter: blur(1px);
    left: 50px;
    box-shadow:
      40px 40px white,
      -40px -40px white,
      80px 60px white,
      100px -70px white,
      110px -20px white,
      20px -20px white,
      120px 40px white,
      150px 10px white,
      180px 20px white,
      50px -60px white,
      100px 20px white,
      150px -80px white,
      170px -50px white,
      185px -70px white,
      190px 40px white,
      220px -10px white,
      230px -60px white,
      240px -30px white,
      250px 20px white,
      260px -80px white,
      -20px 20px white,
      10px 10px white,
      280px -40px white,
      300px -10px white,
      320px -100px white,
      290px -110px white,
      100px -100px white,
      80px -120px white;
    animation: fall 2.5s linear infinite;
  }

  .snowflake {
    left: 0;
  }

  .snowflake1 {
    top: -80px;
    left: 60px;
    animation-delay: 0.5s;
  }

  .snowflake2 {
    top: -70px;
    left: 100px;
    animation-delay: 1s;
  }

  .snow-ball:hover .snow-globe {
    animation: shake 0.3s ease;
    animation-iteration-count: 2;
  }

  @keyframes shake {
    0% {
      transform: rotate(0);
    }
    25% {
      transform: rotate(-30deg);
    }
    50% {
      transform: rotate(0);
    }
    75% {
      transform: rotate(30deg);
    }
    100% {
      transform: rotate(0);
    }
  }

  .snow-ball:hover .shadow {
    opacity: 0;
  }

  .snow-ball:hover .snowfall {
    animation: bounce 0.5s ease;
    animation-iteration-count: 2;
  }

  @keyframes bounce {
    0%,
    100% {
      transform: translateX(0);
    }
    10%,
    30%,
    50%,
    70%,
    90% {
      transform: translateX(-20px);
    }
    20%,
    40%,
    60%,
    80% {
      transform: translateX(20px);
    }
  }

  h1 {
    position: relative;
    display: inline-block;
    font-weight: 700;
    font-size: clamp(2.648rem, 6vw, 4.241rem);
    letter-spacing: -1px;
    animation: heading;
    animation-duration: 3s;
    animation-fill-mode: forwards;
  }

  @keyframes heading {
    0% {
      top: -200px;
    }
    100% {
      top: -2px;
    }
  }

  p {
    font-size: 1.5rem;
    font-weight: 700;
    letter-spacing: 0.2rem;
    padding: 0.5rem;
    text-transform: lowercase;
    position: relative;
    animation-name: content;
    animation-duration: 3s;
    animation-fill-mode: forwards;
  }

  @keyframes content {
    0% {
      left: -1000px;
    }
    100% {
      left: 10px;
    }
  }

  .cocktail-image {
    position: absolute;
    width: 150px; /* Smaller image size */
    height: auto;
    object-fit: cover;
    bottom: 6rem;
    left: 5rem;
  }

  @keyframes fall {
    0% {
      transform: translateY(-50px);
      opacity: 0.9;
    }
    100% {
      transform: translateY(380px);
      opacity: 0.2;
    }
  }
</style>
