<script>
  import {
    Hero,
    Reviews,
    TicketCarousel,
    HowItWorks,
    HeadLine,
    WhatWeDo,
  } from '$lib/index'
  export let items
  export let itemCollection
</script>

<svelte:head>
  <title>{items[0].title}</title>
</svelte:head>

<Hero {items} />
<Reviews {items} />
<HeadLine title="Explore Walks" />
<TicketCarousel {itemCollection} />
<HeadLine title="How It Works" />
<HowItWorks {items} />
<HeadLine title="What We Do" />
<WhatWeDo {items} />
