<template lang="html">
    <div class="wrap">
        <h2> Pokemons: </h2>
        <ul>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/ditto"> Ditto </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/pikachu"> Pikachu </a> </li>
            <li> <a @click.prevent="puxarAcao" href="https://pokeapi.co/api/v2/pokemon/bulbasaur"> Bulbasaur </a> </li>
        </ul>    
        <div>
            <p>{{pokemon}}</p>
        </div>    
    </div>        
</template>

<script>
export default {
    data: () => ({
        pokemon: {}
    }),
    methods:{
        puxarAcao(event){
            const url = event.currentTarget.href
            fetch(url)
            .then(response => response.json())
            .then(response => {
                this.pokemon=response;
            })
        }
    }
}
</script>

<style lang="stylus">

</style>