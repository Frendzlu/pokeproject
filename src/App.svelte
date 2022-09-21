<script>
	import "./lib/Tailwind.css";
	import { Router, Link, Route } from "svelte-routing";
	import Home from "./routes/Home.svelte";
	import NotFound from "./routes/404.svelte";
	import MultiSelect from "./lib/MultiSelect.svelte";
	let homeComp;

	function clearShit() {
		homeComp.clearPokes()
	}
	export let url = "";
	let searchStr = ""
	let typeval
</script>

<Router {url}>
	<nav
		class="bg-white border-gray-200 dark:bg-gray-900"
	>
		<div class="container flex flex-wrap justify-between items-center mx-auto">
			<div class="hidden w-full md:block md:w-auto" id="navbar-default">
				<ul class="flex flex-col p-4 bg-gray-50 rounded-lg border border-gray-100 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium md:border-0 md:bg-white dark:bg-gray-800 md:dark:bg-gray-900 dark:border-gray-700">
					<li>
						<Link
							class="block py-2 pr-4 pl-3 text-white bg-blue-700 rounded md:bg-transparent md:text-blue-700 md:p-0 dark:text-white"
							to="/">Home</Link>
					</li>
					<li>
						<button style="color: white; background-color: red; padding: 5px; border: 2px solid brown; border-radius: 4px" on:click={clearShit}>Clear storage</button>
					</li>
					<li class="m-2">
						<input type="text" bind:value={searchStr} on:input={() => {homeComp.currentPage = 0}}>
					</li>
					<li>
						<MultiSelect id='lang' bind:value={typeval} inputEvent={() => {homeComp.currentPage = 0}}>
							<option style="color: #78c850" value="grass">Grass</option>
							<option style="color: #f08030" value="fire">Fire</option>
							<option style="color: #6890f0" value="water">Water</option>
							<option style="color: #a8b820" value="bug">Bug</option>
							<option style="color: #a8a878" value="normal">Normal</option>
							<option style="color: #a040a0" value="poison">Poison</option>
							<option style="color: #f8d030" value="electric">Electric</option>
							<option style="color: #e0c068" value="ground">Ground</option>
							<option style="color: #ee99ac" value="fairy">Fairy</option>
							<option style="color: #c03028" value="fighting">Fighting</option>
							<option style="color: #f85888" value="psychic">Psychic</option>
							<option style="color: #b8a038" value="rock">Rock</option>
							<option style="color: #705898" value="ghost">Ghost</option>
							<option style="color: #98d8d8" value="ice">Ice</option>
							<option style="color: #7038f8" value="dragon">Dragon</option>
							<option style="color: #454545" value="steel">Steel</option>
							<option style="color: #5eb9b2" value="flying">Flying</option>
							<option style="color: #2d1c1c" value="dark">Dark</option>
							<option style="color: #260940" value="shadow">Shadow</option>
							<option style="color: #aeaeae" value="unknown">Unknown</option>
						</MultiSelect>
					</li>
				</ul>
			</div>
		</div>
	</nav>
	<div>
		<Route path="/"><Home bind:this={homeComp} searchStr={searchStr} typeval={typeval}/></Route>
		<Route path="*" component={NotFound} />
	</div>
</Router>
