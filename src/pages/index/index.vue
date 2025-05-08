<template>
  <navbar title="首页" />
  <view class="content">
    111
  </view>
  <button @click="toSearch">
    按钮
  </button>
  <up-button type="primary" @click="showToast">点击测试</up-button>
</template>

<script setup lang="ts">
const toSearch = () => {
  uni.navigateTo({
    url: '/pages/search/index'
  })
}

const showToast = () => {
  console.log('点击了')
}
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}
</style>
