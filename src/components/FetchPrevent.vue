<template lang="html">
    <div class="container">
        <h2> Pokemons abilities: </h2>
        <ul>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/ditto"> Ditto </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/pikachu"> Pikachu </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/bulbasaur"> Bulbasaur </a> </li>
        </ul>
        <div>
            <div v-for="value in habilidades" :key="pokemon.order+value.ability.name">
                <p>{{value.ability.name}}</p>
            </div>
            <div>
                <img :src="img">
            </div>    
        </div>       
    </div>        
</template>

<script>
export default {
    data: () => ({
        pokemon: {},
        habilidades: {},
        img: '',
    }),
    methods:{
        // axios: usar async com endpoint 
        // usar pagina dinamica, uma pra cada pokemon 
        // usar jet pro grid com rupture 
        puxarAcao(event){
            const url = event.currentTarget.href
            fetch(url)
            .then(response => response.json())
            .then(response => {
                this.pokemon=response;
                this.habilidades = this.pokemon.abilities;
                this.img = this.pokemon.sprites.front_default;
                // console.log(this.pokemon.sprites.front_default);
            });
        }
    }
}
</script>

<style lang="stylus" scoped>
// com scoped não pega o estilo
    ul 
        text-align left   
</style>