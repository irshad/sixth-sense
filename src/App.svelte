<script>
	import { Router, Route } from "svelte-routing";
    import Dashboard from "./pages/Dashboard.svelte";
    import SixthSense from "./pages/SixthSense.svelte";
    import RotationError from "./components/RotationError.svelte";
</script>

<div class="wrapper">
    <Router>
        <Route path="/" component={Dashboard} />
        <Route path="game" component={SixthSense} />
    </Router>
	<!-- <SixthSense/> -->
</div>
<div class="warning-message">
	<RotationError />
</div>

<style>
	.warning-message { display: none; }
	@media only screen and (orientation: portrait) {
		.wrapper { display: none; }
		.warning-message { display: block; }
	}
	@media only screen and (orientation: landscape) {
		.warning-message { display: none; }
	}
</style>