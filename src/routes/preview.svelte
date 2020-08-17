<script>
  import { onMount } from "svelte";
  import SongEntry from "../components/SongEntry.svelte";
  import { fade, fly } from "svelte/transition";

  onMount(() => {
    document.getElementsByTagName("html")[0].className = "red-bg";
  });

  const trackList = [
    { title: "Intro", duration: "3:01" },
    {
      title: "High School",
      duration: "3:57",
      featuring: "Suffix & SevenOMore",
    },
    { title: "Go", duration: "2:31", featuring: "George Kalukusha" },
    { title: "Game Time [FIFA]", duration: "3:15" },
    { title: "RT", duration: "", featuring: "David Kalilani" },
    { title: "Not There", duration: "3:22", featuring: "Kim of Diamonds" },
    { title: "Don't Shoot", duration: "4:03", featuring: "Mista Gray" },
    { title: "Winning", duration: "3:33" },
    { title: "Chimfana", duration: "3:41" },
    { title: "No", duration: "4:03", featuring: "Cozizwa" },
    {
      title: "God's Love",
      duration: "4:03",
      featuring: "Kelvin Sings & Grace",
    },
    { title: "Dear Daughter", duration: "3:48" },
    { title: "Alinafe", duration: "4:03", featuring: "Beracah" },
  ];
</script>

<style>
  div.img-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    margin-top: 6rem;
    margin-bottom: 2rem;
  }

  div#motif {
    background-color: var(--bg-yellow);
    padding: 5px;
    width: 50px;
    height: 50px;
    border-radius: 99px;
    border: 2px solid white;
    margin-right: 1rem;
  }

  div#motif img {
    width: 50px;
    height: 50px;
  }

  div#summary {
    display: flex;
    color: white;
    align-items: center;
    margin-bottom: 1rem;
    padding: 1rem 0;
    border-bottom: 1px solid black;
  }

  div#summary h2 {
    text-transform: uppercase;
    margin-bottom: 0rem;
  }

  div#summary h3 {
    color: #ccc;
    margin-bottom: 0rem;
  }

  button {
    font-weight: bold;
    margin: 1rem 0;
    width: 70%;
    padding: 1rem 0;
    border-radius: 0.5rem;
    border: none;
    background-color: var(--bg-yellow);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  button img {
    height: 25px;
    width: 25px;
    margin-right: 0.5rem;
  }
</style>

<div>
  <div class="img-container" in:fade={{ delay: 400 }}>
    <img
      src="/album-art.png"
      alt="Alinafe Album Art"
      style="width: 70%; margin: 0px auto;" />
    <button>
      <img src="/shopping-cart.png" alt="Shopping Cart" />
      Preorder Now @MK5,000
    </button>
  </div>
  <div in:fly={{ delay: 600, y: 300 }}>
    <div id="summary">
      <div id="motif">
        <img src="/pattern-round.png" alt="Alinafe Chitenje Pattern" />
      </div>
      <div>
        <h2>Alinafe_Liwu</h2>
        <h3>13 Songs</h3>
      </div>
    </div>
    {#each trackList as track, i}
      <!-- content here -->
      <SongEntry {...track} number={i} />
    {/each}
  </div>
</div>
