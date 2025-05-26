<template>
  <view>
    <!-- 2.0.19支持autoBack，默认为false -->
    <up-navbar :safeAreaInsetTop="true" title="个人中心" @rightClick="rightClick" :autoBack="true">
    </up-navbar>
    <view class="content">
      111
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

<style scoped>
.content {
  /* 添加上边距，确保内容不被导航栏覆盖 */
  margin-top: 188rpx;
  /* 可以根据实际导航栏高度调整 */
  /* 或者使用padding-top */
  /* padding-top: 88rpx; */
}
</style>