<template lang="html">
    <div class="wrap">
        <h2> Pokemons abilities: </h2>
        <ul>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/ditto"> Ditto </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/pikachu"> Pikachu </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/bulbasaur"> Bulbasaur </a> </li>
        </ul>
        <div  v-for="(value) in habilidades" :key="key+value">
            <!-- <p>index:{{index}}</p>
            <p>key:{{key}}</p>
            <p>value:{{value}}</p> -->
            <p>{{value.ability.name}}</p>
        </div>        
        <!-- <div>
            <p>{{habilidades}}</p> 
            <div class="rep"> </div>
            <p>{{pokemon}}</p>
        </div>     -->
    </div>        
</template>

<script>
export default {
    data: () => ({
        pokemon: {},
        habilidades: {}
    }),
    methods:{
        puxarAcao(event){
            const url = event.currentTarget.href
            fetch(url)
            .then(response => response.json())
            .then(response => {
                this.pokemon=response;
                this.habilidades = this.pokemon.abilities;
            });
            
        }
    }
}
</script>

<style lang="stylus">
.rep
    width 100px
    height 10px
    background-color pink
</style>