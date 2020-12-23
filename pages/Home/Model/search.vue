<template>
	<view class="content">
		<view class="top">
			<view class="iconfont icon-fanhui" style="color: #fff;" @tap="getback"></view>
			<view class="txt">搜索</view>
		</view>
		<view class="head_top">
			<view class="search">
				<uni-search-bar :radius="100" @confirm="search" placeholder="搜索医院、医生、疾病"></uni-search-bar>
			</view>
		</view>
		<view class="main">
			
		</view>
	</view>
</template>

<script>
	import uniSearchBar from '@/components/uni-search-bar/uni-search-bar.vue'
	export default {
		components:{
			uniSearchBar
		},
		data() {
			return {
				news:[]
			}
		},
		onLoad() {
	
		},
		methods: {
			//返回
			getback(){
				uni.navigateTo({
				    url: '../index'
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
			background: #4f9da2;
			.iconfont{
				font-size: 40rpx;
				color: #fff;
				float: left;
				margin-top: 20rpx;
			}
			.txt{
				font-size:36rpx;
				font-family:PingFang SC;
				font-weight:bold;
				color:#fff;
				text-align: center;
				margin-top: 20rpx;
			}
		}
		.head_top{
			width: 100%;
			height: 120rpx;
			background: #4f9da2;
			.search{
				margin-left: 25rpx;
				.uni-searchbar{
					width: 90%;
					height: 50rpx;
					background: #4f9da2;
				}
			}
		}
		.main{
			width: 670rpx;
			margin-top: 50rpx;
			
		}
	}
</style>
