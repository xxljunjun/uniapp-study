<template>
  <view class="guess">
    <view class="title">
      <view class="left"> 猜你喜欢 </view>
      <view class="right">
        换一组
        <image src="/static/junjun/Tsize_17.gif" class="icon" />
      </view>
    </view>
    <!-- 轮播图 -->
    <view class="swiper-box">
      <swiper
        class="swiper"
        :indicator-dots="false"
        :autoplay="true"
        :circular="true"
        @change="changeIndex"
      >
        <swiper-item v-for="(item, index) in swiperArr" :key="index">
          <view class="swiper-item"> a </view>
        </swiper-item>
      </swiper>
    </view>
    <view class="gun">
      <view class="sliders"></view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      currentIndex: 0,
      swiperArr: [
        { id: 1, path: '/static/junjun/Tsize_11.jpg' },
        { id: 2, path: '/static/junjun/Tsize_11.jpg' },
        { id: 3, path: '/static/junjun/Tsize_11.jpg' },
      ],
    }
  },
  methods: {
    changeIndex(e) {
      console.log('00000000', e)
      //e.detail.current
      let slider = document.getElementsByClassName('sliders')[0]
      if (e.detail.current == 0) {
        slider.style.left = 0
      } else if (e.detail.current == 1) {
        slider.style.left = '50px'
      } else if (e.detail.current == 2) {
        slider.style.left = '100px'
      }
    },
  },
  components: {},
}
</script>

<style lang="scss" scoped>
.guess {
  padding: 0 25rpx;
  margin-bottom: 90rpx;
  .title {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    .left {
      font-size: 38rpx;
      color: #000;
      font-weight: bolder;
    }
    .right {
      color: #888888;
      font-size: 26rpx;
      .icon {
        height: 25rpx;
        width: 25rpx;
        margin-left: 12rpx;
      }
    }
  }
  .swiper-box {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 450rpx;
    width: 700rpx;
    position: relative;
    .swiper {
      width: 700rpx;
      height: 450rpx;
      background: red;
    }
  }
  .gun {
    margin-top: 35rpx;
    width: 150rpx;
    height: 8rpx;
    background: #d8d8d8;
    border-radius: 4rpx;
    margin-left: 300rpx;
    .sliders {
      width: 50rpx;
      height: 8rpx;
      background: #ff0141;
      border-radius: 4rpx;
      position: relative;
      left: 0; //0到50的滚动距离
    }
  }
}
</style>