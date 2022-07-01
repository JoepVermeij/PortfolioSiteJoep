<template>
 <div class="AboutMe" id="aboutMe">
     <div class="AboutMeContainer">
        <h2>ABOUT ME</h2>
        <div class="AboutMeInfo">
         <h3>C#</h3>
         <div class="progressbar">
            <div data-aos="slide-right" class="csharp"></div>
         </div>
         <h3>Javascript</h3>
         <div class="progressbar">
            <div data-aos="slide-right" class="js"></div>
         </div>
         <h3>HTML/CSS</h3>
         <div class="progressbar">
            <div data-aos="slide-right" class="html"></div>
         </div>
         <h3>Vue.js</h3>
         <div class="progressbar">
            <div data-aos="slide-right" class="vuejs"></div>
         </div>
         <h3>SQL</h3>
         <div class="progressbar">
            <div data-aos="slide-right" class="sql"></div>
         </div>
         <h3>Python</h3>
         <div class="progressbar">
            <div data-aos="slide-right" class="python"></div>
         </div>
         <div class="history">
            <div class="year"><h4>2021</h4></div>
            <p>From accountant to programmer.</p>
            <p>I am Joep Vermeij a junior developer driven by my passion for technology, Creativity and analytical thinking.</p>
            <p>In september I started learning programming at PXL university.</p>
            <div class="year"><h4>2022</h4></div>
            <p>This year I'm focusing on my studies and developing my first project with a team.</p>
            <p>You can find my first project 'ElectricVehiclesEverywhere' below.</p>
            <p>After my first year as a student I developed this portfolio page, started learning python and now I'm open for new opportunities.</p>
         </div>
         </div>
     </div>
    <div @click="GoToPortfolio"  id="downarrow2">
      <img class="downarrow2-1" src="../assets/down-arrow-white.svg" alt="down arrow image" />
      <img class="downarrow2-2"  src="../assets/down-arrow-green.svg" alt="down arrow image" />
    </div>
 </div>
</template>

<script>
export default {
    name: 'AboutMe',
    methods: {
        GoToPortfolio(){
      var element = document.getElementById('portfolio1');
      var top = element.offsetTop;
      var left = element.offsetLeft;
      window.scroll(left, top-104);
    }
    }
}
</script>

<style scoped>
#downarrow2{
  position: absolute;
  display: flex;
  z-index: 8;
  margin-left: calc(75% - 4rem);
  bottom: 1rem;
  width:4rem;
}
.downarrow2-1{
  opacity: 1;
transform: translateY(0rem);
transition: 1s all ease-in-out;
}
.downarrow2-2{
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  opacity: 0;
  transform: translateY(-1rem) ;
transition: 1s all ease-in-out;
}
.AboutMe {
    width: 100%;
    overflow: hidden;
    background: var(--accent-black) ;
    color: var(--accent-white);
    position: relative;
    min-height: calc(100vh - 6rem);
    padding-bottom: 6rem;
}
p{
    font-family: Arial, Helvetica, sans-serif;
    font-weight: bold;
    width: 30rem;
    font-size: 1.1rem;
    padding: 0;
    margin-top: 1rem;
    width: 100%;
}
.AboutMeContainer{
    width: 50%;
    margin-left: 50%;
}
.AboutMeInfo{
    padding: 0 0 0 2%;
}
.history{
    margin: 1.5rem 2rem;
    width: 80%;
}
h2{
    font-size: 4rem;
    text-align: center;
    margin-bottom: 0;
}
h3{
    margin-left: 2rem;
}
h4{
    font-size: 1.4rem;
    margin: 2rem 0 0 0;
}
.year{
  position: relative;
  width: 100%;
}
.year::after{
    position: absolute;
    content: "";
    height: 2px;
    width: 100%;
    background: var(--accent-white);
}
.progressbar{
    border: 1px solid var(--accent-white);
    margin: 1rem 1rem 1rem 2rem;
    height: 1rem;
    width: 80%;
    border-radius: 2rem;
    overflow: hidden;
}
.csharp{
    background: var(--accent-white);
    width: 80%;
    height: 100%;
}
.vuejs{
    background: var(--accent-white);
    width: 55%;
    height: 100%;
}
.js{
    background: var(--accent-white);
    width: 90%;
    height: 100%;
}
.html{
    background: var(--accent-white);
    width: 95%;
    height: 100%;
}
.sql{
    background: var(--accent-white);
    width: 85%;
    height: 100%;
}
.python{
    background: var(--accent-white);
    width: 30%;
    height: 100%;
}

@media (hover: hover) {  

  #downarrow2:hover > .downarrow2-2{
    opacity: 1;
  transform: translateY(0rem);
  }
  #downarrow2:hover > .downarrow2-1{
    transform: translateY(4rem);
    opacity: 0;
  }
  #downarrow2:hover{
    cursor: pointer;
  }

 }
@media only screen and (max-width: 600px) {
  #downarrow2:active > .downarrow2-2{
    opacity: 1;
  transform: translateY(0rem);
  }
  #downarrow2:active > .downarrow2-1{
    transform: translateY(4rem);
    opacity: 0;
  }
  #downarrow2:active{
    cursor: pointer;
  }
  .AboutMe{
    min-height: calc(var(--vh, 1vh) * 100 - 6rem);
  }
  .AboutMeContainer{
    width: 100%;
    margin: 0 0 5rem 0;
  }
  .progressbar{
    width: 80%;
    margin-left: 2rem;
  }
  .AboutMeInfo{
    width: 96%;
    padding: 0 2%;
    
  }
  #downarrow2{
    margin-left: calc(50% - 2rem);
  }
}
</style>