<script>
  export let index
  export let title
  export let year
  export let poster
</script>

<article>
  <p>#{index}</p>
  <img alt={title} src={poster} />
  <h3>{title}</h3>
  <span>{year}</span>
  {#if 2020 - year < 5}
    <i>New</i>
  {/if}
</article>

<style>
  article {
    border: 1px solid #eee;
    border-radius: 4px;
    padding: 16px;
    background-color: #fa440752;
    margin-bottom: 8px;
    text-align: center;
  }
  h3 {
    font-size: 24px;
    margin-bottom: 4px;
  }
</style>
