<script>
  import { fade } from "svelte/transition";
  import { onMount } from "svelte";

  export let segment;
  let showNav = false;
  onMount(() => {
    setTimeout(() => {
      showNav = true;
    }, 500);
  });
</script>

<style>
  div#nav {
    display: flex;
    flex-direction: row;
    position: absolute;
    z-index: 10;
    padding-top: 5rem;
    padding-left: 5rem;
    justify-content: center;
    width: calc(100% - 5rem);
  }

  @media screen and (max-width: 600px) {
    div#nav {
      width: 90%;
      padding-left: 1em;
    }
  }
  nav {
    font-weight: 300;
    padding: 0 1em;
  }

  ul {
    margin: 0;
    padding: 0;
  }

  /* clearfix */
  ul::after {
    content: "";
    display: block;
    clear: both;
  }

  li {
    display: block;
    float: left;
    color: var(--bg-yellow);
  }

  [aria-current] {
    position: relative;
    display: inline-block;
  }

  a {
    text-decoration: none;
    padding: 1em 6em;
    display: block;
    font-weight: bold;
    text-transform: uppercase;
  }
  li:nth-child(3) {
    color: var(--bg-red);
  }

  @media screen and (max-width: 895px) {
    a {
      padding: 1em 2em;
    }
  }

  @media screen and (max-width: 600px) {
    a {
      padding: 1em 2.5em;
    }
  }

  @media screen and (max-width: 450px) {
    a {
      padding: 1em 1.5em;
    }
  }
</style>

<div id="nav">
  <nav style="--bg-yellow=var(--bg-yellow)">
    {#if showNav}
      <ul>
        <li in:fade={{ delay: 500 }}>
          <a aria-current={segment === undefined ? 'page' : undefined} href=".">
            preorder
          </a>
        </li>
        <li in:fade={{ delay: 700 }}>
          <a
            aria-current={segment === 'preview' ? 'page' : undefined}
            href="preview">
            preview
          </a>
        </li>
        <li in:fade={{ delay: 900 }}>
          <a
            aria-current={segment === 'preview' ? 'page' : undefined}
            href="preview">
            about
          </a>
        </li>
      </ul>
    {/if}
  </nav>
</div>
