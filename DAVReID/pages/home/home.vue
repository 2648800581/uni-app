<template>
	<view class="home">
		<view class="button-container">
			<button class="query-btn" @click="goToQueryPage()">车辆查询集</button>
			<button class="upload-btn" @click="chooseImage()">上传数据</button>
		</view>
		<view class="description">选择您想要查询的目标车辆图片</view>
		<view class="car-images">
			<!-- First row of images -->
			<view class="image-row">
				<image class="car-image" v-for="(image, index) in carImageList.slice(0, 3)" :key="index" :src="image"
					mode="aspectFill" @click="handleImageClick(index, 1)"></image>
			</view>
			<!-- Second row of images -->
			<view class="image-row">
				<image class="car-image" v-for="(image, index) in carImageList.slice(3, 6)" :key="index + 3"
					:src="image" mode="aspectFill" @click="handleImageClick(index + 3, 2)"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				carImageList: [
					'/static/Ve_01_q.png',
					'/static/Ve_02_q.png',
					'/static/Ve_03_q.png',
					'/static/Ve_04_q.png',
					'/static/Ve_05_q.png',
					'/static/Ve_06_q.png'
				]
			}
		},
		methods: {
			goToQueryPage() {
				uni.navigateTo({
					url: '/pages/query/query'
				})
			},
			handleImageClick(index, pageNum) {
				pageNum = index + 1;
				uni.navigateTo({
					url: '/pages/show/show' + pageNum + '?index=' + index
				})
			},
			chooseImage() {
				uni.chooseImage({
					count: 1, // 只能选择一张图片
					sizeType: ['compressed'], // 压缩图片
					sourceType: ['album', 'camera'], // 从相册选择或者拍照
					success: (res) => {
						const tempFilePaths = res.tempFilePaths;
						this.uploadFile(tempFilePaths[0]);
					},
					fail: (err) => {
						console.error('选择图片失败', err);
					}
				});
			},
			uploadFile(filePath) {
				uni.uploadFile({
					url: 'https://example.com/upload',
					filePath: filePath,
					name: 'file',
					success: (res) => {
						console.log('上传成功', res.data);
						// 处理上传成功的逻辑
					},
					fail: (err) => {
						console.error('上传失败', err);
						// 处理上传失败的逻辑
					}
				});
			}
		}
	}
</script>

<style scoped lang="scss">
	.home {
		background-image: url('/static/background.jpg');
		background-size: cover;
		background-position: center;
		height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.button-container {
		display: flex;
		justify-content: center;
		margin-top: 50upx;
	}

	.query-btn,
	.upload-btn {
		width: 300upx;
		height: 100upx;
		background-color: #22aaff;
		border-radius: 50upx;
		color: #dfdfdf;
		font-size: 44upx;
		text-align: center;
		line-height: 100upx;
		font-weight: 400;
		margin-right: 20upx;
	}

	.description {
		margin-top: 30upx;
		font-size: 40upx;
		font-weight: bold;
		color: #ffffff;
	}

	.car-images {
		margin-top: 30upx;
	}

	.image-row {
		display: flex;
		justify-content: space-around;
		margin-bottom: 90upx;
	}

	.car-image {
		width: 600upx;
		height: 600upx;
		margin: 0 100upx;
	}
</style>