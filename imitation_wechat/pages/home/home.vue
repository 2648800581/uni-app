<template>
	<view class="container">
		<scroll-view class="chat-content" scroll-y>
			<view v-for="(message, index) in messages" :key="index">
				<view class="message">
					<image class="avatar" :src="message.avatar" mode="aspectFill" @click="goToProfile(message.userId)">
					</image>
					<view class="message-content">
						<view class="message-header">
							<text class="nickname">{{ message.nickname }}</text>
						</view>
						<view class="message-text">
							<text class="text">{{ message.text }}</text>
						</view>
					</view>
				</view>
				<view v-if="index !== messages.length - 1" class="divider"></view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				messages: [{
						nickname: '小八姑娘',
						avatar: '../../static/xbgn.jpg',
						userId: '123',
						text: '今天中午出去吃饭吧！',
					},
					{
						nickname: '有机弄蛙',
						avatar: '../../static/yjnw.jpg',
						userId: '456',
						text: '这次的英语水平测试好难啊，感觉过不了了',
					},
					{
						nickname: '有机小浅',
						avatar: '../../static/yjxq.jpg',
						userId: '789',
						text: '今天去图书馆学习',
					},
					{
						nickname: '蜻蜓队长',
						avatar: '../../static/qtdz.jpg',
						userId: '101',
						text: '科目四没刷题，结果运气好过了，哈哈哈',
					},
					{
						nickname: '醒醒',
						avatar: '../../static/xx.jpg',
						userId: '112',
						text: '去食堂打包一个新疆炒米粉',
					},
					{
						nickname: 'Eaiz',
						avatar: '../../static/Eaiz.jpg',
						userId: '131',
						text: '彪彪，给我带一份米粉，加个蛋',
					},
					{
						nickname: 'To Overcome All',
						avatar: '../../static/ocm.jpg',
						userId: '415',
						text: '今天晚上一起五排上分',
					},
					{
						nickname: '柏豪',
						avatar: '../../static/bh.jpg',
						userId: '161',
						text: '今天还不去图书馆学习？',
					},
				],
			};
		},
		methods: {
			goToProfile(userId) {
				// 根据传入的 userId 判断跳转的目标页面
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
	};
</script>

<style scoped>
	.container {
		padding: 20rpx;
	}

	.chat-content {
		height: 100vh;
	}

	.message {
		display: flex;
		align-items: center;
		margin-bottom: 20rpx;
	}

	.avatar {
		width: 90rpx;
		height: 90rpx;
		border-radius: 0;
	}

	.message-content {
		margin-left: 10rpx;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.message-header {
		margin-bottom: 0rpx;
	}

	.nickname {
		font-size: 34rpx;
		color: #242424;
	}

	.message-text {
		margin-top: 0rpx;
	}

	.text {
		font-size: 30rpx;
		color: #333;
	}

	.divider {
		height: 1rpx;
		background-color: #ccc;
		margin-left: 100rpx;
		/* 根据布局调整分隔线的偏移量 */
	}
</style>