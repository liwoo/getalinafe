<script>
  let innerHeight;
</script>

<svelte:window bind:innerHeight />

<div class="container" style={`height: ${innerHeight - 50}px;`}>
  <slot />
</div>

<style>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
    max-width: 60%;
    text-align: center;
    margin: 0 auto;
  }

  @media screen and (max-width: 600px) {
    div.container {
      max-width: 90%;
    }
  }
</style>
