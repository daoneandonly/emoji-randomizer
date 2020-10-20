<script>
	import ExcludeList from './ExcludeList.svelte'
	import Header from './Header.svelte'
	import Input from './Input.svelte'
	import GenerateButton from './GenerateButton.svelte'
	
 	$: length = 3;
	$: sprintName = '';
	$: spacing = false;
	$: emojiList = [];
	$: categories = [];

	let emojiData = '' ;
	let emojiArray = [];
	let excludedCategories = ['Flags', 'Objects'];
	let includedCategories = ['Activities'];
	
	async function getData () {
		let response = await fetch("https://unpkg.com/emoji.json@12.1.1/emoji.json");
		return await response.json();
	}
	
	function createList (){
		getData().then(function (d) {
			emojiData = d.filter(d => !d.name.includes('skin') && !d.group.includes('Component'));
			categories = [...new Set(emojiData.map(a => a.group))]
		
			emojiList = updateList(emojiData)
		})
	}
	
	createList();
	
	function updateList(data){
		return filterData(data).map(d => d.char);
	}
	
	function filterData(data){
		let excludedData = data;
		for (let a in excludedCategories) {
			excludedData = excludedData.filter(d => !d.group.includes(excludedCategories[a]))
		}
		return excludedData;
	}
	
	function renderSprintName() {
			emojiArray = [];
			createEmojiArray();
			updateSprintName(emojiArray);
	}
	
	function createEmojiArray(){
			for(let i = 0; i  < length; i++) {
				emojiArray.push(generateEmoji());
			}
	}
	
	function updateSprintName(arrayOfEmoji) {
			sprintName = '';	
			arrayOfEmoji.forEach(d => {
				sprintName += d
				if(spacing){
					sprintName += ' '													
				}
			});
	}
	
	function copyInput () {
			let input = document.querySelector('.sprintName');
			input.select()
			document.execCommand('copy');
			window.getSelection().removeAllRanges()
	}
	
	function generateEmoji () {
		return emojiList[Math.floor(Math.random() * emojiList.length)]
	}
	
	function requestEmoji (request) {
		let t = emojiData.filter(d => d.group.includes(request)).map(d => d.char).length
		return emojiData.filter(d => d.group.includes(request)).map(d => d.char)[Math.floor(Math.random() * t)]
	}
	
	function handleLengthChange() {
		if (emojiArray.length === 0){
			renderSprintName();
		}
		if(length > emojiArray.length) {
			emojiArray.push(generateEmoji());
			updateSprintName(emojiArray);
		} 
		if (length < emojiArray.length) {
			emojiArray.pop()
			updateSprintName(emojiArray);
		}
	}
	
	function changeSpacing() {
		updateSprintName(emojiArray);
	}
	
	function handleExcludes(e) {
		if (e.target.checked === true){
			excludedCategories.push(e.target.value)
		} else {
			excludedCategories = excludedCategories.filter(d => d !== e.target.value)
		}
		emojiList = updateList(emojiData)
	}
</script>

<div class='container'>
	
	<Header {handleLengthChange} bind:length={length} />

	<Input {copyInput} {sprintName}/>
	
	<GenerateButton {emojiList} {renderSprintName} />
	
	<section class='options'>
		<h2>
			Options
		</h2>
		<label for='spacing'>
			<input id='spacing' type='checkbox' bind:checked={spacing} on:change={changeSpacing}/>
			Spaces between emoji
		</label>
		<ExcludeList 
			{categories} 
			{handleExcludes} 
			{requestEmoji} 
			{excludedCategories} 
			emojiListLength={emojiList.length} 
		/>
	</section>
</div>


<style>
	.container {
		display: flex;
		flex-direction: column;
		max-width: 35em;
		margin: auto;
	}

</style>
