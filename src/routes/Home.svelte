<script>
	import PokemonTile from "../lib/PokemonTile.svelte";
	import "../lib/Tailwind.css";
	async function getApiData() {
		const res = await fetch(`https://pokeapi.co/api/v2/pokemon`);
		const text = await res.json();

		if (res.ok) {
			return text;
		} else {
			throw new Error(text);
		}
	}
	let promise = getApiData();

	function getPokemonId(str) {
		let x = str.split("/");
		return x[x.length - 2];
	}
	
	function titleCase(str) {
		console.log(str[0])
		let x = str.charAt(0).toUpperCase()
		return x + str.substring(1)
	}
</script>

<content class="flex flex-wrap p-3" style="background-color: #eaeaea;">
{#await promise}
	<p>...waiting for pokemons to spawn</p>
{:then json}
	{#each json.results as pokemon}
		<PokemonTile
			id={getPokemonId(pokemon.url)}
			pokemonName={titleCase(pokemon.name)}
		/>
	{/each}
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
</content>
