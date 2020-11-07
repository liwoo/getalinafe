<script>
  export let title = "Intro";
  export let featuring;
  export let duration = "3:02";
  export let number = 1;
</script>

<style>
  a {
    text-decoration: none;
  }

  div#song-entry {
    color: white;
    display: flex;
    justify-content: space-between;
    margin: 2rem 0;
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
</style>

<a href="/track">
  <div id="song-entry">
    <div id="song-head">
      <caption>{number + 1}</caption>
      <h2>
        {title}
        {#if featuring}<strong>(ft {featuring})</strong>{/if}
      </h2>
    </div>
    <caption>{duration}</caption>
  </div>
</a>
