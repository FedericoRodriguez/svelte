<script>
  export let initialCounter = 0
  let contador = initialCounter
  function handleClick() {
    contador++
  }
</script>

<button on:click={handleClick}>Contador</button>
<span>Amount of Cliks: {contador}!</span>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  span {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
