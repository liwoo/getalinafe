<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function playSong(songId) {
    analytics.logEvent("plays", {
      content_type: title,
      content_id: songId,
    });

    dispatch("play", {
      track: songId,
    });
  }

  export let title = "Intro";
  export let featuring;
  export let duration = "3:02";
  export let number = 1;
</script>

<style>
  div#song-entry {
    color: white;
    display: flex;
    justify-content: space-between;
    margin: 2rem 0;
    cursor: pointer;
  }

  div#song-entry caption {
    opacity: 0.5;
  }

  div#song-head h2 {
    font-size: medium;
  }

  div#song-head {
    display: flex;
  }

  div#song-head strong {
    font-weight: lighter;
    opacity: 0.7;
  }

  div#song-head caption {
    margin-right: 1rem;
  }

  svg {
    margin: 0.1rem 0.4rem;
  }
</style>

<div id="song-entry" on:click={playSong(number)}>
  <div id="song-head">
    <caption>{number + 1}</caption>
    <h2>
      {title}
      {#if featuring}<strong>(ft {featuring})</strong>{/if}
    </h2>
    <!-- TODO: Hover Player -->
    <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg">
      <g fill="none" fill-rule="evenodd" stroke="#FFF">
        <path stroke-linecap="square" d="M.5 17.5h11" />
        <path
          stroke-width="2"
          stroke-linecap="square"
          d="M5.5 1.682v13.636M1.625 10.6l3.75 4.8M10.25 10.6l-4.5 4.8" />
        <path
          d="M108 23C108-32.228 63.228-77 8-77S-92-32.228-92 23"
          stroke-width="4" />
      </g>
    </svg>
  </div>
  <caption>{duration}</caption>
</div>
