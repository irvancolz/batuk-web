
<script>

</script>

<div class={`container ${$$restProps.class}`}>
    <div class="light_container">
        <div class="lamp purple">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp purple odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp aqua">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp aqua odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp lime">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp lime odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp blue">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp blue odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp pink">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
        </div>
        <div class="lamp pink odd">
            <div class="lamp_foot"></div>
            <div class="lamp_body">
                <div class="flame"></div>
                <div class="light"></div>
                <div class="glare"></div>
            </div>
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
        --bg: rgb(9, 117, 225);
        --glare:linear-gradient(180deg, rgba(9, 117, 225, 0.751) 0%, rgba(9,118,225,0.751) 52%, rgba(9,118,225,0.2518384062609419) 87%, rgba(9,118,225,0) 100%);
        --light: linear-gradient(180deg, rgb(9, 117, 225) 0%, rgba(9, 117, 225,1) 20%,  rgba(9, 117, 225,0.3)  60%, rgba(9, 117, 225,0)  70%);
    }
    .lamp.purple{
        --bg: rgb(222, 23, 222);
        --glare:linear-gradient(180deg, rgba(222, 23, 222, 0.751) 0%, rgba(222, 23, 222,0.751) 52%, rgba(222, 23, 222,0.2518384062609419) 87%, rgba(222, 23, 222,0) 100%);
        --light: linear-gradient(180deg, rgb(222, 23, 222) 0%, rgba(222, 23, 222,1) 20%,  rgba(222, 23, 222,0.3)  60%, rgba(222, 23, 222,0)  70%);
    }
    .lamp.aqua{
        --bg:rgb(20, 227, 227);
        --glare:linear-gradient(180deg, rgba(20, 227, 227, 0.751) 0%, rgba(20, 227, 227,0.751) 52%, rgba(20, 227, 227,0.2518384062609419) 87%, rgba(20, 227, 227,0) 100%);
        --light: linear-gradient(180deg, rgb(20, 227, 227) 0%, rgba(20, 227, 227,1) 20%,  rgba(20, 227, 227,0.3)  60%, rgba(20, 227, 227,0)  70%);
    }
    .lamp.lime{
        --bg: rgb(83, 231, 27);
        --glare:linear-gradient(180deg, rgba(183, 231, 27, 0.751) 0%, rgba(183, 231, 27,0.751) 52%, rgba(183, 231, 27,0.2518384062609419) 87%, rgba(183, 231, 27,0) 100%);
        --light: linear-gradient(180deg, rgb(183, 231, 27) 0%, rgba(183, 231, 27,1) 20%,  rgba(183, 231, 27,0.3)  60%, rgba(183, 231, 27,0)  70%);
    }
    .lamp.pink{
        --bg: rgb(219, 44, 73);
        --glare:linear-gradient(180deg, rgba(219, 44, 73, 0.751) 0%, rgba(219, 44, 73,0.751) 52%, rgba(219, 44, 73,0.2518384062609419) 87%, rgba(219, 44, 73,0) 100%);
        --light: linear-gradient(180deg, rgb(219, 44, 73) 0%, rgba(219, 44, 73,1) 20%,  rgba(219, 44, 73,0.3)  60%, rgba(219, 44, 73,0)  70%);
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
        --time: 8s;
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
        animation-delay:4s;
    }
    .flame{
        content: '';
        position: absolute;
        z-index: 2;
        top: 100%;
        left: 50%;
        translate: -50% 0;
        width: 2rem;
        height: 300px;
        border-top-left-radius: 20px 20rem;
        border-top-right-radius:20px 20rem;
        border-bottom-left-radius: 1 10px;
        background: rgb(245,245,220);
        background: linear-gradient(180deg, rgba(245,245,220,1) 0%, rgba(255, 255, 245, 0.539) 30%, rgba(255,255,255,0.12578798609287467) 70%, rgba(255,255,255,0) 100%);
        filter: blur(2px);
    }


    .glare, .light{
        position: absolute;
        top: 100%;
        left: 50%;
        translate: -50% 0;
        border-top-left-radius: 3.75rem 50rem;
        border-top-right-radius: 3.75rem 50rem;
        border-bottom-left-radius: 2.5rem 5rem;
        border-bottom-right-radius: 2.5rem 5rem;
        height: 1000px;
        background: var(--bg);
    }
    
    .light{
        width: 3rem;
        border-top-left-radius: 1.25rem 20rem;
        border-top-right-radius: 1.25rem 20rem;
        z-index: 1;
        background: var(--light);
    }
    
    .glare{
        width: 5rem;
        background: var(--glare);
        filter: blur(5px);
    }

    @keyframes rotate {
        0%{
            rotate: 45deg;
        }
        50%{
            rotate: -45deg;
        }
        100%{
            rotate: 45deg;
        }
    }
</style>