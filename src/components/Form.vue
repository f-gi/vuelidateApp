<template lang="html">
<!-- section -->
    <div class="container"> <!-- container -->
        <h2> Criar conta </h2>
        <div class="message">
            <p> ola </p>
        </div>    
        <!-- não precisa action="#" -->
        <form >
            <fieldset>
                <div class="input-content">
                    <!-- {{ $v.name }} -->
                    <label for="nome">Nome*</label>
                    <input 
                        v-model="$v.criarConta.name.$model" 
                        type="text"
                        id="nome" 
                        @change="$v.criarConta.name.$touch()" 
                        :class="{'input-focus':$v.criarConta.name.$error}"
                    />
                    <span v-if="$v.criarConta.name.$error"> Este campo é requerido </span>
                </div> 
                <div class="input-content">
                    <!-- {{ $v.mail }} -->
                    <label for="email">E-mail*</label>
                    <input 
                        v-model="$v.criarConta.mail.$model" 
                        type="email" 
                        id="email" 
                        :class="{'input-focus':$v.criarConta.mail.$error}"
                    />
                    <!-- <span v-if="$v.mail.$model"> Este campo é requerido </span>  -->
                    <span v-if="$v.criarConta.mail.$error"> Este E-mail é invalido </span>
                </div>
                <div class="input-content">
                    <!-- {{ $v.password }} -->
                    <label for="senha">Senha*</label>
                    <input 
                        v-model="$v.criarConta.password.$model" 
                        type="password" 
                        id="senha" 
                        :class="{'input-focus':$v.criarConta.password.$error}"
                    />
                    <span v-if="$v.criarConta.password.$error"> Este campo é requerido </span>
                </div>
                <div class="input-content">
                    <!-- {{ $v.conf_password }} -->
                    <label for="confsenha">Confirme sua senha*</label>
                    <input 
                        v-model="$v.criarConta.conf_password.$model" 
                        type="password" 
                        id="confsenha" 
                        :class="{'input-focus':$v.criarConta.conf_password.$error}"/>
                    <!-- <span v-if="$v.conf_password.$sameAs"> Senhas diferentes </span> -->
                    <span v-if="$v.criarConta.conf_password.$error"> As senhas informadas não coincidem </span>
                </div>
                <div class="input-content">
                    <label class="check" for="receberEmail">Aceitar receber e-mails?</label>
                    <input class="check" type="checkbox" v-model="receberEmail" id="receberEmail" />
                </div>    
                <div class="input-content">
                    <label class="check" for="termos">Aceita os Termos e Condições?</label>
                    <input class="check" type="checkbox" v-model="termos" id="termos" />
                </div>    
                <div class="input-content">
                    <label for="msg">Mensagem:</label>
                    <textarea v-model="message" id="msg"></textarea>
                </div> 
                <!-- @click.prevent="$v.$touch()" não precisa disso -->
                <button  class="btn" @click.prevent="$v.$touch()">Criar</button>
                {{$v}}
                <!-- <Botao :type="submit"/> -->
                <!-- <Botao/> -->
            </fieldset>
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
        criarConta:{
            name: '',
            mail: '',
            password: '',
            conf_password: '',
            receberEmail: '',
            termos: '',
            message: ''            
        }
    }),
    validations: {
        criarConta:{
            name: { required },
            mail: { required, email },
            password: { required },
            conf_password: { 
                required,
                sameAs: sameAs('password'),
            },              
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
// com scoped no <style> ele não pega as infos do config

@import '../assets/stylus/config.styl'
@import '../assets/stylus/general.styl'

.input-focus
    border-color $color-primary   

.container   
    form 
        font-family $font-primary
        font-size 20px
        fieldset
            border 0
            padding 0
            margin 0
            min-width 0
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
        .check
            margin 0 0 8px 0
            @media screen and (min-width: 600px)
                display inline
                width 20px 
        input.check 
            @media screen and (min-width: 600px)
                margin 0 0 0 20px
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