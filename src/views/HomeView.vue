<template>
  <div class="home">
    <h1>Reactive vs Ref</h1>
    <h3> {{ironman}} </h3>
    <h3> {{hulk}} </h3>

    <button @click="changeIronman"> changeIronman </button>      
    <button @click="changeHulk"> changeHulk </button>      

    <h3> IRONMAN:   {{ironmanIsAlive}}</h3>  
    <h3> HULK:   {{hulkIsAlive}}</h3>  
    <button @click="changeStatus" >Cambiar Status</button>
  </div>
</template>

<script>

import {ref, reactive} from 'vue'

export default {
  name: 'Home',
  setup() {

    const ironman = ref({name: 'Tony', age: 50})
    const hulk = reactive({name: 'Bruce', age: 50})//solo funciona con objetos

    const ironmanIsAlive = reactive(false)
    const hulkIsAlive = ref(true)

    const changeStatus = () => {
      hulkIsAlive.value = !hulkIsAlive.value
      // ironmanIsAlive = !ironmanIsAlive //error, solo lectura, 
    }

    return {
      ironman,
      hulk,
      ironmanIsAlive,
      hulkIsAlive,

      changeIronman: ()=> {
        ironman.value.name = 'Tony Stark'
        ironman.value.age = 55
      },
      changeHulk: ()=> {
        hulk.name = "Bruce banner"
        hulk.age = 45
      },
      changeStatus
    }
  }

}
</script>
