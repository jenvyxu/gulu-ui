<template>
  <article class="markdown-body" v-html="content" />
</template>

<script lang="ts">
import { ref } from 'vue'
export default {
  props: {
    path: {
      type: String
    }
  },
  setup(props) {
    const content = ref<String>(null)
    import(props.path).then(result => {
      content.value = result.default
    })
    return {
      content
    }
  }
}
</script>