<template lang="html">
    <div class="wrap">
        <h2> Criar conta </h2>
        <form action="#">
            <div class="input-content">
                <!-- {{ $v.name }} -->
                <label for="nome">Nome*</label>
                <input 
                    v-model="$v.name.$model" 
                    type="text"
                    id="nome" 
                    @change="$v.name.$touch()" 
                    :class=" $v.name.$error ? 'input-focus' : ''"
                />
                <span v-if="$v.name.$error"> Este campo é requerido </span>
            </div> 
            <div class="input-content">
                <!-- {{ $v.mail }} -->
                <label for="email">E-mail*</label>
                <input 
                    v-model="$v.mail.$model" 
                    type="email" id="email" 
                    :class=" $v.mail.$error ? 'input-focus' : ''"/>
                <!-- <span v-if="$v.mail.$model"> Este campo é requerido </span>  -->
                <span v-if="$v.mail.$error"> Este E-mail é invalido </span>
            </div>
            <div class="input-content">
                <!-- {{ $v.password }} -->
                <label for="senha">Senha*</label>
                <input 
                    v-model="$v.password.$model" 
                    type="password" 
                    id="senha" 
                    :class=" $v.password.$error ? 'input-focus' : ''"/>
                <span v-if="$v.password.$error"> Este campo é requerido </span>
            </div>
            <div class="input-content">
                <!-- {{ $v.conf_password }} -->
                <label for="confsenha">Confirme sua senha*</label>
                <input 
                    v-model="$v.conf_password.$model" 
                    type="password" 
                    id="confsenha" 
                    :class=" $v.conf_password.$error ? 'input-focus' : ''"/>
                <!-- <span v-if="$v.conf_password.$sameAs"> Senhas diferentes </span> -->
                <span v-if="$v.conf_password.$err"> As senhas informadas não coincidem </span>
            </div>
            <div class="input-content">
                <label for="msg">Mensagem:</label>
                <textarea v-model="message" id="msg"></textarea>
            </div> 
            <button  class="btn" @click.prevent="$v.$touch()">Criar</button>
            <!-- <Botao/> -->
        </form>
        
    </div>    
</template>

<script>
// import Botao from "./Botao.vue";
import { required, email, sameAs } from 'vuelidate/lib/validators'

export default {
    components: {
        // Botao
    },
    data: () => ({
        name: '',
        mail: '',
        password: '',
        conf_password: '',
        message: ''
    }),
    validations: {
        name: { required },
        mail: { required, email },
        password: { required },
        conf_password: { 
            required,
            sameAs: sameAs('password'),
        },
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

.input-focus
    border-color $color-primary   

.wrap   
    background-color $color-zero
    width 100% 
    padding 10px
    text-align center
    @media screen and (min-width: 600px)
        max-width 40%
        margin 80px auto
        padding-left 50px
        text-align left
    form 
        font-family $font-primary
        font-size 20px
        label, input, textarea
            display block 
        input, textarea
            border-radius 10px
            width 100%
        input
            height 25px
        input:focus 
            font-size 20px   
        textarea
            height 85px
        .input-content
            margin 15px auto
            width 80%
            @media screen and (min-width: 600px)
                margin-top 20px
                margin 20px 0 
            span
                font-size 14px
                color $color-primary 
            .input-focus
                border-color $color-primary  
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