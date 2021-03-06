<script>
  import Nav from "../components/Nav.svelte";
  import AltNav from "../components/AltNav.svelte";
  import About from "./about.svelte";
  import { fade } from "svelte/transition";

  export let segment;

  let alinafeYellow = "#F4B653";
  let windowHeight = "500px";
  let windowWidth;
  let scrollY;

  $: toggle = [
    "preview",
    "preorder",
    "about",
    "track",
    "donate",
    "drugs-self-assessment",
    "alcohol-self-assessment",
  ].includes(segment);
  $: shapeHeightFactor = windowWidth < 600 ? 0.96 : 0.9;
  $: shapeHeight = toggle ? windowHeight : windowHeight * shapeHeightFactor;
  $: topShapeWidth = toggle ? windowWidth : windowWidth * 0.6;
  $: bottomShapeWidth = toggle ? windowWidth : windowWidth * 0.3;
</script>

<svelte:window
  bind:innerHeight={windowHeight}
  bind:innerWidth={windowWidth}
  bind:scrollY
/>

<div
  id="background-shape"
  transition:fade
  style="--window-height: {windowHeight}px; --offset-width: {windowWidth *
    0.2}px"
  class:alt={toggle}
/>
{#if toggle}
  <AltNav {segment} />
{:else}
  <Nav {segment} />
{/if}

<main>
  {#if toggle}
    <div class="container" class:padded={toggle}>
      <slot />
    </div>
  {:else}
    <slot />
  {/if}
</main>

<style>
  main {
    position: relative;
    margin: 0 auto;
    box-sizing: border-box;
    display: flex;
    justify-content: center;
  }

  div.container {
    margin: 1rem;
  }

  :global(:root) {
    --bg-yellow: #f4b653;
    --bg-red: #bd3b3b;
  }

  div#background-shape {
    position: absolute;
    z-index: -100;
    transition: 0.3s;
    top: 0;
    bottom: 0;
    width: calc(50% - var(--offset-width));
    border-width: calc(var(--window-height) - 6rem)
      calc(var(--offset-width) + 10rem) 0 0;
    margin: 3rem;
    border-style: solid;
    border-color: var(--bg-red) transparent transparent transparent;
  }

  div#background-shape.alt {
    width: 100%;
    border-width: var(--window-height) 0 0 0;
    margin: 0;
  }

  @media screen and (max-width: 600px) {
    div#background-shape {
      border-width: calc(var(--window-height) - 2rem)
        calc(var(--offset-width) + 5rem) 0 0;
      margin: 1em;
    }
  }

  @media screen and (max-width: 750px) {
    div.container {
      width: 90%;
    }
  }

  :global(html) {
    background-color: var(--bg-yellow);
    transition-delay: 0s;
  }

  :global(html).red-bg {
    background-color: var(--bg-red);
    transition-delay: 1s;
  }
</style>
