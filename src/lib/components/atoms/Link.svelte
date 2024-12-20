<script>
  export let color = ''
  export let href = ''
  export let title = ''
  export let icon = null
  export let iconWidth = '24px'
  export let iconHeight = '24px'
  export let iconColor = ''
  export let filter = ''
  export let fontSize = ''
  export let decoration = ''
</script>

<a
  data-sveltekit-reload
  {href}
  style="--clr: {color}; --font-size: {fontSize}; --filter: {filter}; --decoration: {decoration};"
  {...$$restProps}
>
  {title}
  {#if icon}
    <span>
      <svelte:component this={icon} width={iconWidth} height={iconHeight} svgColor={iconColor} />
    </span>
  {/if}
  <slot></slot>
</a>

<style>
  a {
    display: flex;   
    line-height: 1.5em; 
    align-items: center;
    text-decoration: none;    
    color: var(--clr);
    font-size: var(--font-size);
    white-space: nowrap;
    filter: var(--filter);
    text-transform: none;
    text-decoration: var(--decoration);
    font-weight: 300;
  }

  span {
    display: flex;
    align-items: center;
  }
</style>
