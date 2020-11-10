<script>
  import BuyButton from "./BuyButton.svelte";
  import Player from "./Player.svelte";
  import { createEventDispatcher } from "svelte";
  import { fade } from "svelte/transition";

  const dispatch = createEventDispatcher();
  export let track;
  export let stopPlaying = false;
  export let trackNumber;
  export let prevTrack;
  export let nextTrack;

  function playSong(e) {
    dispatch("play", {
      track: e.detail.track,
    });
  }
</script>

<style>
  .img-container img {
    width: 70%;
    margin: 0px auto;
  }

  div.img-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    margin-bottom: 2rem;
    flex: 1;
  }

  @media screen and (max-width: 750px) {
    .img-container img {
      width: 50%;
      margin: 0px auto;
    }

    .img-container div {
      margin-top: -3rem;
    }
  }
</style>

<div class="img-container" in:fade={{ delay: 400 }}>
  <img
    src="https://res.cloudinary.com/tiyeni/image/upload/q_auto/v1601138202/alinafe_art.jpg"
    alt="Alinafe Album Art" />
  <BuyButton />
  {#if track}
    <div in:fade>
      <Player
        {track}
        {stopPlaying}
        {trackNumber}
        prevSong={prevTrack}
        on:play={playSong}
        nextSong={nextTrack} />
    </div>
  {/if}
</div>
