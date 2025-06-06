<template>
	<view class="container">
		<view class="grid">
			<view class="item" v-for="(item, index) in emotionList" :key="index">
				<image :src="item.image" class="emotion" @click="selectEmotion(item.text)" mode="aspectFill"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				emotionList: [{
						text: '魔鬼',
						image: '/static/mg.png'
					},
					{
						text: '怒',
						image: '/static/n.png'
					},
					{
						text: '生气',
						image: '/static/sq.png'
					},
					{
						text: '惊呆',
						image: '/static/jd.png'
					},
					{
						text: '亲',
						image: '/static/q.png'
					},
					{
						text: '呆',
						image: '/static/d.png'
					},
					{
						text: '吃惊',
						image: '/static/cj.png'
					},
					{
						text: '鄙视',
						image: '/static/bs1.png'
					},
					{
						text: '尴尬',
						image: '/static/gg.png'
					},
					{
						text: '悲伤',
						image: '/static/bs.png'
					},
					{
						text: '乏力',
						image: '/static/fl.png'
					},
					{
						text: '流汗',
						image: '/static/lh.png'
					},
					{
						text: '卖萌',
						image: '/static/mm1.png'
					},
					{
						text: '难受',
						image: '/static/ns.png'
					},
					{
						text: '耍酷',
						image: '/static/sk.png'
					},
					{
						text: '喜爱',
						image: '/static/xa.png'
					},
					{
						text: '笑嘻',
						image: '/static/xx1.png'
					},
					{
						text: '晕',
						image: '/static/y.png'
					},
					{
						text: '眨眼',
						image: '/static/zy.png'
					},
				]
			};
		},
		methods: {
			selectEmotion(text) {
				uni.showToast({
					title: text,
					icon: 'none'
				});
			}
		}
	};
</script>

<style>
	.container {
		padding: 20rpx;
	}

	.grid {
		display: flex;
		flex-wrap: wrap;
		justify-content: flex-start;
	}

	.item {
		width: 33.33%;
		padding: 10rpx;
		box-sizing: border-box;
		text-align: center;
	}

	.emotion {
		width: 128rpx;
		height: 128rpx;
	}
</style>