<template lang="html">
  <div class="sliderContainer">
    <h2 class="sliderContainer__title"> Carrossel </h2>
    <VueSlickCarousel v-bind="settings">
        <div><h3>1</h3></div>
        <div><h3>2</h3></div>
        <div><h3>2</h3></div>
        <div><h3>2</h3></div>
        <div><h3>2</h3></div>
    </VueSlickCarousel>
  </div>
</template>

<script>
  import VueSlickCarousel from 'vue-slick-carousel'
  import 'vue-slick-carousel/dist/vue-slick-carousel.css'
  import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

  export default {
    name: 'Carousel',
    components: { VueSlickCarousel },
    data: () => ({
        settings:{
            "arrows": true,
            "dots": true,
            "dotsClass": "slick-dots custom-dot-class",
            "edgeFriction": 0.35,
            "infinite": false,
            "speed": 500,
            "slidesToShow": 1,
            "slidesToScroll": 1            
        }
    }),
  }
</script>

<style lang="stylus">

@import '../assets/stylus/config.styl'

.sliderContainer   
    background-color $color-zero
    width 100% 
    padding 10px
    text-align center
    @media screen and (min-width: 600px)
        max-width 45%
        margin 0 auto
        text-align center
    .sliderContainer__title
        font-family $font-primary 
    .slick-dots
        position static
        align-items center
        text-align center
    .slick-prev:before, .slick-next:before
        color $color-primary
    .slick-next
        right 5px
    .slick-prev
        // tira o click do botão 
        left 5px
    
</style>