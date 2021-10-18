<script>
	import Navbar from "./Navbar.svelte"
	import Footer from "./Footer.svelte"
	import Chooser from "./Chooser.svelte"
	import SoloRegistration from "./SoloRegistration.svelte"
	import TeamRegistration from "./TeamRegistration.svelte"
	import Success from "./Success.svelte"
	import Failed from "./Failed.svelte"
	import Tracker from "./Tracker.svelte"
	let hide_solo = true;
	let hide_team = true;
	let success = false;
	let failed = false;
	let tracker = "";
	let main_url="https://expocon.pythonanywhere.com";
	//let main_url="http://localhost:5000";
</script>

<Navbar/>
<Tracker bind:tracker/>

{#if success}
	<Success bind:hide_solo bind:hide_team/>
{/if}

{#if failed}
	<Failed bind:hide_solo bind:hide_team/>
{/if}

{#if !hide_solo}
	<SoloRegistration bind:success bind:failed bind:main_url bind:tracker/>
{/if}

{#if !hide_team}
	<TeamRegistration bind:success bind:failed bind:main_url bind:tracker/>
{/if}

<Chooser bind:hide_solo bind:hide_team bind:success bind:failed/>
<Footer/>
