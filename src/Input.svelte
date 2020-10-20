<script>
	export let copyInput
	export let sprintName	

</script>

<div class='buttons'>
	<div class='copy' on:click={() => copyInput()} >
		<svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path d="M16 1H4c-1.1 0-2 .9-2 2v14h2V3h12V1zm3 4H8c-1.1 0-2 .9-2 2v14c0 1.1.9 2 2 2h11c1.1 0 2-.9 2-2V7c0-1.1-.9-2-2-2zm0 16H8V7h11v14z"/></svg>
	</div>
	<div class='copy'>
		<svg xmlns="http://www.w3.org/2000/svg" width="1em" height="1em" viewBox="0 0 24 24"><path d="M17 3l5.25 4.5L17 12l5.25 4.5L17 21v-3h-2.74l-2.82-2.82l2.12-2.12L15.5 15H17V9h-1.5l-9 9H2v-3h3.26l9-9H17V3M2 6h4.5l2.82 2.82l-2.12 2.12L5.26 9H2V6z" /></svg>
	</div>
</div>
<input type='text' class='sprintName' bind:value={sprintName} readonly>
<style>
	.buttons {
		display: flex;
		justify-content: flex-end;
		position: relative;
		top: 1.8em;
		font-size: 1.5em;
		width: 95%;
	}
	
	.sprintName {
		font-size: 1.5em;
		text-align: center;
		width: 100%;
		border: 1px solid rgba(0,0,0,0.3);
		border-radius: 6px;
		outline: none;
	}
		
	.copy {
		fill: rgba(0,0,0,0.15)
	}
	
	.copy svg {
		transition: .2s all;
	}	
	
	.copy:hover svg {
		fill: rgba(57, 119, 219,0.6);
		transition: .2s all;
	}
	
	.copy:active svg  {
		fill: hotpink;
		transition: .2s all;
	}
	
</style>