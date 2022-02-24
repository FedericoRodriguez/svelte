<script>
  import Counter from './Counter.svelte'
  export let initialCounter
</script>

<main>
  <Counter />

  <Counter {initialCounter} />

  <Counter initialCounter={10} />
</main>
<span>Out Side Styles for this span</span>

<style>
  span {
    color: #03f;
  }
</style>
