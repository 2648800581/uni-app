<template>
	<view class="profile">
		<view class="avatar-container">
			<u-avatar :src="userInfo.avatar" shape="square" size="100"></u-avatar>
			<text class="nickname">{{ userInfo.nickname }}</text>
		</view>
		<view class="info-container">
			<view class="info-line">
				<text class="label">微信号：</text>
				<text class="value">{{ userInfo.wechatId }}</text>
			</view>
			<view class="info-line">
				<text class="label">地区：</text>
				<text class="value">{{ userInfo.location }}</text>
			</view>
			<view class="info-line">
				<text class="label">个性签名：</text>
				<text class="value">{{ userInfo.signature }}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				userInfo: {
					avatar: require('static/ocm.jpg'),
					nickname: 'To Overcome All',
					wechatId: 'toa123456',
					location: '中国',
					signature: '且行且珍惜'
				}
			}
		}
	}
</script>

<style lang="scss">
	.profile {
		display: flex;
		align-items: center;
		flex-direction: column;
		padding: 20px;
		height: 100vh;
		width: 100%;
		box-sizing: border-box;
		background: linear-gradient(#00ffff 0%, #ffaaff 80%);
	}

	.avatar-container {
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.nickname {
		font-size: 24px;
		font-weight: bold;
		color: #55557f;
		margin-top: 10px;
	}

	.info-container {
		margin-top: 20px;
		text-align: left;
		flex-grow: 1;
		display: flex;
		flex-direction: column;
		justify-content: space-evenly;
	}

	.info-line {
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		margin-bottom: 10px;
	}

	.label {
		font-size: 16px;
		color: #000000;
		margin-right: 10px;
	}

	.value {
		font-size: 16px;
		color: #000000;
	}
</style>