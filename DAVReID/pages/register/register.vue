<template>
	<div class="registration-form">
		<input v-model="username" type="text" placeholder="用户名" class="input-field">
		<input v-model="password" type="password" placeholder="密码" class="input-field">
		<button class="submit-button">注册</button>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				username: '',
				password: ''
			};
		}
	};
</script>

<style scoped>
	.registration-form {
		background-image: url('/static/background.jpg');
		/* 替换 'background.jpg' 为您的背景图文件名 */
		background-size: cover;
		/* 使背景图充满整个容器 */
		background-position: center;
		/* 将背景图居中 */
		height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.input-field {
		margin: 10px;
		padding: 10px;
		border: 1px solid #ccc;
		border-radius: 5px;
		/* 白色背景 */
		color: #ffffff;
		/* 白色文字 */
	}

	.submit-button {
		margin: 10px;
		padding: 10px 20px;
		border: none;
		border-radius: 5px;
		background-color: #007bff;
		/* 蓝色按钮 */
		color: #ffffff;
		/* 白色文字 */
		cursor: pointer;
	}

	.submit-button:hover {
		background-color: #0056b3;
		/* 鼠标悬停时的背景色 */
	}
</style>