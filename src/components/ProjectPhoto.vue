<template>	
    <div class="container">
<transition :name="direction">
        <div v-show="visiblePhoto===index" class="photo-slide">
        <slot></slot>
        </div>
</transition>
    </div>
</template>

<script>
export default {
    name: 'ProjectPhoto',
    props: {
         visiblePhoto: String,
         index: String,
         direction: String,
    }
}
</script>

<style scoped>
.container{
    position: absolute;
    overflow: hidden;
}
.left-enter-active{
  animation: leftInAnimation 0.4s ease-in-out;
}
.left-leave-active{

  animation: leftOutAnimation 0.4s ease-in-out;
}
@keyframes leftInAnimation{
  from {transform: translateX(100%);}
  to{transform: translateX(0)}
}
@keyframes leftOutAnimation{
  from {transform: translateX(0);}
  to{transform: translateX(-100%)}
  
}
.right-enter-active{
  animation: rightInAnimation 0.4s ease-in-out;
}
.right-leave-active{

  animation: rightOutAnimation 0.4s ease-in-out;
}
@keyframes rightInAnimation{
  from {transform: translateX(-100%);}
  to{transform: translateX(0)}
}
@keyframes rightOutAnimation{
  from {transform: translateX(0);}
  to{transform: translateX(100%)}
  
}
</style>