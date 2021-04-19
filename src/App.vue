<template>

  <div id="app">
    <router-view></router-view>
    <main-tab-bar></main-tab-bar>

  </div>

</template>



<script>

import MainTabBar from './components/MainTabBar.vue'

export default {
  name: 'App',
  components: {
    MainTabBar
  }

}
</script>





<style>
/* 设置初始样式 style里引用css文件用@import*/
@import "./assets/css/base.css";



</style>
