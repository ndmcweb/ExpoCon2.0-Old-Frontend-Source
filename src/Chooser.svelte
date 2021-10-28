<script type="text/javascript">
  	import {scrollToTop} from "svelte-scrollto";

	export let hide_solo;
	export let hide_team;
	export let success;
	export let failed;
	
	function go_solo() {
		hide_solo = false;
		hide_team = true;
		success = false;
		failed = false;
		scrollToTop();
	}

	function go_team() {
		hide_solo = true;
		hide_team = false;
		success = false;
		failed = false;
		scrollToTop();
	}
</script>

<style>
	.flex-awesome {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}
</style>

<div class="container my-4">
	<div class="container">
	  
	  <div class="row">
	    
	    <div class="col-md">
	    	<div class="card w-auto h-100 bg-dark" style="width: 18rem;">
	    	  <div class="card-body flex-awesome">
	    	  	<div>
	    	  		<h5 class="card-title">Team Segments</h5>
	    	  		<h6 class="card-subtitle mb-2 text-muted">Join with your Team</h6>
	    	  	</div>
	    	    <div>
	    	    	<ul>
	    	    		<li>Team Math Contest</li>
	    	    		<li>Math Relay-tionship</li>
	    	    		<li>Math Crafts (team members are optional)</li>
	    	    	</ul>
	    	    	<br>
	    	    	<p>
	    	    		Please take note:
	    	    		<br>Team registration is separate from solo one.
	    	    		So, you can use the same mobile number used for solo registration
	    	    	</p>
	    	    </div>

	    	    <button type="button" href="#" class="card-link btn btn-primary">
	    	    		REGISTRATION IS CLOSED
	    	    </button>
<!-- 	    	    <button type="button" href="#" class="card-link btn btn-primary" on:click={go_team}>
	    	    		REGISTER TEAM SEGMENTS
	    	    </button> -->
	    	  </div>
	    	</div>
	    </div>
	    
	    <div class="col-md">
	    	<div class="card w-auto h-100 bg-dark" style="width: 18rem;">
	    	  <div class="card-body flex-awesome">
	    	    <div>
	    	    	<h5 class="card-title">Solo Segments</h5>
	    	    	<h6 class="card-subtitle mb-2 text-muted">Register for individual segments</h6>
	    	    </div>
	    	    <div>
	    	    	<ul>
	    	    		<li>Math Olympiad</li>
	    	    		<li>Math Maker</li>
	    	    		<li>Math Meme</li>
	    	    		<li>Thoughts on Papyrus</li>
	    	    		<li>Applied Calculus</li>
	    	    		<li>Quiz</li>
	    	    		<li>Sudoku</li>
	    	    		<li>The Formula King</li>
	    	    		<li>Decipherio</li>
	    	    	</ul>
	    	    </div>
	    	    <button type="button" href="#" class="card-link btn btn-success">
	    	    	REGISTRATION IS CLOSED
	    	    </button>
<!-- 	    	    <button type="button" href="#" class="card-link btn btn-success" on:click={go_solo}>
	    	    	REGISTER SOLO SEGMENTS
	    	    </button> -->
	    	  </div>
	    	</div>
	    </div>
	  
	  </div>
	
	</div>
</div>