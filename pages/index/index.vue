<template>
	<view class="content">
		<view class="footer">
			<ul>
				<li class="navbar navbar_index" @tap="index">
					<view class="index">
						<view class="iconfont icon-shouye"></view>
						<span class="txt">首页</span>
					</view>
				</li>
				<li class="navbar navbar_information" @tap="information">
					<view class="info">
						<view class="iconfont icon-zixun"></view>
						<span class="txt">资讯</span>
					</view>
				</li>
				<li class="navbar navbar_shop" @tap="shop">
					<view class="shop">
						<view class="iconfont icon-mall"></view>
						<span class="txt">商城</span>
					</view>
				</li>
				<li class="navbar navbar_my" @tap="my">
					<view class="my">
						<view class="iconfont icon-wode"></view>
						<span class="txt">我的</span>
					</view>
				</li>
			</ul>
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
			index(){
				uni.navigateTo({
				    url: '../Home/index'
				});
			},
			information(){
				uni.navigateTo({
				    url: '../Information/Information'
				});
			},
			shop(){
				uni.navigateTo({
				    url: '../Shop/shop'
				});
			},
			my(){
				uni.navigateTo({
				    url: '../My/My'
				});
			}
		}
	}
</script>

<style lang="scss">
	@import url("../../static/iconfont/iconfont.css");
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		.footer{
			width: 100%;
			height: 100rpx;
			position: fixed;
			bottom: 0;
			z-index: 999;
			background: #fff;
			margin: 0;
			padding: 0;
			border-top: 3rpx solid #eee;
			.navbar{
				list-style: none;
				float: left;
				font-size: 24rpx;
				width: 25%;
				color:rgba(153,153,153,1);
				margin-top: 12rpx;
				text-align: center;
				margin-left: -48rpx;
				margin-right: 49rpx;
				.iconfont{
					font-size: 40rpx;
					margin-bottom: 5rpx;
				}
				.txt{
					width:69rpx;
					height:23rpx;
					text-align: center;
				}
			}
		}
	}
</style>
