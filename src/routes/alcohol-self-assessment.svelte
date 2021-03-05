<script>
  (function () {
    var qs,
      js,
      q,
      s,
      d = document,
      gi = d.getElementById,
      ce = d.createElement,
      gt = d.getElementsByTagName,
      id = "typef_orm",
      b = "https://embed.typeform.com/";
    if (!gi.call(d, id)) {
      js = ce.call(d, "script");
      js.id = id;
      js.src = b + "embed.js";
      q = gt.call(d, "script")[0];
      q.parentNode.insertBefore(js, q);
    }
  })();
</script>

<main>
  <div class="container">
    <div
      class="typeform-widget"
      data-url="https://form.typeform.com/to/G2Zju91i?typeform-medium=embed-snippet"
      style="width: 100%; height: 500px;"
    />
  </div>
</main>

<style>
  main {
    width: 80%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .container {
    display: block;
    width: 60%;
    margin: 0 auto;
  }

  @media screen and (max-width: 600px) {
    div.container {
      width: 90%;
    }
  }
</style>
