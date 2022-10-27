<script>
  import Counter from './Counter.svelte'
  import Input from './Input.svelte'
  export let initialCounter

  const commonProps = { maxCounter: 15 }
</script>

<main>
  <Counter {...commonProps} />

  <Counter {initialCounter} {...commonProps} />

  <Counter initialCounter={10} {...commonProps} />
</main>
<span>We have all the films you need</span>
<Input />

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }
  span {
    color: #03f;
  }
  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
