<template>
  <div class="about">
    <h1>{{title}}</h1>
    <button @click="changeTitle">Cambiar titulo</button>
  </div>
</template>


<script>

import { 
         ref, 
         onMounted,
         onUpdated,
         onUnmounted,
         onBeforeMount,
         onBeforeUpdate,
         onBeforeUnmount,
         onErrorCaptured,
         onRenderTracked,
         onRenderTriggered,
         onActivated,
         onDeactivated,
         onServerPrefetch,
         } from "vue";

export default {
  setup() {

    const title = ref('about')

    console.log("setup se llamo")

    onMounted(()=>{console.log("onMounted se llamo")})
    onUpdated(()=>{console.log("onUpdated se llamo")})
    onUnmounted(()=>{console.log("onUnmounted se llamo")})
    onBeforeMount(()=>{console.log("onBeforeMount se llamo")})
    onBeforeUpdate(()=>{console.log("onBeforeUpdate se llamo")})
    onBeforeUnmount(()=>{console.log("onBeforeUnmount se llamo")})
    onErrorCaptured(()=>{console.log("onErrorCaptured se llamo")})
    onRenderTracked(()=>{console.log("onRenderTracked se llamo")})
    onRenderTriggered(()=>{console.log("onRenderTriggered se llamo")})
    onActivated(()=>{console.log("onActivated se llamo")})
    onDeactivated(()=>{console.log("onDeactivated se llamo")})
    onServerPrefetch(()=>{console.log("onServerPrefetch se llamo")})

    return {
      title,
      changeTitle: () => title.value = 'New About'
    }

  },
}
</script>
