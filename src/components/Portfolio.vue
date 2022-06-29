<template>
  <div id="portfolio1" ref="last">
    <div data-aos="fade-left" class="PortfolioItem">
      <div @mousemove="MovingAnimation" @mouseleave="OutAnimation" @mouseenter="InAnimation" class="portfoliocontainer" id="portfoliocontainer">
        <div :style="`transform:rotateY(${xAxis}deg) rotateX(${yAxis}deg); transition:${transition}`" class="PortfolioCard">
            <h1 :style="`transform:translateZ(${ZTitle}px)`"><span class="accent-green">E</span>LECTRIC <span class="accent-green">V</span>EHICLES <span
                    class="accent-green">E</span>VERYWHERE</h1>
            <button @click="ShowModal" :style="`transform:translateZ(${ZButton}px)`">Read More</button>
        </div>
      </div>
      <div class="portfolio__bg">
        <img src="../assets/Werkplekleren.png" alt="" />
      </div>
      
      <div @click="GoToAboutMe" id="downarrow3">
        <img class="downarrow3-1" src="../assets/down-arrow.svg" alt="down arrow image" />
        <img class="downarrow3-2"  src="../assets/down-arrow-green.svg" alt="down arrow image" />
      </div>
    </div>
    <div id="myModal" class="modal" >
      <div class="modal-content">
        <div class="modaldescription">
          <h2>ELECTRIC VEHICLES EVERYWHERE</h2>
          <h3>School Project</h3>
          <ul>
            <li>5 developers</li>
            <li>5 months</li>
            <li>Fully functional front to back</li>
            <li>Hire an electric vehicle</li>
            <li>Frontend: HTML/CSS/JS</li>
            <li>Backend: .NET/NODE.JS/SQL</li>
            <li><a  href="https://github.com/JoepVermeij/Projects/tree/main/ElectricVehiclesEverywhere"><button>Github</button></a></li>
          </ul>
          <button @click="CloseModal" class="modalclose">close</button>
        </div>
        <div class="modalphoto">
        <project-photo v-for="(Photo, index) in Photos" :key="Photo" :index="index" :visiblePhoto="visiblePhoto" :direction="direction">
             <img :src="require(`../assets/WerkplekLeren1/${Photo}`)" alt="projectfoto">
            </project-photo>
        </div>
        <div @click="NextPhoto" class="nextarrow"><img src="../assets/next.svg" alt="next"></div>
        <div @click="PreviousPhoto" class="previousarrow"><img src="../assets/previous.svg" alt="previous"></div>
      </div>
      
    </div>
  </div>
</template>

<script>
import ProjectPhoto from "./ProjectPhoto.vue"
export default {
  name: 'Portfolio',
  components: {
    ProjectPhoto ,
  },
  data() {
    return {
      xAxis: 0,
      yAxis: 0,
      transition: 'all 0.5s ease',
      ZTitle: 0,
      ZButton: 0,
      ModalTransform: 0,
      Photos: [
        'Modal-1.png',
        'Modal-2.png',
        'Modal-3.png',
        'Modal-4.png',
        'Modal-5.png',
        'Modal-6.png',
        'Modal-7.png',
      ],
      visiblePhoto:0,
      direction: ''
    }
  },
  computed: {
    TransitionNone(){
       this.transition= 'none';
    },
  },
  methods: {
    GoToAboutMe(){
      var element = document.getElementById('contact');
      var top = element.offsetTop;
      var left = element.offsetLeft;
      window.scroll(left, top-104);
    },
    MovingAnimation(event) {
      this.xAxis = (window.innerWidth*3/4 - event.pageX) /30;
      this.yAxis = (window.innerHeight*2.3 - event.pageY) /30;
      this.ZTitle = 35;
      this.ZButton = 25;
      },
    OutAnimation() {
      this.transition = 'all 0.5s ease';
      this.xAxis = 0;
      this.yAxis = 0;     
      this.ZTitle = 0; 
      this.ZButton = 0;

    },
    InAnimation(){
      setTimeout(() => {this.transition= 'none';}, 300)
    },
    ShowModal() {
        this.ModalTransform = 1;
    },
    CloseModal() {
        this.ModalTransform = 0;
    },
    NextPhoto(){
      this.direction = 'left';
      if (this.visiblePhoto == 6){
        this.visiblePhoto = 0;
      } 
      else {this.visiblePhoto++;}  

    },
    PreviousPhoto(){
      this.direction = 'right';
      if (this.visiblePhoto == 0){
        this.visiblePhoto = 6;
      } 
      else {this.visiblePhoto--;}     
    },
    
  },
  mounted: function() {
    document.addEventListener("click", (event) => {
      let modal = document.getElementById("myModal");
      console.log(event.target);
      if (event.target == modal) {
        this.ModalTransform = 0;
      } 
    })
  }
  
}

</script>

