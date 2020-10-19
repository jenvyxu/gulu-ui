<template>
  <h1>按钮主题</h1>
  <div>
    <Button>你好</Button>
    <Button theme="button">你好</Button>
    <Button theme="link">你好</Button>
    <Button theme="text">你好</Button>
    <Button theme="button">normal button</Button>
    <Button theme="link">link button</Button>
    <Button theme="text">text button</Button>
  </div>
  <h1>按钮大小</h1>
  <div>
    <Button size="small">小按钮</Button>
    <Button>普通按钮</Button>
    <Button size="big">大按钮</Button>
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