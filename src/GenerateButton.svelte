<script>
	export let emojiList 
	export let renderSprintName
</script>

{#if emojiList.length === 0}
		<button class='generate'>
			Can't load emoji!
		</button>
	{:else}
		<button class='generate' on:click={renderSprintName}>
			 Generate sprint name
		</button>
{/if}	

<style>
	
	button.generate {
		font-size: 1.5em;
		font-family: monospace;
		border-radius: 6px;
		border: none;
		background-color: hotpink;
		color: white;
		cursor: pointer;
		transition: .1s transform;
		padding: 1em;
	}

	button.generate:active {
		transition: .1s transform;
		transform: translateY(2px)
	}
	
</style>