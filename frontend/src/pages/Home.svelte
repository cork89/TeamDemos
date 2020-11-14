<script>
	import DemoHistory from "../components/DemoHistory.svelte";
	import Demo from "../components/Demo.svelte";
	export let team = "";
</script>

<style>
	main {
		background-color: darkgray;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		max-width: none;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	.container {
		display: flex;
	/* }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	} */
</style>

<main>
	<div class="container">
		<DemoHistory />
		<Demo team={team}/>
	</div>
</main>
