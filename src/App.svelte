<script>
	import Input from './Input.svelte';
	const commonProps = {maxCounter: 5};
</script>
<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	h1 {
		margin: 2rem 0;
	}
</style>
<main>
	<h1>🎥 Search a Movie 🍿</h1>
	<Input/>
</main>
