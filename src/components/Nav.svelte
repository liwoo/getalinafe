<script>
  export let segment;
</script>

<style>
  nav {
    position: absolute;
    margin-top: 7%;
    font-weight: 300;
    padding: 0 1em;
    left: 5%;
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
  }

  [aria-current] {
    position: relative;
    display: inline-block;
  }

  a {
    text-decoration: none;
    padding: 1em 2em;
    display: block;
    font-weight: bold;
    text-transform: uppercase;
    color: var(--bg-yellow);
  }
</style>

<nav style="--bg-yellow=var(--bg-yellow)">
  <ul>
    <li>
      <a aria-current={segment === undefined ? 'page' : undefined} href=".">
        preview
      </a>
    </li>
    <li>
      <a aria-current={segment === 'about' ? 'page' : undefined} href="about">
        sample
      </a>
    </li>
    <li>
      <a aria-current={segment === 'about' ? 'page' : undefined} href="about">
        about
      </a>
    </li>
  </ul>
</nav>
