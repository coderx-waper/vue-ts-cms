<template>
  <div class="home">
    <el-container class="el-container">
      <el-aside :width="isCollapse ? '60px' : '210px'"
        ><nav-menu :isCollapse="isCollapse"
      /></el-aside>
      <el-container class="page">
        <el-header class="page-header"
          ><nav-header @changeFold="changeFold"
        /></el-header>
        <el-main class="page-content">
          <div class="page-content-info">
            <router-view></router-view>
          </div>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import NavMenu from 'components/nav-menu'
import NavHeader from 'components/nav-header'
export default defineComponent({
  name: 'Home',
  components: {
    NavMenu,
    NavHeader
  },
  setup() {
    const isCollapse = ref(false)
    const changeFold = (isFold: boolean) => {
      isCollapse.value = isFold
    }
    return {
      isCollapse,
      changeFold
    }
  }
})
</script>

<style lang="less">
.home {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.el-container,
.page {
  height: 100%;
}

.page-content {
  height: calc(100% - 48px);
  .page-content-info {
    background-color: #fff;
    border-radius: 5px;
  }
}

.page-header {
  height: 48px !important;
}

.el-aside {
  overflow-x: hidden;
  overflow-y: auto;
  line-height: 200px;
  text-align: left;
  cursor: pointer;
  background-color: #001529;
  transition: width 0.3s linear;
  scrollbar-width: none; /* firefox */
  -ms-overflow-style: none; /* IE 10+ */

  &::-webkit-scrollbar {
    display: none;
  }
}

.el-main {
  color: #333;
  text-align: center;
  background-color: #f0f2f5;
}
</style>
