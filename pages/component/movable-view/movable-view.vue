<template>
	<view class="page-body">
		<page-head title="movable-view,可拖动视图"></page-head>
		<!-- match-media相当于媒体查询功能 -->
		 <view>
			<match-media :min-width="375" :max-width="800" >
				<view>当页面最小宽度 375px， 页面宽度最大 800px 时显示</view>
			</match-media>

			<match-media :min-height="400" :orientation="landscape">
				<view>当页面高度不小于 400px 且屏幕方向为横向时展示这里</view>
			</match-media>
		</view>
		<view class="uni-padding-wrap uni-common-mt">
			<view class="uni-title uni-common-mt">
				示例 1
				<text>\nmovable-view 区域小于 movable-area</text>
			</view>
			<movable-area>
				<movable-view :x="x" :y="y" direction="all" @change="onChange">text</movable-view>
			</movable-area>
			<view @tap="tap" class="uni-link uni-center uni-common-mt">
				点击这里移动至 (30px, 30px)
			</view>
			<view class="uni-title uni-common-mt">
				示例 2
				<text>\nmovable-view区域大于movable-area</text>
			</view>
			<movable-area>
				<movable-view class="max" direction="all">text</movable-view>
			</movable-area>
			<view class="uni-title uni-common-mt">
				示例 3
				<text>\n只可以横向移动</text>
			</view>
			<movable-area>
				<movable-view direction="horizontal">text</movable-view>
			</movable-area>
			<view class="uni-title uni-common-mt">
				示例 4
				<text>\n只可以纵向移动</text>
			</view>
			<movable-area>
				<movable-view direction="vertical">text</movable-view>
			</movable-area>
			<view class="uni-title uni-common-mt">
				示例 5
				<text>\n可超出边界</text>
			</view>
			<movable-area>
				<movable-view direction="all" out-of-bounds>text</movable-view>
			</movable-area>
			<view class="uni-title uni-common-mt">
				示例 6
				<text>\n带有惯性</text>
			</view>
			<movable-area>
				<movable-view direction="all" inertia>text</movable-view>
			</movable-area>
			<view class="uni-title uni-common-mt">
				示例 7
				<text>\n可放缩</text>
			</view>
			<movable-area scale-area>
				<movable-view direction="all" @scale="onScale" scale scale-min="0.5" scale-max="4" :scale-value="scale">text</movable-view>
			</movable-area>
			<view @tap="tap2" class="uni-link uni-center uni-common-mt" style="padding-bottom:80rpx;">
				点击这里放大3倍
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				x: 0,
				y: 0,
				scale: 2,
				old: {
					x: 0,
					y: 0,
					scale: 2
				}
			}
		},
		methods: {
			tap: function(e) {
				// 解决view层不同步的问题
				this.x = this.old.x
				this.y = this.old.y
				this.$nextTick(function() {
					this.x = 30
					this.y = 30
				})
			},
			tap2() {
				// 解决view层不同步的问题
				this.scale = this.old.scale
				this.scale = this.old.scale
				this.$nextTick(function() {
					this.scale = 3
				})
			},
			onChange: function(e) {
				this.old.x = e.detail.x
				this.old.y = e.detail.y
			},
			onScale: function(e) {
				this.old.scale = e.detail.scale
			}
		}
	}
</script>

<style>
	movable-view {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 150rpx;
		width: 150rpx;
		background-color: #007AFF;
		color: #fff;
	}

	movable-area {
		height: 300rpx;
		width: 100%;
		background-color: #D8D8D8;
		overflow: hidden;
	}

	.max {
		width:500rpx;
		height: 500rpx;
	}
</style>