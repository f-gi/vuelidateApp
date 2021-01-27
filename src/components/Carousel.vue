<template lang="html">
  <div class="sliderContainer">
    <h2 class="sliderContainer__title"> Carrossel </h2>
    <!-- não da pra usar .length dentro do v-if? -->
    <VueSlickCarousel v-if="pokeTeste.length>9" v-bind="settings" class="sliderContainer__carrossel">
        <div  v-for="(pokemon, index) in pokeTeste" :key="index" class="sliderContainer__for">
            <div>
                <img :src="pokemon.sprites.front_default"> 
            </div>        
        </div>
    </VueSlickCarousel>
  </div>
</template>

<script>
  import VueSlickCarousel from 'vue-slick-carousel';
  import 'vue-slick-carousel/dist/vue-slick-carousel.css';
  import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css';
  import axios from "axios";

  export default {
    name: 'Carousel',
    components: { VueSlickCarousel },
    data: () => ({
        pokeTeste:[],
        pokepoke: [],
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
    mounted() {
        this.getPokemons();
    },
    methods: {
        async getPokemons() {
            // get de https://pokeapi.co/api/v2/pokemon/ rertorna __ob__ observer
            for(let i=1; i<=10; i++){
                const response = await axios.get("https://pokeapi.co/api/v2/pokemon/"+i);
                this.pokeTeste.push(response.data);
            }
            const response = await axios.get("https://pokeapi.co/api/v2/pokemon?limit=10");
            this.pokepoke = response.data;
            console.log(this.pokepoke);
        },
    },
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
    .slick-slide img
        display inline
</style>