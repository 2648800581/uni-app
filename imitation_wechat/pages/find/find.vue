<template>
	<view>
		<view>
			<u-cell-group>
				<u-cell icon="moments" title="朋友圈" @click="goView(1)" isLink></u-cell>
				<u-cell icon="scan" title="扫一扫" @click="goView(2)" isLink></u-cell>
				<u-cell icon="chrome-circle-fill" title="摇一摇" @click="goView(3)" isLink></u-cell>
				<u-cell icon="integral-fill" title="搜一搜" @click="goView(4)" isLink></u-cell>
				<u-cell icon="play-circle-fill" title="音乐厅" @click="goView(5)" isLink></u-cell>
			</u-cell-group>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
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
							url: '/pages/scan/scan'
						})
						break
					case 3:
						uni.navigateTo({
							url: '/pages/shake/shake'
						})
						break
					case 4:
						uni.navigateTo({
							url: '/pages/search/search'
						})
						break
					case 5:
						uni.navigateTo({
							url: '/pages/heart/heart'
						})
						break
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
</style>