<script>
	import { Link } from "svelte-routing";

	let options = [];
	let selected;

	fetch("http://localhost:3000/")
		.then((res) => {
			let json = res.json();
			console.log(json);
			return json;
		})
		.then((data) => {
			console.log(data);
			options = data.teams;
			let favorite = localStorage.getItem("favoriteTeam");
			console.log(favorite);
			let savedTeam = options.findIndex((team) => team.name == favorite);
			if (savedTeam) selected = options[savedTeam].name;
		})
		.catch((err) => []);

	function saveTeam(event) {
		console.log(event.target.value);
		localStorage.setItem("favoriteTeam", event.target.value);
	}
</script>

<style>
	.grid-container {
		/* height: 4rem;
		width: 8rem;
		
		border-color: #f1c40f;
		color: #f1c40f;
		font-size: 1.25rem; */
		display: grid;
		grid-template-columns: 2fr 3fr;
		grid-template-rows: 1fr;
		gap: 0px 0px;
		grid-template-areas: "left . right";
		grid-area: grid-container;
		background-color: #333;
		color: #f1c40f;
	}
	.left {
		grid-area: left;
		padding: 5px;
	}
	.right {
		grid-area: right;
		padding: 5px;
	}
	.link {
		outline: solid;
		background-color: #444;
		text-align: center;
		max-width: fit-content;
		padding: 3px;
	}
</style>

<header>
	<div class="grid-container">
		<div class="left">
			
				<Link to="/">
					<div class="link">Home</div>
				</Link>
			
			<Link to="create">
				<div class="link">Create Agile Team</div>
			</Link>
		</div>
		<div class="right">
			Agile Team:
			<select bind:value={selected} on:blur={saveTeam}>
				{#each options as option}
					<option>{option.name}</option>
				{/each}
			</select>
			<button>settings</button>
			<button>login</button>
		</div>
	</div>
</header>
