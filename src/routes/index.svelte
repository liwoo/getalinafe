<script>
  import { onMount } from "svelte";
  import { scale, fade } from "svelte/transition";
  let windowHeight;
  let windowWidth;
  $: alinafeArtWidth =
    windowWidth < 850 ? (windowWidth < 450 ? 350 : 400) : 600;
  let showImage = false;
  onMount(() => {
    setTimeout(() => {
      showImage = true;
    }, 2500);
    document.getElementsByTagName("html")[0].className = "";
  });
</script>

<svelte:head>
  <title>Alinafe by Liwu</title>
</svelte:head>

<svelte:window bind:innerHeight={windowHeight} bind:innerWidth={windowWidth} />

<main>
  {#if showImage}
    <div class="options" in:fade>
      <a href="alcohol-self-assessment"> Take the Alcohol Self Assessment </a>
      <a href="drugs-self-assessment"> Take the Drugs Self Assessment Test </a>
    </div>
  {/if}
</main>

<style>
  a {
    background: #282828;
    padding: 1rem 1.5rem;
    height: 2rem;
    color: white;
    text-decoration: none;
    border-radius: 0.5rem;
  }

  main {
    height: 80vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .options {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin: 0rem 1rem;
  }
  @media screen and (max-width: 850px) {
    .options {
      height: 20vh;
      flex-direction: column;
      justify-content: space-around;
    }
  }
</style>
