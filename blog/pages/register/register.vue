<template>
	<view class="content">
		<view class="header">
			<image :src="logo"></image>
		</view>
		<view class="body">
			<u-form :model="form" ref="uForm" :border-bottom="false">
				<u-form-item label="用户名" prop="username" label-align="left" label-width="120">
					<u-input v-model="form.username" :border="true" placeholder="请输入登录用户名"></u-input>
				</u-form-item>
				<u-form-item label="密码" prop="password" label-align="left" label-width="120">
					<u-input v-model="form.password" type="password" :border="true" :passwordIcon="true" placeholder="请输入登录密码"></u-input>
				</u-form-item>
				<u-form-item label="昵称" prop="nickname" label-align="left" label-width="120">
					<u-input v-model="form.nickname" :border="true" placeholder="请输入昵称"></u-input>
				</u-form-item>
				<u-form-item label="性别" prop="sex" label-align="left" label-width="120">
					<u-input v-model="form.sex" style="display: none;"></u-input>
					<u-input v-model="sex" type="select" :border="true" @click="show = true" placeholder="请选择性别" />
					<u-action-sheet :list="sex_list" v-model="show" @click="actionSheetCallback"></u-action-sheet>
				</u-form-item>
				<u-form-item label="岗位" prop="job" label-align="left" label-width="120">
					<u-radio-group v-model="form.job" @change="radioGroupChange">
						<u-radio
							@change="radioChange"
							v-for="(item, index) in job_list"
							:name="item.id"
							:disabled="item.disable"
							label-size="20"
							active-color="green"
						>{{item.name}}</u-radio>
					</u-radio-group>
				</u-form-item>
				<u-form-item label="图像" prop="avatar" label-align="left" label-width="120">
					<u-upload></u-upload>
				</u-form-item>
			</u-form>
			<view class="register">
				 <u-button type="primary" size="default" shape="circle" class="login-button" @click="register" :loading="loading" :disabled="disable">登录</u-button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				logo: '/static/study_1.jpg',
				form: {
					username: '',
					password: '',
					sex: '',
					job: '',
					nickname: ''
				},
				loading: false,
				disable: false,
				sex: '',
				show: false,
				sex_list: [
					{
						id: 1,
						text: '男'
					},
					{
						id: 2,
						text: '女'
					},
					{
						id: 3,
						text: '保密'
					}
				],
				job_list: [
					{
						id: 1,
						name: 'PHPer',
						disable: false
					},
					{
						id: 2,
						name: 'Javaer',
						disable: false
					},
					{
						id: 3,
						name: 'Golanger',
						disable: false
					},
				]
			}
		},
		methods: {
			actionSheetCallback(index) {
				this.sex = this.sex_list[index].text;
				this.form.sex = this.sex_list[index].id;
			},
			
			radioGroupChange(e) {
				console.log(e)
			},
			
			radioChange(e) {
				console.log(e)
			},
			register() {
				console.log('注册')
			}
		},
		onReady() {
			this.$refs.uForm.setRules();
		}
	}
</script>

<style lang="scss">
		.content {
			display: flex;
			flex-direction: column; //主轴方向
			justify-content: space-between;
			align-items: center;
			background-color: $u-type-primary-light;
			height: calc(100vh - 44px);
			width: 750rpx;
		}
		
		.header {
			height: 30%;
			width: 100%;
			image {
				width: 100%;
				height: 100%;
			}
		}
		
		.body {
			margin-top: 5%;
			width: 80%;
			//flex: auto;
			height: 65%;
			overflow: scroll;
		}
		
</style>
