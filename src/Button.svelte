<script>
export let requestEmoji
export let category
export let excludedCategories
export let handleExcludes
</script>

<li>
	<label for={category}>
		<input 
					 type=checkbox 
					 value={category} 
					 id={category}
					 checked={(excludedCategories.includes(category))}
					 on:change={(e) => handleExcludes(e)}
		>
		<span>{requestEmoji(category)} {category}</span>
	</label>
</li>

<style>
	li {
		box-sizing: border-box;
		width: 33%;
		list-style: none;
	}

	label:hover {
		cursor: pointer;
	}

	li input {
		display: none;
	}

	li span {
		margin: 15px;
	}

	li label {
		margin: .5em;
		padding: 5px;
		border: 1px solid black;
		border-radius: 4px;
		display:flex;
		justify-content: center;
		align-items: center;
		text-align: center;
		border: none;
		background-color: rgba(0,0,0,0.01);
		box-shadow: 0 5px 5px rgba(0,0,0,0.35);
		transition: .1s transform;
		min-height: 5em;
		user-select: none;
	}

	li label:active {
		transform: translateY(2px);
		transition: .1s transform;
	}

	li input:checked + span {
		opacity: .4;
		text-decoration: line-through;
	}
</style>
