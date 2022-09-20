<script>
	export let id;
	export let pokemonName;
</script>

<div class="container w-48 m-2 shadow-2xl" {id} style="background-color: #fff;">
	<div class="container flex flex-row shadow-xl" style="background-color: #aeaeff">
		<div class="w-12 h-8 content-center">
			<p style="color: #555; text-align: center;">#{id}</p>
		</div>
		<b class="h-8 w-36" style="text-align: center;">{pokemonName}</b>
	</div>
	<img
		class="w-48 h-48"
		src={`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${id}.png`}
		alt="{pokemonName} front image"/>
</div>
