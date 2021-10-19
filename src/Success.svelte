<script>
  import {scrollToTop} from "svelte-scrollto";
  export let hide_solo;
  export let hide_team;

  hide_team = true;
  hide_solo = true;

  scrollToTop();
</script>

<div class="container">
  <div class="alert alert-success my-4" role="alert">
    Your Registration was <strong>Successful</strong> <br>
    Currently we're not sending email confirmation.
  </div>
</div>