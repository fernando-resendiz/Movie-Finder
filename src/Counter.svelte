<script>
    export let initialCounter = 0;
    export let maxCounter;
    let counter = initialCounter;
    $: isOddOrEven = counter % 2 === 0 ? 'Is Even': 'Is Odd';
    $: if(maxCounter && counter > maxCounter){
        counter = maxCounter;
    }
    const increaseCount = () => {
        counter++;
    }

</script>

<style>
    span {
        color:red;
    }
</style>

<button on:click={increaseCount}>Incrementar</button>
<span>{counter}</span>
<span>{isOddOrEven}</span>