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
				<input class="input phone" @input="Inputphone" v-model="phone" type="text" placeholder="请输入手机号" />
				<button class="verification get" v-if="get_show" @tap="get">
					{{btn_txt}}
				</button>
				<view class="verification time" v-if="time_show">
					{{time}}s后重新获取
				</view>
			</view>
			<view class="uni-form-item uni-column">
				<input class="input verification_code" @input="Inputverification" v-model="verification_code" placeholder="请输入验证码" />
			</view>
		</view>
		<view class="button">
			<button class="submit" @tap="submit">提交</button>
		</view>
	</view>
</template>

<script>
	export default {
		components: {
			
		},
		onLoad() {
			console.log('默认验证码：123456')
			console.log('密码格式：数字加字母，长度6位以上')
		},
		data() {
			return {
				phone: '',
				password: '',
				password2: '',
				verification_code: '',
				btn_txt:'获取验证码',
				checked: false,
				get_show: true,
				time_show: false,
				time: ''
			}
		},
		methods: {
			//返回上一页
			getback() {
				uni.navigateTo({
					url: '../login'
				});
			},
			Inputphone: function(event) {
				this.phone = event.target.value
			},
			Inputpassword: function(event) {
				this.password = event.target.value
			},
			Inputpassword2: function(event) {
				this.password2 = event.target.value
			},
			Inputverification: function(event) {
				this.verification_code = event.target.value
			},
			change() {
				this.checked = !this.checked
			},
			//获取验证码
			get() {
				if (this.phone === '') {
					uni.showToast({
						title: '请输入手机号码',
						icon: "none"
					});
				} else {
					if(!(/^1(3|4|5|6|7|8|9)\d{9}$/.test(this.phone))){
						 uni.showToast({
							title: '手机号错误',
							icon: "none"
						 });
					}else{
						this.get_show = false
						this.time_show = true
						// if (this.time > 0) {
						// 	uni.showToast({
						// 		title: '不能重复获取',
						// 		icon: "none"
						// 	});
						// 	return;
						// } else {
							this.time = 60
							let timer = setInterval(() => {
								this.time--;
								if (this.time < 1) {
									clearInterval(timer);
									this.time = 0
									this.get_show = true
									this.time_show = false
									this.btn_txt = '重新获取'
								}
							}, 1000)
						// }
					}
					
				}
			},
			//提交
			submit() {
				if(this.password !== ''){
					if(!(/^(?![0-9]+$)(?![a-zA-Z]+$)[0-9A-Za-z]{6,}$/.test(this.password))){
						uni.showToast({
							title: '密码格式不正确',
							icon: "none"
						});
					}else{
						if (this.password !== this.password2) {
							uni.showToast({
								title: '两次密码输入不一致',
								icon: "none"
							});
							this.password = '',
							this.password2 = ''
						} else {
							if (this.verification_code !== '123456') {
								uni.showToast({
									title: '验证码错误',
									icon: "none"
								});
							} else {
								uni.navigateTo({
									url: '../login'
								});
								this.phone = '',
								this.password = '',
								this.password2 = '',
								this.verification_code = ''
							}
						}
					}
					
				}else{
					uni.showToast({
						title: '请输入新密码',
						icon: "none"
					});
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

		.top {
			width: 100%;
			height: 90rpx;
			border-bottom: 2rpx solid #eee;

			.iconfont {
				font-size: 40rpx;
				color: rgba(51, 51, 51, 1);
				float: left;
				margin-top: 20rpx;
			}

			.txt {
				font-size: 36rpx;
				font-family: PingFang SC;
				font-weight: bold;
				color: rgba(51, 51, 51, 1);
				text-align: center;
				margin-top: 20rpx;
			}
		}

		.logo {
			width: 180rpx;
			height: 180rpx;
			margin-top: 10rpx;
		}

		.head-title {
			width: 310rpx;
			height: 120rpx;
			margin-top: 30rpx;
			font-weight: 600;
			font-size: 39rpx;
		}

		.main {
			width: 650rpx;
			.input {
				height: 80rpx;
				border-bottom: 2rpx solid rgba(213, 217, 225, 1);
				background-color: #FFF !important;

				.uni-input-input {
					background-color: #FFF !important;
				}
			}

			.phone {
				width: 65%;
			}

			.verification {
				width: 34%;
				height: 81rpx;
				float: right;
				margin-top: -81rpx;
			}

			.get {
				font-size: 30rpx;
			}

			.time {
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: center;
				font-size: 24rpx;
				border: 2rpx solid rgba(213, 217, 225, 1);
				box-sizing: border-box;
				border-radius: 10rpx;
				color: rgba(155, 217, 225, 1);
			}

			.checked_box {
				margin-top: 20rpx;

				.checked_option {
					transform: scale(0.7);
					float: left;
					color: rgba(47, 109, 224, 1);
				}

				.checked_txt {
					font-size: 28rpx;
					float: left;
					margin-top: 6rpx;
					color: #169bd5;
					font-weight: 500;
				}
			}
		}

		.button {
			margin-top: 100rpx;

			.submit {
				width: 640rpx;
				background: #169bd5;
				color: #fff;
				font-size: 36rpx;
			}
		}
	}
</style>
