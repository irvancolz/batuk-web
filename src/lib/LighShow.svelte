
<script>

</script>

<div class={`container ${$$restProps.class}`}>
    <div class="light_container">
        <div class="lamp">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
        <div class="lamp odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
        <div class="lamp">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
        <div class="lamp odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
        <div class="lamp">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
        <div class="lamp odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
        <div class="lamp">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
        <div class="lamp odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body"></div>
        </div>
    </div>
</div>
<style>
    .container{
        position: absolute;
        inset: 0 0 0 0;
    }
    .light_container{
        display: flex;
        justify-content: space-evenly;
    }
    .lamp{
        position: relative;
    }
    .lamp_foot, .lamp_body{
        border: 2px solid rgb(11, 11, 11);
        background-color: rgb(0, 0, 0);

    }
    .lamp_foot{
        position: absolute;
        top: 0;
        left: 50%;
        translate: -50% 0;
        height: 1.5rem;
        width: .5rem;
    }
    .lamp_body{
        --light: rgba(245, 245, 220, 0.525);
        --time: 4s;
        position: relative;
        translate: 0 1rem;
        height: 4rem;
        width: 2rem;
        transform-origin: top center;
        border-top-left-radius:.5rem 5rem;
        border-top-right-radius: .5rem 5rem;
        animation: rotate var(--time) ease-in-out infinite;
    }

    .lamp.odd .lamp_body{
        animation-delay:2s;
    }
    .lamp_body::after{
        content: '';
        position: absolute;
        top: 100%;
        left: -9.1rem;
        width: 20rem;
        border-bottom: 10000px solid var(--light);
        border-left: 9.1rem solid transparent;
        border-right: 9.1rem solid transparent;
        filter: blur(2px) drop-shadow(0px 0px 5rem var(--light));
    }
    @keyframes rotate {
        0%{
            rotate: 20deg;
        }
        50%{
            rotate: -20deg;
        }
        100%{
            rotate: 20deg;
        }
    }
</style>