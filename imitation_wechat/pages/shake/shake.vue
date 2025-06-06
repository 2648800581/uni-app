<template>
	<view class="container">
		<view class="shake-box" @touchstart="startShake" @touchend="endShake">
			<image :src="shakeImage" class="shake-image" :class="{ shaking: shaking }" mode="aspectFill" />
		</view>
		<view class="hint-text">{{ hintText }}</view>
	</view>
</template>

<script>
	import uni from '@dcloudio/uni-app';

	export default {
		data() {
			return {
				shakeImage: '/static/yyy.png', // 摇一摇图片路径
				shaking: false, // 是否正在摇动中
				hintText: '摇一摇开始', // 提示文本
				shakeStartTime: 0, // 摇动开始时间
				shakeEndTime: 0, // 摇动结束时间
				shakeThreshold: 1000, // 摇动的时间阈值，单位ms
			};
		},
		methods: {
			startShake() {
				this.shaking = true;
				this.hintText = '摇一摇中...';
				this.shakeStartTime = new Date().getTime();
			},
			endShake() {
				this.shaking = false;
				this.shakeEndTime = new Date().getTime();

				if (this.shakeEndTime - this.shakeStartTime >= this.shakeThreshold) {
					this.doShakeAction();
				} else {
					this.hintText = '摇动时间太短';
				}
			},
			doShakeAction() {
				uni.startAccelerometer({
					success: () => {
						uni.onAccelerometerChange(res => {
							// 获取手机加速度感应数据，判断摇动强度
							const {
								x,
								y,
								z
							} = res;
							const strength = Math.sqrt(x * x + y * y + z * z);

							if (strength > 1.5) {
								this.handleShake();
							}
						});
					},
					fail: err => {
						console.error('启用加速度感应失败:', err);
					}
				});
			},
			handleShake() {
				// 处理摇动操作
				console.log('摇一摇成功！');
				uni.showToast({
					title: '摇一摇成功！',
					icon: 'success'
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
		height: 100vh;
		/* 设置容器高度为屏幕高度 */
	}

	.shake-box {
		width: 300rpx;
		height: 300rpx;
	}

	.shake-image {
		width: 100%;
		height: 100%;
		transition: transform 0.3s;
	}

	.shaking {
		animation: shake 0.3s infinite linear;
	}

	@keyframes shake {

		0%,
		100% {
			transform: rotate(-3deg);
		}

		50% {
			transform: rotate(3deg);
		}
	}

	.hint-text {
		margin-top: 20rpx;
		font-size: 30rpx;
		color: #666;
	}
</style>