<script>
  import {Hero} from "$lib";

</script>
<Hero />

<style>

:global(:root) {
  font-size: 16px;
}
:global(body){
  max-width: 100vw;
  overflow-x: hidden;
}
:global(*),
:global(*::after),
:global(*::before) {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}


</style>