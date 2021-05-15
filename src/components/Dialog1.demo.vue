<demo>常规使用</demo>
<template>
  <Button @click="toggle">toggle</Button>
  <Dialog
    v-model:visible="visible"
    :closeOnClickOverlay="false"
    :ok="f1"
    :cancel="f2">
    <template v-slot:title>
      <strong>加粗的标题</strong>
    </template>
    <template v-slot:content> 
      <p>内容1</p>
      <p>内容2</p>
    </template>
  </Dialog>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
import Dialog from '../lib/Dialog.vue'
import { ref } from 'vue'

export default {
  components: {
    Button,
    Dialog
  },
  setup() {
    const visible = ref(false)
    const toggle = () => {
      visible.value = !visible.value
    }
    const f1 = () => {
      // 返回false可以阻止dialog关闭
      return false
    }
    const f2 = () => {
      
    }
    return { toggle, visible, f1, f2,}
  }
}
</script>