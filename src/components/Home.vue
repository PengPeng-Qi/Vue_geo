<template>
    <el-container class="home-container">
      <!-- 头部区域 -->
      <el-header>
        <div>
            <img src="../assets/logo.eb8e4955.svg" alt="" style="padding: 0 0 0 15px;">
            <span><b>特色农业气象微信小程序后台管理系统</b></span>
        </div>
        <!-- header菜单区域 -->
            <!-- node设置菜单为横项菜单 -->
        <el-menu
        default-active="./Welcome"
        mode="horizontal"
        background-color="#0F8C75"
        text-color="#fff"
        active-text-color="#fff"
        @open="handleOpen"
        @close="handleClose"
        router>
        <!-- 一级菜单区域 -->
        <el-menu-item index="./Welcome">
            <!-- 图标 -->
            <i class="el-icon-house" style="color: white;"></i>
            <!-- 文本 -->
            <span>首页</span>
        </el-menu-item>
        <el-submenu index="2">
            <template slot="title">
            <i class="el-icon-box" style="color: white;"></i>
            <span>产品发布管理</span>
            </template>
            <el-menu-item index="2-1">
            <i class="el-icon-circle-plus-outline" style="color: white;"></i>
            <span>产品发布</span>
            </el-menu-item>
            <el-menu-item index="2-2">
            <i class="el-icon-circle-check" style="color: white;"></i>
            <span>已发布产品管理</span>
            </el-menu-item>
        </el-submenu>
        <el-menu-item index="3">
            <i class="el-icon-coin" style="color: white;"></i>
            <span>数据发布管理</span>
        </el-menu-item>
        <el-menu-item index="4">
            <i class="el-icon-potato-strips" style="color: white;"></i>
            <span>用户管理</span>
        </el-menu-item>
        <el-menu-item index="5">
            <i class="el-icon-setting" style="color: white;"></i>
            <span>运维管理</span>
        </el-menu-item>
        <el-submenu index="6">
            <template slot="title">
            <i class="el-icon-user" style="color: white;"></i>
            <span>系统管理员</span>
            </template>
            <el-menu-item index="../login">
                <i class="el-icon-circle-close" style="color: white;"></i>
                <span type="info" @click="logout">安全退出</span>
            </el-menu-item>
        </el-submenu>
        </el-menu>
      </el-header>
      <!-- 页面主体区域 -->
      <el-container>
        <!-- 右侧内容主体 -->
        <el-main>
          <!-- 路由占位符 -->
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
</template>

<script>
export default {
  data () {
    return {
      // 左侧菜单数据
      menulist: []
    }
  },
  created () {
    this.getMenuList()
  },
  methods: {
    logout () {
      window.sessionStorage.clear()
      this.$router.push('/login')
    },
    // 获取所有的菜单
    async getMenuList () {
      const { data: res } = await this.$http.get('menus')
      if (res.meta.status !== 200) return this.$message.error(res.meta.msg)
      this.menulist = res.data
    }
  }
}
</script>

<style scoped>
.home-container {
    height: 100%;
}
.el-header {
    background-color: #0F8C75;
    display: flex;
    justify-content: space-between;
    padding-left: 0;
    align-items: center;
    color: #fff;
    font-size: 20px;
}

.el-header > div {
    display: flex;
    align-items: center;
}

.el-header > div span {
    margin-left: 15px;
}

.el-main {
    background-color: #F2F2F2;
}
.el-menu-item.is-active {
   background-color: #0A6F5D !important;
   border-bottom-color: #0A6F5D !important;
}
.el-menu-item.is-hover.is-active{
  background-color: #0F8C75 !important;
  border-bottom-color: none;
}
</style>
