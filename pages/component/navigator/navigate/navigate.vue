<template>
	<view>
		<page-head :title="title"></page-head>
	</view>
</template>
<script>
	export default {
		data() {
			return {
				title: '新建的页面'
			}
		},
		onLoad: function (option) { 
			//option为object类型，会序列化上个页面传递的参数
			console.log(option); //打印出上个页面传递的参数。
			console.log(option.title); //打印出上个页面传递的参数。
		}
	}
</script>
