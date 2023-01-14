<template>
  <div id="Navbar">
  <div>
      <div @click="GoToHomePage" class="Nav-Item-Copyright">
        <a data-name="ⓒ JOEP VERMEIJ" class="copyright"> ⓒ JOEP VERMEIJ</a>
      </div>
      <div @click="GoToContact" class="Nav-Item">
        <a data-name="contact">CONTACT</a>
      </div>
      <div @click="GoToPortfolioSchool" class="Nav-Item">
        <a data-name="Education" >Education</a>
      </div>
      <div @click="GoToPortfolio" class="Nav-Item">
        <a data-name="portfolio" >PORTFOLIO</a>
      </div>
      <div @click="GoToAboutMe" class="Nav-Item">
        <a data-name="ABOUT ME">ABOUT ME</a>
      </div>
      <div class="Hamburger" >
        <div @click="DisplayHamburgerMenu" class="menu-btn" :class="menuOpen">
          <div class="menu-btn__burger"></div>
        </div>
        <div class="HamburgerMenu" :class="menuOpen">
          <div @click="GoToHomePage" class="HamburgerItem HomeItem">Home</div>
          <div @click="GoToAboutMe" class="HamburgerItem">About me</div>
          <div @click="GoToPortfolio" class="HamburgerItem">Portfolio</div>
          <div @click="GoToPortfolioSchool" class="HamburgerItem">School</div>
          <div @click="GoToContact" class="HamburgerItem">Contact</div>
        </div>
    </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Header',
  data() {
    return {
      HamburgerMenuDisplay: 'none',
      menuOpen:'',
    }
  },
  methods: {
  GoToPortfolio(){
      var element = document.getElementById('portfolio1');
      var top = element.offsetTop;
      var left = element.offsetLeft;
      window.scroll(left, top-104);
        this.menuOpen = '';
      this.HamburgerMenuDisplay= 'none';
    },
  GoToPortfolioSchool(){
      var element = document.getElementById('portfolio1school');
      var top = element.offsetTop;
      var left = element.offsetLeft;
      window.scroll(left, top-104);
        this.menuOpen = '';
      this.HamburgerMenuDisplay= 'none';
    },
    GoToHomePage(){
      window.scrollTo(0, 0);
        this.menuOpen = '';
      this.HamburgerMenuDisplay= 'none';
    },
    GoToAboutMe(){
      var element = document.getElementById('aboutMe');
      var top = element.offsetTop;
      var left = element.offsetLeft;
      window.scroll(left, top-104);
        this.menuOpen = '';
      this.HamburgerMenuDisplay= 'none';
    },
    GoToContact(){
      var element = document.getElementById('contact');
      var top = element.offsetTop;
      var left = element.offsetLeft;
      window.scroll(left, top-104);
        this.menuOpen = '';
      this.HamburgerMenuDisplay= 'none';
    },
    DisplayHamburgerMenu(){
      if(this.menuOpen == ''){
        this.menuOpen = 'open';
        this.HamburgerMenuDisplay= 'flex'; 
      }
      else{
        this.menuOpen = '';
        this.HamburgerMenuDisplay= 'none';
      }
    },  
  },
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#Navbar {
  z-index:9;
  position: fixed;
  height: 104px;
  width: 100vw;
  top: 0;
  background: var(--accent-black);
}
.Nav-Item, .Nav-Item-Copyright{
	cursor: pointer;
}
a {
    text-decoration: none;
    font-size: 2rem;
    float: right;
    padding: 1rem;
    margin: 1rem;
    overflow: visible;
    text-transform: uppercase;
	  transition: all 300ms ease;
	  position: relative;
	  width: fit-content;
    color: var(--accent-white);
}
a::before {
	content: attr(data-name);
	position: absolute;
	top: 1rem;
	left: -0.25rem;
	height: 1rem;
	overflow: hidden;
	transition: all 300ms ease;
	padding-left: 20px;
  background: var(--accent-black);
}

a::after {
	content: "";
	height: 0.1rem;
	width: 0;
	position: absolute;
	top: 47%;
	left: 50%;
	transform: translate(-50%, -50%);
	background: var(--accent-purple);
	transition: all 300ms ease;
  padding: 0;
  margin: 0;
}
@media (hover: hover) {   
  a:hover::before {
    top: 1rem;
    left: 0.1rem;
    color: var(--accent-purple);
  }
  a:hover::after {
    width: 90%;
    outline: 0.1rem solid  var(--accent-black);
  }
  a:hover{
    transform: skew(10deg);

  }
}
.copyright{
    float: left;
    font-size: 2rem;
    padding-top: 1rem;
}
.Hamburger{
  display: none;
}
@media only screen and (max-width: 800px) {
  .Nav-Item{
    display: none;
  }
  .copyright{
    padding: 1rem 0 1rem 1rem;
    margin: 1rem 0 1rem 1rem;
  }
  .Hamburger{
    display: block;
    float: right;
    height: 4.5rem;
    padding: 0 1rem 0 0;
    margin: 1rem 0;
  }
  .Hamburger > svg{  
    display: 'block';
    height: 4.5rem;
  }
  .menu-btn {
  position: relative;
  z-index: 23;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 4.5rem;
  height: 4.5rem;
  cursor: pointer;
  transition: all .5s ease-in-out;
  }
  .menu-btn__burger {
  width: 3rem;
  height:  0.5rem;
  background: var(--accent-white);
  border-radius: 5px;
  transition: all .5s ease-in-out;
  }
  .menu-btn__burger::before,
  .menu-btn__burger::after {
  content: '';
  position: absolute;
  width: 3rem;
  height: 0.5rem;
  background: var(--accent-white);
  border-radius: 5px;
  transition: all .5s ease-in-out;
  }
  .menu-btn__burger::before {
  transform: translateY(-16px);
  }
  .menu-btn__burger::after {
  transform: translateY(16px);
  }
  .menu-btn.open .menu-btn__burger {
  transform: translateX(-50px);
  background: transparent;
  }
  .menu-btn.open .menu-btn__burger::before {
  transform: rotate(45deg) translate(35px, -35px);
  background: var(--accent-black);
  }
  .menu-btn.open .menu-btn__burger::after {
  transform: rotate(-45deg) translate(35px, 35px);
  background: var(--accent-black);
  }
  .HamburgerMenu{
    position: absolute;
    bottom: 0;
    top: 0;
    left: 0;
    right: 0;
    height: 80vh;
    height: calc(var(--vh, 1vh) * 100 - 20vh);
    width: 100%;
    background: var(--accent-white);
    visibility: hidden;
    flex-direction: column;
    padding: 15vh 0;
    justify-content: space-around;
    opacity: 0;
    transform: translateX(100vw);
    transition: visibility 0s, opacity 1s, transform 0.5s ease-in-out;
  }
  .HamburgerMenu.open{
    opacity: 1;
    visibility: visible;
    transform: translateX(0);
  }
  .HamburgerItem{
    width: 100%;
    font-size: 4rem;
    padding: 1rem 0;
    text-align: center;
    border-bottom: 2px solid var(--accent-black);
  }
  .HomeItem{
    border-top: 2px solid var(--accent-black);
  }
  .HamburgerItem:active{
    color: var(--accent-purple);
    background: var(--accent-black);
  }
  .HamburgerMenuSvg{
    position: absolute;
    top:1rem;
    right:1rem;
    width: 4.5rem;
  }
  .HamburgerMenuSvg svg{
    height: 100%;
  }
  @media only screen and (max-width: 315px) {
    .Nav-Item-Copyright{
      display: none;
    }
  }
}
</style>
