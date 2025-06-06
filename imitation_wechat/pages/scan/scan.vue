<template>
	<view class="container">
		<view class="scan-box">
			<camera :device-position="cameraPosition" :flash="flash" @scanCode="handleScan" @load="handleCameraLoad" />
		</view>
		<view class="scan-tip">将二维码放置在框内，即可自动扫描</view>
		<view class="button" @tap="toggleFlash">
			<image :src="flash ? '/static/sgdgb.png' : '/static/sgddk.png'" class="icon" />
			<text class="text">{{ flash ? '关闭闪光灯' : '打开闪光灯' }}</text>
		</view>
	</view>
</template>

<script>
	import uni from '@dcloudio/uni-app';

	export default {
		data() {
			return {
				cameraPosition: 'back', // 摄像头位置，可选值为 'front' 或 'back'
				flash: false, // 是否打开闪光灯
			};
		},
		methods: {
			handleScan(result) {
				// 处理扫描结果，result 参数即为扫描到的内容
				console.log('扫描结果：', result);
			},
			handleCameraLoad() {
				uni.getSetting({
					success: (res) => {
						if (!res.authSetting['scope.camera']) {
							uni.authorize({
								scope: 'scope.camera',
								success() {
									console.log('用户已允许访问摄像头');
								},
								fail() {
									console.error('用户拒绝访问摄像头');
								},
							});
						}
					},
				});
			},
			toggleFlash() {
				uni.setCameraFlash({
					flash: !this.flash,
					success() {
						console.log('闪光灯状态设置成功');
					},
					fail(err) {
						console.error('闪光灯状态设置失败:', err);
					},
				});
			},
		},
	};
</script>

<style>
	.container {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.scan-box {
		width: 600rpx;
		height: 600rpx;
		position: relative;
	}

	.scan-tip {
		margin-top: 30rpx;
		font-size: 30rpx;
		color: #666;
	}

	.button {
		display: flex;
		align-items: center;
		justify-content: center;
		margin-top: 50rpx;
		background-color: rgba(0, 0, 0, 0.5);
		padding: 20rpx 40rpx;
		border-radius: 50rpx;
	}

	.icon {
		width: 40rpx;
		height: 40rpx;
		margin-right: 10rpx;
	}

	.text {
		font-size: 30rpx;
		color: #ffffff;
	}
</style>