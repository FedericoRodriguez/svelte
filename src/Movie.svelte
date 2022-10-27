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
    box-shadow: 5px 10px #888888;
    border-radius: 4px;
    padding: 16px;
    background-color: #fa440752;
    margin-bottom: 8px;
    text-align: center;
    margin: 1em 0;
    width: 15%;
    align-self: stretch;
  }
  h3 {
    margin-bottom: 4px;
    font-size: 1rem;
  }
  img {
    width: 10vw;
  }
</style>
