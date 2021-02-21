<script>
    export let Title, Year, Poster;
</script>

<style>
    .container{
        color: rgb(45, 45, 45);
        background-color: white;
        width: 320px;
        max-width: 95vw;
        border-radius: 15px;
        display: flex;
        flex-direction: column;
        overflow: hidden;
        margin: 10px 0;
        position: relative;
        padding: 4px 0 0 0;
    }
    h2, p{
        text-align: center;
        align-self: center;
        margin: 4px 0;
    }
    .img{
        width: 100%;
        border-radius: 15px;
        display: flex;
        overflow: hidden;
        margin: 4px 0 0 0;
    }
    img{
        width: 100%;
    }
</style>

<div class=container>
    <h2>{Title}</h2>
    <p>{Year}</p>
    {#if Poster !== 'N/A'}
        <div class="img">
            <img src={Poster} alt={Title}>
        </div>
    {/if}
</div>