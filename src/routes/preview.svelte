<script>
  import { onMount } from "svelte";
  import SongEntry from "../components/SongEntry.svelte";
  import PlayerAndArt from "../components/PlayerAndArt.svelte";
  import { fly, fade } from "svelte/transition";

  let modalOpen = false;
  let playingTrack;
  let innerWidth;
  let downloadLoading;
  let stopPlaying = false;
  let prevSong;
  let nextSong;

  onMount(() => {
    document.getElementsByTagName("html")[0].className = "red-bg";
    prevSong = trackList[trackList.length - 1];
    nextSong = trackList[1];
  });

  const trackList = [
    {
      title: "Intro",
      duration: "3:01",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893850/01._Intro.mp3",
    },
    {
      title: "High School",
      duration: "3:57",
      featuring: "Suffix & SevenOMore",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893885/02._Highschool_ft_Suffix___SevenOmore.mp3",
    },
    {
      title: "Go",
      duration: "2:31",
      featuring: "George Kalukusha",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893890/03._Go_ft_George_Kalukusha.mp3",
    },
    {
      title: "Game Time [FIFA]",
      duration: "3:15",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893911/04._Game_Time_FIFA.mp3",
    },
    {
      title: "RT",
      duration: "3:49",
      featuring: "David Kalilani",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893922/05._RT_ft_David_Kalilani.mp3",
    },
    {
      title: "Not There",
      duration: "3:22",
      featuring: "Kim of Diamonds",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893878/06._Not_There_ft_Kim_of_Diamonds.mp3",
    },
    {
      title: "Don't Shoot",
      duration: "4:03",
      featuring: "Mista Gray",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893855/07._Don_t_Shoot_ft_Mista_Gray.mp3",
    },
    {
      title: "Winning",
      duration: "3:33",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893830/08._Winning.mp3",
    },
    {
      title: "Chimfana",
      duration: "3:41",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893876/09._Chimfana.mp3",
    },
    {
      title: "No",
      duration: "4:03",
      featuring: "Cozizwa",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893950/10._No_ft_Cozizwa.mp3",
    },
    {
      title: "God's Love",
      duration: "4:03",
      featuring: "Kelvin Sings & Grace",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893953/11._God_s_Love_ft_Kelvin_Sings___Grace.mp3",
    },
    {
      title: "Dear Daughter",
      duration: "3:48",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893941/12._Dear_Daughter.mp3",
    },
    {
      title: "Alinafe",
      duration: "4:03",
      featuring: "Beracah",
      link:
        "https://res.cloudinary.com/tiyeni/video/upload/v1604893950/13._Alinafe_ft_Beracah.mp3",
    },
  ];

  $: {
    nextSong =
      trackList[trackList.length - 1 === playingTrack ? 0 : playingTrack + 1];
    prevSong =
      trackList[playingTrack === 0 ? trackList.length - 1 : playingTrack - 1];
  }

  function playTrack(e) {
    if (innerWidth < 751) {
      modalOpen = true;
      stopPlaying = false;
    }
    playingTrack = e.detail.track;
  }

  function stop() {
    stopPlaying = true;
    modalOpen = false;
  }

  async function downloadAlbum() {
    analytics.logEvent("downloads", {
      content_type: "album",
      content_id: "album",
    });
    // Note that in the URL, characters are URL escaped!
    // Create an invisible A element
    const data =
      "https://firebasestorage.googleapis.com/v0/b/getalinafe.appspot.com/o/Liwu%20-%20Alinafe%20Album.zip?alt=media&token=4ce04a24-8fa1-440b-be4d-5734c4eeafaf";
    const fileName = "Alinafe_Liwu [2020].zip";
    const type = "application/zip";

    downloadLoading = true;
    let blob = await fetch(data).then((r) => r.blob());
    downloadLoading = false;
    const a = document.createElement("a");
    a.style.display = "none";
    document.body.appendChild(a);

    // Set the HREF to a Blob representation of the data to be downloaded
    a.href = window.URL.createObjectURL(new Blob([blob], { type }));

    // Use download attribute to set set desired file name
    a.setAttribute("download", fileName);

    // Trigger the download by simulating click
    a.click();

    // Cleanup
    window.URL.revokeObjectURL(a.href);
    document.body.removeChild(a);
  }
