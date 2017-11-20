<template>
  <div id="app">
    <el-container>
      <el-header>
        <nav-header></nav-header>
      </el-header>
      <el-main>
        <router-view></router-view>
      </el-main>
      <el-footer>
        <nav-footer></nav-footer>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
import NavHeader from '@/components/Header.vue'
import NavFooter from '@/components/Footer.vue'
export default {
  name: 'app',
  components: {
    NavHeader: NavHeader,
    NavFooter: NavFooter
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
