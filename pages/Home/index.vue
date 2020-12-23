<template>
	<view class="content">
		<view class="head_top">
			<view class="headtitle">小医在诊</view>
			<view class="headfunction">
				<view class="head_location">
						<!-- 三级联动 -->
						<pick-regions :defaultRegion="defaultRegionCode"  @getRegion="handleGetRegion">
							<image src="../../static/img/Home/icon_pic/region.png" class="region" v-if="show"></image>
							<view class="text">
								{{regionName}}
							</view>
							<view class="dian" v-if="down">.</view>
							<image src="../../static/img/Home/icon_pic/down.png" class="down" v-if="down"></image>
						</pick-regions>
				</view>
				<view class="head_search"  @tap="seach">
				   <image src="../../static/img/Home/icon_pic/seach.png" class="seach_pic"></image>
				   <view class="search_txt">
						搜索医院、医生、疾病
				   </view>
				</view>
				<view class="head_information" @tap="information">
					消息
				</view>
			</view>
		</view>
		<view class="more"></view>
		<view class="main">
			<view class="advertise">
				<uni-swiper-dot :info="info" :current="current" field="content" :mode="mode" :dotsStyles="dotsStyles">
				    <swiper class="swiper-box" @change="change">
				        <swiper-item v-for="(item ,index) in info" :key="index">
							<image :src="item.src" class="advertise_pic"></image>
				        </swiper-item>
				    </swiper>
				</uni-swiper-dot>
			</view>
			<view class="subfield_advisory bg">
				<view class="module inquiry">
					<!-- <view class="iconfont icon-wenzhen"></view> -->
					<image src="../../static/img/Home/icon_pic/inquiry.png" class="icon_pic pic1"></image>
					<view class="module_title">问诊</view>
				</view>
				<view class="module consult">
					<!-- <view class="iconfont icon-S_mingyiwenzhengaoxieyazhuanqu"></view> -->
					<image src="../../static/img/Home/icon_pic/consult.png" class="icon_pic pic2"></image>
					<view class="module_title">咨询</view>
				</view>
				<view class="module high-end">
					<!-- <view class="iconfont icon-yiliao"></view> -->
					<image src="../../static/img/Home/icon_pic/high_end.png" class="icon_pic pic3"></image>
					<view class="module_title">高端就医</view>
				</view>
			</view>
			<view class="announcement_top">
				<view class="title">
					公告
				</view>
				<image src="../../static/img/Home/icon_pic/sign.png" class="sign"></image>
				<view class="more">
					更多
				</view>
			</view>
			<view class="subfield_announcement">
				<view class="list uni-flex uni-column">
					<view class="wrap-item">
						<view class="lis uni-flex uni-column" :animation="animationData">
							<view class="uni-flex uni-column" v-for="(item, index) in list" :key="index">
								<view class="swiper-item item_title uni-flex list_item">
									<view class="type uni-flex-item justify-align-center uni-flex">{{ item.type }}</view>
									<view class="time uni-flex-item justify-align-center uni-flex">{{ item.time }}</view>
									<view class="news uni-flex-item justify-align-center uni-flex">{{ item.news }}</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
			<view class="announcement_down">
			</view>
			<view class="subfield_outpatient bg">
				<view class="outpatient_title">
					专科门诊
				</view>
				<view class="outpatient_count">
					累计服务 <span class="nub">{{count}}</span>人次
				</view>
				<view class="department">	
					<view class="department_code" v-for="(item, index) in department" :key="item.code+index">
						<image :src="item.pic" class="department_pic"></image>
						<view class="department_name">
							{{item.name}}
						</view>
					</view>
				</view>
				<view class="all">
					<view class="all_box">
						<image src="../../static/img/Home/icon_pic/all.png" class="all_pic"></image>
						<view class="all_name">
							所有
						</view>
					</view>
				</view>
			</view>
			<view class="subfield_doctors bg" v-for="(item,index) in doctors" :key="item.id">
				<view class="doctors_top">
					<view class="doctors_title">
						专家名医
					</view>
					<view class="doctors_more">
						更多
					</view>
				</view>
				<view class="doctors_content">
					<image src="../../static/img/Home/icon_pic/favorite.png" class="favorite" :v-if="item.favorite=== 'false'"></image>
					<image src="../../static/img/Home/icon_pic/favorite_active.png" class="favorite active" v-if="item.favorite=== 'true'"></image>
					<view class="doctors_photo">
						<image :src="item.photo" class="photos"></image>
					</view>
					<view class="doctors_info">
						<view class="info_one">
							
						</view>
						<view class="info_two">
							
						</view>
						<view class="info_three">
							
						</view>
						<view class="info_four">
							
						</view>
					</view>
					<view class="doctors_tag">
						
					</view>
				</view>
			</view>
		</view>
		<Index></Index>
	</view>
