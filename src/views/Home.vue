<template>
  <div class="home">
    <Carousel
      :navegacion="true"
      :paginacion="true"
      :startAutoPlay="false"
      :timeout="5000"
      class="carousel"
      v-slot="{ currentSlide }">
      <Slide v-for="(slide, index) in carouselSlides" :key="index">
        <div v-show="currentSlide === index + 1" class="slide-informacion">
          <img :src="require(`../assets/${slide}.jpg`)" alt="" />
        </div>
      </Slide>
        
    </Carousel>
  </div>
</template>
<script>
import Carousel from '../components/Carousel.vue';
import Slide from '../components/Slide.vue';




export default {
  name: 'Home',
  components: {
    Carsel,
    Slide,
   
    
  },
  setup() {
    const carouselSlides = ['Dp1','Dp2','Dp3'];
    return { carouselSlides };
  },
  
  
};
</script>

<style lang="scss" scoped>
  .carousel {
    max-height: 80vh;
    height: 80vh;

  .slide-informacion {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    max-height: 100%;
    height: 100%;
    img {
      min-width: 100%;
      height: 100%;
      object-fit: cover;


    }
  }
}
</style>
