<template>
	<view class="body">
		 <view class="header">
			 <view class="logo">
				 <image :src="logo"></image>
			 </view>
		 </view>
		 <view class="content">
			 <u-form :model="form"  :border-bottom="false" :error-type="errorType">
			 	<u-form-item label="用户名" label-align="right" label-width="120" prop="username">
			 		<u-input v-model="form.username" :border="border"></u-input>
			 	</u-form-item>
			 	<u-form-item label="密码" label-align="right" label-width="120" prop="password">
			 		<u-input v-model="form.password" type="password" :border="border" :passwordIcon="passwordIcon"></u-input>
			 	</u-form-item>
			 </u-form>
			 <view class="submit">
				 <u-button type="primary" size="default" shape="square" class="login-button" @click="login" :loading="loading" :disabled="disable">登录</u-button>
				 <navigator url="/pages/register/register" open-type="navigate" class="customer-register">没有账号,去注册!</navigator>
			 </view>
		 </view>
		 <view class="footer">
			 <u-link class='iconfont iconbeian customer-pos' :under-line="true" href="https://beian.miit.gov.cn/#/Integrated/index">湘ICP备20005842号-1</u-link>
		 </view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				logo: '/static/study.jpg',
				form: {
					username: '',
					password: ''
				},
				errorType: [
					'message', 'border','toast'
				],
				border: true,
				passwordIcon: true,
				loading: false,
				disable: false,
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.body {
		height: calc(100vh - 44px);
		background-color: $u-type-primary-light;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		
		.header {
			height: 50%;
			width: 90%;
			.logo {
				display: flex;
				flex-direction: row;
				justify-content: center;
				align-items: center;
				width: 100%;
				height: 100%;
				image {
					height: 30vh;
					width: 400rpx;
					border-radius: 50%;
				}
			}
			
		}
		.content {
			height: 40%;
			width: 80%;
			.submit {
				width: 100%;
				display: flex;
				flex-direction: column;
				justify-content: flex-start;
				align-items: flex-end;
				.login-button {
					width: 80%;
					margin-left: 20%;
				}
				.customer-register {
					color: $u-type-warning;
				}
			}
		}
		
		.footer {
			height: 9%;
			display: flex;
			flex-direction: column;
			justify-content: flex-end;
			align-items: center;
		}
	}
</style>
