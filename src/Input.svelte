<script>
    import Movie from './Movie.svelte';
    let value = '';
    let response = [];
    const APIKEY = '1bfa5520';
    let loading = false;

    const handleInput = (event) => value = event.target.value;
    $:if(value.length > 2){
        loading = true;
        fetch(`https://www.omdbapi.com/?s=${value}&apikey=${APIKEY}`)
            .then(res => res.json())
            .then(apiResponse => {
                response = apiResponse.Search || [];
                console.log(apiResponse.Search)
                loading = false;
            })
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
{#if loading}
    <p>Loading...</p>
{:else}
    {#if response.length > 0}
    <p>{response.length} Movies found 🙌</p>
    {#each response as {Title, Year, Poster}}
        <Movie class="Movie" {Title} {Year} {Poster}/>
    {/each}
    {:else if value.length > 2}
        <p>No movies were found</p>
    {/if}
{/if}


