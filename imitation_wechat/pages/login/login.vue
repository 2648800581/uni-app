<template>
	<view>
		<view class="u-demo-block">
			<text class="u-demo-block__title" style="text-align: center;">有机小浅</text>
			<view class="u-demo-block__content" style="text-align: center;">
				<u-avatar :src="src1"></u-avatar>
			</view>
		</view>
		<view class="login">
			<view class="input-content">
				<view class="input-box">
					<image class="input-bg" :src="require('static/zh.png')" mode="scaleToFill"></image>
					<input class="input-phone" type="text" v-model="phone" placeholder="登录账号" />
				</view>
				<view class="input-box">
					<image class="input-bg" :src="require('static/mm.png')" mode="scaleToFill"></image>
					<input class="input-phone" type="text" v-model="password" placeholder="登录密码" v-if="!inputType" />
					<input class="input-phone" type="password" v-model="password" placeholder="登录密码" v-if="inputType" />
					<image class="input-type" :src="inputType ? require('static/eye2.png') : require('static/eye1.png')"
						mode="widthFix" @click="changePw()">
					</image>
				</view>
			</view>
			<button class="login-btn" type="default" @click="doLogin()">登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src1: require('../../static/yjxq.jpg'),
				inputType: true, //显示密码
				phone: '',
				password: ''
			}
		},
		methods: {
			//隐藏显示密码
			changePw() {
				let pw = this.password
				this.inputType = !this.inputType
				this.$nextTick(() => {
					this.password = pw
				})
			},
			//账号密码登录
			doLogin() {
				this.form
				let name = 'admin'
				let pass = '12345'
				if (this.phone.length == 0 || this.password.length == 0) { //校验非空
					wx.showToast({ //弹框提示
						icon: 'none',
						title: '登录账号或密码不能为空!',
						duration: 2000,
					})
				} else if (this.phone === name && this.password === pass) { //勾选协议
					uni.switchTab({
						url: '/pages/home/home',
					})
				} else {
					uni.showToast({
						icon: 'none',
						title: '账号或密码错误!',
					})
				}
			},
			onReady() {}
		}
	}
</script>

<style scoped lang="scss">
	.u-demo-block {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		height: 16vh;
	}

	.login {
		.bg-content {
			width: 100%;
			height: 450upx;
			position: relative;
			overflow: hidden;

			.bg {
				// width: 100%;
				width: 30upx;
				height: auto;
				position: absolute;
				bottom: 0;
				left: 50%;
				transform: translateX(-50%);
			}
		}

		.title {
			padding: 47upx;
			text-indent: 55upx;
			font-size: 48upx;
			font-weight: 400;
			color: #333333;
		}

		.input-content {
			padding: 0 23upx;

			.input-box {
				position: relative;
				margin: 0 auto;
				padding: 0 50upx;
				height: 120upx;

				.input-bg {
					position: absolute;
					left: 0;
					right: 0;
					top: 32upx;
					bottom: 0;
					width: 40upx;
					height: 40upx;
				}

				.input-phone {
					width: 100%;
					height: 100upx;
				}

				.input-type {
					z-index: 2;
					position: absolute;
					right: 50upx;
					top: 30upx;
					width: 40upx;
					height: auto;
				}
			}
		}

		.login-btn {
			margin-top: 86upx;
			width: 92%;
			height: 104upx;
			background: #19b061;
			border-radius: 52px;
			color: #000000;
			box-shadow: 0upx 0upx 20upx rgba(204, 0, 0, 0.2);
		}

		.checkbox {
			width: 92%;
			margin: 20upx auto;
			font-size: 28upx;

			.user {
				color: #0096FF;
			}
		}
	}
</style>