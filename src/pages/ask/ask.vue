<template>
  <view>
    <!-- 2.0.19支持autoBack，默认为false -->
    <up-navbar :safeAreaInsetTop="true" title="个人中心" @rightClick="rightClick" :autoBack="true">
    </up-navbar>
    <view>
      124
    </view>
  </view>
</template>

<script setup lang="ts">

// 定义方法  
const rightClick = () => {
  console.log('rightClick');
};

const leftClick = () => {
  console.log('leftClick');
};

</script>

<style scoped></style>