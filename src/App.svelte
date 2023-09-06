<script>
  import Button from "./lib/Button.svelte";
  import services from "./suscriptions.json";

  let money = 0;

  function addMoney(amount) {
    let newMoney = money + amount;
    money = parseFloat(newMoney.toFixed(2));
  }
</script>

<main>
  <section id="intro">
    <h1 style="textAlign: center">
      How much <span class="green-text">money</span> I'm losing on subscriptions
      <span style="font-size: 1.5em">💸</span>
    </h1>
    <span class="lose-money green-text">{money}$ / mo</span>
    <small
      >* All prices are based on the cheapest subscription plan available</small
    >
  </section>

  <section class="services-container">
    {#each services as service}
      <Button {...service} onClick={(value) => addMoney(value)} />
    {/each}
  </section>

  <section class="btn-container">
    <a
      class="button-action"
      target="_blank"
      href="https://forms.gle/xE3D2sNqmKy3BGVG6">Suggest a service</a
    >
  </section>
</main>

<footer>
  <a
    id="linkedIn"
    href="https://www.linkedin.com/in/carlos-villermosa/"
    target="_blank">Carlos Villermosa</a
  >
  <a href="https://twitter.com/carlosviller" target="_blank">
    <img src="/twitter.svg" alt="Twitter" />
  </a>
  <a href="https://github.com/CarlosViller" target="_blank">
    <img src="/github.svg" alt="Github" />
  </a>
</footer>
