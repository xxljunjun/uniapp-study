<template>
	<view class="mypost">
		 <TopBack title="Mypost"/>
		 <view class="reject">

		 </view>
		 <view class="detailbox" v-for="item in detailArr" :key="item.id">
			<Box
				:items="item"
				:canDelete="canDelete"
			/>
		</view>
	</view>
</template>

<script>
import TopBack from "./component/topBack"
import Box from "./component/Box"
	export default {
		data(){
			return{
				detailArr:[],
				canDelete:false,
			}
		},
		mounted(){
			this.getMypostList()
		},
		methods:{
			getMypostList(){
				this.detailArr = [
					{
						id:1,detail:{
							title:"19 ercedes-Benz GLS450 steering systems failed",
							Vehicle:"2003 BMW 530i 3.0L",
							dtcarr:["P0171","P0174","P0101"],
							text:"The customer states the check engine light is on and the vehicle exhibits a hard start ",
							author:"Milan Collier",
							num1:"22",
							num2:"33",
							imgsrc:[
								"/static/daotong/img_1.png",
								"/static/daotong/img_2.png",
								"/static/daotong/img_3.png",
							]
						}
					},
					{
						id:2,detail:{
							title:"19 ercedes-Benz GLS450 steering systems failed",
							Vehicle:"2003 BMW 530i 3.0L",
							dtcarr:["P0171","P0174","P0101"],
							text:"The customer states the check engine light is on and the vehicle exhibits a hard start ",
							author:"Milan Collier",
							num1:"22",
							num2:"33",
							imgsrc:[
								"/static/daotong/img_3.png",
								"/static/daotong/img_2.png",
								"/static/daotong/img_1.png",
							]
						}
					},
					{
						id:3,detail:{
							title:"19 ercedes-Benz GLS450 steering systems failed",
							Vehicle:"2003 BMW 530i 3.0L",
							dtcarr:["P0171","P0174","P0101"],
							text:"The customer states the check engine light is on and the vehicle exhibits a hard start ",
							author:"Milan Collier",
							num1:"22",
							num2:"33",
							imgsrc:[
								"/static/daotong/img_2.png",
								"/static/daotong/img_3.png",
								"/static/daotong/img_1.png",
							]
						}
					},
				]
			}
		},
		components:{
			TopBack,
			Box
		}
	}
</script>

<style lang="scss" scoped>
.mypost{
	padding-top:88rpx ;
	width:750px;
	background:rgba(224,224,224,1);
	.detailbox{
		padding: 30rpx 0 0 30rpx;
	}
	.reject{
		width: 690rpx;
		height: 592rpx;
		background:rgba(245,245,245,1);
		box-shadow:0px 2rpx 6rpx 0px rgba(0,0,0,0.08);
		border-radius:12rpx;
		margin-left:30rpx;
		margin-top:30rpx;
		background:#fff;
	}
}
</style>