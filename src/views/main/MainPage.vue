<script setup lang="ts">
import MainHeader from './components/MainHeader.vue'
</script>

<template>
  <el-container>
    <MainHeader />
    <router-view></router-view>
  </el-container>
</template>

<style scoped></style>
