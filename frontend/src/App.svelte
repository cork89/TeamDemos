<script>
	import Home from "./pages/Home.svelte";
	import Create from "./pages/Create.svelte";
	import Header from "./Header.svelte";
	import Footer from "./Footer.svelte";
	import NotFound from "./pages/NotFound.svelte";
	import { Router, Route } from "svelte-routing";
	export let url = "";
	export let team = "";

	function handleMessage(event) {
		team = event.detail;
	}
</script>

<style>
	:global(body) {
		background-color: #111;
	}
	/* .grid-container {
		display: grid;
		grid-template-columns: 1fr;
		grid-template-rows: 1fr 6fr 1fr;
		gap: 0px 0px;
		grid-template-areas:
			"header"
			"Main"
			"footer";
	}
	header {
		grid-area: header;
	}
	main {
		grid-area: Main;
		background-color: darkgray;
	}
	Footer {
		grid-area: footer;
	} */
</style>
<!-- 
<div class="grid-container">
	<Header />
	<Home name={name}/>
	<Footer />
</div> -->

<Router url="{url}">
	<Header on:message={handleMessage} />
  <div>
    <Route path="create" component="{Create}" /> 
    <!--for now the router just support case sensitive,
        one workaround colud be add two time the route
        Example.
       <Route path="About" component="{About}" /> 
    -->
		<Route path="/"><Home team={team}/></Route>
		<Route component="{NotFound}" />
  </div>
	<Footer />
</Router>
