<script>
	import {fly} from 'svelte/transition';
	import {flip} from 'svelte/animate';
	let numbers = [1,2,3,4,5,6,7,8,9,1].map(number => ({number}));
	
	function shuffle() { 
		numbers = numbers.sort(() => .5 - Math.random())
	}
	function remove() { 
		numbers = numbers.slice(1)
	}
</script>



<div>
	{#each numbers as numberObject (numberObject)}
		<p out:fly={{x: -500, duration: 5000}} animate:flip>{numberObject.number}</p>
	{/each}
</div>

<button on:click={shuffle}>
	shuffle
</button>
<button on:click={remove}>
	remove
</button>
 
<style>
	div {
		border-color:gray;
		border-radius:20px;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
	}
	p {
		
		width: 50%;
		display: inline-block;
	}
</style>