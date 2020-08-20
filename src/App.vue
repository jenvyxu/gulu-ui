<template>
  <router-view />
</template>

<script>
import { ref, provide } from 'vue'

export default {
  name: 'App',
  setup(){
    const menuvisible = ref(false)
    provide('menuvisible', menuvisible)
  }

}
</script>
