<script>
  import Nav from "../components/Nav.svelte";

  export let segment;

  let alinafeYellow = "#F4B653";
  let windowHeight = "500px";
  let windowWidth;
  $: toggle = ["preview", "preorder", "about"].includes(segment);
  $: shapeHeightFactor = windowWidth < 600 ? 0.97 : 0.9;
  $: shapeHeight = toggle ? windowHeight : windowHeight * shapeHeightFactor;
  $: topShapeWidth = toggle ? windowWidth : windowWidth * 0.6;
  $: bottomShapeWidth = toggle ? windowWidth : windowWidth * 0.3;
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

  div#background-shape {
    position: absolute;
    z-index: -100;
    transition: 0.3s;
    left: 0;
    right: 0;
  }

  @media screen and (max-width: 600px) {
    div#background-shape {
      margin: 1em;
    }
  }
</style>

<svelte:window bind:innerHeight={windowHeight} bind:innerWidth={windowWidth} />

<div id="background-shape" style="margin: {toggle ? `0` : `3rem`};">
  <svg
    xmlns="http://www.w3.org/2000/svg"
    width={windowWidth}
    height={windowHeight}>
    <path
      d="M.165 {shapeHeight}V.62h{topShapeWidth}L{bottomShapeWidth}
      {shapeHeight}z"
      style="transition: 0.4s;"
      fill="#BD3B3B"
      fill-rule="evenodd" />
  </svg>
</div>

<Nav {segment} />

<main>
  <slot />
</main>
