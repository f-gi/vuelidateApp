<template lang="html">
    <button  class="btn" type="submit" @click="click">
        {{ text }} 
    </button>
</template>

<script>
// import Botao from "./components/Botao.vue";

export default {
    data() {
        return{
            text: "Enviar",
        }
    },
    methods: {
        click: function(){
            console.log("clicou");
        }
    }
}
</script>

<style lang="stylus">
@import '../assets/stylus/general.styl'

.btn 
    background-color $color-primary
    font-family $font-primary
    font-size 16px
    height 30px
    width 100px
    border-radius 10px
    font-weight 700
    margin 15px auto
    @media screen and (min-width: 600px)
        margin 25px 0
</style>