<script>
  import { fly } from "svelte/transition";
</script>

<style>
  nav {
    display: flex;
    position: fixed;
    flex-direction: row;
    background-color: var(--bg-red);
    left: 0;
    right: 0;
    z-index: 100;
    justify-content: space-between;
    padding-left: 5%;
    padding-right: 5%;
    padding-top: 3rem;
    padding-bottom: 1rem;
    color: #fff;
    align-items: center;
  }

  nav h1 {
    font-size: medium;
  }
</style>

<nav in:fly={{ delay: 200, y: -200 }}>
  <div>
    <a href="/">
      <svg width="32" height="21" xmlns="http://www.w3.org/2000/svg">
        <g stroke="#FFF" fill="none" fill-rule="evenodd">
          <path stroke-linecap="square" d="M31 11H2" />
          <path d="M8.045 1.91L1.5 11.401l6.545 8.507" />
        </g>
      </svg>
    </a>
  </div>
  <div>
    <h1>Alinafe Track List</h1>
  </div>
  <div />
</nav>
