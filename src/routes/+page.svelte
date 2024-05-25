<script>
  import {Hero} from "$lib";

</script>
<Hero />
<div class="exp"></div>

<style>

:global(:root) {
  font-size: 16px;
}

:global(*),
:global(*::after),
:global(*::before) {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.exp{
    height: 1rem;
}

</style>