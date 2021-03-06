<script>
  import { fly, fade } from "svelte/transition";
  import BuyButton from "./BuyButton.svelte";
  export let scrollY;
  export let segment;
</script>

<svelte:window bind:scrollY />

<nav in:fly={{ delay: 200, y: -200 }}>
  <div>
    <a href="/">
      <svg width="32" height="21" xmlns="http://www.w3.org/2000/svg">
        <g stroke="#FFF" fill="none" fill-rule="evenodd">
          <path stroke-linecap="square" d="M31 11H2" />
          <path d="M8.045 1.91L1.5 11.401l6.545 8.507" />
        </g>
      </svg>
    </a>
  </div>
  <div
    style="width: 100%; text-align: center; display: flex; justify-content: center;"
  >
    {#if scrollY < 450}
      {#if segment === "preview"}
        <h1>Alinafe Tracklist</h1>
      {:else if segment === "donate"}
        <h1>Donate</h1>
      {:else if segment === "drugs-self-assessment"}
        <h1>Drug Self Assessment</h1>
      {:else if segment === "alcohol-self-assessment"}
        <h1>Alcohol Self Assessment</h1>
      {:else}
        <h1>About</h1>
      {/if}
    {:else}
      <div>
        <BuyButton />
      </div>
    {/if}
  </div>
  <div />
</nav>

<style>
  nav {
    display: flex;
    position: fixed;
    flex-direction: row;
    background-color: var(--bg-red);
    left: 0;
    right: 0;
    z-index: 100;
    justify-content: space-between;
    padding-left: 5%;
    padding-right: 5%;
    padding-top: 3rem;
    padding-bottom: 1rem;
    color: #fff;
    align-items: center;
  }

  nav h1 {
    font-size: medium;
  }
</style>
