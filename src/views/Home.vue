<template>
<div>
  <el-row>
    <el-form ref="form" :model="form" :rules="form.rules" label-width="80px">
      <el-form-item prop="message">
          <el-input v-model="form.message" placeholder="关键字"></el-input>
      </el-form-item>
      <el-form-item>
          <el-button type="primary" @click="onSubmit('form')">查询</el-button>
      </el-form-item>
    </el-form>
  </el-row>
  <div v-if="get_movies">
    <el-row type="flex" class="row-bg" justify="center">
      <el-table :data="movies" style="width: 100%">
        <el-table-column prop="images.medium" label="电源预览" width="180">
          <template slot-scope="props">
            <img :src="props.row.images.medium" alt="">
          </template>
        </el-table-column>
        <el-table-column prop="title" label="电影名称" width="180"></el-table-column>
        <el-table-column prop="year" label="上映年份" width="180"></el-table-column>
        <el-table-column prop="rating.average" label="豆瓣评分" width="180"></el-table-column>
        <el-table-column prop="alt" label="详情" width="180">
          <template slot-scope="props">
           <a :href="props.row.alt" target="_blank">去豆瓣电影查看详情</a>
          </template>
        </el-table-column>
      </el-table>
    </el-row>
  </div>
</div>
</template>

<script>
import axios from 'axios'
export default{
  data () {
    return {
      form: {
        message: '',
        rules: {
          message: [
            {required: true, message: '请输入要查询的电影或电视剧的名称。', trigger: 'blur'}
          ]
        }
      },
      movies: [],
      get_movies: false
    }
  },
  methods: {
    onSubmit (formName) {
      let self = this
      this.$refs[formName].validate((valid) => {
        if (valid) {
          axios.get('https://api.douban.com/v2/movie/search?q=' + this.form.message)
          .then((response) => {
            console.log(response)
            self.movies = response.data.subjects
            self.get_movies = true
          })
          .catch((error) => {
            console.log(error)
            return false
          })
        } else {
          return false
        }
      })
    }
  }
}
</script>

