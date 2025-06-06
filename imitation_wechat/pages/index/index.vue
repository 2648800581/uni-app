<template>
	<view class="u-page">
		<view class="u-demo-block">
			<view class="u-demo-block__content">
				<view class="album">
					<view class="album__avatar">
						<image src="/static/yjxq.jpg" mode="" style="width: 36px; height: 36px;"></image>
					</view>
					<view class="album__content">
						<u--text text="有机小浅" color="#47526d" bold size="15"></u--text>
						<u--text margin="0 0 8px 0" text="梵高的星空!!!"></u--text>
						<u-album :urls="urls1"></u-album>
					</view>
				</view>
			</view>
		</view>
		<view class="u-demo-block">
			<view class="u-demo-block__content">
				<view class="album">
					<view class="album__avatar">
						<image src="/static/xbgn.jpg" mode="" style="width: 36px; height: 36px;"></image>
					</view>
					<view class="album__content">
						<u--text text="小八姑娘" color="#47526d" bold size="15"></u--text>
						<u--text margin="0 0 8px 0" text="花开堪折直须折 莫待无花空折枝"></u--text>
						<u-album :urls="urls2"></u-album>
					</view>
				</view>
			</view>
		</view>
		<view class="u-demo-block">
			<view class="u-demo-block__content">
				<view class="album">
					<view class="album__avatar">
						<image src="/static/yjnw.jpg" mode="" style="width: 36px;height: 36px;"></image>
					</view>
					<view class="album__content">
						<u--text text="有机弄蛙" color="#47526d" bold size="15"></u--text>
						<view :style="{ marginBottom: '8px', width: albumWidth + 'px' }">
							<u--text text="花开花落自有时 人来人往任由之" :customStyle="{ width: albumWidth + 'px' }"></u--text>
						</view>
						<u-album :urls="urls3" @albumWidth="width => albumWidth = width" multipleSize="68"></u-album>
					</view>
				</view>
			</view>
		</view>
		<view class="u-demo-block">
			<view class="u-demo-block__content">
				<view class="album">
					<view class="album__avatar">
						<image src="/static/qtdz.jpg" mode="" style="width: 36px;height: 36px;"></image>
					</view>
					<view class="album__content">
						<u--text text="蜻蜓队长" color="#47526d" bold size="15"></u--text>
						<u--text margin="0 0 8px 0" text="君子知命不惧, 日日自新!"></u--text>
						<u-album :urls="urls4" rowCount="2" maxCount="4" multipleMode="scaleToFill"></u-album>
					</view>
				</view>
			</view>
		</view>
		<view class="u-demo-block">
			<view class="u-demo-block__content">
				<view class="album">
					<view class="album__avatar">
						<image src="/static/xx.jpg" mode="" style="width: 36px;height: 36px;"></image>
					</view>
					<view class="album__content">
						<u--text text="醒醒" color="#47526d" bold size="15"></u--text>
						<u--text margin="0 0 8px 0" text="无暇明眸凝秋水 有志丈夫立人魁"></u--text>
						<u-album :urls="urls5" rowCount="2" maxCount="4" multipleSize="50"></u-album>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
import { Static } from "vue"
	export default {
		data() {
			return {
				albumWidth: 0,
				urls1: [
					require('../../static/01.jpg'),
				],
				urls2: [
					require('../../static/02.jpg'),
					require('../../static/03.jpg'),
					require('../../static/04.jpg'),
				],
				urls3: [
					require('../../static/05.jpg'),
					require('../../static/06.jpg'),
					require('../../static/07.jpg'),
				],
				urls4: [
					require('../../static/08.jpg'),
					require('../../static/09.jpg'),
				],
				urls5: [
					require('../../static/10.jpg'),
					require('../../static/11.jpg'),
				]
			}
		}
	}
</script>

<style lang="scss">
	.album {
		@include flex;
		align-items: flex-start;

		&__avatar {
			background-color: $u-bg-color;
			padding: 5px;
			border-radius: 3px;
		}

		&__content {
			margin-left: 10px;
			flex: 1;
		}
	}
</style>