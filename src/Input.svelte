<script>
    import Movie from './Movie.svelte';
    let value = '';
    let response = [];
    const API_KEY = '1bfa5520';

    const handleInput = (event) => value = event.target.value;
    $:if(value.length > 2){
        response = fetch(`https://www.omdbapi.com/?s=${value}&apikey=${API_KEY}`)
            .then(res => {
               if(!res.ok){
                throw new Error('An error occurred while fetching the movies');
               }else{
                   return res;
               }
            })
            .then(res => res.json())
            .then(apiResponse => apiResponse.Search || [])
    }else{
        response = [];
    }
</script>

<style>
    p, input{
        margin: 8px 0;
    }
</style>

<input placeholder="Movie Title" {value} on:input={handleInput}>
{#await response}
    <p>Loading...</p>
{:then response}
    {#if response.length > 0}
        <p>{response.length} Movies found 🙌</p>
        {#each response as {Title, Year, Poster}}
            <Movie {Title} {Year} {Poster}/>
        {/each}
    {:else if value.length > 2}
        <p>No movies were found</p>
    {/if}
{:catch error}
    <p>❌{error}❌</p>
{/await}


