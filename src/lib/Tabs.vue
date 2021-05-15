<template>
  <div class="jen-tabs">
    <div class="jen-tabs-nav" ref="container">
      <div class="jen-tabs-nav-item"
        :class="{selected: t === selected}"
        v-for="(t, index) in titles"
        :key="index"
        :ref="el => { if (selected === t) selectedItem = el }"
        @click="select(t)">
        {{t}}
        </div>
        <div class="jen-tabs-nav-indicator" ref="indicator"></div>
    </div>
    <div class="jen-tabs-content">
      <component :is="current" :key="current.props.title" />
    </div>
  </div>
</template>
<script lang="ts">
import { computed, onMounted, ref, watchEffect } from 'vue'
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
      // @ts-ignore
      if(tag.type.name !== Tab.name) {
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
    // 设置指示条的宽度和位置
    const selectedItem = ref<HTMLDivElement>(null)
    const indicator = ref<HTMLDivElement>(null)
    const container = ref<HTMLDivElement>(null)
    onMounted(() => {
      watchEffect(() => {
        const { width, left: left1 } = selectedItem.value.getBoundingClientRect()
        indicator.value.style.width = width + 'px'
        const { left: left2 } = container.value.getBoundingClientRect()
        const left = left1 - left2
        indicator.value.style.left = left + 'px'  
      })      
    })

    return {
      defaults,
      titles,
      current,
      select,
      indicator,
      container,
      selectedItem
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
    position: relative;
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
    &-indicator {
      position: absolute;
      height: 3px;
      background: $blue;
      left: 0;
      bottom: -1px;
      width: 100px;
      transition: all 250ms;
    }
  }
  &-content {
    padding: 8px 0;
  }
}
</style>