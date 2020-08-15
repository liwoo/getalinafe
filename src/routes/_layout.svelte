<script>
  import Nav from "../components/Nav.svelte";

  export let segment;
</script>

<style>
  main {
    position: relative;
    margin: 0 auto;
    box-sizing: border-box;
  }

  :global(:root) {
    --bg-yellow: #f4b653;
    --bg-red: #bd3b3b;
  }
</style>

<Nav {segment} />

<main>
  <slot />
</main>
