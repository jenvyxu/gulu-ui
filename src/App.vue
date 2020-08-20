<template>
  <router-view />
</template>

<script>
import { ref, provide } from 'vue'

export default {
  name: 'App',
  setup(){
    const width = document.documentElement.clientWidth
    const menuvisible = ref(width <= 500 ? false : true)
    provide('menuvisible', menuvisible)
  }

}
</script>
