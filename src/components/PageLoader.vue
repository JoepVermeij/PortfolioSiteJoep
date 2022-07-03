<template>
    <div class="page-loader">
        <transition 
        appear
        name="fade"
        @enter="PageLoadAnimation">
        <div class="page-loader1">
            <h1>WELCOME</h1>
        </div>      
        </transition>
        <transition 
        appear
        name="fade"
        @enter="PageLoadAnimation2">
        <div class="page-loader2">
        </div>      
        </transition>
    </div>
</template>

<script>
import gsap from 'gsap'
export default {
    data() {
        return {
        }
    },
    methods:{
        PageLoadAnimation(el){
            console.log("PageLoad");
            gsap.to(el, {
                y: -2000,
                display: 'none',
                duration: 2,
                delay: 1
            })
        },
        PageLoadAnimation2(el){
            console.log("PageLoad");
            gsap.to(el, {
                y: -2000,
                display: 'none',
                duration: 2,
                delay: 1.5
            })
        }
    }
}
</script>

<style scoped>
    .page-loader1 {
        z-index: 31;
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background: var(--accent-black);
        color: var(--accent-white);
    }
    h1{
        font-size: 10rem;
    }
    .page-loader2 {
        z-index: 29;
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 100vw;
        height: 100vh;
        background: var(--accent-purple);
    }
    @media only screen and (max-width: 800px) {
        
    h1{
        font-size: 6rem;
    }
    }
</style>
