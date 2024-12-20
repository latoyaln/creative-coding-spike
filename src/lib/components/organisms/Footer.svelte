<script>
  import { Link, CocktailIcon, Button, ArrowRight } from '$lib/index'
  import logo from '$lib/assets/logo.webp'
  import nix from '$lib/assets/nix-18.webp'
  export let footerItems
</script>

<footer>
  <!-- LOGO -->
  <img src={logo} height="50" width="50" alt="onder navigatie" />

  <section>
    <!-- NIEUWSBRIEF -->
    <!-- form veranderen met molecule van patrick -->
    <form>
      <legend>{footerItems[0].newsletterTitle}</legend>
      <p>{footerItems[0].newsLetterDescription}</p>

      <label>
        Email*
        <!-- input veranderen met atom van patrick -->
        <input type="email" name="email" placeholder={footerItems[0].placeholderText} required />
      </label>
      <Button
        type="submit"
        variant="primary"
        title="Abonneer"
        icon={ArrowRight}
        iconColor="var(--btn-primary-text-clr)"
        size="sm"
      />
    </form>

    <!-- Navigatie -->
    <nav>
      <ul>
        <h4>Navigatie</h4>
        <!-- moet later dynamische content zijn in contentful -->
        {#each footerItems[0].footerLinksCollection.items as item}
          <li>
            <Link
              href={item.slug}
              aria-label={item.title}
              title={item.title}
              fontSize="1rem"
              color="var(--txt-primary-clr)"
              decoration="underline"
            ></Link>
          </li>
        {/each}
      </ul>

      <ul>
        <h4>Bronnen</h4>
        <!-- moet later dynamische content zijn in contentful -->
        {#each footerItems[0].footerLinksCollection.items as item}
          <!-- moet later andere links zijn -->
          <li>
            <Link
              href={item.slug}
              aria-label={item.title}
              title={item.title}
              fontSize="1rem"
              color="var(--txt-primary-clr)"
              decoration="underline"
            ></Link>
          </li>
        {/each}
      </ul>

      <ul>
        <h4>Social</h4>
        <!-- moet later dynamische content zijn in contentful -->
        {#each footerItems[0].socialMediaIconsCollection.items as item}
          <li>
            <Link
              href={item.url}
              fontSize="1rem"
              aria-label={item.title}
              color="var(--txt-primary-clr)"
              decoration="underline"
            >
              {item.assetCollection.items[0].title}
            </Link>
          </li>
        {/each}
      </ul>

      <ul class="review">
        <h4>Review ons</h4>
        <!-- moet later dynamische content zijn in contentful -->
        <li>
          <form
            aria-label="review ons op Tripadvisor"
            class="feedback"
            action="https://www.tripadvisor.nl/Attraction_Review-g188590-d25182767-Reviews-Cocktail_Walk-Amsterdam_North_Holland_Province.html"
          >
            <!-- mogelijk nog een ander icon op de deze knoppen -->
            <Button
              type="submit"
              variant="primary"
              title="Tripadvisor"
              icon={CocktailIcon}
              iconColor="var(--btn-primary-text-clr)"
              size="sm"
            />
          </form>
        </li>
        <li>
          <form
            class="feedback"
            aria-label="review ons op Trustpilot"
            action="https://uk.trustpilot.com/review/wogoamsterdam.com?utm_medium=trustbox&utm_source=TrustBoxReviewCollector"
          >
            <Button
              type="submit"
              variant="primary"
              title="Trustpilot"
              icon={CocktailIcon}
              iconColor="var(--btn-primary-text-clr)"
              size="sm"
            />
          </form>
        </li>
      </ul>
    </nav>
  </section>

  <div class="line"></div>

  <!-- COPYRIGHT -->
  <div>
    <!-- jaartal moet later dynamische content zijn in contentful -->
    <p><small>© 2024 WOGO Amsterdam. Alle rechten voorbehouden.</small></p>
    <img src={nix} height="30" width="90" alt="nix 18 is niet voor niks" />
  </div>
</footer>

<style>
  legend,
  h4 {
    font-family: 'LuloClean', sans-serif;
  }
  footer {
    width: 100%;
    padding: 2em 5vw;
    display: flex;
    flex-direction: column;
    gap: 2em;
    background-color: var(--accent1-tertiary);
    color: var(--txt-tertiary-clr);
  }
  h4 {
    font-size: 1em;
    line-height: 2em;
    margin-bottom: 0.5em;
  }
  legend {
    font-size: 1.7em;
  }
  form {
    display: grid;
    gap: 1em;
    width: 100%;

    @media screen and (min-width: 48em) {
      width: 30rem;
    }
  }
  .feedback {
    margin-top: 1rem;
    width: 100%;
  }
  input:where([type='email']) {
    display: block;
    margin: 1rem 0;
    font-size: 1rem;
    font-family: inherit;
    padding: 1rem;
    width: 100%;
    border: 0;
    background-color: var(--accent2-quaternary);
    border-radius: 10px;
  }

  input::placeholder {
    color: var(--accent1-tertiary);
  }

  nav {
    display: flex;
    flex-wrap: wrap;
    gap: 2em 5em;
    justify-content: space-evenly;

    @media screen and (min-width: 48em) {
      flex-wrap: nowrap;
    }
  }

  section {
    display: flex;
    flex-direction: column;
    gap: 2em;

    @media screen and (min-width: 48em) {
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      justify-content: center;
      gap: 5em;
      width: 100%;
    }
  }

  ul {
    list-style: none;
  }

  div {
    display: flex;
    justify-content: space-evenly;
    align-items: center;
  }

  .line {
    width: 90%;
    margin: 0 auto;
    height: 0.5px;
    border: 0;
    background-color: var(--accent2-quaternary);
  }
</style>
