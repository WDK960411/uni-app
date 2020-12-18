<template>
	<view class="content">
		<view class="top">
			<view class="iconfont icon-fanhui" style="color: rgba(51,51,51,1);" @tap="getback"></view>
			<view class="txt">密码重置</view>
		</view>
		<view class="main">
			<view class="uni-form-item uni-column">
				<input class="input password" @input="Inputpassword" v-model="password" password type="text" placeholder="请输入新密码" />
			</view>
			<view class="uni-form-item uni-column">
				<input class="input password2" @input="Inputpassword2" v-model="password2" password type="text" placeholder="请确认新密码" />
			</view>
			<view class="uni-form-item uni-column">
				<input class="input phone" @input="Inputphone"  v-model="phone" type="text" placeholder="请输入手机号" />
				<button class="verification get" v-if="get_show" @tap="get">
					获取验证码
				</button>
				<view class="verification time" v-if="time_show">
					{{time}}秒后再获取
				</view>
			</view>
			<view class="uni-form-item uni-column" >
				<input class="input verification_code" @input="Inputverification" v-model="verification_code" placeholder="请输入验证码" />
			</view>
		</view>
		<view class="button">
			<button  class="submit" @tap="submit">提交</button>
		</view>
	</view>
</template>

<script>
	import Index from "../../index/index.vue"
	export default {
		components:{
			Index,
		},
		data() {
			return {
				phone:'',
				password:'',
				password2:'',
				verification_code:'',
				checked:false,
				get_show:true,
				time_show:false,
				time: '59'
			}
		},
		onLoad() {
	
		},
		methods: {
			//返回上一页
			getback(){
				uni.navigateTo({
				    url: '../login'
				});
			},
			Inputphone:function(event) {
				this.phone = event.target.value
			},
			Inputpassword:function(event) {
				this.password = event.target.value
			},
			Inputpassword2:function(event) {
				this.password2 = event.target.value
			},
			Inputverification:function(event) {
				this.verification_code = event.target.value
			},
			change(){
				this.checked = !this.checked
			},
			//获取验证码
			get(){
				if(this.phone === ''){
					alert('请输入手机号码')
				}else{
					this.get_show = false
					this.time_show = true
				}
			},
			//提交
			submit(){
				if(this.password !== this.password2){
					alert('两次密码输入不一致')
					this.password = '',
					this.password2 = ''
				}else{
					if(this.time_show = false){
						alert('请先获取验证码')
					}else{
						this.phone = '',
						this.password = '',
						this.password2 = '',
						this.verification_code = '',
						uni.navigateTo({
							url: '../login'
						});
					}
				}
			}
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
		.logo{
			width: 180rpx;
			height: 180rpx;
			margin-top: 10rpx;
		}
		.head-title{
			width: 310rpx;
			height: 120rpx;
			margin-top: 30rpx;
			font-weight: 600;
			font-size: 39rpx;
		}
		.main{
			width: 660rpx;
			.input{
				height: 80rpx;
				border-bottom: 2rpx solid rgba(213,217,225,1);
				background-color: #FFF !important;
				.uni-input-input{
					background-color: #FFF !important;
				}
			}
			.phone{
				width: 65%;
			}
			.verification{
				width: 34%;
				height: 81rpx;
				float: right;
				margin-top: -81rpx;
			}
			.get{
				font-size: 30rpx;
			}
			.time{
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: center;
				font-size: 24rpx;
				border: 2rpx solid rgba(213,217,225,1);
				box-sizing: border-box;
				border-radius: 10rpx;
				color: rgba(155,217,225,1);
			}
			.checked_box{
				margin-top: 20rpx;
				.checked_option{
					transform:scale(0.7);
					float: left;
					color:rgba(47,109,224,1);
				}
				.checked_txt{
					font-size: 28rpx;
					float: left;
					margin-top: 6rpx;
					color:#169bd5;
					font-weight: 500;
				}
			}
		}
		.button{
			margin-top: 100rpx;
			.submit{
				width: 690rpx;
				background:#169bd5;
				color: #fff;
				font-size: 36rpx;
			}
		}
	}
</style>
