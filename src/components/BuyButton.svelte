<script>
  import * as sapper from "@sapper/app";

  function goToDonate() {
    analytics.logEvent("donates", {
      content_type: "goToDonate",
      content_id: "fromButton",
    });
    sapper.goto("/donate");
  }
</script>

<style>
  button {
    font-weight: bold;
    margin: 1rem 0;
    padding: 1rem;
    border-radius: 0.5rem;
    border: none;
    background-color: var(--bg-yellow);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  @media screen and (max-width: 750px) {
    button {
      padding: 0.5rem;
    }
  }

  button img {
    height: 25px;
    width: 25px;
    margin-right: 0.5rem;
  }
</style>

<button on:click={goToDonate}>
  <img src="/heart.png" alt="Donate" />
  Donate From MK1,000
</button>
