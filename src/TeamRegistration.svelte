<script>
	export let success = false;
	export let failed = false;
	export let main_url;

	let warn = false;
	let alert = "";

	let team_name = "";
	let school = "";
	let contact = "";
	let player_1 = "";
	let player_2 = "";
	let player_3 = "";
	let tracker = "";
	let events = [];


	function submit() {
		if(team_name == "" || school == "" || contact == "" || player_1 == "") {
			warn = true;
			alert = "please fill all required field"
		} 

		else if (!Number(contact)) {
			warn = true;
			alert = "Number should be a numeric value. No need to include country code"

		}

		else if (events.length == 0) {
			warn = true;
			alert = "Please select one or more event from the check list"

		}

		else if ((events.includes("10") || events.includes("11")) && (player_2 == "" || player_3 == ""))  {
			warn = true;
			alert = "For 'Team Math Contest' and 'Math Relay-tionship' your team needs minimum three team members."	
		}

		else {
			let tracker = localStorage.getItem("t");

			let data = {
				name: team_name,
				school: school,
				player_1: player_1,
				player_2: player_2,
				player_3: player_3,
				tracker: tracker,
				joined_events: events
			}

			console.log(JSON.stringify(data));

			async function register() {
				console.log("ok")
				const response = await fetch(main_url+'/team/'+contact, 
			  	{
			  		method: 'post',	
					headers: {
				    	'Accept': 'application/json, text/plain, */*',
				    	'Content-Type': 'application/json'
				  	},
				  	body: JSON.stringify(data)
				})
			  const res = await response.json();
			  return res;
			}


			async function get_name_data() {
				console.log("ok")
				const response = await fetch(main_url+'/team_name/'+team_name)
			  const res = await response.json();
			  return res;
			}


			get_name_data().then(names => {
				if(names.length == 0) {
					register().then(response => {
					  validate(response);
					});
				} else {
					warn = true;
					alert = "The teamname '"+team_name+"' is already taken. Try with a new teamname"
				}
			});
		}
	}

	function validate(res) {
		console.log(res)
		if (res.status == "done commiting data to database") {
			success = true;
			failed = false;
		} else {
			success = false;
			failed = true;
		}
	}

</script>

<style>
	.hide {
		display: none;
	}
</style>

<div class="container card my-4 p-4 bg-dark">
	<h3 class="mb-4">Team Event Registration</h3>
		
		<!--team name-->
		<div class="mb-4">
			<label for="exampleFormControlInput1" class="form-label">Unique Team Name</label>
			<input bind:value={team_name} type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="example: The Domi-Matrix, So Obtuse ...">
		</div>

		<!--school name-->
		<div class="mb-4">
			<label for="exampleFormControlInput1" class="form-label">Name of Institue</label>
			<input bind:value={school} type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="My awesome school">
		</div>

		<!--contact-->
		<div class="mb-4">
			<label for="exampleFormControlInput1" class="form-label">Mobile Number to Contact</label>
			<input bind:value={contact} type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="01#########">
		</div>

		<div>
			<label class="form-label mb-3">Select the events for your team</label>
		</div>


		<!-- Team Math Contest -->	
		<div class="form-check m-2">
		  <input bind:group={events} name="events" value="10" class="form-check-input" type="checkbox" id="flexCheckDefault">
		  <label class="form-check-label" for="flexCheckDefault">
		  	Team Math Contest
		  </label>
		</div>

		<!-- event Math Relay-tionship -->	
		<div class="form-check m-2">
		  <input bind:group={events} name="events" value="11" class="form-check-input" type="checkbox" id="flexCheckDefault">
		  <label class="form-check-label" for="flexCheckDefault">
		  	Math Relay-tionship
		  </label>
		</div>

		<!-- event MathCrafts -->	
		<div class="form-check m-2">
		  <input bind:group={events} name="events" value="12" class="form-check-input" type="checkbox" id="flexCheckDefault">
		  <label class="form-check-label" for="flexCheckDefault">
		  	Math Crafts
		  </label>
		</div>

		<!--Player 1-->
		<div class="mb-4 mt-3">
			<label for="exampleFormControlInput1" class="form-label">Name of 1st Teammate*</label>
			<input bind:value={player_1} type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="fearless team leader">
		</div>

		<!--Player 2-->
		<div class="mb-4">
			<label for="exampleFormControlInput1" class="form-label">Name of 2nd Teammate</label>
			<input bind:value={player_2} type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="[optional for MathCrafts]">
		</div>

		<!--Player 3-->
		<div class="mb-4">
			<label for="exampleFormControlInput1" class="form-label">Name of 3rd Teammate</label>
			<input bind:value={player_3} type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="[optional for MathCrafts]">
		</div>


		{#if warn}
			<div class="alert alert-danger my-4" role="alert">
				We found some problems.
				<br>
				The software detects that:
				<ul>
					<li>{alert}</li>
				</ul>
			</div>
		{/if}

		<div class="mt-4 d-flex flex-row-reverse">
			<button type="submit" class="btn btn-success mx-2" on:click={submit}>Proceed</button>
			<a href="/" type="button" class="btn btn-outline-danger mx-2">Discard</a>
		</div>
	<!--/form-->
</div>