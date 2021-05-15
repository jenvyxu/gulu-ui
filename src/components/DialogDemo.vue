<template>
  <div>
    <h1>Dialog 示例</h1>
    <Button @click="toggle">toggle</Button>
    <Dialog
      v-model:visible="x"
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
    <h1>示例2</h1>
    <Button @click="showDialog">show Dialog</Button>
  </div>
</template>
<script lang="ts">
import Dialog from '../lib/Dialog.vue'
import Button from '../lib/Button.vue'
import { ref } from 'vue'
import { openDialog } from '../lib/openDialog'
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
    const showDialog = () => {
      console.log('show dialog')
      openDialog({
        title: '标题',
        content: '你好',
        closeOnClickOverlay: false,
        ok: () => {
          console.log('ok')
        },
        cancel: () => {
          console.log('cancel')
        }
    })}
    return {
      toggle,
      x,
      f1,
      f2,
      showDialog
    }
  }

}
</script>

<style>

</style>