</script>

<style>
  .container {
    display: flex;
    flex-direction: row;
    margin-top: 10%;
    align-items: flex-start;
  }

  #modal {
    display: none;
    box-shadow: 1px -3px 13px -1px rgba(0, 0, 0, 0.5);
    -webkit-box-shadow: 1px -3px 13px -1px rgba(0, 0, 0, 0.5);
    -moz-box-shadow: 1px -3px 13px -1px rgba(0, 0, 0, 0.5);
    border-top-left-radius: 0.5rem;
    border-top-right-radius: 0.5rem;
  }

  #modal svg {
    float: right;
    margin: 1rem;
    cursor: pointer;
  }

  #player-art-container {
    display: block;
  }

  @media screen and (max-width: 750px) {
    .container {
      flex-direction: column-reverse;
      margin-top: 15%;
    }

    div#summary h2 {
      text-transform: uppercase;
      cursor: pointer;
      text-decoration: underline;
      margin-bottom: 0rem;
      font-size: 1rem;
    }

    .summary-container {
      width: 100%;
      margin-top: 10%;
    }

    #player-art-container {
      display: none;
      flex-grow: 1;
    }

    #modal {
      display: block;
      position: fixed;
      background-color: var(--bg-red);
      left: 0;
      bottom: 0;
      top: 5%;
      height: 100%;
      z-index: 500;
    }
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

  .summary-container {
    flex-grow: 1;
    width: 100%;
  }

  div#summary h2 {
    text-transform: uppercase;
    cursor: pointer;
    text-decoration: underline;
    margin-bottom: 0rem;
  }

  div#summary h3 {
    color: #ccc;
    margin-bottom: 0rem;
  }
</style>

<svelte:head>
  <title>Download Alinafe | Liwu</title>
  <!--  Essential META Tags -->
</svelte:head>

<svelte:window bind:innerWidth />

{#if modalOpen && playingTrack >= 0}
  <div id="modal" in:fly={{ y: 600 }} out:fly={{ y: 600 }}>
    <svg
      on:click={stop}
      width="10"
      height="11"
      xmlns="http://www.w3.org/2000/svg"><g
        fill="none"
        fill-rule="evenodd"
        stroke="#FFF">
        <path
          d="M87 22C87-33.228 42.228-78-13-78S-113-33.228-113 22"
          stroke-width="4" />
        <path
          stroke-linecap="square"
          d="M9.286 10.312L.714.687M9.286.688L.714 10.313" />
      </g></svg>
    <PlayerAndArt
      track={trackList[Number(playingTrack)]}
      {stopPlaying}
      nextTrack={nextSong}
      on:play={playTrack}
      trackNumber={playingTrack}
      prevTrack={prevSong} />
  </div>
{/if}

<div class="container">
  {#if !modalOpen && !stopPlaying}
    <div id="player-art-container">
      <PlayerAndArt
        track={trackList[Number(playingTrack)]}
        trackNumber={playingTrack}
        on:play={playTrack}
        nextTrack={nextSong}
        prevTrack={prevSong} />
    </div>
  {/if}
  <div in:fly={{ delay: 600, y: 300 }} class="summary-container">
    <div id="summary">
      <div id="motif">
        <img src="/pattern-round.png" alt="Alinafe Chitenje Pattern" />
      </div>
      <div>
        {#if downloadLoading}
          <h3 transition:fade>
            Downloading Album (Could take up to 5 Minutes). Please Wait...
          </h3>
        {:else}
          <h2 transition:fade on:click={downloadAlbum}>
            Download Alinafe_Liwu.zip [110 MB]
          </h2>
        {/if}
        <h3>13 Songs</h3>
      </div>
    </div>
    {#each trackList as track, i}
      <!-- content here -->
      <SongEntry {...track} number={i} on:play={playTrack} />
    {/each}
  </div>
</div>
