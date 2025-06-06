<template>
	<view>
		<view class="login">
			<view class="title">DAVReID车辆重识别</view>
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
			<button class="login-btn" type="default" @click="doLogin()">登 录</button>
			<view class="register-text" @click="goToRegister()">还没有账号？注册</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
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
					uni.reLaunch({
						url: '/pages/home/home',
					})
				} else {
					uni.showToast({
						icon: 'none',
						title: '账号或密码错误!',
					})
				}
			},
			goToRegister() {
				// 导航到注册页面
				uni.navigateTo({
					url: '/pages/register/register' // 确保你的路由配置正确
				})
			},
			onReady() {}
		}
	}
</script>

<style scoped lang="scss">
	.login {
		background-image: url('/static/background.jpg');
		/* 替换 'background.jpg' 为您的背景图文件名 */
		background-size: cover;
		/* 使背景图充满整个容器 */
		background-position: center;
		/* 将背景图居中 */
		height: 100vh;

		.title {
			padding: 47upx;
			text-indent: 55upx;
			font-size: 64upx;
			font-weight: 600;
			color: #ffffff;
			/* 调整文字颜色为蓝色 */
			text-align: center;
			/* 居中显示 */
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
					color: #ffffff;
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
			background: #22aaff;
			border-radius: 52px;
			color: #e5e5e5;
			/* 修改文字颜色为白色 */
			font-size: 46upx;
			/* 修改文字大小 */
			font-weight: 500;
			/* 加粗文字 */
			text-align: center;
			/* 居中显示文本 */
			line-height: 104upx;
			box-shadow: 0upx 0upx 20upx rgba(204, 0, 0, 0.2);
		}

		.register-text {
			text-align: center;
			color: #ffffff;
			font-size: 30upx;
			margin-top: 20upx;
			cursor: pointer;
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