<template>
	<view class="container">
		<view class="search-box">
			<input class="search-input" type="text" placeholder="请输入关键词" @confirm="addKeyword" v-model="newKeyword" />
			<button class="add-btn" @tap="addKeyword">添加</button>
		</view>
		<view class="keyword-list">
			<view v-for="keyword in keywordList" :key="keyword" class="keyword-item">
				{{ keyword }}
				<button class="delete-btn" @tap="removeKeyword(keyword)">删除</button>
			</view>
		</view>
		<button class="search-btn" @tap="search">搜索</button>
		<view class="result-list">
			<view v-for="(result, index) in results" :key="index" class="result-item">
				{{ result }}
			</view>
		</view>
	</view>
</template>

<script>
	import uni from '@dcloudio/uni-app';

	export default {
		data() {
			return {
				newKeyword: '', // 输入框中的关键词
				keywordList: [], // 关键词列表
				results: [] // 搜索结果列表
			};
		},
		methods: {
			addKeyword() {
				const keyword = this.newKeyword.trim();
				if (keyword !== '' && !this.keywordList.includes(keyword)) {
					this.keywordList.push(keyword);
				}
				this.newKeyword = ''; // 清空输入框
			},
			removeKeyword(keyword) {
				const index = this.keywordList.indexOf(keyword);
				if (index > -1) {
					this.keywordList.splice(index, 1);
				}
			},
			search() {
				if (this.keywordList.length === 0) {
					uni.showToast({
						title: '请添加关键词',
						icon: 'none'
					});
					return;
				}

				// 调用相应的API进行搜索
				uni.showLoading({
					title: '正在搜索...'
				});

				// 这里使用setTimeout模拟异步请求
				setTimeout(() => {
					// 假设搜索结果是一个数组
					this.results = this.keywordList.reduce((acc, keyword) => {
						return [...acc, ...Array(5).fill(`关键词“${keyword}”的搜索结果`)];
					}, []);

					uni.hideLoading();
				}, 1000);
			}
		}
	};
</script>

<style>
	.container {
		padding: 20rpx;
	}

	.search-box {
		display: flex;
		align-items: center;
		margin-bottom: 20rpx;
	}

	.search-input {
		flex: 1;
		height: 60rpx;
		padding: 0 20rpx;
		border: 1rpx solid #ccc;
		border-radius: 30rpx;
		outline: none;
		font-size: 28rpx;
	}

	.search-btn {
		height: 60rpx;
		padding: 0 20rpx;
		border: none;
		outline: none;
		background-color: #aaaaff;
		color: #fff;
		border-radius: 30rpx;
		font-size: 28rpx;
	}

	.result-item {
		padding: 20rpx;
		border-bottom: 1rpx solid #ccc;
		font-size: 32rpx;
		color: #333;
	}

	.add-btn {
		font-size: 26rpx;
		padding: 5rpx 10rpx;
	}

	.keyword-item {
		font-size: 24rpx;
	}

	.delete-btn {
		font-size: 20rpx;
	}
</style>