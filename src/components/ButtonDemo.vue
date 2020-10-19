<template>
  <div>
    <Button>你好</Button>
    <Button theme="button">你好</Button>
    <Button theme="link">你好</Button>
    <Button theme="text">你好</Button>
    <Button theme="button">normal button</Button>
    <Button theme="link">link button</Button>
    <Button theme="text">text button</Button>
  </div>
</template>

<script lang="ts">
import Button from '../lib/Button.vue'
export default {
  components: {
    Button
  },
  setup(props){

  }
}
</script>

<style>

</style>