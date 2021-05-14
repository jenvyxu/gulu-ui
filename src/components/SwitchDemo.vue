<template>
  <div>
    <h1>Switch 组件示例</h1>
    <Demo :component="Switch1Demo" />
    <Demo :component="Switch2Demo" />
  </div>
</template>

<script type="ts">
import Switch from '../lib/Switch.vue'
import { ref } from 'vue'
import Button from '../lib/Button.vue'
import Switch1Demo from '../components/Switch1.demo.vue'
import Switch2Demo from '../components/Switch2.demo.vue'
import Demo from './Demo.vue'

export default {
  components: {
    Switch,
    Button,
    Demo
  },
  setup() {
    const bool = ref(false)
    return { bool, Switch1Demo, Switch2Demo }
  }
}
</script>
