<template>
  <router-view />
</template>

<script>
import { ref, provide } from 'vue'
import { router } from './router'

export default {
  name: 'App',
  setup(){
    const width = document.documentElement.clientWidth
    const menuvisible = ref(width <= 500 ? false : true)
    provide('menuvisible', menuvisible)
    router.afterEach(() => {
      if (width <= 500) {
        menuvisible.value = false
      }
    })
  }
}
</script>
