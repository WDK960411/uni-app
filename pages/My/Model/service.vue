<template>
	<view class="content">
		<view class="top">
			<view class="iconfont icon-fanhui" style="color: rgba(51,51,51,1);" @tap="getback"></view>
			<view class="txt">客服</view>
		</view>
		<view class="phone">400-800-5888</view>
		<view class="call" @click="call">
			一键呼叫
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {
	
		},
		methods: {
			//返回
			getback(){
				uni.navigateTo({
				    url: '../My'
				});
			},	
			//拨打电话
			call(){
				uni.makePhoneCall({
				    phoneNumber: '400-800-5888' 
				});
			}
		}
	}
</script>

<style lang="scss">
	@import url("../../../static/iconfont/iconfont.css");
	.content{
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
		.phone{
			font-size:48rpx;
			font-family:PingFang SC;
			font-weight:bold;
			color:rgba(51,51,51,1);
			margin-top: 100rpx;
		}
		.call{
			width:690rpx;
			height:90rpx;
			background:rgba(255,255,255,1);
			border:1rpx solid rgba(47,109,224,1);
			border-radius:10rpx;
			font-size:36rpx;
			font-family:PingFang SC;
			font-weight:bold;
			color:rgba(47,109,224,1);
			margin-top: 60rpx;
			display: flex;
			flex-direction: column;
			align-items: center;
			justify-content: center;
		}
	}
</style>
