<template>
  <h1 v-if="!pokemon && !errorMessage">Buscando... </h1>
  <h1 v-else-if="errorMessage"> {{errorMessage}} </h1>

  <template v-else>
    <h3>{{pokemon.name}}</h3>
    <img 
    :alt="pokemon.name"
    :src="(pokemon.sprites) && pokemon.sprites.front_default" 
    >
    <br>
    <router-link :to="{name: 'pokemon-search'}" >Regresar</router-link>
  </template>

</template>

<script>

import { watch } from 'vue';
import { useRoute, onBeforeRouteLeave } from "vue-router";
import usePokemon from "@/composables/usePokemon";

export default {
  setup(){
    const route = useRoute()

    const { pokemon, errorMessage, isLoading, searchPokemon } = usePokemon(route.params.id)
    watch(
      ()=> route.params.id, //que es lo que controlamos q cambie
      ()=> searchPokemon(route.params.id)
      
    )

    onBeforeRouteLeave(()=>{

      const answer = window.confirm('¿Esta seguro que desa salir?')
      if(!answer) return false //bloqueamos la salida
    
    })

    return { 
      pokemon, 
      errorMessage, 
      isLoading, 
    } 
  }

}
</script>

