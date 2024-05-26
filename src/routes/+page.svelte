<script>
  import {Hero, IntroSection} from "$lib";
  import Lenis from "@studio-freight/lenis";
  import ScrollTrigger from "gsap/dist/ScrollTrigger";
  import { onMount } from "svelte";
  
  onMount(() => {
    const lenis = new Lenis({
      duration: 1.5,
      easing: (x) => 1 - Math.pow(1 - x, 4),
    });

    function lenisRaf(time) {
      lenis.raf(time);
      ScrollTrigger.update();
      requestAnimationFrame(lenisRaf);
    }

    lenis.on("scroll", () => {
      ScrollTrigger.update();
    });

    requestAnimationFrame(lenisRaf);
  })
</script>

<Hero />
<IntroSection />

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