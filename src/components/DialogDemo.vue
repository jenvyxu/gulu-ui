<template>
  <div>
    <h1>Dialog 示例</h1>
    <Button @click="toggle">toggle</Button>
    <Dialog v-model:visible="x" :closeOnClickOverlay="false" :ok="f1" :cancel="f2" />
  </div>
</template>
<script lang="ts">
import Dialog from '../lib/Dialog.vue'
import Button from '../lib/Button.vue'
import { ref } from 'vue'
export default {
  components: {
    Dialog,
    Button
  },
  setup() {
    const x = ref(false)
    const toggle = () => {
      x.value = !x.value
    }
    const f1 = () => {
      // 可以阻止dialog关闭
      return false
    }
    const f2 = () => {
      
    }
    return {
      toggle,
      x,
      f1,
      f2
    }
  }

}
</script>

<style>

</style>