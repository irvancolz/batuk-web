<script>
    import img2 from '$lib/images/house2.png'
    import img3 from '$lib/images/house3.png'
    import audioMp3 from '$lib/audio/audio.mp3'
    import audioWav from '$lib/audio/audio.wav'
    import audioOgg from '$lib/audio/audio.ogg'
    import doorFront from "$lib/images/Door.png"
    import doorBack from "$lib/images/Door-back.png"
    import play from '$lib/images/play.png'
    import pause from '$lib/images/pause.png'
    import {gsap} from 'gsap';
    import {ScrollTrigger} from 'gsap/dist/ScrollTrigger';
  import { onMount } from 'svelte';
  import LighShow from './LighShow.svelte';

    gsap.registerPlugin(ScrollTrigger)

    let audio;

    function togglePlay(){
        if(!audio.paused){
            audio.pause()
            return
        }
        audio.currentTime = 0
        audio.play()
    }

    function initFakeEvent(){
        const evt = new Event('click')
        audio.dispatchEvent(evt)
    }

    onMount(() => {
        audio.volume = .1
        const fadeDuration = 10
        const scale = 1.05
        const tl = gsap.timeline({ scrollTrigger: {
            trigger:'.container',
            end: '+=1000px',
            pin: true,
            scrub: true
        }})

        tl.to('.door', {rotateY: '-105deg', duration: 20})
        .fromTo('.door', { scale: 1, xPercent: 0, duration: 3,}, { scale: scale, xPercent: -2, duration: fadeDuration})
        .to('.light', { opacity: 0}, '<')
        .fromTo('.door_front', {opacity: 1,   duration: fadeDuration, }, {opacity: 0,   duration: 3}, '<')
        .fromTo('.door_back', {opacity: 1,   duration: fadeDuration, }, {opacity: 0,  duration: 3}, '<')
        .to('.background', { opacity: 0}, '<')
        .to('.door_overlay', { opacity: 0}, '<')
        .to('.outside_open', { opacity: 0, scale: scale, duration: fadeDuration}, '<')
        .call(initFakeEvent)
        .to('.inside', {filter: 'brightness(1)', duration: .3})
        .from(".lightshow", {opacity: 0})
        .to('.inside', { duration: 40})

    })

</script>

<div class="container">
    <img class="inside" src={img3} alt="">
    <button class="play_btn" on:click={togglePlay}>hello</button>
    <LighShow class='lightshow' />
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
    <div class="door_overlay"></div>
    <div class="door">
        <img class="door_front" src={doorFront} alt="">
        <img class="door_back" src={doorBack} alt="">
    </div>
    <audio bind:this={audio} class="bg_music" loop>
        <source src={audioMp3} type="audio/mpeg">
        <source src={audioOgg} type="image/ogg">
        <source src={audioWav} type="image/wav">
    </audio>
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
        /* filter: brightness(0.1); */
    }

    .play_btn{
        position: absolute;
        aspect-ratio: 1;
        display: grid;
        place-items: center;
        width: 2rem;
        right: 16.25vw;
        top: 56.5vh;
        /* background-color: transparent; */
        outline-color: transparent;
        border-color: transparent;
        cursor: pointer;
    }
    .door, .door_overlay{
        position: absolute;
        aspect-ratio: 1034/1800;
        width: 17.5vw;
        top: 50%;
        left: 50%;
        translate: -52% -43%;
    }
    .door{
        transform-style: preserve-3d;
        transform-origin: left;
        transform: perspective(2300px);
    }
    .door_overlay{
        background-color: #0b0401;
    }
    .door img{
        position: absolute;
        inset: 0 0 0 0;
        object-fit: cover;
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
        filter: drop-shadow(0px 0px 20px white);
    } 

    .light_beige{
        --border-col: rgba(245, 245, 220, 0.63);
    }

    .light_left{
        rotate: 40deg;
        animation: light_left 2.5s ease-in-out infinite;
    }

    .light_left.light_beige.first, .light_right.light_beige.first{
        animation-delay: 1s;
    }
    .light_left.light_purple, .light_right.light_purple{
        animation-delay: .5s;
    }

    .light_right{
        rotate: -40deg;
        animation: light_right 2.5s ease-in-out infinite;
        right: 0;
    }

    .bg_music{
        height: 1px;
        width: 1px;
        overflow: hidden;
        opacity: 0;
        position: absolute;
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