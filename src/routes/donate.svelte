<script>
  import { fade } from "svelte/transition";
  let innerHeight;
</script>

<style>
  .container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
    text-align: center;
    max-width: 60%;
    margin: 0 auto;
  }

  @media screen and (max-width: 600px) {
    div.container {
      max-width: 90%;
    }
  }

  h1,
  h3 {
    background: var(--bg-yellow);
    padding: 1rem;
  }
  h2 {
    color: var(--bg-yellow);
  }
</style>

<svelte:head>
  <title>Donate | Liwu</title>
</svelte:head>

<svelte:window bind:innerHeight />

<div class="container" style={`height: ${innerHeight - 50}px;`}>
  <div>
    <h1 in:fade={{ delay: 200 }}>Why Donate?</h1>
    <h3 in:fade={{ delay: 600 }}>
      Well, because you feel like it! Only give if the music touches you or a
      loved one. ❤️
    </h3>
    <h3 in:fade={{ delay: 1000 }}>
      Being an independent artist, I depend on my personal savings to take care
      of recording fees, music videos, promotion etc.
    </h3>
    <h2 in:fade={{ delay: 1800 }}>
      🆘
      <br />
      All Donations of no less that
      <strong>MK1,000</strong>
      may be made to Dali Mizaya through
      <strong>TNM Mpamba</strong>
      (+265 882 49 43 65) or
      <strong>Airtel Money</strong>
      (+265 997 24 54 28)
    </h2>
  </div>
</div>
