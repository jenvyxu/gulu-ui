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

<style lang="scss">
$h: 32px;
$border-color: #d9d9d9;
$color: #333;
$blue: #40a9ff;
$radius: 4px;
.jen-button {
  box-sizing: border-box;
  height: $h;
  padding: 0 12px;
  cursor: pointer;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  white-space: nowrap;
  background: white;
  color: $color;
  border: 1px solid $border-color;
  border-radius: $radius;
  box-shadow: 0 1px 0 fade-out(black, 0.95);
  & + & {
    margin-left: 8px;
  }
  &:hover,
  &:focus{
    color: $blue;
    border-color: $blue;
  }
  &:focus{
    outline: none;
  }
  &::-moz-focus-inner {
    border: 0;
  }
}
</style>