<style scoped>
#downarrow3{
  position: absolute;
  display: flex;
  z-index: 6;
  bottom: 2rem;
  width:4rem;
}
.downarrow3-1{
  opacity: 1;
transform: translateY(0rem);
transition: 1s all ease-in-out;
}
.downarrow3-2{
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  opacity: 0;
  transform: translateY(-2rem) ;
transition: 1s all ease-in-out;
}
#portfolio1{
  width: 100%;
  height: calc(100vh - 6rem);
  z-index: -8;
  background: var(--accent-white);
}
.modal {
  display: flex; 
  position: fixed; 
  z-index: 10;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgb(0,0,0); 
  background-color: rgba(0,0,0,0.4); 
  justify-content: center;
  align-items: center;
  transform: scale(v-bind(ModalTransform));
}
.modal-content {
  position: inherit;
  background-color: var(--accent-white);
  margin-top: 7rem;
  width: 110rem;
  height: 40rem;
  border-radius: 1rem;
  overflow: hidden;
  display: flex;
  transform: scale(v-bind(ModalTransform));
  transition:
    transform 1s cubic-bezier(.04,.64,.51,.82),
    opacity 1s cubic-bezier(.04,.64,.51,.82);
  
}
.modal-content button{
  margin: -0.5rem 0 0 0;
  font-size: 1rem;
  background: var(--accent-black);
  color: var(--accent-white);
}
.modaldescription{
  width: 26rem;
  padding: 2rem;
}
.modaldescription h2{
  font-size: 2.5rem;
  border-bottom: 3px solid var(--accent-black);
}
.modaldescription h3{
  font-size: 2rem;
}
.modaldescription ul{
  list-style: '-   ';
  padding: 0;
}
.modaldescription li{

  margin: 1rem;
  font-size: 1.5rem;
}
.modalphoto{
  height: 40rem;
  width: 80rem;
  background: BLACK;
  overflow: hidden;
}
.modalphoto img{
  width: 100%;
}
.accent-green {
    color: #00c040;
}
.PortfolioCard h1{
  margin-top: 200px;
  font-family: "Koliko Bold", sans-serif;
  font-size: 1.8rem;
  color: #182c4c;
  transition: all 0.5s ease-out;
}
button {
  display: block;
  margin: 5rem auto;
  font-family: Roboto, sans-serif;
  font-size: larger;
  color: #00c040;
  background-color: #182c4c;
  padding: 0.7rem 2rem 0.7rem 2rem;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  transition: all ease-in-out 500ms;
  text-decoration: none;
}
button:hover {
  color: #ffffff;
}
a{
  text-decoration: none;
}
.PortfolioItem {
    width: 50%;
    z-index: 3;
    margin-left: 50%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
}
.portfoliocontainer{
  width: 600px;
  height: 650px;
  display: flex;
  justify-content: center;
  align-items: center;
  perspective: 1300px;
}
.PortfolioCard {
  text-align: center;
  transform-style: preserve-3d;
  width: 400px;
  height: 550px;
  background: url(../assets/WerkpleklerenCard.png);
  box-shadow: 0 1rem 1rem black;
}
.portfolio__bg{
  position: absolute;
  margin-left: 0;
  width: 100%;
  height: 100%;
  z-index: -5;
  overflow: hidden;
}
.portfolio__bg img{
  position: absolute;
  height: calc(100% - 4rem);
  width: 100%;
  padding: 2rem;
  filter: blur(1rem);
}
.modalclose{
  width: 25rem;
}
.nextarrow{
  position: absolute;
  align-self: center;
  right: 3rem;
  width: 4rem;
  cursor: pointer;
}
.nextarrow:hover > img, .previousarrow:hover > img{
    filter: invert(91%) sepia(100%) saturate(0%) hue-rotate(297deg) brightness(105%) contrast(101%);
}
.previousarrow{
  position: absolute;
  align-self: center;
  left: 33rem;
  width: 4rem;
  cursor: pointer;
}
@media (hover: hover) {  

#downarrow3:hover > .downarrow3-1{
  transform: translateY(4rem);
  opacity: 0;
}
#downarrow3:hover > .downarrow3-2{
  opacity: 1;
transform: translateY(0rem);
}
#downarrow3:hover{
  cursor: pointer;
}
.modal-content button:hover{
  color: var(--accent-purple);
}
 }
  @media only screen and (max-width: 600px) {
    
    #downarrow3:active > .downarrow3-1{
      transform: translateY(4rem);
      opacity: 0;
    }
    #downarrow3:active > .downarrow3-2{
      opacity: 1;
    transform: translateY(0rem);
    }
    #downarrow3:active{
      cursor: pointer;
    }
    .modal-content button:active{
      color: var(--accent-purple);
    }
    #portfolio1{
      height: calc(var(--vh, 1vh) * 100 - 6rem);
    }
    .modalphoto{
      display: none;
    }
    .modal-content {
      margin-top: 0.1rem;
      height: unset;
      width: 90%;
    }
    .PortfolioItem {
      margin: 0;
      width: 100%;
    }
    .portfoliocontainer{
      width: 100%;
      margin: 0;
    }
    .portfolio__bg{
      margin: 0;
    }
    .modaldescription{
      width: 100%;
    }
    .modalclose{
      width: 100%;
    }
    .nextarrow, .previousarrow{
      display: none;
    }
    }
</style>
