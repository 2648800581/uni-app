<template>
	<div class="outer-container">
		<div class="background">
			<!-- Content Container -->
			<div class="content-container">
				<div class="query">
					<div class="title">车辆查询集图像库</div>
					<div class="image-container">
						<img class="car-image" v-for="(image, index) in carImageList" :key="index" :src="image"
							mode="aspectFill" />
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				carImageList: this.shuffle(Array.from({
					length: 99
				}, (_, i) => `/static/vehicle/v-${String(i + 1).padStart(2, '0')}.png`))
			};
		},
		methods: {
			shuffle(array) {
				// Fisher-Yates shuffle algorithm
				for (let i = array.length - 1; i > 0; i--) {
					const j = Math.floor(Math.random() * (i + 1));
					[array[i], array[j]] = [array[j], array[i]];
				}
				return array;
			}
		}
	};
</script>

<style scoped lang="scss">
	.outer-container {
		position: relative;
		/* Ensure relative positioning for its children */
	}

	.background {
		background-color: #d5d5d5;
		/* 设置背景色 */
		width: 100vw;
		/* 使用视口宽度作为全宽度 */
		height: 100vh;
		/* 使用视口高度作为全高度 */
		position: absolute;
		/* 确保背景相对于 .outer-container 固定 */
		top: 0;
		left: 0;
		/* 从左上角定位 */
		background-image: url('/static/background.jpg');
		/* 添加背景图片 */
		background-size: cover;
		/* 将背景图片覆盖整个容器 */
		background-position: center;
		/* 设置背景图片位置 */
	}

	.content-container {
		position: fixed;
		/* Ensure content container remains fixed */
		width: 100%;
		height: 100%;
		overflow-y: auto;
		/* Enable vertical scrolling */
	}

	.query {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.title {
		margin-top: 50upx;
		font-size: 44upx;
		font-weight: bold;
		color: #ffffff;
	}

	.image-container {
		display: grid;
		grid-template-columns: repeat(5, minmax(200px, 1fr));
		/* 每行显示6张图片，留有适当空隙 */
		gap: 30px;
		margin-top: 30upx;
	}

	.car-image {
		width: 500upx;
		height: 500upx;
		/* Ensure image takes up full height of its container */
		object-fit: cover;
		/* Scale image to be as small as possible while ensuring its aspect ratio is preserved */
	}
</style>