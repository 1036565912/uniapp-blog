<template>
	<view class="login">
		<view class="content">
			<view class='logo'>
				<image :src="logo_img" mode="scaleToFill"></image>
			</view>
			<view class="form">
				<u-form :model="form">
					<u-form-item label="用户名" label-align="right" label-width="100rpx">
						<u-input v-model="form.username" :border="border"></u-input>
					</u-form-item>
					<u-form-item label="密码" label-align="right" label-width="100rpx">
						<u-input v-model="form.password" type="password" :border="border" :passwordIcon="passwordIcon"></u-input>
					</u-form-item>
				</u-form>
				<u-button type="info" size="medium" shape="square" class="custom-style">登录</u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				logo_img: '../../static/study.jpg',
				border: true,
				passwordIcon: true,
				form: {
					username: '',
					password: ''
				}
			};
		}
	}
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		justify-content: center;
		background-color: $u-type-primary-light;
	}
	
	.logo {
		border-radius: 50%;
		margin-top: 100px;  
		margin-left: auto;
		margin-right: auto;
		height: 150px;
	}
	
	.logo image {
		width: 150px;
		height: 150px;
		border-radius: 50%;
	}
	.form {
		width: 90%;
		margin-top: 92rpx;
		margin-left: auto;
		margin-right: auto;
	}
	
	
	.form .custom-style {
		color: $uni-color-primary;
		width: 200rpx;
		margin-left: 475rpx;
	}
</style>
