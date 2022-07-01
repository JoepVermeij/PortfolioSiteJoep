<template>
<div class="body" >
  <PageLoader/>
  <Header/>
  <LeftSide/>
  <LandingPage/>
  <AboutMe/>
  <Portfolio />
  <ContactPage />
</div>
</template>

<script>
import Header from './components/Header.vue'
import LandingPage from './components/LandingPage.vue'
import Portfolio from './components/Portfolio.vue'
import LeftSide from './components/LeftSide.vue'
import AboutMe from './components/AboutMe.vue'
import ContactPage from './ContactPage.vue'
import PageLoader from './components/PageLoader.vue'
import AOS from 'aos'
import 'aos/dist/aos.css';


export default {
  name: 'App',
  components: {
    Header,
    LandingPage,
    Portfolio,
    LeftSide,
    AboutMe,
    ContactPage,
    PageLoader
  },
  mounted () {
    AOS.init()
  },
  created () {
    AOS.init({
      duration: 1200,
      disable: function() {
        var maxWidth = 600;
        return window.innerWidth < maxWidth;
      }
    })
}
}
let vh = window.innerHeight * 0.01;
document.documentElement.style.setProperty('--vh', `${vh}px`);
</script>

<style>
:root {
    --accent-black: #2e2424;
    --accent-purple: #91994A;
    --accent-white: #F2EBE2;
}
html{
  width: 100%;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  scroll-behavior:smooth;
}
body{
  width: 100%;
  padding: 0;
  margin: 0;
  background: var(--accent-black);
  color: var(--accent-black); 
  -ms-overflow-style: none; 
  scrollbar-width: none;
  overflow-x: hidden;
  box-sizing: border-box;
}
body::-webkit-scrollbar {
  display: none;
}
#app {
  font-family: Staatliches, Roboto, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
@media only screen and (hover: hover) and (max-width: 600px)  {
  html{
    overflow-x: hidden;
  }
}
</style>
