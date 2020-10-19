<template>
  <button class="jen-button" :class="{[`theme-${theme}`]: theme}">
    <slot />
  </button>
</template>

<script>
export default {
  inheritAttrs: false,
  props: {
    theme: {
      type: String,
      default: 'button'
    }
  },
  setup(props, context) {

  }
}
</script>

<style>

</style>