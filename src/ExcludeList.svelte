<script> 
	import Button from './Button.svelte'
	
	export let categories
	export let handleExcludes
	export let requestEmoji
	export let excludedCategories
	export let emojiListLength
</script>

<h3>
	Exclude emoji ({emojiListLength})
</h3>
<ul>
	{#each categories as category}
	<Button
		{requestEmoji}
		{category}
		{excludedCategories}
		{handleExcludes}
	/>
	{/each}	
</ul>

<style type="text/scss">
		
	ul {
		display:flex;
		flex-wrap: wrap;
		margin: 0;
		padding: 0;
	}
	
</style>