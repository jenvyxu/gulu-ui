<template>
  <div class="jen-tabs">
    <div class="jen-tabs-nav">
      <div class="jen-tabs-nav-item"
        :class="{selected: t === selected}"
        v-for="(t, index) in titles"
        :key="index"
        @click="select(t)">
        {{t}}
        </div>
    </div>
    <div class="jen-tabs-content">
      <component :is="current" />
    </div>
  </div>
</template>
<script lang="ts">
import { computed } from 'vue'
import Tab from './Tab.vue'
export default {
  props: {
    selected: {
      type: String
    }
  },
  setup(props, context) {
    // 获取标签内部的组件
    const defaults = context.slots.default()
    const titles = defaults.map((tag) => tag.props.title)
    // 检查内部子组件是否为Tab组件
    defaults.forEach((tag) => {
      if(tag.type !== Tab) {
        throw new Error('Tabs子标签必须是Tab')
      }
    })
    // 当前想要显示的内容
    const current = computed(() => {
      return defaults.filter((tag) => tag.props.title === props.selected)[0]
    }) 
    // 切换tab
    const select = (title: string) => {
      context.emit('update:selected', title)
    }
    return {
      defaults,
      titles,
      current,
      select
    }
  }
}
</script>
<style lang="scss">
$blue: #40a9ff;
$color: #333;
$border-color: #d9d9d9;
.jen-tabs {
  &-nav {
    display: flex;
    color: $color;
    border-bottom: 1px solid $border-color;
    &-item {
      padding: 8px 0;
      margin: 0 16px;
      cursor: pointer;
      &:first-child {
        margin-left: 0;
      }
      &.selected {
        color: $blue;
      }
    }
  }
  &-content {
    padding: 8px 0;
  }
}
</style>