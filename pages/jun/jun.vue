<template>
  <view class="xxl">
    <view class="header">
      <image src="/static/daotong/back.png" class="back" @tap="back"/>
      <text class="title">New Post</text>
    </view>
<!-- 导入报告按钮 -->
    <view class="addBox">
      <view class="text_1">
        <image src="/static/daotong/jia@2x.png" class="jia" />
        <text class="intext_1">Import diagnostic report</text>
      </view>
      <view class="text_2">Import report, auto input vehicle fault information</view>
    </view>
<!-- Vehicle -->
    <view class="line">
      <text class="dot">*</text>
      <text class="line_text">Vehicle</text>
       <image src="/static/daotong/prompt.png" class="tishi" />
    </view>
    <view class="inp_Box">
      <input class="inp" placeholder="Pelese select" disabled/>
      <image src="/static/daotong/vin.png" class="vin"/>
    </view>
<!-- Mileage -->
    <view class="line">
      <text class="dot">*</text>
      <text class="line_text">Mileage</text>
    </view>
    <view class="inp_Box">
      <input class="smallinp" placeholder="Pelese enter"/>
      <input class="largeinp" disabled v-model="unit" @touchend.stop="openUnit"/>
      <image src="/static/daotong/speak.png" class="speak1"/>
      <image src="/static/daotong/rightArrow.png" class="downArrow"/>
      <view class="chooseUnit_Box" v-if="unitState">
        <ul>
          <li v-for="item in unitArr" :key="item.id" @touchend.self="toChooseUnit(item.id)">{{item.unit}}</li>
        </ul>
      </view>
    </view>
<!-- System -->
    <view class="line">
      <text class="dot">*</text>
      <text class="line_text">System</text>
    </view>
    <view class="inp_Box">
      <input class="inp" placeholder="Pelese select" disabled/>
      <image src="/static/daotong/rightArrow.png" class="rightArrow"/>
    </view>
<!-- DOC -->
    <view class="line">
      <text class="dot">*</text>
      <text class="line_text">DOC</text>
    </view>
    <view class="inp_Box">
      <input class="inp" placeholder="Pelese select"/>
      <image src="/static/daotong/speak.png" class="speak"/>
    </view>
<!-- 提交 -->
    <view class="sb_Box">
      <navigator url="/pages/about/about">
        <button type="primary" class="brn">Next step</button>
      </navigator>
    </view>
  </view>
</template>

<script>
  export default {
    data(){
      return{
        unit:"Miles",
        unitArr:[
          {id:1,unit:"Miles"},
          {id:2,unit:"Kilometers"}
        ],
        unitState:false,
      }
    },
    onLoad() {
    
		},
    mounted(){
      document.body.addEventListener('touchend', this.clickBody)
    },
    destroyed(){
      document.body.removeEventListener('touchend', this.clickBody)
    },
    methods:{
      back(){
        uni.navigateBack({
            delta: 1
        });
      },
      openUnit(){
        this.unitState = true
      },
      toChooseUnit(id){
        if(id==1){
          this.unit = "Miles"
        }else{
          this.unit = "Kilometers"
        }
        this.unitState = false
      },
      clickBody(){
        this.unitState = false
      }
    }
  }
</script>

