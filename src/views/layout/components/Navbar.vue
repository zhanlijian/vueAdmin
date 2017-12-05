<template>
  <el-menu class="navbar" mode="horizontal">
    <hamburger class="hamburger-container" :toggleClick="toggleSideBar" :isActive="sidebar.opened"></hamburger>
    <!-- <breadcrumb></breadcrumb> -->
      
        <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
            <el-menu-item index="1" v-on:click="keyPath(1)">
            <router-link active-class="active" :to="`/example/table`">处理中心</router-link>
            </el-menu-item>
            <el-menu-item index="2" v-on:click="keyPath(2)">
            <router-link active-class="active" :to="`/example/tree`">个人门户</router-link>
            </el-menu-item>
            <el-menu-item index="3" v-on:click="keyPath(3)">
            <router-link active-class="active" :to="`/form/index`">组件拆分</router-link>
            </el-menu-item>
             <el-menu-item index="4" v-on:click="keyPath(4)">
            <router-link active-class="active" :to="`/`">我的工作台</router-link>
            </el-menu-item>
        </el-menu>

 
  </el-menu>
</template>

<script>
import { mapGetters } from 'vuex'
import Breadcrumb from '@/components/Breadcrumb'
import Hamburger from '@/components/Hamburger'

export default {
  props: {
    activeIndex: {
    }
  },      
  components: {
    Breadcrumb,
    Hamburger
  },
  computed: {
    ...mapGetters([
      'sidebar'
    ])
  },
  methods: {
    handleSelect(key, keyPath) {
            },
    keyPath(key) {
            this.$emit("keyPatha",key);
            console.log('d',key);
            },
    toggleSideBar() {
      this.$store.dispatch('ToggleSideBar')
    }
    }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.el-menu--horizontal, .el-menu--horizontal .el-menu--horizontal .el-menu-item{ border-bottom: 0}
.navbar {
  height: 50px;
  line-height: 50px;
  border-radius: 0px !important;
  background: rgb(0, 140, 213);
  .el-menu{background:none;}
  .el-menu-demo,.el-menu-item{height:50px;line-height:50px; display:inline-block; border-bottom: 0;color: #ffffff; }
  .el-menu--horizontal .el-menu-item:focus, .el-menu--horizontal .el-menu-item:hover{background: rgb(0, 125, 190);}
  .hamburger-container {
    line-height: 58px;
    height: 50px;
    float: left;
    padding: 0 10px;
  }
  .screenfull {
    position: absolute;
    right: 90px;
    top: 16px;
    color: red;
  }
}
</style>

