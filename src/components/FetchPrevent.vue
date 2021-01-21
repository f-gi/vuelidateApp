<template lang="html">
    <div class="container">
        <h2> Pokemons abilities: </h2>
        <ul>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/ditto"> Ditto </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/pikachu"> Pikachu </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/bulbasaur"> Bulbasaur </a> </li>
        </ul>
        <div>
            <!-- pokemon.order -->
            <div v-for="value in habilidades" :key="pokemon.order+value.ability.name">
                <p>{{value.ability.name}}</p>
            </div>
        </div>       
    </div>        
</template>

<script>
export default {
    data: () => ({
        pokemon: {},
        habilidades: {},
    }),
    methods:{
        // usar async com endpoint 
        puxarAcao(event){
            const url = event.currentTarget.href
            fetch(url)
            .then(response => response.json())
            .then(response => {
                this.pokemon=response;
                // console.log(this.pokemon.order);
                this.habilidades = this.pokemon.abilities;
                // console.log(this.habilidades);
            });
        }
    }
}
</script>

<style lang="stylus">
// com scoped não pega o estilo
    ul 
        text-align left !important    
</style>