<script>
	import { onMount } from "svelte";
	export let name;
	const response = fetch('http://localhost:8081/stocks');
	let posts = [];
	onMount(async function () {
  		const response = await fetch('http://localhost:8081/stocks');
  		const data = await response.json();
  		console.log(data);
		posts = data;
	});
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{#each posts as article}
    <div>
      <p>Stock ID: {article.id} Stock Name:{article.name} Quantity:{article.quantity} Price: {article.price}</p>
    </div>
  	{/each}

</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>