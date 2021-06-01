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
      <view class="daily">
        <ul class="lb" :class="{marquee_top:animate}">
          <li v-for="(item, index) in list" >{{item}}</li>
        </ul>
        <!-- <image src="/static/junjun/Tsize_11.gif" class="header animated bounceOutUp"/> -->
        <!-- <view class="text animate__animated animate__bounceOutUp">成功购买口袋妖怪复刻</view> -->
      </view>
      <swiper
        class="swiper"
        :indicator-dots="true"
        :autoplay="true"
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
    <!-- 标签 -->
    <view class="box">
        <view class="box-top"></view>
        <view class="box-middle"></view>
        <view class="box-bottom"></view>
    </view>
    <view class="guess"></view>
  </view>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      animate: false,
      list: ["恭喜***获得10积分", "恭喜***获得20积分", "恭喜***获得40积分"]
    }
  },
  mounted(){
      let that = this;
      const timer = setInterval(() => {
        this.animate = true;
  
        setTimeout(() => {
          that.list.push(this.list[0]);
          that.list.shift();
          that.animate = false;
          console.log(Math.random());
        }, 500);
      }, 3000);
      // 通过$once来监听定时器，在beforeDestroy钩子可以被清除。
      this.$once("hook:beforeDestroy", () => {
        clearInterval(timer);
    });
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
    position:relative;
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
    .daily{
      width:280rpx;
      height:50rpx;
      background:#fff;
      opacity:0.7;
      border-radius:50rpx;
      position:absolute;
      bottom:34rpx;
      right:22rpx;
      z-index:11;
      display:flex;
      align-items:center;
      overflow:hidden;
      .marquee_top {
        transition: all 0.5s;
        margin-top: -100rpx;
      }
      .header{
        width:30rpx;
        height:30rpx;
        margin:0 10rpx;
      }
      .text{
        width:225rpx;
        white-space:nowrap; //强制不换行
        overflow:hidden;
        text-overflow:ellipsis;
      }
    }
  }
}
</style>