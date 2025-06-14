<template>
  <view class="navbar-container" :style="navbarStyle">
    <up-navbar :safeAreaInsetTop="true" :title="props.title" @rightClick="rightClick" :autoBack="true">
    </up-navbar>
  </view>
  <!-- 提供一个占位元素，高度等于导航栏高度，确保内容不被遮挡 -->
  <view class="navbar-placeholder" :style="placeholderStyle"></view>
</template>

<script setup lang="ts">
import { ref, onMounted, computed } from 'vue';

const props = defineProps({
  //背景颜色
  title: {
    type: String,
    default: '默认页'
  },
});

// 定义状态栏高度和导航栏高度
const statusBarHeight = ref(0);
const navbarHeight = ref(0);
const platform = ref('');
const totalHeight = ref(0);

// 计算导航栏样式
const navbarStyle = computed(() => {
  return {
    paddingTop: `${statusBarHeight.value}rpx`,
    height: `${navbarHeight.value}rpx`,
  };
});

// 计算占位元素样式
const placeholderStyle = computed(() => {
  return {
    height: `${totalHeight.value}rpx`
  };
});

// 在组件挂载时获取系统信息
onMounted(() => {
  try {
    // 获取系统信息
    const systemInfo = uni.getSystemInfoSync();
    // 状态栏高度（px转换为rpx）
    statusBarHeight.value = (systemInfo?.statusBarHeight || 0) * 2; // px转rpx，一般是2倍关系
    // 获取平台信息
    platform.value = systemInfo.platform;

    // 根据平台设置导航栏高度
    if (platform.value === 'android') {
      navbarHeight.value = 90; // 安卓导航栏高度
    } else if (platform.value === 'ios') {
      navbarHeight.value = 88; // iOS导航栏高度
    } else {
      navbarHeight.value = 88; // 默认导航栏高度
    }

    // 计算总高度
    totalHeight.value = statusBarHeight.value + navbarHeight.value;

    console.log('平台:', platform.value);
    console.log('状态栏高度:', statusBarHeight.value, 'rpx');
    console.log('导航栏高度:', navbarHeight.value, 'rpx');
    console.log('总高度:', totalHeight.value, 'rpx');
  } catch (e) {
    console.error('获取系统信息失败:', e);
    // 设置默认值
    navbarHeight.value = 88;
    totalHeight.value = 88;
  }
});

// 定义方法  
const rightClick = () => {
  console.log('rightClick');
};

const leftClick = () => {
  console.log('leftClick');
};
</script>

<style scoped>
.navbar-container {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 999;
}

.navbar-placeholder {
  width: 100%;
}
</style>