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
  <input placeholder="Search Movies..." {value} on:input={handlerInput} />

  {#await response}
    Loading...
  {:then movies}
    <strong>Tenemos {movies.length} peliculas</strong>
    {#each movies as { Title: movieTitle, Poster, Year }, index}
      <Movie {index} title={movieTitle} poster={Poster} year={Year} />
    {:else}
      <strong>No tenemos peliculas</strong>
    {/each}
  {:catch error}
    <p>Something went wrong: {error.message}</p>
  {/await}
</div>

<style>
  input {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 1em;
    font-weight: 100;
  }
</style>
