<template>
	<view class="box">
		<view class="title">
			{{items.detail.title}}
		</view>
		<view class="Vehicle">
			{{items.detail.Vehicle}}
		</view>
		<view class="dtcBox">
			<view class="dtc" v-for="(val,index) in items.detail.dtcarr" :key="index">
				{{val}}
			</view>
		</view>
		<view class="text">
			{{items.detail.text}}
		</view>
		<view class="img_Box">
			<view v-for="(item,index) in items.detail.imgsrc" :key="index">
				<image :src="item" class="comimg"/>
			</view>
		</view>
		<view class="author_Box">
			<text>{{items.detail.author}}</text>
			<image src="/static/daotong/zan.png" class="zan"/>
			<text>{{items.detail.num1}}</text>
			<image src="/static/daotong/yan.png" class="yan"/>
			<text>{{items.detail.num2}}</text>
		</view>
		<view class="close_box" @tap="toClose">
			<image src="/static/daotong/close_1.png" class="close"/>
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{

			}
		},
		mounted(){
			console.log(this.items)
		},
		props:{
			items:{
				type:Object,
				default:()=>{
					return {}
				},
				required:true
			}
		},
		methods:{
			toClose(){
				//调接口删除
				console.log("删除")
			}
		}
	}
</script>

<style lang="scss" scoped>
.box{
	width:690rpx;
	height:541rpx;
	background:rgba(245,245,245,1);
	box-shadow:0px 2rpx 6rpx 0px rgba(0,0,0,0.08);
	border-radius:14rpx;
	position: relative;
	.title{

	}
	.dtcBox{
		display: flex;
	}
	.img_Box{
		display: flex;
			.comimg{
			width: 205rpx;
			height: 115rpx;
		}
	}
	.author_Box{
		.zan{
			width: 36rpx;
			height: 36rpx;
		}
		.yan{
			width: 36rpx;
			height: 36rpx;
		}
	}
	.close_box{
		.close{
			width: 48rpx;
			height: 30rpx;
			position: absolute;
			right: 30rpx;
			bottom: 30rpx;
		}
	}
}

</style>