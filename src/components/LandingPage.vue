<template>
  <div class="LandingPage">
    <div class="skillscontainer">
    <div data-aos="slide-right" data-aos-delay="2200"  Class="LandingPage-Skills1">
      <h3>FLEXIBLE</h3>
    </div>
    <div data-aos="slide-right" data-aos-delay="2400"  Class="LandingPage-Skills2">
      <h3>PRAGMATIC</h3>
    </div>
    <div data-aos="slide-right" data-aos-delay="2600"  Class="LandingPage-Skills3">
      <h3>FULLSTACK</h3>
    </div>
    <div data-aos="slide-right" data-aos-delay="2800" Class="LandingPage-Skills4">
      <h3>Developer</h3>
    </div>
    <div class="image"></div>
    <div @click="GoToAboutMe"  id="downarrow">
      <img class="downarrow1"  src="../assets/down-arrow.svg" alt="down arrow image" />
      <img class="downarrow2"  src="../assets/down-arrow-green.svg" alt="down arrow image" />
    </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LandingPage',
  methods: {
    GoToAboutMe(){
      var element = document.getElementById('aboutMe');
      var top = element.offsetTop;
      var left = element.offsetLeft;
      window.scroll(left, top-104);
    }
  },
}
</script>

<style scoped>
#downarrow{
  position: absolute;
  display: flex;
  margin-left: calc(75% - 2rem);
  bottom: 0;
  width:4rem;
}
.downarrow1{
  opacity: 1;
transform: translateY(0rem);
transition: 1s all ease-in-out;
}
.downarrow2{
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  opacity: 0;
  transform: translateY(-1rem) ;
transition: 1s all ease-in-out;
}

.LandingPage{
  width: 100%;
  min-height: 100vh;
  background: var(--accent-white);
  overflow: hidden;
}

.LandingPage-Skills1{
  left: 40%;
  width: 100%;
  position: absolute;
  white-space: nowrap;
  top: -5vh;
  font-size: 10rem;
  font-weight: normal;
  animation: skillsflow 8s linear -2s infinite;
}
.LandingPage-Skills2{
  left: 42.5%;
  width: 100%;
  position: absolute;
  top: 15vh;
  font-size: 10rem;
  font-weight: normal;
  animation: skillsflow 8s linear -1s infinite;
  white-space: nowrap;
}
.LandingPage-Skills3{
  left: 45%;
  width: 100%;
  position: absolute;
  top: 35vh;
  font-size: 10rem;
  font-weight: normal;
  animation: skillsflow 8s linear infinite;
  white-space: nowrap;
 
}
.LandingPage-Skills4{
  left: 47.5%;
  width: 100%;
  position: absolute;
  white-space: nowrap;
  top: 55vh;
  font-size: 10rem;
  font-weight: normal;
  animation: skillsflow 8s linear infinite;
 
}
.image{
  display: none;
}
@media (hover: hover) {  
  #downarrow:hover > .downarrow2
  {
  opacity: 1;
  transform: translateY(0rem);
  }
  #downarrow:hover > .downarrow1
  {
  transform: translateY(4rem);
  opacity: 0;
  }
  #downarrow:hover{
  cursor: pointer;
  }

 }
@media only screen and (max-width: 600px) {  
  #downarrow:active > .downarrow2
  {
  opacity: 1;
  transform: translateY(0rem);
  }
  #downarrow:active > .downarrow1
  {
  transform: translateY(4rem);
  opacity: 0;
  }
  #downarrow:active{
  cursor: pointer;
  }
  .LandingPage{
    margin-left: 0;
    position: relative;  
    min-height: calc(24rem + 100vw);
    height: calc(var(--vh, 1vh) * 100);
  }
  .image{
    position:absolute;
    display: block;
    height: calc(100vw);
    bottom: 0;
    width: 100%;
    background: url('../assets/PortfolioJoep1.png');
    background-size: cover;
    background-position-x: center;

  }
  .skillscontainer{
    padding-top: 6.5rem;
    min-height: 17.5rem;
    height: calc(100% - 100vw - 6.5rem);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  h3{
    margin:0;
  }
  .LandingPage-Skills1{
    margin:0;
    position: relative;
    font-size: 3rem;
    left: 15%;
    width: 90%;
    top: unset;
  }
  .LandingPage-Skills2{
    margin:0;
    position: relative;
    font-size: 3rem;
    left: 17.5%;
    width: 87.5%;
    top: unset; 
  }
  .LandingPage-Skills3{
    margin:0;
    position: relative;
    font-size: 3rem;
    left: 20%;
    width: 85%;
    top: unset; 
  }
  .LandingPage-Skills4{
    margin:0;
    position: relative;
    font-size: 3rem;
    left: 22.5%;
    width: 82.5%;
    top: unset; 
  }
  .downarrow1{
    content:url("../assets/down-arrow-white.svg")
  }
  #downarrow{
  margin-left: calc(50% - 2rem);
}
}
</style>
