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

  // Audio play and stop functions
  function playAudio() {
    const audio = document.getElementById('linkAudio')
    audio.play()
  }

  function stopAudio() {
    const audio = document.getElementById('linkAudio')
    audio.pause()
    audio.currentTime = 0
  }
</script>

<a
  data-sveltekit-reload
  {href}
  style="--clr: {color}; --font-size: {fontSize}; --filter: {filter}; --decoration: {decoration};"
  {...$$restProps}
  on:mouseover={playAudio}
  on:mouseout={stopAudio}
  on:focus={playAudio}
  on:blur={stopAudio}
>
  {title}
  {#if icon}
    <span>
      <svelte:component this={icon} width={iconWidth} height={iconHeight} svgColor={iconColor} />
    </span>
  {/if}
  <slot></slot>
</a>

<!-- Audio element -->
<audio id="linkAudio" src="/src/lib/assets/winterbells.mp3"></audio>

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
    transition:
      color 0.3s ease,
      filter 0.3s ease;
  }

  span {
    display: flex;
    align-items: center;
  }

  a:hover,
  a:focus {
    filter: brightness(1.2);
  }
</style>
