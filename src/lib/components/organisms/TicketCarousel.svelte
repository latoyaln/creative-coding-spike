<script>
  import { TicketCard, Link, ArrowRightShort, ArrowLeftShort, ArrowRight, Button } from '$lib'
  import { onMount } from 'svelte'
  export let itemCollection

  let activeInd = 0

  function scrollLeftOrRight(direction) {
    const carouselElement = document.querySelector('.card-container')
    const cardElement = document.querySelector('.ticket-card')
    const offsetWidth = activeInd >= 3 ? carouselElement.offsetWidth : cardElement.offsetWidth
    const scrollXBy = direction === 'left' ? -300 : 300
    const scrollWidth = carouselElement.scrollWidth
    const scrollLeft = carouselElement.scrollLeft

    if (direction === 'left' && scrollLeft === 0) {
      carouselElement.scrollTo({
        left: activeInd === 0 ? scrollWidth - carouselElement.offsetWidth : scrollXBy,
        behavior: 'smooth',
      })
    } else if (direction === 'right' && Math.abs(scrollWidth - (scrollLeft + offsetWidth)) <= 1) {
      carouselElement.scrollTo({
        left: 0,
        behavior: 'smooth',
      })
    } else {
      carouselElement.scrollBy({
        left: scrollXBy,
        behavior: 'smooth',
      })
    }
    updateActiveIndicator(direction)
    updateProgressBar()
  }

  function updateActiveIndicator(direction) {
    if (direction === 'right') {
      activeInd =
        activeInd >= itemCollection.componentsCollection.items.length - 1 ? 0 : activeInd + 1
    } else {
      activeInd =
        activeInd === 0 ? itemCollection.componentsCollection.items.length - 1 : activeInd - 1
    }
  }

  function scrollToSlide(index) {
    activeInd = index
    const carouselElement = document.querySelector('.card-container')
    const offsetWidth = carouselElement.offsetWidth
    carouselElement.scrollTo({
      left: offsetWidth * index,
      behavior: 'smooth',
    })

    updateProgressBar()
  }

  function updateProgressBar() {
    const progressBar = document.querySelector('.carousel-progress-bar')
    if (progressBar) {
      progressBar.style.width = `${((activeInd + 1) / itemCollection.componentsCollection.items.length) * 100}%`
    }
  }

  onMount(() => {
    const carouselElements = document.querySelectorAll('.carousel-arrow, .carousel-progress-bar')
    carouselElements.forEach((element) => {
      element.hidden = false
    })
  })
</script>

{#if itemCollection}
  <section>
    <button
      type="button"
      class="carousel-arrow carousel-arrow--prev"
      on:click={() => scrollLeftOrRight('left')}
      title="prev slide"
      hidden
    >
      <ArrowLeftShort />
    </button>

    <div class="card-container">
      <TicketCard {itemCollection} />
    </div>

    <button
      class="carousel-arrow carousel-arrow--next"
      on:click={() => scrollLeftOrRight('right')}
      title="next slide"
      hidden
    >
      <ArrowRightShort />
    </button>

    <div class="carousel-progress">
      <div class="carousel-progress-bar"></div>
    </div>
  </section>
  <div class="carousel-title">
    <Link
      href="/walks-overview"
      title="see all walks"
      size="m"
      fontSize="var(--fs-lg)"
      color="var(--cs-midnight-lagoon"
      icon={ArrowRight}
      iconColor="var(--cs-midnight-lagoon)"
    />
  </div>
{/if}

<style>
  .carousel-title {
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 3rem 2rem;
    background-color: var(--cs-sky-glacier);
  }

  section {
    --arrow-size: 40px;
    width: 100%;
    position: relative;
    overflow: hidden;
    background-color: var(--cs-sky-glacier);
  }

  .card-container {
    gap: 8px;
    width: 100%;
    display: flex;
    margin: 0 0 0 2rem;
    overflow-x: auto;
    overflow-y: hidden;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
  }

  .card-container::-webkit-scrollbar {
    display: none;
  }

  .carousel-arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    justify-content: center;
    top: 0;
    bottom: 64px;
    background-color: var(--cs-tidepool-blue);
    color: var(--cs-sky-glacier);
    margin-block: auto;
    height: fit-content;
    width: 48px;
    border: none;
    border-radius: 50%;
    cursor: pointer;
    opacity: 0.5;
    transition:
      opacity 100ms,
      box-shadow 0.3s;
    z-index: 2;
  }

  .carousel-arrow:hover,
  .carousel-arrow:focus {
    opacity: 1;
    box-shadow: 0 0 15px var(--cs-sky-dusty);
  }

  .carousel-progress {
    position: absolute;
    bottom: 0;
    left: 1;
    width: 100%;
    height: 5px;
    background-color: var(--cs-sky-dusty);
    overflow: hidden;
  }

  .carousel-progress-bar {
    height: 100%;
    width: 0%;
    background-color: var(--cs-midnight-lagoon);
    box-shadow: 0 0 10px var(--cs-midnight-lagoon);
    transition: width 0.3s ease-out;
  }
</style>
