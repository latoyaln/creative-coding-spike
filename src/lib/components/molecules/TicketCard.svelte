<script>
  import { Filter, TicketCard, RetroBackground } from '$lib/index'
  export let itemCollection
  export let cities
</script>

<div class="main-layout">
  <RetroBackground />

  <div class="transition-overlay"></div>

  <section class="header">
    <h1>Tickets</h1>
    <Filter {cities} />
  </section>

  <section class="tickets">
    <TicketCard {itemCollection} />
  </section>
</div>

<style>
  .main-layout {
    position: relative;
    background: white;
    overflow: hidden;
    min-height: 100vh;
    color: hsl(0, 0%, 10%);
  }

  .header {
    margin: 7rem 4rem 4rem 4rem;
    position: relative;
    z-index: 2;
  }

  h1 {
    font-size: 3.5rem;
    color: hsl(0, 0%, 20%);
    text-shadow: 2px 2px hsl(45, 85%, 40%);
  }

  .tickets {
    display: flex;
    flex-wrap: wrap;
    gap: 1rem;
    justify-content: center;
    position: relative;
    z-index: 2;
  }
</style>
