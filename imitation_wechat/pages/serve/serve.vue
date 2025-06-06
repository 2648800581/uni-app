<template>
	<view class="container">
		<view class="top">
			<view class="top-item">
				<image src="../../static/sfk.png" class="icon-big"></image>
				<text class="text-big">收付款</text>
			</view>
			<view class="top-item">
				<image src="../../static/qb.png" class="icon-big"></image>
				<text class="text-big">钱包</text>
			</view>
		</view>
		<view class="category">
			<text class="category-title">金融理财</text>
			<view class="category-row">
				<view class="category-item" v-for="(item, index) in financialList" :key="index">
					<image :src="item.icon" class="icon-small"></image>
					<text class="text-small">{{ item.title }}</text>
				</view>
			</view>
		</view>
		<view class="category">
			<text class="category-title">生活服务</text>
			<view class="category-row">
				<view class="category-item" v-for="(item, index) in lifeList" :key="index">
					<image :src="item.icon" class="icon-small"></image>
					<text class="text-small">{{ item.title }}</text>
				</view>
			</view>
		</view>
		<view class="category">
			<text class="category-title">交通出行</text>
			<view class="category-row">
				<view class="category-item" v-for="(item, index) in travelList" :key="index">
					<image :src="item.icon" class="icon-small"></image>
					<text class="text-small">{{ item.title }}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				financialList: [{
						title: '信用卡还款',
						icon: '/static/xykhk.png'
					},
					{
						title: '理财通',
						icon: '/static/lct.png'
					},
					{
						title: '保险服务',
						icon: '/static/bxfw.png'
					},
				],
				lifeList: [{
						title: '手机充值',
						icon: '/static/sjcz.png'
					},
					{
						title: '生活缴费',
						icon: '/static/shjf.png'
					},
					{
						title: '城市服务',
						icon: '/static/csfw.png'
					},
					{
						title: '医疗健康',
						icon: '/static/yljk.png'
					},
				],
				travelList: [{
						title: '出行服务',
						icon: '/static/cxfw.png'
					},
					{
						title: '火车票机票',
						icon: '/static/hcpjp.png'
					},
					{
						title: '滴滴出行',
						icon: '/static/ddcx.png'
					},
					{
						title: '酒店',
						icon: '/static/jd1.png'
					},
				]
			};
		}
	};
</script>

<style>
	.container {
		background-color: #19b061;
		height: 12vh;
		padding: 20rpx;
		border-radius: 10px;
		box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
	}

	.top {
		display: flex;
		justify-content: space-between;
		margin-bottom: 20rpx;
	}

	.top-item {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-left: 80rpx;
		margin-right: 80rpx;
	}

	.icon-big {
		width: 140rpx;
		height: 120rpx;
	}

	.text-big {
		font-size: 36rpx;
		font-weight: bold;
		color: #ffffff;
		margin-top: 10rpx;
	}

	.category {
		margin-bottom: 20rpx;
	}

	.category-title {
		font-size: 28rpx;
		color: #333;
		margin-bottom: 10rpx;
	}

	.category-row {
		display: flex;
		justify-content: center;
	}

	.category-item {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-right: 40rpx;
	}

	.icon-small {
		width: 100rpx;
		height: 100rpx;
	}

	.text-small {
		font-size: 32rpx;
		font-weight: bold;
		color: #666;
		margin-top: 10rpx;
	}
</style>