</template>

<script>
	import uniSwiperDot from "@/components/uni-swiper-dot/uni-swiper-dot.vue"
	import pickRegions from '@/components/pick-regions/pick-regions.vue'
	import Index from "../index/index.vue"
	export default {
		components:{
			Index,
			uniSwiperDot,
			pickRegions
		},
		data() {
			return {
				info: [
					{
						src: '../../static/img/Home/pic1.jpg'
					}, 
					{
						src: '../../static/img/Home/pic2.jpg'
					},
					{
						src: '../../static/img/Home/pic3.jpg'
					},
				],
				list: [
					{
						type:'置顶',
						time:'12/20',
						news: '为了确保您的资金安全，请设置支付密码'
					},
					{
						type:'公告',
						time:'12/10',
						news: '新版本震撼发布'
					},
					{
						type:'问诊',
						time:'12/22',
						news: '22日新增确诊病例15例，其中本土1例在辽宁'
					},
					{
						type:'问诊',
						time:'12/22',
						news: '变异新冠病毒或推高儿童感染率'
					},
				],
				department:[
					{
						code:'paediatric',
						name:'儿科',
						pic:'../../static/img/Home/icon_pic/paediatric.png'
					},
					{
						code:'gynecology',
						name:'妇科',
						pic:'../../static/img/Home/icon_pic/gynecology.png'
					},
					{
						code:'dentistry',
						name:'牙科',
						pic:'../../static/img/Home/icon_pic/dentistry.png'
					},
					{
						code:'dermatology',
						name:'手足科',
						pic:'../../static/img/Home/icon_pic/dermatology.png'
					},
					{
						code:'orthopedics',
						name:'骨科',
						pic:'../../static/img/Home/icon_pic/orthopedics.png'
					},
					{
						code:'ophthalmology',
						name:'眼科',
						pic:'../../static/img/Home/icon_pic/ophthalmology.png'
					},
				],
				doctors:[
					{
						id:'a1',
						name:'刘一明',
						rank:'主任医师',
						photo:'../../static/img/Home/photo.png',
						hospital:'山东省立医院',
						department:'眼耳鼻喉科',
						score:'5',
						count:'7098',
						specialize:'擅长：白内障、青光眼、眼外伤、泪道、角膜及眼底病的诊疗',
						label:['2小时必回','效果反馈好','本月名医'],
						favorite: 'false'
					},
					{
						id:'b1',
						name:'刘二明',
						rank:'副主任医师',
						photo:'../../static/img/Home/photo.png',
						hospital:'山东省立医院',
						department:'眼耳鼻喉科',
						score:'4.9',
						count:'6099',
						specialize:'擅长：白内障、青光眼、眼外伤、泪道、角膜及眼底病的诊疗',
						label:['效果反馈好','本月名医'],
						favorite: 'true'
					},
				],
				scrollHeight: 0, //向上滚动距离
				height: 0, //.lis高度（滚动框高度）
				animationData: {}, //动画对象
				dotsStyles:{
					color:'#fff',
					backgroundColor:'#fff',
					border:'#fff',
				},
				current: 0,
				mode: 'round',
				show: true,
				down: false,
				region:[],
				defaultRegion:['山东省','济南市','市中区'],
				defaultRegionCode:'370103',
				count: '123456'
			}
		},
		onLoad() {
	
		},
		mounted() {
			this.prizeScroll();
		},
		computed:{
			regionName(){
				// 转为字符串
				this.region.map(item=>item.name).join(' ')
				this.region = this.region.map(item=>item.name)[1]
				if(this.region !== undefined){
					return this.region.slice(0,2)
				}else{
					return 
				}
			}
		},
		methods: {
			getHeight(Class) {
				let query = uni.createSelectorQuery().in(this);
				query.selectAll(Class).boundingClientRect(data => {
					this.height = data[0].height;
				}).exec();
			},
			prizeScroll() {
				let speed = 100;
				let animation = uni.createAnimation({
					duration: this.getHeight('.lis') / speed,
					timingFunction: 'linear',
					delay: 0
				});
				this.animation = animation;
				setInterval(() => {
					if (this.scrollHeight >= this.height) {
						animation.translateY(0).step();
						this.scrollHeight = 0;
						this.animationData = animation.export();
					} else {
						this.scrollHeight = this.scrollHeight + 1;
						animation.translateY(-this.scrollHeight).step();
						this.animationData = animation.export();
					}
				}, speed);
			},
			change(e) {
				this.current = e.detail.current;
			},
			seach(){
				uni.navigateTo({
					url: './Model/search'
				});
			},
			// 获取选择的地区
			handleGetRegion(region){
				this.show = false
				this.region = region
				this.down = true
			},
			information(){
				
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
		background: #f2f2f2;
		.head_top{
			width: 100%;
			height: 150rpx;
			background: #4f9da2;
			position: fixed;
			top: 0rpx;
			z-index: 999;
			.headtitle{
				width:150rpx;
				height:46rpx;
				font-size:32rpx;
				font-family:PingFang SC;
				font-weight:bold;
				color:#fff;
				margin: 10rpx auto;
			}
			.headfunction{
				.head_location{
					width: 95rpx;
					height: 60rpx;
					font-size: 26rpx;
					color: #333333;
					float: left;
					margin-right: 10rpx;
					text-align: center;
					line-height: 60rpx;
					margin-left: 10rpx;
					.region{
						width: 35rpx;
						height: 35rpx;
						background-size: cover;
						position: absolute;
						top: 75rpx;
						left: 25rpx;
					}
					.text{
						width: 50rpx;
						float: left;
						font-size: 20rpx;
						margin-right: 5rpx;
					}
					.dian{
						width: 2rpx;
						height: 2rpx;
						float: left;
						margin-right: 8rpx;
					}
					.down{
						width: 30rpx;
						height: 30rpx;
						background-size: cover;
						float: left;
						margin-top: 17rpx;
					}
				}
				.head_search{
					width: 70%;
					height: 60rpx;
					background: #fff;
					border-radius: 30rpx;
					float: left;
					.seach_pic{
						width: 40rpx;
						height: 40rpx;
						background-size: cover;
						float: left;
						margin-left: 100rpx;
						margin-top: 10rpx;
						margin-right: 20rpx;
					}
					.search_txt{
						height: 25rpx;
						font-size: 26rpx;
						float: left;
						margin-top: 10rpx;
					}
				}
				.head_information{
					width: 100rox;
					height: 60rpx;
					font-size: 26rpx;
					color: #fff;
					float: right;
					text-align: center;
					line-height: 60rpx;
					margin-right: 10rpx;
				}
			}
			
		}
		.more{
			height: 150rpx;
		}
		.main{
			width: 97%;
			z-index: 998;
			.bg{
				width: 100%;
				background: #fff;
				border-radius: 20rpx;
				margin-top: 15rpx;
			}
			.advertise{
				width: 100%;
				height: 300rpx;
				background: #fff;
				border-radius: 15rpx;
				margin-top: 15rpx;
				.advertise_pic{
					width: 100%;
					height: 100%;
					background-size: cover;
					border-radius: 15rpx;
				}
			}
			.subfield_advisory{
				height: 200rpx;
				.module{
					width: 30%;
					height: 95%;
					// background: #0077AA;
					margin-left: 2.3%;
					float: left;
					margin-top: 0.6%;
					border-radius: 10rpx;
					// .iconfont{
					.icon_pic{
						width: 65%;
						height: 65%;
						color: #fff;
						margin-left: 17%;
						background-size: cover;
					}
					.pic3{
						width: 50%;
						height: 50%;
						margin-top: 10rpx;
						margin-left: 55rpx;
						margin-bottom: 17rpx;
					}
					.module_title{
						text-align: center;
					}
				}
			}
			.announcement_top{
				width: 100%;
				height: 70rpx;
				background: #fff;
				border-radius: 10rpx 10rpx 0 0;
				margin-top: 15rpx;
				.title{
					width: 80rpx;
					height: 40rpx;
					font-size: 26rpx;
					color: #169bd5;
					margin: 10rpx 17rpx;
					float: left;
					text-align: center;
				}
				.sign{
					width: 30rpx;
					height: 30rpx;
					float: left;
					margin-top: 10rpx;
				}
				.more{
					width: 100rpx;
					height: 40rpx;
					float: right;
					margin-top: 10rpx;
					font-size: 26rpx;
					color: #169bd5;
					text-align: center;
				}
			}
			.subfield_announcement{
				width: 100%;
				background: #fff;
				height: 80rpx;
				z-index: 996;
				box-sizing: border-box;
				overflow: hidden;
				.list{
					z-index: 995;
					margin-left: 30rpx;
					width: 80%;
					.type{
						width: 20%;
						height: 40rpx;
						font-size: 26rpx;
						color: #169bd5;
						float: left;
					}
					.time{
						width: 20%;
						height: 40rpx;
						font-size: 26rpx;
						color: #169bd5;
						float: left;
					}
					.news{
						width: 50%;
						height: 40rpx;
						overflow: hidden;
						text-overflow:ellipsis;
						white-space: nowrap;
						font-size: 26rpx;
						color: #169bd5;
					}
				}
			}
			.announcement_down{
				width: 100%;
				height: 50rpx;
				background: #fff;
				border-radius: 0 0 10rpx 10rpx;
			}
			.subfield_outpatient{
				height: 200rpx;
				.outpatient_title{
					width: 120rpx;
					height: 40rpx;
					font-size: 26rpx;
					letter-spacing: normal;
					font-weight: 600;
					float: left;
					color: #333;
					margin-top: 10rpx;
					margin-left: 10rpx;
					text-align: center;
					line-height: 40rpx;
				}
				.outpatient_count{
					width: 250rpx;
					height: 40rpx;
					font-size: 18rpx;
					float: left;
					color: #333;
					margin-top: 10rpx;
					margin-left: 20rpx;
					text-align: center;
					line-height: 40rpx;
					.nub{
						color: red;
					}
				}
				.department{
					width: 75%;
					height: 120rpx;
					float: left;
					margin-left: 10rpx;
					margin-top: 20rpx;
					.department_code{
						width: 16%;
						height: 120rpx;
						float: left;
						margin-left: 0.5%;
						.department_pic{
							width: 95%;
							height: 70rpx;
							background-size: cover;
						}
						.department_name{
							width: 95%;
							height: 40rpx;
							font-size: 26rpx;
							text-align: center;
							line-height: 40rpx;
							color: #1296db;
						}
					}
				}
				.all{
					width: 20%;
					height: 140rpx;
					margin-left: 20rpx;
					float: left;
					.all_box{
						width: 95%;
						height: 120rpx;
						float: left;
						margin-top: 30rpx;
						.all_pic{
							width: 60rpx;
							height: 60rpx;
							background-size: cover;
							margin-left: 36rpx;
						}
						.all_name{
							width: 95%;
							height: 40rpx;
							font-size: 26rpx;
							text-align: center;
							line-height: 40rpx;
							color: #1296db;
						}
					}
				}
			}
			.subfield_doctors{
				height: 400rpx;
				.doctors_top{
					width: 100%;
					height: 50rpx;
					margin-top: 10rpx;
					.doctors_title{
						width: 120rpx;
						height: 40rpx;
						font-size: 26rpx;
						color: #333;
						font-weight: 600;
						margin: 10rpx 17rpx;
						float: left;
						text-align: center;
					}
					.doctors_more{
						width: 100rpx;
						height: 40rpx;
						float: right;
						margin-top: 10rpx;
						margin-right: 10rpx;
						font-size: 26rpx;
						color: #169bd5;
						text-align: center;
					}
				}
				.doctors_content{
					width: 95%;
					height: 320rpx;
					margin: 0 auto;
					border: #eee dashed 2rpx;
					position: relative;
					z-index: 995;
					border-radius: 10rpx;
					.favorite{
						width: 36rpx;
						height: 36rpx;
						background-size: cover;
						position: absolute;
						top: 25rpx;
						right: 20rpx;
						z-index: 996;
					}
					.doctors_photo{
						width: 235rpx;
						height: 235rpx;
						border: #ccc 18rpx solid;
						background-size: cover;
						// margin: 20rpx 15rpx;
						position: absolute;
						top: 20rpx;
						left: 10rpx;
						box-sizing: border-box;
						.photos{
							width: 200rpx;
							height: 200rpx;
							background-size: cover;
						}
					}
					.doctors_info{
						width: 420rpx;
						height: 235rpx;
						border: #007AFF solid 2rpx;
						box-sizing: border-box;
						position: absolute;
						top: 20rpx;
						left: 260rpx;
					}
				}
			}
		}
	}
</style>
