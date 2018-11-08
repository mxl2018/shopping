<template>
  <div id="app">
    <div class="login">
        <el-form ref="form" :rules="rules" :model="form" label-width="80px" show-message status-icon>
          <img src="../assets/images/avatar.jpg" alt=""  class="img">
          <el-form-item label="用户名"  prop="username">
            <el-input v-model="form.username" placeholder="请输入用户名"></el-input>
          </el-form-item>
          <el-form-item label="密码"  prop="password">
            <el-input v-model="form.password" placeholder="请输入密码" type="password"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" class="el-button" @click="login('form')">登录</el-button>
            <el-button @click="reset('form')">重置</el-button>
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
      },
      rules: {
        username: [
          { required: true, message: '请输入用户名', trigger: 'change' },
          { min: 3, max: 5, message: '长度在 3 到 5 个字符', trigger: 'change' }
        ],
        password: [
          { required: true, message: '请输入密码', trigger: 'change' },
          {
            min: 6,
            max: 12,
            message: '长度在 6 到 12个字符',
            trigger: 'change'
          }
        ]
      }
    }
  },
  methods: {
    // 重置功能
    reset(form) {
      this.$refs[form].resetFields()
    },
    // 表单校验功能
    login(form) {
      this.$refs[form].validate(valid => {
        this.$axios
          .post('http://localhost:8888/api/private/v1/login', this.form)
          .then(res => {
            // console.log(res.data)
            if (res.data.meta.status === 200) {
              localStorage.setItem('token', 'res.data.meta.token')
              this.$message.success({ message: '登录成功' })
              this.$router.push({ path: '/home' })
              // alert('submit!')
            } else {
              // console.log('error submit!!')
              this.$message.error({ message: '用户名或密码错误' })
              return false
            }
          })
      })
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
    padding: 50px;
    border-radius: 10px;
    position: relative;
    .el-button:nth-child(2) {
      margin-left: 50px;
    }
    .img {
      border: 10px solid #fff;
      border-radius: 50%;
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      top: -85px;
    }
  }
}
</style>
