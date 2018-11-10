<template>
    <div class="home">
        <el-container class="el-container">
            <el-header class="el-header">
                <div class="logo"></div>
                <div class="loginout">
                    欢迎光临 <a href="javascript:;"  @click="loginout"> 退出</a>
                </div>
                <h1>电商后台管理系统</h1>
            </el-header>
            <el-container>
            <el-aside width="200px" class="aside">
              <el-menu
                default-active="1-1"
                class="el-menu-vertical-demo"
                @open="handleOpen"
                @close="handleClose"
                background-color="#545c64"
                text-color="#fff"
                active-text-color="#ffd04b">
                <el-submenu index="1">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>用户管理</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="1-1"><i class="el-icon-menu"></i>用户列表</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
                <el-submenu index="2">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span>权限管理</span>
                  </template>
                  <el-menu-item-group>
                    <el-menu-item index="2-1"><i class="el-icon-menu"></i>角色列表</el-menu-item>
                  </el-menu-item-group>
                   <el-menu-item-group>
                    <el-menu-item index="2-2"><i class="el-icon-menu"></i>权限列表</el-menu-item>
                  </el-menu-item-group>
                </el-submenu>
              </el-menu>
            </el-aside>
            <el-main class="main">Main</el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
export default {
  data() {
    return {
      dialogVisible: false
    }
  },
  methods: {
    handleClose(done) {},
    loginout() {
      this.$confirm('你确定要退出吗', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      })
        .then(() => {
          localStorage.removeItem('token')
          this.$router.push('/login')
          this.$message({
            type: 'success',
            message: '退出成功!'
          })
        })
        .catch(() => {
          this.$message({
            type: 'info',
            message: '已取消退出'
          })
        })
    }
  }
}
</script>

<style lang="less">
.home {
  height: 100%;
  .el-container {
    height: 100%;
    .el-header {
      width: 100%;
      height: 60px;
      background-color: #b3c1cd;
      .logo {
        float: left;
        width: 180px;
        height: 60px;
        background-image: url('../assets/images/logo.png');
        background-size: contain;
        background-position: center center;
        background-repeat: no-repeat;
      }
      h1 {
        height: 60px;
        line-height: 60px;
        font-size: 28px;
        text-align: center;
        color: white;
        overflow: hidden;
      }
      .loginout {
        float: right;
        width: 180px;
        height: 60px;
        line-height: 60px;
        text-align: right;
        color: black;
        font-weight: 700;
        a {
          color: darkorange;
        }
      }
    }
    .aside {
      width: 200px;
      height: 100%;
      background-color: #545c64;
      .el-submenu {
        width: 200px;
      }
    }
    .main {
      background-color: #d4dfe4;
    }
  }
}
</style>
