<template>
	<view class="container">
		<view class="header">
			<text class="title">我的收藏</text>
		</view>

		<view v-if="items.length === 0" class="empty">
			<text>暂无收藏</text>
		</view>

		<view v-else class="list">
			<view v-for="(item, index) in items" :key="index" class="list-item">
				<image class="thumbnail" :src="item.thumbnail" mode="aspectFill"></image>
				<view class="info">
					<text class="title">{{ item.title }}</text>
					<text class="description">{{ item.description }}</text>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				items: [{
						title: '醒醒',
						description: '我在睡觉，别打扰我！',
						thumbnail: '../../static/xx.jpg',
					},
					{
						title: '有机弄蛙',
						description: '我在吃饭，别打扰我！',
						thumbnail: '../../static/yjnw.jpg',
					},
				],
			};
		},
	};
</script>

<style scoped>
	.container {
		padding: 20rpx;
	}

	.header {
		margin-bottom: 20rpx;
	}

	.title {
		font-size: 38rpx;
		font-weight: bold;
		color: #55557f;
	}

	.empty {
		height: 200rpx;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.list-item {
		display: flex;
		margin-bottom: 20rpx;
		padding-bottom: 10rpx;
		border-bottom: 1px solid #ccc;
	}

	.thumbnail {
		width: 100rpx;
		height: 100rpx;
		margin-right: 20rpx;
		border-radius: 5rpx;
	}

	.info {
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.title {
		font-size: 28rpx;
		font-weight: bold;
	}

	.description {
		font-size: 24rpx;
		color: #999;
	}
</style>