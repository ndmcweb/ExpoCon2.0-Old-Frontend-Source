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
    registration <strong>Unsuccessful</strong>
    <br>
    <ul>
      <li>please make sure you entered a valid email</li>
    </ul>
    <br>
    <strong>Please contact us if the problem continues</strong>
  </div>
</div>