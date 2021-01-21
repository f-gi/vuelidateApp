<template lang="html">
<!-- section -->
    <div class="container"> 
        <h2> Criar conta </h2> 
        <div v-if="sucess">
            <p> Conta criada com sucesso! </p>
        </div>
        <form @submit.prevent="submit" class="formulario" v-else>
            <fieldset>
                <div class="formulario__input">
                    <label for="nome">Nome*</label>
                    <input 
                        v-model="$v.criarConta.name.$model" 
                        type="text"
                        id="nome" 
                        @change="$v.criarConta.name.$touch()" 
                        :class="{'formulario__input--focusError':$v.criarConta.name.$error}"
                    />
                    <span v-if="$v.criarConta.name.$error"> Seu nome precisa ter no minimo {{$v.criarConta.name.$params.minLength.min}} letras.</span>
                {{$v.criarConta.name.minLength}}
                </div> 
                <div class="formulario__input">
                    <label for="email">E-mail*</label>
                    <input 
                        v-model="$v.criarConta.mail.$model" 
                        type="email" 
                        id="email"
                        :class="{'formulario__input--focusError':$v.criarConta.mail.$error}"
                    />
                    <span v-if="$v.criarConta.mail.$error"> Este E-mail é invalido </span>
                </div>
                <div class="formulario__input">
                    <label for="senha">Senha*</label>
                    <input 
                        v-model="$v.criarConta.password.$model" 
                        type="password" 
                        id="senha" 
                        :class="{'formulario__input--focusError':$v.criarConta.password.$error}"
                    />
                    <span v-if="$v.criarConta.password.$error"> A senha precisa ter entre {{$v.criarConta.password.$params.minLength.min}} e {{$v.criarConta.password.$params.maxLength.max}} caracteres </span>

                </div>
                <div class="formulario__input">
                    <label for="confsenha">Confirme sua senha*</label>
                    <input 
                        v-model="$v.criarConta.conf_password.$model" 
                        type="password" 
                        id="confsenha" 
                        :class="{'formulario__input--focusError':$v.criarConta.conf_password.$error}"/>
                    <span v-if="$v.criarConta.conf_password.$error"> As senhas informadas não coincidem </span>
                </div>
                <div class="formulario__input">
                    <label class="formulario__input--check" for="receberEmail">Aceitar receber e-mails?</label>
                    <input 
                        class="formulario__input--check" 
                        type="checkbox" 
                        v-model="$v.criarConta.receberEmail" 
                        id="receberEmail" 
                    />
                </div>    
                <div class="formulario__input">
                    <label class="formulario__input--check" for="termos">Aceita os Termos e Condições?</label>
                    <input 
                        class="formulario__input--check" 
                        type="checkbox" 
                        v-model="$v.criarConta.termos" 
                        id="termos" 
                    />
                </div>    
                <div class="formulario__input">
                    <label for="msg">Mensagem:</label>
                    <textarea v-model="$v.criarConta.message" id="msg"></textarea>
                </div> 
                <!-- @click.prevent="$v.$touch()" não precisa disso -->
                <!-- <button  class="btn" @click.prevent="$v.$touch()">Criar</button> -->
                <button  class="formulario__btn" type="submit" :disabled="$v.$invalid">Criar</button>
                <!-- @click.prevent="click", o prevent do submit fica no form, não no botão em si -->
                <!-- <Botao :type="submit"/> usando emit para o type dinamico em componente -->
            </fieldset>
        </form>
    </div>    
</template>

<script>
import { required, email, sameAs, minLength, maxLength } from 'vuelidate/lib/validators'

export default {
    components: {
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
        },
        sucess: false,
    }),
    validations: {
        criarConta:{
            name: { 
                required, 
                minLength: minLength(4)
            },
            mail: { 
                required, 
                email 
            },
            password: { 
                required,
                minLength: minLength(6),
                maxLength: maxLength(30)
            },
            conf_password: { 
                required,
                sameAs: sameAs('password'),
            },               
        }
    },
    methods: {
        click: function(){
            console.log("clicou");
        },
        submit() {
            // this.$v.$touch()
            this.sucess=true;
        }
    }    
}
</script>

<style lang="stylus">
// com scoped no <style> ele não pega as infos do config

@import '../assets/stylus/config.styl'
@import '../assets/stylus/general.styl' 

.container   
    .formulario 
        font-family $font-primary
        font-size $subtitle-desk
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
            font-size $subtitle-desk  
        textarea
            height 85px
        .formulario__input
            margin 15px auto
            width 80%
            @media screen and (min-width: 600px)
                margin 20px 0 
            span
                font-size $legend
                color $color-primary 
            input
                outline none                
            input:focus 
                border-color $color-primary
            .formulario__input--focusError
                border-color $color-primary
            .formulario__input--check
                margin 0 0 8px 0
                @media screen and (min-width: 600px)
                    display inline
                    width 20px  
        .formulario__btn 
            background-color $color-primary
            font-family $font-primary
            font-size $subtitle-desk
            height 30px
            width 100px
            border-radius 10px
            font-weight 700
            margin 15px auto
            @media screen and (min-width: 600px)
                margin 25px 0            
</style>