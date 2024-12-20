<script>
  import { Image, RouteIcon, CocktailIcon, Button } from '$lib/index'
  export let itemCollection
  const items = itemCollection.componentsCollection.items
</script>

{#each items as item}
  <article class="ticket-card">
    <div class="image-container">
      <Image
        src={item.image.url}
        alt={item.image.title}
        brdRadius="var(--radius-lg)"
        opacity="0.6"
        loading="lazy"
      />

      <div class="top-right-wrapper">
        <Button type="button" variant="cs" title="Boek Nu" size="m" />
      </div>
    </div>

    <div>
      <h3>{item.title}</h3>
      <p>
        <span><RouteIcon width="25" height="25" fill="#fff" /></span>
        {item.location}
      </p>

      <p>
        <span><CocktailIcon width="25" height="25" fill="#fff" /></span>
        {item.cocktailDescription}
      </p>

      <p>{item.price}</p>
    </div>
  </article>
{/each}

<style>
  article {
    min-width: 320px;
    height: 400px;
    border-radius: var(--radius-lg);
    background-color: rgba(37, 98, 121, 0.8);
    color: #fff;
    scroll-snap-align: start;
    scroll-snap-align: center;
  }

  .image-container {
    position: relative;
    background: linear-gradient(137deg, rgba(206, 101, 56, 1) 0%, rgba(32, 22, 17, 1) 0%);
  }

  .top-right-wrapper {
    position: absolute;
    top: 1em;
    right: 1em;
  }

  div:nth-of-type(2) {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    padding: 1em;
  }

  h3 {
    font-size: var(--fs-lg);
  }
  p {
    display: flex;
    align-items: center;
    gap: 1rem;
    font-size: var(--fs-md);
  }

  @media screen and (min-width: 48em) {
    article {
      min-width: 500px;
      height: 550px;
    }

    div:nth-of-type(2) {
      padding: 1em 2em;
    }

    h3 {
      font-size: var(--fs-lg);
    }

    p {
      font-size: var(--fs-md);
    }
  }
</style>
