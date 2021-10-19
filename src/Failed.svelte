<script>
  import {scrollToTop} from "svelte-scrollto";

  export let hide_solo;
  export let hide_team;

  hide_team = true;
  hide_solo = true;

  scrollToTop();
</script>

<div class="container">
  <div class="alert alert-danger my-4" role="alert">
    Registration <strong>Unsuccessful</strong>
    <br>
    <ul>
      <li>Please make sure you entered a valid email</li>
    </ul>
    <ul>
      <li>Please make sure you're not using the same phone number twice</li>
    </ul>
    <br>
    <strong>Please contact us if the problem continues</strong>
  </div>
</div>