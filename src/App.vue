// template principal
<template> 
  <Form/>
</template>

<script>
// import Botao from "./components/Botao.vue";
import Form from "./components/Form.vue"

export default {
  // name: 'App',
  components: {
    Form
  },
};
</script>

<style lang="stylus">
@import './assets/stylus/general.styl'

body
  font-family $font-primary 
  margin 0

</style>
