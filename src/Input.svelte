<script>
    let value = '';
    const APIKEY = '1bfa5520';

    const handleInput = (event) => value = event.target.value;
    $:if(value.length > 2){
        fetch(`https://www.omdbapi.com/?s=${value}&apikey=${APIKEY}`)
            .then(res => res.json())
            .then(json => console.log(json))
    }
</script>

<input placeholder="Movie Title" {value} on:input={handleInput}>