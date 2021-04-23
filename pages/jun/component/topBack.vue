<template>
  <view class="header">
    <image src="/static/daotong/back.png" class="back" @tap="back" />
    <text class="title">{{ title }}</text>
  </view>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    title: String,
  },
  methods: {
    back() {
      uni.navigateBack({
        delta: 1,
      });
    },
  },
};
</script>

<style lang="scss" scoped>
/* 自定义导航栏 */
.header {
  height: 88rpx;
  width: 750rpx;
  background: linear-gradient(
    360deg,
    rgba(210, 210, 210, 1) 0%,
    rgba(255, 255, 255, 1) 100%
  );
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  z-index: 99;
  .back {
    height: 48rpx;
    width: 48rpx;
    position: relative;
    left: -235rpx;
  }
  .title {
    text-align: center;
    font-size: 36rpx;
    font-family: HelveticaNeue-Medium, HelveticaNeue;
    font-weight: 600;
    color: rgba(0, 0, 0, 1);
    line-height: 44rpx;
  }
}
</style>