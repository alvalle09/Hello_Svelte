<script>

	export let name;	
	let fetched = false;
	let count = 0;

	function handleClick() {
		count += 1;
		fetched = false;
	}
	// define `fetch`
	const fetch = () => {
		fetched = true;
		count = 0;
	}

	// create list array 
	const list = [
		{ type: 'Apple', color: 'Green'},
		{ type: 'Banana', color: 'Yellow'},
		{ type: 'Grape', color: 'Purple'},
	]

</script>

<main>
	<!-- string interpolation of variables -->
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	<!-- assign even handler -->
	<button on:click={handleClick}>
		Clicked {count} {count === 1 ? 'time' : 'times'}
	</button>

	<button on:click="{fetch}">
		Fetch Data
	</button>

	<!-- render conditionally -->
	{#if fetched}
		<div>done!</div>
	{/if}
	
	<table>
		<thead>
			<th>Index</th>
			<th>Type</th>
			<th>color</th>
		</thead>
		<tbody>
			<!-- loop through `list` -->
			{#each list as row, i}
			<tr>
				<td>{i}</td>
				<td>{row.type}</td>
				<td>{row.color}</td>
			</tr>
			{/each}
		</tbody>
	</table>
	
	
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