<script>
  import { fade } from "svelte/transition";
  import Container from "../components/Container.svelte";
</script>

<svelte:head>
  <title>Donate | Liwu</title>
</svelte:head>

<Container>
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
    <h4 in:fade={{ delay: 1800 }}>
      🆘
      <br />
      All Donations of no less that
      <strong>MK1,000</strong>
      may be made to Timothy Mizaya through
      <strong>TNM Mpamba</strong>
      (+265 882 49 43 65) or
      <strong>Airtel Money</strong>
      (+265 997 24 54 28)
    </h4>
    <br />
    <a href="https://paypal.me/daliuja?locale.x=en_US">Donate through PayPal</a>
  </div>
</Container>

<style>
  h1,
  h3 {
    background: var(--bg-yellow);
    padding: 1rem;
  }
  h4 {
    color: var(--bg-yellow);
  }

  a {
    text-decoration: none;
    padding: 0.5rem;
    border: 2px solid var(--bg-yellow);
    border-radius: 0.2rem;
    color: var(--bg-yellow);
  }
</style>
