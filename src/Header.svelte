<script>
	export let handleLengthChange 
	export let length
</script>

<header>
	<h1>
		A sprint name in
		<input type='number' min=1 max=9 class='length' bind:value={length} on:change={handleLengthChange}>
		emojis
	</h1>
</header>

<style>
	h1 {
		font-size: 2.3em;
		text-align: center;
	}
		
	.length {
		display: inline-block;
		width: auto;
		min-width: auto;
		max-width: 2em;
		border: none;
		font-weight: bold;
		padding: none;
		margin: none;
	}
</style>