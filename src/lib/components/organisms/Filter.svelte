<script>
  import { page } from '$app/stores'
  import { onMount } from 'svelte'

  let filter = []
  export let cities = []

  onMount(() => {
    const urlSearchParams = new URLSearchParams($page.url.search)
    filter = urlSearchParams.getAll('locatie') || []
  })

  function applyFilter() {
    return function (event) {
      event.preventDefault()
      const formData = new FormData(event.target)
      const locatie = formData.get('locatie')
      const url = new URL(window.location)

      if (locatie) {
        url.searchParams.set('locatie', locatie)
      } else {
        url.searchParams.delete('locatie')
      }

      document.querySelector('section').classList.add('fade-out')
      setTimeout(() => {
        window.location = url
      }, 500) // Match the transition duration
    }
  }
</script>

<section>
  <form on:submit={applyFilter()}>
    <select name="locatie" id="locatie-select" tabindex="0">
      <option value="" selected={!filter}>Alle locaties</option>
      {#each cities as city}
        <option value={city} selected={filter === city}>
          {city}
        </option>
      {/each}
    </select>
    <button type="submit">Pas filter toe</button>
  </form>
</section>

<style>
  section {
    margin: 2rem 0;
    color: white;
    display: flex;
    flex-direction: column;
    gap: 1rem;
    opacity: 1;
    transform: scale(1);
    transition:
      opacity 0.5s ease-in-out,
      transform 0.5s ease-in-out;
  }

  section.fade-out {
    opacity: 0;
    transform: scale(0.55);
  }

  form {
    display: flex;
    gap: 1rem;
    transition: all 0.3s ease-in-out;
  }

  form:has(select:focus) {
    transform: scale(1.02);
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 0.8rem;
    padding: 0.5rem;
  }

  form select {
    padding: 0.5rem;
    border: none;
    background-color: var(--accent2-primary);
    color: var(--accent1-primary);
    text-transform: uppercase;
    border-radius: 0.8rem;
    transition:
      background-color 1.3s ease-in-out,
      color 1.3s ease-in-out;
  }

  form select:focus {
    background-color: var(--accent1-primary);
    color: var(--accent2-primary);
  }

  button {
    padding: 0.5rem 1rem;
    background-color: var(--accent1-primary);
    color: var(--accent2-primary);
    border: none;
    border-radius: 0.8rem;
    text-transform: uppercase;
    transition: transform 0.3s ease-in-out;
  }

  button:hover {
    transform: scale(1.05);
  }
</style>
