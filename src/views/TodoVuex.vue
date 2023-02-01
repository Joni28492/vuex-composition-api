<template>
  <h1>Lista de tareas de Thanos </h1>
  <!-- <h4> Pendientes: {{ $store.state.todos.filter(t=> !t.completed).length }} </h4> -->
  <h4> Pendientes: {{ pending.length }} </h4>
  <hr>

  <!-- <h4> Todos: {{ all.length }} </h4>
  <h4> Completados: {{ completed.length }} </h4> -->

  <button 
  :class="{'active' : currentTab === 'all'}"
  @click="currentTab = 'all'">Todos</button>
  <button 
  :class="{'active' : currentTab === 'pending'}"
  @click="currentTab = 'pending'">Pendientes</button>
  <button 
  :class="{'active' : currentTab === 'completed'}"
  @click="currentTab = 'completed'" >Completados</button>

  <div>
    <ul>
      <li v-for="todo in getTodosByTab" :key="todo.id"
        :class="{'completed' : todo.completed}"
        @dblclick="toggleTodo(todo.id)"
      >
        {{todo.text}}
      </li>
    </ul>
  </div> 

  <button @click="isOpen=true">Crear Todo</button>

  <modal v-if="isOpen" @on:close="isOpen=false">

    <template v-slot:header>
      <h1>Nueva tarea</h1>
    </template>

    <template v-slot:body>
      <form @submit.prevent="createTodo(newTodoText); isOpen=false">
        <input 
          type="text" 
          placeholder="Nueva tarea"
          v-model="newTodoText"  
        >
      <br>
      <br>
      <button type="submit">Agregar</button>
      </form>
    </template>
    
   


  </modal>
  <!-- Modal -->
  <!-- 
    Formulario
      submit.prevent
      input
      createTodo(text)
   -->

</template>

<script>

import useTodo from '@/composables/useTodo'
import { ref } from 'vue';


import Modal from "@/components/Modal.vue";
export default {
  components: {Modal},
  setup(){
    const { currentTab, getTodosByTab, toggleTodo , pending, createTodo} = useTodo()
    
    
    
    return {
      currentTab,
      getTodosByTab,
      toggleTodo,
      pending, 
      createTodo,
      isOpen: ref(false),
      newTodoText: ref('')
    
      
    }

  }

}

</script>

<style scoped>


div {
  display: flex;
  justify-content: center;
  text-align: center;
}

ul {
  width: 300px;
  text-align: left;
}

li {
  cursor: pointer;
}

.active {
  background-color: #2c3e50;
  color: white
}


.completed {
  text-decoration: line-through;
}


</style>