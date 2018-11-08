<template>
    <div class="home">
        <el-container class="el-container">
            <el-header class="el-header">
                <div class="logo"></div>
                <div class="loginout">
                    欢迎光临 <a href="javascript:;"> 退出</a>
                </div>
                <h1>电商后台管理系统</h1>
            </el-header>
            <el-container>
            <el-aside width="200px" class="aside">Aside</el-aside>
            <el-main class="main">Main</el-main>
            </el-container>
        </el-container>
    </div>
</template>

<script>
export default {}
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
    }
    .main {
      background-color: #d4dfe4;
    }
  }
}
</style>
