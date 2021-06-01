<template>
  <view class="Tindex">
    <!-- 头部搜索框 -->
    <view class="top">
      <input
        class="inp"
        placeholder="请输入游戏名称或商品ID"
        placeholder-class="palceInp"
      />
      <image src="/static/junjun/Tsize_06.gif" class="search" />
      <image src="/static/junjun/Tsize_03.gif" class="kefu" />
    </view>
    <!-- 轮播图 -->
    <view class="swiper-box">
      <swiper
        class="swiper"
        :indicator-dots="true"
        :autoplay="true"
        :interval="interval"
        :duration="duration"
        :circular="true"
      >
        <swiper-item>
          <view class="swiper-item">
            <image src="/static/junjun/Tsize_11.jpg" class="swiper-img" />
          </view>
        </swiper-item>
        <swiper-item>
          <view class="swiper-item">
            <image src="/static/junjun/Tsize_11.jpg" class="swiper-img" />
          </view>
        </swiper-item>
        <swiper-item>
          <view class="swiper-item">
            <image src="/static/junjun/Tsize_11.jpg" class="swiper-img" />
          </view>
        </swiper-item>
      </swiper>
    </view>
    <view class="box"></view>
    <view class="guess"></view>
  </view>
</template>

<script>
export default {
  props: {},
  data() {
    return {}
  },
  methods: {},
  components: {},
}
</script>

<style lang="scss" scoped>
.Tindex {
  font-size: 26rpx;
  .top {
    height: 90rpx;
    width: 750rpx;
    background: #ff0141;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: relative;
    .search {
      width: 30rpx;
      height: 30rpx;
      position: absolute;
      top: 30rpx;
      left: 50rpx;
      z-index: 10;
    }
    .inp {
      width: 620rpx;
      height: 70rpx;
      background: #f6f6f6;
      border-radius: 70rpx;
      margin-left: 20rpx;
      color: #000;
      font-size: 26rpx;
      /deep/.uni-input-wrapper {
        padding-left: 50rpx;
      }
    }
    .palceInp {
      color: #939393;
      font-size: 26rpx;
      left: 85rpx;
    }
    .kefu {
      width: 50rpx;
      height: 50rpx;
      margin-right: 30rpx;
    }
  }
  .swiper-box {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 338rpx;
    width: 750rpx;
    .swiper {
      width: 710rpx;
      height: 300rpx;
      border-radius: 10rpx;
      .swiper-img {
        border-radius: 10rpx;
        width: 710rpx;
        height: 300rpx;
      }
    }
  }
}
</style>