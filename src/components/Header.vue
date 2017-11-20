<template>
<el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal">
  <el-menu-item index="1"><router-link to="/">首页</router-link></el-menu-item>
  <el-menu-item index="2"><router-link to="/about">关于</router-link></el-menu-item>
</el-menu>
</template>

<script>
export default {
  data () {
    return {
      activeIndex: '1'
    }
  }
}
</script>

