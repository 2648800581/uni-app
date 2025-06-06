<template>
	<view>
		<view class="u-demo-block">
			<text class="u-demo-block__title" style="text-align: center;">有机小浅</text>
			<view class="u-demo-block__content" style="text-align: center;">
				<u-avatar :src="src1"></u-avatar>
			</view>
		</view>
		<view>
			<u-cell-group>
				<u-cell icon="facebook-circle-fill" title="服务" @click="goView(2)" isLink></u-cell>
				<u-cell icon="qzone-circle-fill" title="收藏" @click="goView(5)" isLink></u-cell>
				<u-cell icon="moments-circel-fill" title="朋友圈" @click="goView(1)" isLink></u-cell>
				<u-cell icon="shopping-cart-fill" title="商品" @click="goView(4)" isLink></u-cell>
				<u-cell icon="heart-fill" title="表情" @click="goView(6)" isLink></u-cell>
			</u-cell-group>
		</view>
		<view class="cell-view">
			<u-cell-group>
				<u-cell icon="setting-fill" title="切换账号" @click="goView(3)" isLink></u-cell>
			</u-cell-group>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src1: require('../../static/yjxq.jpg'),
			}
		},
		methods: {
			goView(arr) {
				switch (arr) {
					case 1:
						uni.navigateTo({
							url: '/pages/index/index'
						})
						break
					case 2:
						uni.navigateTo({
							url: '/pages/serve/serve'
						})
						break
					case 3:
						uni.navigateTo({
							url: '/pages/login/login'
						})
						break
					case 4:
						uni.navigateTo({
							url: '/pages/product/product'
						})
						break
					case 5:
						uni.navigateTo({
							url: '/pages/collect/collect'
						})
						break
					case 6:
						uni.navigateTo({
							url: '/pages/emote/emote'
						})
						break
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.u-demo-block {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 16vh;
	}

	.cell-view {
		margin-top: 30upx;
		background: #ffffff;
	}
</style>