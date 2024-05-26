<script>
    import img2 from '$lib/images/house2.png'
    import img3 from '$lib/images/house3.png'
    import doorFront from "$lib/images/Door.png"
    import doorBack from "$lib/images/Door-back.png"
    import {gsap} from 'gsap';
    import {ScrollTrigger} from 'gsap/dist/ScrollTrigger';
  import { onMount } from 'svelte';

    gsap.registerPlugin(ScrollTrigger)

    onMount(() => {
        const tl = gsap.timeline({ scrollTrigger: {
            trigger:'.container',
            end: '+=1000px',
            pin: true,
            scrub: true
        }})
        tl.to('.door', {rotateY: '-105deg', duration: 10})
        .fromTo('.door', { scale: 1, xPercent: 0, duration: 3, yPercent: 0}, { scale: 1.5, xPercent: -25,yPercent: 3, duration: 3})
        .fromTo('.door_front', {opacity: 1,   duration: 3, }, {opacity: 0,   duration: 3}, '<')
        .fromTo('.door_back', {opacity: 1,   duration: 3, }, {opacity: 0,  duration: 3}, '<')
        .to('.light', { opacity: 0}, '<')
        .to('.background', { opacity: 0}, '<')
        .to('.outside_open', { opacity: 0, scale: 1.5, duration: 3}, '<')
        .to('.inside', {filter: 'brightness(1)', duration: .3})
        .fromTo('.inside', { scale: 1.5, duration: 3}, { scale: 1, duration: 3})

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
    <div class="door">
        <img class="door_front" src={doorFront} alt="">
        <img class="door_back" src={doorBack} alt="">
    </div>
</div>

<style>
    .container{
        width: 100vw;
        max-width: 100vw;
        aspect-ratio: 665/375;
        position: relative;
        overflow: hidden;
    }

    .inside{
        filter: brightness(0.1);
        transform-origin: 10% 50%;
    }

    .door{
        position: absolute;
        aspect-ratio: 1028/1784;
        width: 17.5vw;
        top: 50%;
        left: 50%;
        translate: -52% -42.90%;
        transform-style: preserve-3d;
        transform-origin: left;
        transform: perspective(2300px);
    }

    .door img{
        position: absolute;
        inset: 0 0 0 0;
        object-fit: contain;
        min-height: 100%;
        min-width: 100%;
        width: 100%;
        height: 100%;
        -webkit-backface-visibility: hidden; /* Safari */
        backface-visibility: hidden;
    }
    .door_back{
        transform: rotateY(-180deg);
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
        background-color: #26262636;
        transition: backround-color .2s ease-out;
        /* animation: party_bg 2s linear infinite; */
    }

    .outside_open{
        object-fit: contain;
        width: 100%;
        height: 100%;
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