<template>
  <div id="portfolio1school" ref="last">
    <div data-aos="fade-left" class="PortfolioItem">
      <div @mousemove="MovingAnimation" @mouseleave="OutAnimation" @mouseenter="InAnimation" class="portfoliocontainer" id="portfoliocontainer">
        <div :style="`transform:rotateY(${xAxis}deg) rotateX(${yAxis}deg); transition:${transition}`" class="PortfolioCard">
            <h1 :style="`transform:translateZ(${ZTitle}px)`">PXL University of Applied Sciences and Arts</h1>
            <button @click="ShowModal" :style="`transform:translateZ(${ZButton}px)`">Read More</button>
        </div>
      </div>
      <div class="portfolio__bg">
        <img src="../assets/pxlbackground.png" alt="" />
      </div>
      
      <div @click="GoToAboutMe" id="downarrow3">
        <img class="downarrow3-1" src="../assets/down-arrow.svg" alt="down arrow image" />
        <img class="downarrow3-2"  src="../assets/down-arrow-green.svg" alt="down arrow image" />
      </div>
    </div>
    <div id="myModal2" class="modal" >
      <div class="modal-content">
        <div class="modaldescription">
          <h2>PXL University of Applied Sciences and Arts</h2>
          <h3>Links</h3>
          <ul>
            <li><a :href="`${publicPath}Logboek_VermeijJoep.pdf`" download="">Logboek</a></li>
            <li><a :href="`${publicPath}Feedback_Ontwikkeling_VermeijJoep.pdf`" download="">Feedback Ontwikkeling</a></li>
            <li><a :href="`${publicPath}WPL3-FG-werkprestaties_VermeijJoep.pdf`" download="">Functioneringsgesprek WerkPrestaties</a></li>
            <li><a :href="`${publicPath}WPL3-EG-werkprestaties_VermeijJoep.pdf`" download="">Evalutiesgesprek WerkPrestaties</a></li>
            <li><a :href="`${publicPath}WPL3-EG-werkkwaliteiten_VermeijJoep.pdf`" download="">Evalutiesgesprek WerkKwaliteiten</a></li>
            <li><a :href="`${publicPath}Pitch_SalviaBioElectronics_VermeijJoep.pdf`" download="">Pitch werkplek</a></li>
            <li><a :href="`${publicPath}Probleem-Advies_VermeijJoep.pdf`" download="">Probleemsituatie + advies/actie</a></li>
            <li><a :href="`${publicPath}Reflectie_leerdoelen_kwaliteiten_VermeijJoep.pdf`" download="">Reflectie Begin WerkplekLeren</a></li>
          </ul>
          <button @click="CloseModal" class="modalclose">close</button>
        </div>
        <div class="modalphoto">
          <h1>EindReflectie</h1>
          <div  class="modalreflectiedescriptioncontainer">
          <div class="modalreflectiedescription">
            <h2>Positieve realisaties</h2>
            <ul>
              <li>Ik kan beter mijn wensen en verwachtingen uiten.</li>
              <li>Ik heb meer ervaring in het gebruiken van frameworks, platformen en coderen.</li>
              <li>Ik kan beter werken met Git.</li>
            </ul>
            <h2>Positief op de werkplek</h2>
            <ul>
              <li>Hoe het bedrijf werkt en dat resultaatgerichtheid een belangrijke waarde is.</li>
              <li>Een diverse en professionele cultuur maar toch sociale en aangename werksfeer.</li>
              <li>Er zijn tijden waar je rustig kan bijpraten, maar ook momenten dat je hard moet werken.</li>
            </ul>
            <h2>Moeilijke Punten</h2>
            <ul>
              <li>Een goede balans vinden tussen werk, school en persoonlijk leven.</li>
              <li>Betere documentatie schrijven.</li>
            </ul></div>
            <div class="modalreflectiedescription">
            <h2>Samenwerking</h2>
            <ul>
              <li>De samenwerking met mijn collega’s verliep zeer goed, ik kon duidelijk mijn voortgang en de verwachtingen van mijn werk communiceren.</li>
              <li>Ik kan er wel voor zorgen dat ik betere voorbereiding heb voor een meeting, zorgen dat de dingen die ik wil laten zien ook daadwerkelijk voorbereid en functioneel zijn.</li>
            </ul>
            <h2>Beeld van de job</h2>
            <ul>
              <li>Het werk dat ik er nu doe is praktisch hetzelfde in omgang en verwachtingen van als ik er fulltime zou werken, het enigste verschil is dat ik niet 5 dagen maar 3 dagen werk.</li>
            </ul>
            <h2>Vooruitblikken op WPL4</h2>
            <ul>
              <li>Ik wil dieper gaan in het ontwikkelen van core business projecten zoals het ontwikkelen van testen voor de firmware of het ontwikkelen van de patiënt app.</li>
              <li>Een uitdaging hiervan is dat het vele niveaus hoger ligt dan mijn huidig werk en dat ik goede documentatie moet schrijven en me aan de normen van de huidige code moet houden.</li>
              <li>Ik moet goed rekening houden met quality assurance, aangezien ik in de gezondheids sector stage doe.</li>
            </ul>
          </div></div>
        </div>
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
      publicPath: process.env.BASE_URL,
      xAxis: 0,
      yAxis: 0,
      transition: 'all 0.5s ease',
      ZTitle: 0,
      ZButton: 0,
      ModalTransform: 0,
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
      this.yAxis = (window.innerHeight*3.25 - event.pageY) /30;
      this.ZTitle = 35;
      this.ZButton = 25;
      },
    OutAnimation() {
      this.transition = 'all 0.5s ease';
      this.xAxis = 0;3
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
    
  },
  mounted: function() {
    document.addEventListener("click", (event) => {
      let modal = document.getElementById("myModal2");
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
  height: 4rem;
}
.downarrow3-1{
  opacity: 1;
transform: translateY(0rem);
transition: 1s all ease-in-out;
width: 100%;
height: 100%;
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
  width:4rem;
  height: 4rem;
}
#portfolio1school{
  width: 100%;
  height: calc(100vh - 6rem);
  z-index: -8;
  background: var(--accent-black);
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
a {
  color: var(--accent-black);
}
a:hover {
  color: var(--accent-purple);
}
.modaldescription{
  width: 26rem;
  padding-left: 1rem;
}
.modaldescription h2{
  font-size: 2.5rem;
  border-bottom: 3px solid var(--accent-black);
}
.modaldescription h3{
  font-size: 2rem;
  padding: 0;
  margin: 0;
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
  display: flex;
  height: 40rem;
  width: 84rem;
  background: var(--accent-black);
  color: var(--accent-white);
  overflow: hidden;
  flex-direction: column;
}
.modalphoto h1{
  font-size: 3rem;
  text-align: center;
}
.modalphoto img{
  width: 100%;
}
.modalreflectiedescriptioncontainer{
  display: flex;

}
.modalreflectiedescription{
  width: 42rem;
  padding: 0 2rem;
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
  color: var(--accent-white);
  background-color: #182c4c;
  padding: 0.7rem 2rem 0.7rem 2rem;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  transition: all ease-in-out 500ms;
  text-decoration: none;
}
button:hover {
  color: var(--accent-purple);
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
  max-height: calc(100vh - 6rem);
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
  background: url(../assets/pxlcard.png);
  box-shadow: 0 1rem 1rem black;
  background-size: cover;
  background-repeat: no-repeat;
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
  @media only screen and (max-width: 1200px) {
    .portfolio__bg{
      display: none;
    }
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
      max-height: calc(var(--vh, 1vh) * 100 - 6rem);
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
