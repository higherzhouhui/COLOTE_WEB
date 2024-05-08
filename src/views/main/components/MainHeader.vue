<script lang="ts" setup>
import { useRouter } from 'vue-router'
const router = useRouter()

const menuList = ['Solutions', 'Team', 'Community', 'Resources', 'Developers']
const routerToHome = () => {
  router.push('/')
}
</script>
<template>
  <div class="header bg-[#06234070]">
    <div
      class="container flex items-center h-[100%] cursor-pointer header-content"
    >
      <div @click="routerToHome">
        <img src="/src/assets/logo.png" class="h-[50px]" />
      </div>
      <div class="flex-1 justify-center menuList">
        <div
          v-for="item in menuList"
          :key="item"
          class="text-white mr-12 cursor-pointer item relative"
        >
          {{ item }}
          <div class="underItem" />
        </div>
      </div>
      <div
        class="download text-white bg-[#0052FF] rounded-full px-3 py-2 cursor-pointer"
      >
        DownLoad
      </div>
    </div>
  </div>
</template>

<style scoped>
.header {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 80px;
  z-index: 9;
  padding: 0 20px;
}
.underItem {
  position: absolute;
  bottom: -8px;
  height: 4px;
  border-radius: 2px;
  left: 50%;
  transform: translate(-50%, 0);
  background: #0052ff;
  transition: width 0.5s;
  width: 0;
  display: flex;
  justify-content: center;
}
.item:hover .underItem {
  width: 100%;
}
.header-content {
  @media screen and (max-width: 900px) {
    justify-content: space-between;
  }
}
.menuList {
  display: flex;
  @media screen and (max-width: 900px) {
    display: none;
  }
}
</style>
