<template>
	<view class="content">
		<view class="top">
			<view class="iconfont icon-fanhui" style="color: rgba(51,51,51,1);" @tap="getback"></view>
			<view class="txt">用户协议</view>
		</view>
		<view class="main">
			
		</view>
	</view>
</template>

<script>
	export default {
		components:{

		},
		data() {
			return {

			}
		},
		onLoad() {
	
		},
		methods: {
			//返回上一页
			getback(){
				uni.navigateTo({
				    url: './register'
				});
			},
		}
	}
</script>

<style lang="scss">
	@import url("../../../static/iconfont/iconfont.css");
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		.top{
			width: 100%;
			height: 90rpx;
			border-bottom: 2rpx solid #eee;
			.iconfont{
				font-size: 40rpx;
				color: rgba(51,51,51,1);
				float: left;
				margin-top: 20rpx;
			}
			.txt{
				font-size:36rpx;
				font-family:PingFang SC;
				font-weight:bold;
				color:rgba(51,51,51,1);
				text-align: center;
				margin-top: 20rpx;
			}
		}
		.main{
			width: 660rpx;
			margin-top: 100rpx;
		}
		
	}
</style>
