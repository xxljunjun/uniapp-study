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
      <input class="inp" placeholder="Pelese select" disabled v-model="Vehicle"/>
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
      <input class="inp" placeholder="Pelese select" disabled v-model="System" @touchend.stop="ischooseSystem =true"/>
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

    <!-- 选择System -->
    <view class="system_BoX" v-if="ischooseSystem">
      <view class="bottom_Box">
        <view class="system_top">
          <text class="sy_text">System</text>
          <image src="/static/daotong/close.png" class="close" @tap="toClose"/>
        </view>
        <view class="system_main">
          <view v-for="item in systemArr" :key="item.id" @tap="toSelectSystem(item)" :class="item.ischeck?'selected item0':'item0 noselcted'">
            {{item.system}}
            <image src="/static/daotong/blue.png" class="blue" v-show="item.ischeck"/>
          </view>
        </view>
        <view class="btn_box">
          <button type="primary" class="Reset" @tap="emptySystem">Reset</button>
          <button type="primary" class="Ok" @tap="okSystem">Ok</button>
        </view>
      </view>
    </view>
  </view>
</template>

<script>
import Image from '../API/image/image.vue'
import view from '../component/view/view.vue'
  export default {
  components: { view, Image },
    data(){
      return{
        unit:"Miles",
        unitArr:[
          {id:1,unit:"Miles"},
          {id:2,unit:"Kilometers"}
        ],
        unitState:false,
        System:"",
        Vehicle:"2003 BMW 530i 3.0L",
        ischooseSystem:false,
        systemArr:[
          {id:1,system:"Engine",ischeck:false},
          {id:2,system:"ADAS system",ischeck:false},
          {id:3,system:"Communication systems",ischeck:false},
          {id:4,system:"Anti-theft and entry system",ischeck:false},
          {id:5,system:"Wheels and tires",ischeck:false},
          {id:6,system:"Engine",ischeck:false},
          {id:7,system:"ADAS system",ischeck:false},
          {id:8,system:"Communication systems",ischeck:false},
          {id:9,system:"Anti-theft and entry system",ischeck:false},
          {id:10,system:"Wheels and tires",ischeck:false},
          {id:11,system:"Engine",ischeck:false},
          {id:12,system:"ADAS system",ischeck:false},
          {id:13,system:"Communication systems",ischeck:false},
          {id:14,system:"Anti-theft and entry system",ischeck:false},
          {id:15,system:"Wheels and tires",ischeck:false},
          {id:16,system:"Engine",ischeck:false},
          {id:17,system:"ADAS system",ischeck:false},
          {id:18,system:"Communication systems",ischeck:false},
          {id:19,system:"Anti-theft and entry system",ischeck:false},
          {id:20,system:"Wheels and tires",ischeck:false},
        ]
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
      okSystem(){
        let arr =this.systemArr.filter(val=>{
          return val.ischeck
        })
        let arr1 =[]
        arr.forEach(val=>{
          arr1.push(val.system)
        })
        this.System = arr1.join()
        this.ischooseSystem = false
      },
      emptySystem(){
        this.systemArr.forEach(val => {
          val.ischeck = false
        });
      },
      toSelectSystem(item){
        item.ischeck = !item.ischeck
      },
      toClose(){
        this.ischooseSystem = false
      },
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
.system_BoX{
  width: 750rpx;
  height: 100%;
  background: rgba(0,0,0,0.4);
  position: fixed;
  bottom: 0;
  z-index: 999;
  .bottom_Box{
    // height: 840rpx;
    width: 750rpx;
    position: fixed;
    bottom: 0;
    .system_top{
      display: flex;
      align-items: center;
      justify-content: center;
      width:750rpx;
      height:90rpx;
      background: linear-gradient(360deg,rgba(210,210,210,1) 0%,rgba(255,255,255,1) 100%);
      box-shadow:0px 2rpx 0px 0px rgba(204,204,204,1);
      border-radius:14rpx 14rpx 0px 0px;
      position: relative;
      .sy_text{
        font-size:36rpx;
        font-family:HelveticaNeue-Medium,HelveticaNeue;
        font-weight:600;
        color:rgba(0,0,0,1);
        line-height:36rpx;
      }
      .close{
        height: 32rpx;
        width: 32rpx;
        position: absolute;
        right: 30rpx;
        top: 30rpx;
      }
    }
    .system_main{
      width:750rpx;
      height:790rpx;
      background:rgba(235,235,235,1);
      padding-left: 30rpx;
      overflow: auto;
      .selected{
        background:rgba(206,221,237,1);
        color: #007EFF;
      }
      .noselcted{
        color:#555555;
        background:rgba(223,223,223,1);
      }
      .item0{
        height: 72rpx;
        min-width: 168rpx;
        max-width:540rpx;
        text-align: center;
        line-height: 72rpx;
        display: inline-block;
        margin-right: 20rpx;
        margin-top: 20rpx;
        padding:0 35rpx;
        border-radius:10rpx;
        position: relative;
        .blue{
          height: 34rpx;
          width: 34rpx;
          position: absolute;
          bottom: 0;
          right: 0;
        }
      }
      
    }
    .btn_box{
      height: 120rpx;
      width: 750rpx;
      display: flex;
      justify-content: center;
      align-items: center;
      text-align: center;
      line-height: 88rpx;
      background:linear-gradient(180deg,rgba(233,233,233,1) 0%,rgba(211,211,211,1) 100%) rgba(235,235,235,1);
      box-shadow:0px -2rpx 6rpx 0px rgba(0,0,0,0.08);
      .Reset{
        width:335rpx;
        height:88rpx;
        background:linear-gradient(360deg,rgba(213,213,213,1) 0%,rgba(241,241,241,1) 100%);
        border-radius:10rpx;
        border:1rpx solid rgba(184,184,184,1);
        color:rgba(0,0,0,1);
        font-size:34rpx;
      }
      .Ok{
        width:335rpx;
        height:88rpx;
        background:linear-gradient(360deg,rgba(0,122,255,1) 0%,rgba(99,174,255,1) 100%);
        border-radius:10rpx;
        border:1rpx solid rgba(18,114,221,1);
        color:rgba(255,255,255,1);
        font-size:34rpx;
      }
    }
  }
}
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
  width:100%;
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
    width:340rpx;
    height:216rpx;
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