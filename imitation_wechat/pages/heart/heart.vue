<template>
	<view class="main">
		<view class="btn-list">
			<view style="text-align:center;">
				<u-button icon="photo-fill" iconColor="#c24a4a" text="上传图片" size="normal" type="info" :plain="true"
					:hairline="true" @click="getPhoto()"></u-button>
				<u-button icon="rewind-right-fill" iconColor="#ffaa00" text="切换音乐" size="normal" type="info"
					:plain="true" :hairline="true" @click="playNextAudio()"></u-button>
				<u-button icon="play-circle-fill" iconColor="#18c605" text="播放音乐" size="normal" type="info"
					:plain="true" :hairline="true" @click="doPlay()"></u-button>
				<u-button icon="pause-circle-fill" iconColor="#04a0b4" text="暂停音乐" size="normal" type="info"
					:plain="true" :hairline="true" @click="doPause()"></u-button>
				<view style="margin-top: 20rpx;">
					播放进度:{{ currentTime }} / {{ duration }}
				</view>
			</view>
		</view>
		<view class="content">
			<view class="wrap">
				<template v-for="(a, b) in imgList">
					<image :src="a" v-if="b <= 5" class="box"></image>
					<image :src="a" v-if="b > 5" class="square"></image>
				</template>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: 'audio-component',
		data() {
			return {
				imgList: [],
				currentAudioIndex: 0,
				currentTime: "00:00",
				duration: "00:00",
				isFirstPlay: true,
				audioList: [
					"/static/xn.mp3",
					"/static/fcddh.mp3",
					"/static/dz.mp3",
					"/static/h.mp3",
					"/static/gyc.mp3",
					"/static/ls.mp3",
					"/static/melody.mp3",
					"/static/qfl.mp3",
					"/static/rwhxrwy.mp3",
					"/static/snsyzb.mp3",
					"/static/tkzc.mp3",
					"/static/wr.mp3",
					"/static/wp.mp3",
					"/static/yfzm.mp3",
					"/static/yq.mp3",
					"/static/zwddzp.mp3",
					"/static/ydtg1.mp3",
					"/static/ydtg2.mp3",
				],
				innerAudioContext: null,
				timer: null
			};
		},
		onLoad() {
			this.isFirstPlay = true;
			this.innerAudioContext = uni.createInnerAudioContext();
			this.innerAudioContext.onCanplay(() => {
				this.innerAudioContext.duration;
				setTimeout(() => {
					this.duration = this.formatSeconds(this.innerAudioContext.duration);
				}, 300);
			});
			this.innerAudioContext.onPlay(() => {
				this.timer = setInterval(() => {
					this.currentTime = this.formatSeconds(this.innerAudioContext.currentTime);
				}, 1000);
			});
		},
		onUnload() {
			clearInterval(this.timer);
			this.innerAudioContext.destroy();
		},
		methods: {
			doPlay() {
				this.doPause();
				this.innerAudioContext.src = this.audioList[this.currentAudioIndex];
				this.innerAudioContext.play();
			},
			doPause() {
				this.innerAudioContext.stop();
				clearInterval(this.timer);
			},
			getPhoto() {
				uni.chooseImage({
					count: 6,
					sizeType: ["original", "compressed"],
					sourceType: ["album"],
					success: (res) => {
						for (var i = 0; i < res.tempFilePaths.length; i++) {
							this.imgList.push(res.tempFilePaths[i]);
						}
					},
				});
			},
			playNextAudio() {
				this.innerAudioContext.stop();
				this.currentAudioIndex =
					(this.currentAudioIndex + 1) % this.audioList.length;
				this.innerAudioContext.src = this.audioList[this.currentAudioIndex];
				this.innerAudioContext.play();
			},
			formatSeconds(value) {
				let minute = parseInt(value / 60);
				let second = parseInt(value % 60);
				if (minute < 10) {
					minute = "0" + minute;
				}
				if (second < 10) {
					second = "0" + second;
				}
				return minute + ":" + second;
			}
		},
	};
</script>

<style lang="scss" scoped>
	.main {
		width: 100vw;
		height: 100vh;
		background-color: #00ffff;
	}

	.btn-list {
		display: flex;
		justify-content: center;
	}

	.content {
		width: 100vw;
		height: 90vh;
		display: flex;
		justify-content: center;
		align-items: center;
		background: linear-gradient(#00ffff 0%, #ffaaff 80%);
		overflow: hidden;
	}

	.wrap {
		height: 200px;
		width: 200px;
		margin: 250px auto;
		position: relative;
		perspective: 2000px;

		transform-style: preserve-3d;
		transform: rotateX(20deg) rotateY(30deg);
		transform-origin: 50% 50% 0;
		animation: move 6s linear infinite;
	}

	.wrap .box {
		position: absolute;
		width: 200px;
		height: 200px;
		opacity: 0.8;
		transition: 2s;
	}

	.wrap>image:nth-child(1) {
		transform: rotateY(0deg) translateZ(100px);
	}

	.wrap>image:nth-child(2) {
		transform: translateZ(-100px) rotateY(180deg);
	}

	.wrap>image:nth-child(3) {
		transform: rotateY(90deg) translateZ(100px);
	}

	.wrap>image:nth-child(4) {
		transform: rotateY(-90deg) translateZ(100px);
	}

	.wrap>image:nth-child(5) {
		transform: rotateX(90deg) translateZ(100px);
	}

	.wrap>image:nth-child(6) {
		transform: rotateX(-90deg) translateZ(100px);
	}

	.wrap .square {
		display: bloack;
		width: 100px;
		height: 100px;
		position: absolute;
		left: 50px;
		top: 50px;
	}

	.wrap>image:nth-child(7) {
		transform: rotateY(0deg) translateZ(50px);
	}

	.wrap>image:nth-child(8) {
		transform: translateZ(-50px) rotateY(180deg);
	}

	.wrap>image:nth-child(9) {
		transform: rotateY(90deg) translateZ(50px);
	}

	.wrap>image:nth-child(10) {
		transform: rotateY(-90deg) translateZ(50px);
	}

	.wrap>image:nth-child(11) {
		transform: rotateX(90deg) translateZ(50px);
	}

	.wrap>image:nth-child(12) {
		transform: rotateX(-90deg) translateZ(50px);
	}

	@-webkit-keyframes move {
		0% {
			transform: rotateX(0deg) rotateY(0deg);
		}

		100% {
			transform: rotateX(360deg) rotateY(360deg);
		}
	}

	.wrap:hover {
		cursor: pointer;
	}

	.wrap:hover>image:nth-child(1) {
		transform: rotateY(0deg) translateZ(200px);
	}

	.wrap:hover>image:nth-child(2) {
		transform: translateZ(-200px) rotateY(180deg);
	}

	.wrap:hover>image:nth-child(3) {
		transform: rotateY(90deg) translateZ(200px);
	}

	.wrap:hover>image:nth-child(4) {
		transform: rotateY(-90deg) translateZ(200px);
	}

	.wrap:hover>image:nth-child(5) {
		transform: rotateX(90deg) translateZ(200px);
	}

	.wrap:hover>image:nth-child(6) {
		transform: rotateX(-90deg) translateZ(200px);
	}
</style>