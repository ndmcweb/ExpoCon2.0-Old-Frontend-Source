<script>

	//export let hide_solo;
	export let tracker;
	export let success = false;
	export let failed = false;
	export let main_url;


	let warn = false;
	let alert = "";

	let name = "";
	let school = "";
	let mobile = "";
	let email = "";
	let player_class = "";
	//let tracker = "";
	let events = "";


	function submit() {
		if(name == "" || school == "" || mobile == "" || email == "" || player_class == "") {
			warn = true;
			alert = "please fill all required field"
		} 

		else if (!Number(mobile)) {
			warn = true;
			alert = "Number should be a numeric value. No need to include country code"

		}

		else if (events.length == 0) {
			warn = true;
			alert = "Please select one or more event from the check list"

		}

		else {
			//let tracker = localStorage.getItem("t");

			let data = {
				name: name,
				school: school,
				email: email,
				player_class: player_class,
				joined_events: events,
				tracker: tracker
			}

			console.log(JSON.stringify(data));

			async function register() {
				console.log("ok")
				const response = await fetch(main_url+'/player/'+mobile, 
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

			register().then(response => {
			  validate(response)
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

<!--p>hi {name} {school} {mobile} {email} {player_class} {events}</p-->
<!--div class="container card my-4 p-4 bg-dark" class:hide={hide_solo}-->
<div class="container card my-4 p-4 bg-dark">
	<h3 class="mb-4">Solo Event Registration</h3>
	<!--form-->
		<div class="mb-4">
			  <label for="exampleFormControlInput1" class="form-label">Name</label>
			  <input bind:value={name} name="name" type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="Valorant Pixie">
			</div>

			<!-- school -->
			<div class="mb-4">
			  <label for="exampleFormControlInput1" class="form-label">Name of Institute</label>
			  <input bind:value={school} name="school" type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="My Awesome School">
			</div>

			<!-- mobile -->
			<div class="mb-4">
			  <label for="exampleFormControlInput1" class="form-label">Mobile Number</label>
			  <input bind:value={mobile} name="mobile" type="text" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="013########">
			</div>

			<!-- email -->
			<div class="mb-4">
			  <label for="exampleFormControlInput1" class="form-label">Email address</label>
			  <input bind:value={email} name="email" type="email" class="form-control text-light bg-transparent" id="exampleFormControlInput1" placeholder="pixie.awesome@gmail.com">
			</div>

			<!-- class -->
			<div class="mb-4">
				<label for="exampleFormControlInput1" class="form-label">Select Class</label>
				<select bind:value={player_class} name="class" class="form-select" aria-label="select your class">
				  <option value="1">Class 6</option>
				  <option value="2">Class 7</option>
				  <option value="3">Class 8</option>
				  <option value="4">Class 9</option>
				  <option value="5">Class 10</option>
				  <option value="6">SSC 21</option>
				  <option value="7">Class 12</option>
				  <option value="8">HSC 21</option>
				</select>
			</div>

			<div>
				<label class="form-label mb-3">Select the events you want to join</label>
			</div>


			<!-- event Math Olympiad -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="1" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Math Olympiad
			  </label>
			</div>

			<!-- event Mathematical Content Making -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="2" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Math Maker
			  </label>
			</div>

			<!-- event Math Meme Competition -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="3" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Math Meme
			  </label>
			</div>

			<!-- event Mathematical Fiction Writing -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="4" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Thoughts on Papyrus
			  </label>
			</div>

			<!-- event Applied Calculus -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="5" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Applied Calculus
			  </label>
			</div>

			<!-- event Quiz -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="6" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Quiz
			  </label>
			</div>

			<!-- event Sudoku -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="7" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Sudoku
			  </label>
			</div>

			<!-- event THE FORMULA KING / THE QUICK SOLVER -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="8" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	The Formula King
			  </label>
			</div>

			<!-- event decipherio -->	
			<div class="form-check m-2">
			  <input bind:group={events} name="events" value="9" class="form-check-input" type="checkbox" id="flexCheckDefault">
			  <label class="form-check-label" for="flexCheckDefault">
			  	Decipherio
			  </label>
			</div>

			{#if warn}
				<div class="alert alert-danger my-4" role="alert">
					The form seems incomplete.
					<br>
					Please provide all informations. which includes:
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