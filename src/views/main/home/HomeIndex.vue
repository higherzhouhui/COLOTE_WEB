<script setup lang="ts">
import { reactive, ref } from 'vue'
const currentIndex = ref(0)
const sloganList = reactive([
  'Avatar Intelligence',
  'Technology',
  'Neural Data',
  'New Trend',
  'Metaverse',
  'Web 3.0',
])

const sloganAniamtionList = reactive([
  'animate__animated animate__flipInX',
  'animate__animated animate__flipOutX',
  'animate__animated animate__flipInX',
  'animate__animated animate__flipOutX',
  'animate__animated animate__flipInX',
  'animate__animated animate__flipOutX',
])
setInterval(() => {
  currentIndex.value = currentIndex.value + 1
  if (currentIndex.value > sloganList.length - 1) {
    currentIndex.value = 0
  }
}, 1500)
const itemList = [
  {
    logo: 'data:image/svg+xml,%3Csvg%20xmlns%3D%22http%3A%2F%2Fwww.w3.org%2F2000%2Fsvg%22%20viewBox%3D%220%200%20512%20512%22%3E%3Cpath%20d%3D%22M12.41%20148.02l232.94%20105.67c6.8%203.09%2014.49%203.09%2021.29%200l232.94-105.67c16.55-7.51%2016.55-32.52%200-40.03L266.65%202.31a25.607%2025.607%200%200%200-21.29%200L12.41%20107.98c-16.55%207.51-16.55%2032.53%200%2040.04zm487.18%2088.28l-58.09-26.33-161.64%2073.27c-7.56%203.43-15.59%205.17-23.86%205.17s-16.29-1.74-23.86-5.17L70.51%20209.97l-58.1%2026.33c-16.55%207.5-16.55%2032.5%200%2040l232.94%20105.59c6.8%203.08%2014.49%203.08%2021.29%200L499.59%20276.3c16.55-7.5%2016.55-32.5%200-40zm0%20127.8l-57.87-26.23-161.86%2073.37c-7.56%203.43-15.59%205.17-23.86%205.17s-16.29-1.74-23.86-5.17L70.29%20337.87%2012.41%20364.1c-16.55%207.5-16.55%2032.5%200%2040l232.94%20105.59c6.8%203.08%2014.49%203.08%2021.29%200L499.59%20404.1c16.55-7.5%2016.55-32.5%200-40z%22%2F%3E%3C%2Fsvg%3E',
    label: 'Validator',
    value: 'Node：103',
  },
  { logo: '', label: 'Mining', value: 'Node：1222' },
  { logo: '', label: 'COLE Staked：', value: '229M+' },
  { logo: '', label: 'Transfer：', value: '30M+' },
]
const versionList = [
  { logo: '', label: '1.0 WhitePaper' },
  { logo: '', label: '2.0 GreenPaper' },
  { logo: '', label: '3.0 Blueprint' },
]
</script>

<template>
  <div class="w-screen">
    <div class="h-screen w-screen main">
      <div class="background-video">
        <video
          autoplay
          muted
          playsinline
          loop
          poster="https://www.matrix.io/wp-content/uploads/2023/02/photo_2023-02-06_18-42-18-3.webp"
        >
          <source
            src="https://www.matrix.io/wp-content/uploads/2022/12/manhead.m4v"
            type="video/mp4"
          />
        </video>
      </div>
      <div class="section-container">
        <img src="/src/assets/logo.png" class="h-20" />
        <div class="text-white text-3xl flex">
          <div class="mr-3">This is</div>
          <div :class="sloganAniamtionList[currentIndex]">
            {{ sloganList[currentIndex] }}
          </div>
        </div>
        <div class="itemList">
          <div v-for="(item, index) in itemList" :key="index" class="item">
            <div>
              <div class="label">{{ item.label }}</div>
              <div class="value">{{ item.value }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="comming">
      <div class="container text-center">
        <div
          class="text-white text-4xl pt-20 pb-12 textShadow animate__animated animate__heartBeat w-fit m-auto break-all font-bold"
        >
          COLOTE 3.0 is COMING
        </div>
        <div class="comingList pb-16">
          <div v-for="(item, index) in versionList" :key="index" class="item">
            {{ item.label }}
          </div>
        </div>
        <div class="text-video">
          <div class="left"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.main {
  position: relative;
  width: 100%;
  background-position: center center;
  background-size: cover;
  overflow: hidden;
}

.background-video {
  z-index: -1;
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  overflow: hidden;
}

video {
  width: 100%;
  height: 100%;
  left: -0;
  top: -0;
  object-fit: cover;
  object-position: center center;
}
.section-container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  justify-content: flex-end;
  padding-bottom: 80px;
  gap: 80px;
}
.section-container .itemList {
  width: 1120px;
  max-width: 100%;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  row-gap: 20px;
  column-gap: 40px;
  @media screen and (max-width: 1200px) {
    grid-template-columns: repeat(2, 1fr);
    padding: 0 12px;
  }
}
.item {
  width: 100%;
  border-radius: 9999px;
  border: 2px solid #06f;
  box-shadow: 1px 1px 25px 0px #0167ff;
  font-size: 1.2rem;
  color: #06f;
  transition: all 0.5s;
  cursor: pointer;
  background-color: #172c67e0;
  position: relative;
  padding: 0.8rem 0;
}
.section-container .item:hover {
  transform: scale(1.1);
  color: #fff;
}
.section-container .item::after {
  position: absolute;
  width: 50px;
  height: 50px;
  content: '';
  display: block;
  mask-repeat: no-repeat;
  mask-size: 100% 100%;
  transition: all 0.5s;
  color: #fff;
}
.comming {
  background: #090e29;
}
.textShadow {
  text-shadow: 2px 2px 25px #003cff;
}
.comingList {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
  @media screen and (max-width: 500px) {
    flex-direction: column;
  }
}
.comingList .item {
  max-width: 250px;
  background: transparent;
}
.comingList .item:hover {
  background-color: #06f;
  color: #fff;
}
</style>
