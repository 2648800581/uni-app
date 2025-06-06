<template>
	<view>
		<view slot="header" class="list">
			<view class="list__item">
				<u-avatar shape="square" size="35" icon="man-add-fill" fontSize="26" color="#fe992f"></u-avatar>
				<text class="list__item__user-name">新的朋友</text>
			</view>
			<u-line></u-line>
			<view class="list__item">
				<u-avatar shape="square" size="35" icon="tags-fill" fontSize="26" color="#00c65a"></u-avatar>
				<text class="list__item__user-name">标签</text>
			</view>
			<u-line></u-line>
			<view class="list__item">
				<u-avatar shape="square" size="35" icon="chrome-circle-fill" fontSize="26" color="#1d84e0"></u-avatar>
				<text class="list__item__user-name">朋友圈</text>
			</view>
			<u-line></u-line>
			<view class="list__item">
				<u-avatar shape="square" size="35" icon="qq-fill" fontSize="26" color="#101010"></u-avatar>
				<text class="list__item__user-name">QQ</text>
			</view>
			<u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line>
			<u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line>
			<u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line>
			<u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line><u-line></u-line>
			<!-- 这里开始是八个人的头像和名称 -->
			<view class="list__item" @click="goToProfile('789')">
				<u-avatar :src="src1" shape="square"></u-avatar>
				<text class="list__item__user-name">有机小浅</text>
			</view>
			<u-line></u-line>
			<view class="list__item" @click="goToProfile('123')">
				<u-avatar :src="src2" shape="square"></u-avatar>
				<text class="list__item__user-name">小八姑娘</text>
			</view>
			<u-line></u-line>
			<view class="list__item" @click="goToProfile('456')">
				<u-avatar :src="src3" shape="square"></u-avatar>
				<text class="list__item__user-name">有机弄蛙</text>
			</view>
			<u-line></u-line>
			<view class="list__item" @click="goToProfile('101')">
				<u-avatar :src="src4" shape="square"></u-avatar>
				<text class="list__item__user-name">蜻蜓队长</text>
			</view>
			<u-line></u-line>
			<view class="list__item" @click="goToProfile('112')">
				<u-avatar :src="src5" shape="square"></u-avatar>
				<text class="list__item__user-name">醒醒</text>
			</view>
			<u-line></u-line>
			<view class="list__item" @click="goToProfile('131')">
				<u-avatar :src="src6" shape="square"></u-avatar>
				<text class="list__item__user-name">Eaiz</text>
			</view>
			<u-line></u-line>
			<view class="list__item" @click="goToProfile('415')">
				<u-avatar :src="src7" shape="square"></u-avatar>
				<text class="list__item__user-name">To Overcome All</text>
			</view>
			<u-line></u-line>
			<view class="list__item" @click="goToProfile('161')">
				<u-avatar :src="src8" shape="square"></u-avatar>
				<text class="list__item__user-name">柏豪</text>
			</view>
			<u-line></u-line>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src1: require('../../static/yjxq.jpg'),
				src2: require('../../static/xbgn.jpg'),
				src3: require('../../static/yjnw.jpg'),
				src4: require('../../static/qtdz.jpg'),
				src5: require('../../static/xx.jpg'),
				src6: require('../../static/Eaiz.jpg'),
				src7: require('../../static/ocm.jpg'),
				src8: require('../../static/bh.jpg'),
			}
		},
		methods: {
			goToProfile(userId) {
				// 根据传入的 userId 决定跳转的目标页面
				if (userId === '789') {
					uni.navigateTo({
						url: `/pages/user/yjxq/yjxq?id=${userId}`,
					});
				} else if (userId === '456') {
					uni.navigateTo({
						url: `/pages/user/yjnw/yjnw?id=${userId}`,
					});
				} else if (userId === '123') {
					uni.navigateTo({
						url: `/pages/user/xbgn/xbgn?id=${userId}`,
					});
				} else if (userId === '101') {
					uni.navigateTo({
						url: `/pages/user/qtdz/qtdz?id=${userId}`,
					});
				} else if (userId === '112') {
					uni.navigateTo({
						url: `/pages/user/xx/xx?id=${userId}`,
					});
				} else if (userId === '131') {
					uni.navigateTo({
						url: `/pages/user/Eaiz/Eaiz?id=${userId}`,
					});
				} else if (userId === '415') {
					uni.navigateTo({
						url: `/pages/user/toa/toa?id=${userId}`,
					});
				} else if (userId === '161') {
					uni.navigateTo({
						url: `/pages/user/bh/bh?id=${userId}`,
					});
				}
			},
		},
	}
</script>

<style lang="scss">
	.list {
		&__item {
			@include flex;
			padding: 6px 12px;
			align-items: center;

			&__user-name {
				font-size: 14px;
				margin-left: 10px;
				color: #141414;
			}
		}

		&__footer {
			color: $u-tips-color;
			font-size: 14px;
			text-align: center;
			margin: 15px 0;
		}
	}
</style>