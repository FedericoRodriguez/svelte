<script>
  import Movie from './Movie.svelte'
  let value = ''
  let response = Promise.resolve([])

  const handlerInput = (event) => {
    value = event.target.value
  }

  $: if (value.length > 2) {
    response = fetch(`https://www.omdbapi.com/?s=${value}&apikey=422350ff`)
      //.then((res) => !res.ok && new Error('Something bad happen'))
      .then((res) => res.json())
      .then((apiResponse) => apiResponse.Search || [])
  }
</script>

<div>
  <div class="search-container">
    <input placeholder="Search Movies..." {value} on:input={handlerInput} />
  </div>
  {#await response}
    Loading...
  {:then movies}
    <strong>We have {movies.length} films</strong>
    <section class="article-container">
      {#each movies as { Title: movieTitle, Poster, Year }, index}
        <Movie {index} title={movieTitle} poster={Poster} year={Year} />
      {:else}
        <strong>No Films</strong>
      {/each}
    </section>
  {:catch error}
    <p>Something went wrong: {error.message}</p>
  {/await}
</div>

<style>
  input {
    color: #b81826;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
    width: 670px;
  }
  .search-container {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 50px 0px;
  }
  .article-container {
    display: flex;
    gap: 10px;
    justify-content: center;
    align-items: flex-start;
    padding: 50px 0px;
    flex-wrap: wrap;
  }
</style>
