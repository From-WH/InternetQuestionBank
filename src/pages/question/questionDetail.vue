<template>
	<view class="questionDetail">
		<view class="top">
			<!-- 顶部的bar -->
			<view class="navigationBar">
				<image class="back" @click="handleBack" src="../../static/common/back.png" />
				<view class="navigationBarTitle">详情</view>
			</view>
			<view class="title">
				用递归算法实现，数组长度为5且元素的随机数在2-32间不重复的值间不重复的值
			</view>
			<view class="info">
				<view class="tags">
					<view class="tag">基础</view>
					<view class="tag">算法</view>
				</view>
				<view class="browse">
					<image src="../../static/question/eyes.png"></image>
					<view class="content">1.3k人已浏览</view>
				</view>
			</view>
		</view>
		<view class="main">
			<view class="tab">
				<Tabs :lineScale="0.3" lineColor="#526EE7" lineRadius="4rpx" activeColor="#526EE7" :bold="false"
				 :scroll="false" v-model="tabCurrent" :tabs="tabs"></Tabs>
			</view>
			<swiper :current="tabCurrent" @change="handleSwiperChange" :style="{height: swiperHeight + 'px'}">
				<swiper-item @touchmove.stop>
					<view class="itemCard">
						<view class="itemCardTop">
							<image class="headPicture" src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1441836571,2166773131&fm=26&gp=0.jpg"
							 mode="scaleToFill"></image>
							<view class="nickname">前端每日3+1</view>
						</view>
						<view class="itemBody">
							<!-- 可能有图片 -->
							<view class="images">
								<image src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1441836571,2166773131&fm=26&gp=0.jpg"
								 mode="scaleToFill"></image>
								<image src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1441836571,2166773131&fm=26&gp=0.jpg"
								 mode="scaleToFill"></image>
								<image src="https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=1441836571,2166773131&fm=26&gp=0.jpg"
								 mode="scaleToFill"></image>
							</view>
							<view class="itemMain">
								这是一道大题目，把考点拆成了4个小项；需要侯选人用递归算法实现（限制15行代码以内实现；限制时间10分钟内完成）归算法实现…
							</view>
						</view>
					</view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import Tabs from "../../components/v-tabs/v-tabs.vue"
	import { ref } from "vue";
	export default {
		setup() {
			// 计算屏幕高度 - tab的高度 - 导航栏的高度 = swiper高度
			const swiperHeight = uni.getSystemInfoSync().screenHeight - 251;
			const tabCurrent = ref(0);
			const tabs = ref(['解答']);

			function handleSwiperChange(e) {
				tabCurrent.value = e.detail.current;
			}

			function handleBack() {
				uni.navigateBack({
					delta: 1
				})
			}
			return {
				swiperHeight,
				tabCurrent,
				tabs,
				handleSwiperChange,
				handleBack
			}
		},
		components: {
			Tabs
		}
	}
</script>

<style lang="scss">
	.questionDetail {
		height: 100vh;
		overflow-y: hidden;
		.top {
			display: inline-block;
			position: relative;
			width: 100%;
			height: 396rpx;
			background: linear-gradient(360deg, #809BF5 0%, #506BE6 100%);

			.navigationBar {
				width: calc(100% - 80rpx);
				position: relative;
				display: flex;
				justify-content: center;
				align-items: center;
				margin: calc(50rpx + 30rpx) 40rpx auto 40rpx;

				.back {
					position: absolute;
					left: 0;
					top: 50%;
					transform: translateY(-50%);
					width: 14rpx;
					height: 26rpx;
				}

				.navigationBarTitle {
					font-size: 36rpx;
					color: #fff;
				}
			}

			.title {
				width: 666rpx;
				margin: 0 auto;
				font-size: 32rpx;
				color: #fff;
				margin-top: 54rpx;
			}

			.info {
				display: flex;
				justify-content: space-between;
				align-items: center;
				width: 666rpx;
				margin: 0 auto;
				margin-top: 20rpx;

				.tags {
					display: flex;
					justify-content: flex-start;
					align-items: center;

					.tag {
						color: #fff;
						font-size: 24rpx;
						background: linear-gradient(270deg, #FFD398 0%, #FFA85F 100%);
						border-radius: 2px;
						padding: 2rpx 16rpx;
					}

					.tag:not(:last-child) {
						margin-right: 16rpx;
					}
				}

				.browse {
					display: flex;
					justify-content: flex-start;
					align-items: center;

					image {
						width: 34rpx;
						height: 20rpx;
						margin-right: 10rpx;
					}

					.content {
						font-size: 24rpx;
						color: #fff;
					}
				}
			}
		}

		.main {
			display: inline-block;
			width: 750rpx;
			background: #FFFFFF;
			border-radius: 25px 25px 0px 0px;
			transform: translateY(-64rpx);
			.tab{
				width: 200rpx;
				margin-top: 30rpx;
				transform: translateX(-24rpx);
			}
			.itemCard {
				padding: 30rpx;

				&:not(:first-child) {
					border-top: 2rpx solid #F1F3FC;
				}

				.itemCardTop {
					display: flex;
					justify-content: flex-start;
					align-items: center;

					.headPicture {
						width: 64rpx;
						height: 64rpx;
						border-radius: 50%;
						border: 2px solid #fff;
					}

					.nickname {
						font-size: 28rpx;
						margin-left: 16rpx;
					}
				}

				.itemBody {

					.images {
						display: flex;
						justify-content: flex-start;
						align-items: center;
						margin-top: 20rpx;

						image {
							width: 216rpx;
							height: 162rpx;
							border-radius: 15rpx;

							&:not(:first-child) {
								margin-left: 22rpx;
							}
						}
					}

					.itemMain {
						width: 690rpx;
						color: #666666;
						font-size: 28rpx;
						margin-top: 20rpx;
					}
				}
			}
		}
	}
</style>
