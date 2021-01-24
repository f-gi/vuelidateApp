// template principal
<template> 
  <div>
    <Form/> <br/>
    <Carousel/> <br/>
    <FetchPrevent/> <br/>
  </div>
</template>

<script>
// import Botao from "./components/Botao.vue";
import Form from "./components/Form.vue";
import FetchPrevent from "./components/FetchPrevent.vue";
import Carousel from "./components/Carousel.vue";

export default {
  // name: 'App',
  components: {
    Form,
    FetchPrevent,
    Carousel
  },
};
</script>

<style lang="stylus">
@import './assets/stylus/general.styl'

body
  font-family $font-primary 
  margin 0
</style>
