<template>
	<view class="content">
		<view class="header">
			<image :src="logo"></image>
		</view>
		<view class="body">
			<u-form :model="form" ref="uForm">
				<u-form-item>
					
				</u-form-item>
			</u-form>
		</view>
		<view class="footer">
			3
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				logo: '/static/study_1.jpg',
				form: {
					
				}
			}
		},
		methods: {
			
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
			height: 40%;
			width: 100%;
			image {
				width: 100%;
				height: 100%;
			}
		}
		
		.body {
			border: $u-type-success solid 1rpx;
			height: 50%;
			width: 80%;
		}
		
		.footer {
			border: $u-type-error solid 1rpx;
			flex: auto;
			//height: 10%;
			width: 100%;
		}
</style>
