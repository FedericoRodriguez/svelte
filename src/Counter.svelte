<script>
  export let initialCounter = 0
  export let maxCounter = 9

  let contador = initialCounter

  function handleClick() {
    contador++
  }

  $: isEvenOrOdd = contador % 2 === 0 ? 'Is Even' : 'Is Odd'
  $: if (contador > maxCounter) {
    contador = maxCounter
  }
</script>

<button on:click={handleClick}>Contador</button>
<span>Amount of Cliks: {contador}!</span>
<span>{isEvenOrOdd}</span>

<style>
  span {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
  }
</style>