<style lang="scss" scoped>
/* 自定义导航栏 */
.header{
  height: 88rpx;
  width: 750rpx;
  background: linear-gradient(360deg,rgba(210,210,210,1) 0%,rgba(255,255,255,1) 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  z-index: 99;
  .back{
    height: 48rpx;
    width: 48rpx;
    position: relative;
    left: -235rpx;
  }
  .title{
    text-align: center;
    font-size:36rpx;
    font-family:HelveticaNeue-Medium,HelveticaNeue;
    font-weight:600;
    color:rgba(0,0,0,1);
    line-height:44rpx;
  }
}

/* css样式 */
.sb_Box{
  width:750rpx;
  height:128rpx;
  background:linear-gradient(180deg,rgba(233,233,233,1) 0%,rgba(211,211,211,1) 100%) rgba(235,235,235,1);
  box-shadow:0px -2px 8px 0px rgba(204,204,204,1),0px 2px 0px 0px rgba(240,240,240,1);
  display: flex;
  align-items: center;
  justify-content: center;
}
.brn{
  width:690rpx;
  height:88rpx;
  background:linear-gradient(360deg,rgba(5,124,255,1) 0%,rgba(95,172,255,1) 100%);
  border-radius:10rpx;
  border:1px solid rgba(18,114,221,1);
  font-size:34rpx;
  font-family:HelveticaNeue;
  color:rgba(255,255,255,1);
  line-height:34rpx;
  display: flex;
  align-items: center;
  justify-content: center;
}
.xxl{
  color: #000;
  border-top: 1px solid #ccc;
  background:rgba(235,235,235,1);
  box-shadow:0px -2px 0px 0px rgba(204,204,204,1),0px 2px 0px 0px rgba(249,249,249,1);
  width:750px;
  // height:1206px;
  margin-top: 88rpx;
}
.addBox{
  width: 690rpx;
  height: 150rpx;
  background:rgba(245,245,245,1);
  border-radius:10px;
  border:2px dashed rgba(13,126,255,1);
  margin-top: 30rpx;
  text-align: center; 
  margin-left: 30rpx;
}
.text_1{
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 12rpx;
  margin-top: 30rpx;
}
.text_2{
  font-size:26rpx;
  font-family:HelveticaNeue;
  color:rgba(13,126,255,1);
  line-height:34rpx;
}
.jia{
  height: 36rpx;
  width: 36rpx;
  margin-right: 5rpx;
}
.intext_1{
  font-size:34rpx;
  font-family:HelveticaNeue-Medium,HelveticaNeue;
  font-weight:600;
  color:rgba(13,126,255,1);
  line-height:42rpx;
}
.line{
  padding-left: 30rpx;
  margin-top: 30rpx;
}
.inp_Box{
  padding-left: 30rpx;
  margin: 8rpx 0 40rpx;
  display: flex;
  position: relative;
  .chooseUnit_Box{
    width:340px;
    height:216px;
    border-radius:10rpx;
    background:rgba(245,245,245,1);
    box-shadow:0px 8rpx 14rpx 0px rgba(0,0,0,0.1);
    border:2rpx solid rgba(184,184,184,1);
    position: absolute;
    top: 96rpx;
    right: 22rpx;
    z-index: 66;
    li{
      height: 106rpx;
      line-height: 106rpx;
      padding-left: 30rpx;
      &:first-child{
        border-bottom: 2px solid #ccc;
      }
    }
  }
}
.dot{
  color:rgba(245,44,44,1);
  font-size:34rpx;
  font-family:HelveticaNeue;
  line-height:42rpx;
  margin-right: 5rpx;
  position: relative;
  top: 6rpx;
}
.line_text{
  font-size:34rpx;
  font-family:HelveticaNeue;
  line-height:42rpx;
  font-weight: 500;
}
.tishi{
  height: 44rpx;
  width: 44rpx;
  margin-left: 16rpx;
  position: relative;
  top: 8rpx;
}
.inp{
  background: #fff;
  width: 690rpx;
  height: 88rpx;
  background:rgba(245,245,245,1);
  box-shadow:0px 4rpx 2rpx 0px rgba(226,226,226,1);
  border-radius:10rpx;
  border:2rpx solid rgba(184,184,184,1);
  font-size: 30rpx;
}
.smallinp{
  background: #fff;
  width: 340rpx;
  height: 88rpx;
  background:rgba(245,245,245,1);
  box-shadow:0px 4rpx 2rpx 0px rgba(226,226,226,1);
  border-radius:10rpx;
  border:2rpx solid rgba(184,184,184,1);
  font-size: 30rpx;
}
.largeinp{
  background: #fff;
  width: 340rpx;
  height: 88rpx;
  background:rgba(245,245,245,1);
  box-shadow:0px 4rpx 2rpx 0px rgba(226,226,226,1);
  border-radius:10rpx;
  border:2rpx solid rgba(184,184,184,1);
  margin-left: 10rpx;
  font-size: 30rpx;
}
.vin,.speak,.rightArrow,.downArrow{
  height: 44rpx;
  width: 44rpx;
  position: absolute;
  right: 55rpx;
  top: 22rpx;
}
.speak1{
  height: 44rpx;
  width: 44rpx;
  position: absolute;
  left: 300rpx;
  top: 22rpx;
}
</style>