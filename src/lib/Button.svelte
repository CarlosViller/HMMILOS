<script>
  export let onClick;
  export let price;
  export let name;
  export let color;
  export let logo;

  $: cssVarStyles = `--service-color:${color};`;

  let pressed = false;
</script>

<article class="service-btn-container" style={cssVarStyles}>
  <button
    class={`service-btn`}
    class:pressed
    on:click={() => {
      const value = !pressed ? price : price * -1;
      onClick(value);
      pressed = !pressed;
    }}
  >
    <img src={logo} alt={name} />
  </button>
  <span class="service-name">{name}</span>
</article>

<style>
  .service-btn-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    width: 85px;
  }

  .service-name {
    text-align: center;
    color: black;
    font-family: "Open Sans", sans-serif;
    opacity: 0;
    transition: all 0.5s ease;
    color: #fff;
  }

  .service-btn-container:hover .service-name {
    opacity: 1;
  }

  .service-btn {
    width: 75px;
    aspect-ratio: 1/1;
    background-color: #242424;
    transition: all 0.2s ease;
    border-radius: 5px;
    border: 2px solid #ffffffa6;
    padding: 8px;
    cursor: pointer;
  }

  .service-btn img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  .service-btn:active {
    transform: scale(0.9);
  }

  .service-btn.pressed,
  .service-btn.pressed:hover {
    border-color: var(--service-color);
    -webkit-box-shadow: 0px 0px 50px 5px var(--service-color);
    -moz-box-shadow: 0px 0px 50px 5px var(--service-color);
    box-shadow: 0px 0px 50px 5px var(--service-color);
  }

  .service-btn:not(pressed):hover {
    -webkit-box-shadow: 0px 0px 40px -5px var(--service-color);
    -moz-box-shadow: 0px 0px 40px -5px var(--service-color);
    box-shadow: 0px 0px 40px -5px var(--service-color);
  }
</style>
