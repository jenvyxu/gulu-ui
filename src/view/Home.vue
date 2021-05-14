<template>
  <div>
    <Topnav />
    <div class="banner">
      <h1>JEN UI</h1>
      <h2>a beautiful ui</h2>
      <div class="actions">
        <a href="https://github.com/jenvyxu">Github</a>
        <router-link to="/doc">开始</router-link>
      </div>
    </div>
    <div class="features">
      <svg class="icon">
        <use xlink:href="#icon-vue"></use>
      </svg>
      <svg class="icon">
        <use xlink:href="#icon-typescript"></use>
      </svg>
      <svg class="icon">
        <use xlink:href="#icon-light"></use>
      </svg>
    </div>
  </div>
</template>

<script lang="ts">
import Topnav from '../components/Topnav.vue'
export default {
  components: {
    Topnav
  }
}
</script>

<style lang="scss" scoped>
$green: #02bcb0;
$border-radius: 4px;
$color: #007974;
.banner {
  padding: 100px 0;
  color: $color;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background: linear-gradient(145deg, rgba(227, 255, 253, 1) 0%, rgba(183, 233, 230, 1) 100%);
  clip-path: ellipse(80% 60% at 50% 40%);
  >.actions{
    padding: 8px 0;
    a {
      margin:0 8px;
      background: $green;
      display: inline-block;
      color: white;
      padding: 8px 24px;
      border-radius: $border-radius;
      &:hover {
        text-decoration: none;
      }
    }
  }
}
.features {
  & >svg {
    width: 64px;
    height: 64px;
  }
}

</style>