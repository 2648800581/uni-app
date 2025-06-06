<template>
	<view class="product-list">
		<view class="product" v-for="(item,index) in list " :key="product">
			<view class="image-view">
				<image class="product-image" v-bind:src="item.mgUrl"></image>
			</view>
			<view class="product-title">
				{{item.title}}
			</view>
			<view class="product-price">
				<text class="favour">￥{{item.price}}</text>
				<text class="original">￥{{item.original}}</text>
				<text class="tip">{{item.tip}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{
						mgUrl: "../../static/xie.png",
						title: 'Nike Air Zoom G.T.Jump 2 EP',
						price: '1400',
						original: '1299',
						tip: '京东'
					},
					{
						mgUrl: "../../static/xie2.png",
						title: 'Nike Air Zoom G.T.Jump EP YI JIANLIAN',
						price: '1400',
						original: '1199',
						tip: '京东'

					},
					{
						mgUrl: "../../static/xie3.png",
						title: 'Nike Air Zoom G.T.Cut 2 EP',
						price: '1399',
						original: '1199',
						tip: '京东'

					},
					{
						mgUrl: "../../static/xie4.png",
						title: 'Nike Air Zoom G.T.Jump EP',
						price: '1499',
						original: '899',
						tip: '京东'
					}
				]
			}
		},
		onLoad() {
			const eventChannel = this.getOpenerEventChannel();
			eventChannel.on('setPageData', (data) => {
				console.log(data)
				if (data.data === 1) {
					this.setlist()
				} else {
					this.setlistZ()
				}
			})
		},
		methods: {
			setlist() {
				for (var i = 0; i < 5; i++) {
					this.list.push({
						mgUrl: "../../static/logo.png",
						title: '商品',
						price: '9999',
						original: '8888',
						tip: '京东'
					})
				}
			},
			setlistZ() {
				this.list = [{
					mgUrl: "../../static/logo.png",
					title: '商品',
					price: '9999',
					original: '8888',
					tip: '京东'
				}]
			}
		}

	}
</script>

<style lang="scss">
	.product-list {
		display: flex;
		width: 100vm;
		flex-wrap: wrap;
		flex-direction: row;
	}

	.product {
		padding: 20upx;
		display: flex;
		flex-direction: column;
	}

	.image-view {
		height: 330upx;
		width: 330upx;
		margin: 12px 0;
	}

	.product-image {
		height: 330upx;
		width: 330upx;
	}

	.product-title {
		width: 330upx;
		word-break: break-all;
		display: -webkit-box;
		overflow: hidden;
		line-height: 1.5;
		text-overflow: ellipsis;
		-webkit-box-orient: vertical;
		-webkit-line-clamp: 2;
	}

	.product-price {
		margin-top: 10upx;

		font-size: 28upx;
		line-height: 1.5;
		position: relative;
	}

	.original {
		color: #e80080;
	}

	.favour {
		color: #888888;
		text-decoration: line-through;
		margin-left: 10upx;
	}

	.tip {
		position: absolute;
		right: 10upx;
		background-color: #ff3333;
		color: #ffffff;
		padding: 0 10upx;
		border-radius: 5upx;
	}
</style>