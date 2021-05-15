<template>
  <div class="dialog-overlay"></div>
  <dialog class="dialog-wrapper">
    <header>标题</header>
    <main>
      <p>第一</p>
      <p>第二行</p>
    </main>
    <footer>
      <Button>Ok</Button>
      <Button>Cancel</Button>
    </footer>
  </dialog> 
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
export default {
  components: {
    Button
  }
}
</script>