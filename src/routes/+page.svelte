<script>
  import {Hero} from "$lib";
  import { onMount } from "svelte";
import ScrollTrigger from "gsap/dist/ScrollTrigger";
import Lenis from "@studio-freight/lenis";



  // onMount(() => {
  //   const lenis = new Lenis({
  //     duration: 1.5,
  //     easing: (x) => 1 - Math.pow(1 - x, 4),
  //   });

  //   function lenisRaf(time) {
  //     lenis.raf(time);
  //     ScrollTrigger.update();
  //     requestAnimationFrame(lenisRaf);
  //   }

  //   lenis.on("scroll", () => {
  //     ScrollTrigger.update();
  //   });

  //   requestAnimationFrame(lenisRaf);
  // })

</script>
<Hero />

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


</style>