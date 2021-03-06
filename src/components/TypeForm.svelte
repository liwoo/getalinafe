<script>
  export let href;
</script>

<div class="typeform-widget" data-url={href} />

<style>
  .typeform-widget {
    width: 50vw;
    height: 60vh;
  }

  @media screen and (max-width: 600px) {
    .typeform-widget {
      width: 90vw;
      height: 60vh;
    }
  }
</style>
