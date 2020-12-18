<template>
	<view class="content">
		<view class="headtitle">我的</view>
		<view class="head"  @tap=modifieddata>
			<view class="imghead">
				<image class="img" src="../../static/img/head_portrait.png" mode=""></image>
			</view>
			<view class="data">
				<view class="name">
					张三
				</view>
				<view class="post">
					176****0641
				</view>
			</view>
			<image class="right" src="../../static/img/right.png" mode=""></image>
		</view>
		<view class="mymain">
			<ul class="option">
				<li class="list help" @tap="help">
					<view class="iconfont icon-bangzhu" style="color: #3C7FFC;"></view>
					<view class="txt">帮助</view>
					<image class="you" src="../../static/img/you.png" mode=""></image>
				</li>
				<li class="list service" @tap="service">
					<view class="iconfont icon-htmal5icon31" style="color: #3C7FFC;"></view>
					<view class="txt">客服</view>
					<image class="you" src="../../static/img/you.png" mode=""></image>
				</li>
				<li class="list regard" @tap="regard">
					<view class="iconfont icon-guanyu" style="color: #2EC06F;"></view>
					<view class="txt">关于</view>
					<image class="you" src="../../static/img/you.png" mode=""></image>
				</li>
			</ul>
			<view class="exit" @tap="exit">
				退出
			</view>
		</view>
		<Index></Index>
	</view>
</template>

<script>
	import Index from "../index/index.vue"
	export default {
		components:{
			Index,
		},
		data() {
			return {
				
			}
		},
		onLoad() {
	
		},
		methods: {
			//修改资料
			modifieddata(){
				uni.reLaunch({
					url: './Model/ModifiedData'
				});
			},
			//帮助
			help(){
				console.log('帮助');
				// uni.reLaunch({
				//     url: './Model/service'
				// });
			},
			//客服
			service(){
				uni.reLaunch({
				    url: './Model/service'
				});
			},
			//关于
			regard(){
				console.log('关于');
				// uni.reLaunch({
				//     url: './Model/service'
				// });
			},
			//退出
			exit(){
				uni.reLaunch({
					url: '../login/login'
				});
			}
		}
	}
</script>

<style lang="scss">
	@import url("../../static/iconfont/iconfont.css");
	.content{
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		.headtitle{
			width:100rpx;
			height:46rpx;
			font-size:48rpx;
			font-family:PingFang SC;
			font-weight:bold;
			color:rgba(51,51,51,1);
			position: relative;
			top: 60rpx;
			left: -280rpx;
		}
		.head{
			width: 650rpx;
			height: 260rpx;
			background:linear-gradient(90deg,rgba(47,109,224,1) 0%,rgba(28,84,188,1) 100%);
			border-radius:10px;
			margin-top: 150rpx;
			.imghead{
				width: 150rpx;
				height: 150rpx;
				border: 4rpx solid #FFF;
				border-radius:50%;
				overflow: hidden;
				float: left;
				margin-top: 45rpx;
				margin-left: 50rpx;
				.img{
					width: 150rpx;
					height: 150rpx;
				}
			}
			.data{
				float: left;
				color:rgba(255,255,255,1);
				margin-top: 50rpx;
				margin-left: 40rpx;
				.name{
					font-size:48rpx;
				}
				.post{
					font-size:28rpx;
					margin-top: 45rpx;
					font-family:PingFang SC;
				}
			}
			.right{
				float: right;
				width: 40rpx;
				height: 40rpx;
				margin-top: 100rpx;
				margin-right: 20rpx;
			}
		}
		.mymain{
			margin-top: 50rpx;
			width: 690rpx;
			height: 550rpx;
			.option{
				width:690rpx;
				list-style: none;
				padding: 0;
				.list{
					height: 120rpx;
					border-bottom: 2rpx solid rgba(228,228,228,1);
					.iconfont{
						font-size: 40rpx;
						float: left;
						margin-top: 30rpx;
					}
					.txt{
						font-size:32rpx;
						font-family:PingFang SC;
						font-weight:500;
						color:rgba(51,51,51,1);
						float: left;
						margin-top: 30rpx;
						margin-left: 19rpx;
					}
					.you{
						float: right;
						width: 40rpx;
						height: 40rpx;
						margin-top: 35rpx;
					}
				}
				
			}
			.exit{
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
	}
</style>
