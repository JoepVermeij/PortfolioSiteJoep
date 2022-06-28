<template>
    <div class="LandingPage-Image">
    </div>
</template>

<script>
export default {
  name: 'LeftSide',
}
</script>

<style scoped>
.LandingPage-Image {
  width: 50%;
  height: 100vh;
  position:fixed;
  z-index: 5;
  background-position-y: 100%; 
    background-position-x: 45%;
    background-image: url('../assets/PortfolioJoep3.png');
    background-size: cover;
}
@media only screen and (max-width: 600px) {
  .LandingPage-Image{
    display: none;
}}
</style>
