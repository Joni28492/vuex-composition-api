<template>
  <h1>Aprendiendo Slots</h1>
  <button @click="openModal">Abrir modal</button>

  <!-- <Modal /> -->
  <modal
    v-if="isOpen"
    title="hola mundo"
    @on:close="closeModal"
  >
    <!-- <h2>Titulo del modal</h2>
    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit.</p>
    <button>Salir</button> -->
    <template v-slot:body>
        <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit.</p>
    </template>

    <template v-slot:footer>
        <button @click="closeModal">Salir</button> 
    </template>

    <template v-slot:header>
         <h2>Titulo del modal</h2>
    </template>

    <template v-slot:exposed="{newTitle}">
      <h2>{{newTitle}}</h2>
    </template>
  </modal>
</template>

<script>
import Modal from "@/components/Modal.vue";
import { ref } from 'vue';

export default {
    components: { Modal },
    setup(){

        const isOpen = ref(false)

        return {
            isOpen,
            openModal: () => isOpen.value = true,
            closeModal: () => isOpen.value = false,
        }
    }
}
</script>

<style>

</style>