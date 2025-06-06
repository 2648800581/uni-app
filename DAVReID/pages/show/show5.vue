<template>
	<div class="container">
		<div class="content">
			<!-- 文字标题 -->
			<div class="header">
				<span v-for="(rank, index) in ranks" :key="index" class="rank">{{ rank }}</span>
			</div>

			<!-- 图片显示区域 -->
			<div class="image-container">
				<img v-for="(image, index) in images" :key="index" :src="image.src"
					:style="{ 'animation-delay': index * 1 + 's', 'opacity': image.displayed ? 1 : 0 }"
					:class="{ 'image': true, 'green-border': index > 0 && index < images.length - 1, 'red-border': index === images.length - 1 && image.displayed }" />
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				ranks: ['目标图像', 'Rank-1', 'Rank-2', 'Rank-3', 'Rank-4', 'Rank-5'],
				images: [{
						src: '/static/Ve_05_q.png', // 更改为目标查询图像的路径
						displayed: true // 直接显示，无需等待
					},
					{
						src: '/static/vehicle/v-5-1.png',
						displayed: false
					},
					{
						src: '/static/vehicle/v-5-2.png',
						displayed: false
					},
					{
						src: '/static/vehicle/v-5-3.png',
						displayed: false
					},
					{
						src: '/static/vehicle/v-5-4.png',
						displayed: false
					},
					{
						src: '/static/vehicle/v-5-5.png',
						displayed: false
					}
				]
			};
		},
		mounted() {
			// 等待 1 秒后显示第一张图像（除了目标查询图像）
			setTimeout(() => {
				this.showNextImage(1); // 从第二张开始，跳过目标查询图像
			}, 1000);
		},
		methods: {
			showNextImage(index) {
				if (index < this.images.length) {
					this.$set(this.images, index, {
						...this.images[index],
						displayed: true
					});
					setTimeout(() => {
						this.showNextImage(index + 1); // 显示下一张
					}, 1000); // 每张之间的间隔
				}
			}
		}
	};
</script>

<style scoped>
	.red-border {
		border: 3px solid red;
	}
	.green-border {
		border: 3px solid green;
	}

	.container {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100vh;
		/* 让容器占据整个视窗高度 */
		background-image: url('/static/background.jpg');
		/* Add background image */
		background-size: cover;
		/* Cover the entire container with the background image */
		background-position: center;
	}

	.content {
		text-align: center;
		/* 将内容居中显示 */
	}

	.header {
		display: flex;
		align-items: center;
		justify-content: center;
		margin-bottom: 20px;
		/* 增加文字之间的垂直间隔 */
	}

	.rank {
		margin: 0 104px;
		/* 增加文字之间的水平间隔 */
		font-weight: bold;
		color: #f1f1f1;
	}

	.target-image {
		max-width: 200px;
		max-height: 200px;
	}

	.image-container {
		display: flex;
		justify-content: space-between;
		/* 图片之间的间隔 */
		margin-bottom: 28px;
		/* 增加图片和文字之间的垂直间隔 */
	}

	.image {
		margin: 0 30px;
		/* 增加图片之间的水平间隔 */
		max-width: 200px;
		max-height: 200px;
		animation: fadeIn 0.5s ease;
	}

	@keyframes fadeIn {
		from {
			opacity: 0;
		}

		to {
			opacity: 1;
		}
	}
</style>