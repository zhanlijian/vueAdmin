<template>
<div>
   <el-dropdown class="avatar-container">
      <div class="avatar-wrapper">
        <img class="user-avatar" src="../../../../assets/images/dog.jpg">
        <span>管理员ABC</span>
        <i class="el-icon-arrow-down el-icon--right"></i>
      </div>
      <el-dropdown-menu slot="dropdown">
        <router-link class="inlineBlock" to="/">
          <el-dropdown-item>
            Home
          </el-dropdown-item>
        </router-link>
        <el-dropdown-item divided>
          <span @click="logout" style="display:block;">LogOut</span>
        </el-dropdown-item>
      </el-dropdown-menu>
    </el-dropdown>

  <scroll-bar>
    <el-menu mode="vertical" unique-opened :default-active="$route.path" :collapse="isCollapse" background-color="#304156" text-color="#fff" active-text-color="#409EFF">
      <sidebar-item :routes="routes" :activeIndex="activeIndex"></sidebar-item>
    </el-menu>
  </scroll-bar>

  <footer class="footer">
			<a href="javascript:;"><img src="http://test.oa.suneee.weilian.cn/frame/static/images/logo.png"></a>
	</footer>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import SidebarItem from './SidebarItem'
import ScrollBar from '@/components/ScrollBar'

export default {
  components: { SidebarItem, ScrollBar },
   props: {
    activeIndex: {
    }
    },
  computed: {
    ...mapGetters([
      'sidebar',
      'avatar'
    ]),
    routes() {
      return this.$router.options.routes
    },
    isCollapse() {
      return !this.sidebar.opened
    }
  },
  methods: {
    logout() {
      this.$store.dispatch('LogOut').then(() => {
        location.reload()  // 为了重新实例化vue-router对象 避免bug
      })
    }
  }
}
</script>
<style rel="stylesheet/scss" lang="scss" scoped>
  .sidebar-container{
   .footer {
	position: absolute;
	bottom: 0;
	left: 0;
	width: 100%;
	padding: 0 15px 0;
	height: 50px;
  z-index: 2;
  background: rgb(47, 52, 58);
}
.footer a {
	display: block;width: 100%;height: 50px;position: relative;
	text-align: center;
	line-height: 50px;
}
.footer img {
	display: inline-block;
	max-width: 150px;
	max-height: 50px;
	vertical-align: middle;
}
 
  .avatar-container {
    height: 50px;
    display:block;
    position: absolute;
    top: 0;left: 0;right: 0;
    z-index: 1;
    background: rgb(0, 140, 213);
    border-right: 1px solid rgb(0, 154, 214);
    .avatar-wrapper {
      cursor: pointer;
      padding-top: 7px;
      padding-bottom: 7px;
      padding-left: 17px;
      position: relative;
      span{line-height:36px; color: #fff; font-size:14px;padding-left: 10px;}
      .user-avatar {
        width: 36px;
        height: 36px;
        border-radius: 50%;
        float: left; 
      }
      .el-icon-arrow-down {
    position: absolute;
    right: 10px;
    top: 50%;
    font-size: 12px;
    color: #fff;
    margin-top: -5px;
    font-size:14px;
      }
    }
  }
   }
</style>