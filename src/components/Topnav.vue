<template>
  <div class="topnav">
    <router-link class="logo" to="/">
      <svg class="icon">
        <use xlink:href="#icon-diamond"></use>
      </svg>
      JEN UI
    </router-link>
    <ul class="menu">
      <li><router-link to="/doc/intro">文档</router-link></li>
    </ul>
    <svg class="toggleAside icon" @click="toggleMenu" v-if="toggleMenuButtonVisible">
      <use xlink:href="#icon-menu"></use>
    </svg>
  </div>
</template>

<script lang="ts">
import { inject, Ref } from 'vue'
export default {
  props: {
    toggleMenuButtonVisible: {
      type: Boolean,
      default: false
    }
  },
  setup() {
    const menuVisible = inject<Ref<boolean>>('menuvisible')
    const toggleMenu = () => {
      menuVisible.value = !menuVisible.value
    }
    return {
      toggleMenu
    }
  }
}
</script>

<style lang="scss" scoped>
$color: #007974;
.topnav {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 16px;
  color: $color;
  background: #fff;
  > .logo {
    max-width: 6em;
    margin-right: auto;
    display: flex;
    align-items: center;
    >svg {
      margin-right: 6px;
      width: 28px;
      height: 28px;
    }
  }
  > .menu {
    display: flex;
    white-space: nowrap;
    flex-wrap: nowrap;
    > li {
      margin: 0 1em;
    }
  }
  >.toggleAside {
    display: none;
    width: 24px;
    height: 24px;
    position: absolute;
    left: 16px;
    top: 50%;
    transform: translateY(-50%);
    cursor: pointer;
  }
  @media (max-width: 500px) {
    >.menu {
      display: none;
    }
    >.logo {
      margin: 0 auto;
    }
    >.toggleAside {
      display: inline-block;
    }
  }
}
</style>