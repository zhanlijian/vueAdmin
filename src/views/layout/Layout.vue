<template>
  <div class="app-wrapper" :class="{hideSidebar:!sidebar.opened}">
    <sidebar class="sidebar-container" :routes="routes" :activeIndex="activeIndex"></sidebar>
    <div class="main-container">
      <navbar v-on:keyPatha="keyPathfun"></navbar>
      <app-main></app-main>
    </div>
  </div>
</template>

<script>
import { Navbar, Sidebar, AppMain } from '@/views/layout/components'

export default {
  name: 'layout',
  data() {
    return {
      activeIndex:'1',
    }
  },
  components: {
    Navbar,
    Sidebar,
    AppMain
  },
   methods: {
         keyPathfun:function(key){
         this.activeIndex=key
    }
   },
  computed: {

    sidebar() {
      return this.$store.state.app.sidebar
    },
    routes() {
      return this.$router.options.routes
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@import "src/styles/mixin.scss";
.app-wrapper {
  @include clearfix;
  position: relative;
  height: 100%;
  width: 100%;
}
.sidebar-container{
  padding: 50px 0
}
</style>
