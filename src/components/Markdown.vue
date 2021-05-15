<template>
  <article class="markdown-body" v-html="content" />
</template>

<script lang="ts">
import { ref } from 'vue'

export default {
  props: {
    content: {
      type: String
    }
  },
}
</script>