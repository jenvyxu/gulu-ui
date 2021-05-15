<demo>使用代码打开Dialog</demo>
<template>
  <Button @click="showDialog">show Dialog</Button>
</template>

<script>
import { openDialog } from '../lib/openDialog'
import Button from '../lib/Button.vue'

export default {
  components: {
    Button
  },
  setup() {
    const showDialog = () => {
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
    return { showDialog }
  }
}
</script>
