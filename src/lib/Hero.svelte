<script>
    import img1 from '$lib/images/house1.png'
    import img2 from '$lib/images/house2.png'
    import img3 from '$lib/images/house3.png'
    import {gsap} from 'gsap';
    import {ScrollTrigger} from 'gsap/dist/ScrollTrigger';
  import { onMount } from 'svelte';

    gsap.registerPlugin(ScrollTrigger)

    onMount(() => {
        const tl = gsap.timeline({ scrollTrigger: {
            trigger:'.container',
            start: "bottom 99%",
            end: '+=1000px',
            pin: true,
            scrub: true
        }})
        tl.to('.outside_closed', { opacity: 0})
        .to('.light', { opacity: 0})
        .to('.outside_open', { opacity: 0})
        .to('.background', { opacity: 0})
        .fromTo('.inside', {filter: 'brightness(0.1)'}, {filter: 'brightness(1)'})

        // addEventListener('scroll', () => tl.play())
    })

</script>

<div class="container">
    <img class="inside" src={img3} alt="">
    <div class="background">
        <div class="light light_right light_beige first"></div>
        <div class="light light_right light_purple"></div>
        <div class="light light_right light_beige"></div>
        <div class="light light_left light_beige first"></div>
        <div class="light light_left light_purple"></div>
        <div class="light light_left light_beige"></div>
    </div>
    <div class="background"></div>
    <img class='outside_open' src={img2} alt="">
    <img  class="outside_closed" src={img1} alt="">
</div>

<style>
    .container{
        position: relative;
        height: 100vh;
        overflow: hidden;
    }

    .inside{
        filter: brightness(0.1);
    }

    img, .background{
        position: absolute;
        inset: 0 0 0 0 ;
        width: 100%;
        height: 100%;
        min-height: 100%;
        min-width: 100%;
    }

    .background{
        transition: backround-color .2s ease-out;
        animation: party_bg 2s linear infinite;
    }

    .light{
        --border-col:  rgba(93, 9, 142, 0.486);
        position: absolute;
        transform-origin: bottom center;
        bottom: 0;
        border-top: 900px solid var(--border-col);
        border-left: 1rem solid transparent;
        border-right: 1rem solid transparent;
        height: 0px;
        width: 3rem;
    }

    .light_beige{
        --border-col: rgba(245, 245, 220, 0.63);
    }
    .light_purple{
    }

    .light_left{
        rotate: 40deg;
        animation: light_left 2.5s linear infinite;
    }

    .light_left.light_beige.first, .light_right.light_beige.first{
        animation-delay: 1s;
    }
    .light_left.light_purple, .light_right.light_purple{
        animation-delay: .5s;
    }

    .light_right{
        rotate: -40deg;
        animation: light_right 2.5s linear infinite;
        right: 0;
    }


    @keyframes party_bg {
        0%{
            background-color: rgba(255, 0, 0, 0.173);
        }
        40%{
            background-color: rgba(255, 255, 0, 0.1348);
        }
        60%{
            background-color: rgba(0, 128, 0, 0.123);
        }
        80%{
            background-color: rgba(0, 0, 255, 0.177);
        }
        100%{
            background-color: rgba(255, 0, 0, 0.173);
        }
    }

    @keyframes light_left{
        0%{
            rotate: 30deg;
        }
        50%{
            rotate: 60deg;
        }
        100%{
            rotate: 30deg;
        }
    }
    @keyframes light_right{
        0%{
            rotate: -30deg;
        }
        50%{
            rotate: -60deg;
        }
        100%{
            rotate: -30deg;
        }
    }

</style>