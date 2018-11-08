<template>
  <div id="app">
    <div class="login">
        <el-form ref="form" :model="form" label-width="80px">
          <el-form-item label="用户名">
            <el-input v-model="form.username" placeholder="请输入用户名"></el-input>
          </el-form-item>
          <el-form-item label="密码">
            <el-input v-model="form.password" placeholder="请输入密码"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" class="el-button">登录</el-button>
            <el-button>重置</el-button>
          </el-form-item>
        </el-form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      form: {
        username: '',
        password: ''
      }
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!')
    }
  }
}
</script>

<style lang="less">
.login {
  height: 100%;
  background-color: #2d434c;
  overflow: hidden;
  .el-form {
    width: 400px;
    margin: 200px auto;
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    .el-button:nth-child(2) {
      margin-left: 50px;
    }
  }
}
</style>
