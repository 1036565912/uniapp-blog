<template>
	<view class="login">
		<view class="content">
			<view class='logo'>
				<image :src="logo_img" mode="scaleToFill"></image>
			</view>
			<view class="form">
				<u-form :model="form" ref="uform" :border-bottom="false" :error-type="errorType">
					<u-form-item label="用户名" label-align="right" label-width="100" prop="username">
						<u-input v-model="form.username" :border="border"></u-input>
					</u-form-item>
					<u-form-item label="密码" label-align="right" label-width="100" prop="password">
						<u-input v-model="form.password" type="password" :border="border" :passwordIcon="passwordIcon"></u-input>
					</u-form-item>
				</u-form>
				<u-button type="info" size="medium" shape="square" class="custom-style" @click="login" :loading="loading" :disabled="disable">登录</u-button>
				<navigator url="/pages/register/register" open-type="navigate" class="customer-register">没有账号,去注册!</navigator>
			</view>
			<view class="footer">
				<u-link class='iconfont iconbeian customer-pos' :under-line="true" href="https://beian.miit.gov.cn/#/Integrated/index">湘ICP备20005842号-1</u-link>
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
				loading: false,
				disable: false,
				errorType: [
					'message', 'border','toast'
				],
				form: {
					username: '',
					password: ''
				},
				rules: {
					username: [
						{
							required: true,
							message:  '请输入用户名',
							trigger: ['change', 'blur']
						}
					],
					password: [
						{
							//require: true,
							min: 5,
							message: '密码不能少于5个字符',
							trigger: ['blur', 'change']
						},
						{
							required: true,
							message: '请输入密码',
							trigger: ['change','blur']
						}
					]
				}
			};
		},
		methods: {
			login() {
				this.$refs.uform.validate(valid => {
					console.log(valid);
					if (!valid) {
						return ;
					}
					
					this.loading = true;
					this.disable = true;
					console.log(this.form);
					console.log('正在登录');
				});
				
			}
		},
		onReady() {
			this.$refs.uform.setRules(this.rules);
		}
	}
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		justify-content: center;
		background-color: $u-type-primary-light;
		height: 100%;
	}
	
	.logo {
		border-radius: 50%;
		margin-top: 15vh;  
		margin-left: auto;
		margin-right: auto;
		height: 22.4vh;
	}
	
	.logo image {
		width: 300rpx;
		height: 22.4vh;
		border-radius: 50%;
	}
	.form {
		width: 90%;
		margin-top: 10vh;
		margin-left: auto;
		margin-right: auto;
	}
	
	
	.form .custom-style {
		color: $uni-color-primary;
		width: 570rpx;
		margin-left: 100rpx;
		height: 5.5vh;
		line-height: 5.5vh;
	}
	.footer {
		height: 16.7vh;
		margin-top: 5vh;
		position: relative;
	}
	.footer .customer-pos {
		position: absolute;
		bottom: 0px;
		left: 210rpx;
	}
	.customer-register {
		margin-left: 450rpx;
		color: $uni-color-warning;
	}
</style>
