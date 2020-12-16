<template>
	<view class="content">
		<view class="first">
			1
		</view>
		<view class="second">
			2
		</view>
		<view class="third">
			3
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
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
			align-items: flex-end;
			background-color: $u-type-primary-light;
			height: calc(100vh - 44px);
		}
		
		.first {
			border: $u-type-primary-disabled solid 1rpx;
			height: 30%;
		}
		
		.second {
			border: $u-type-success solid 1rpx;
			height: 30%;
			
		}
		
		.third {
			border: $u-type-error solid 1rpx;
			height: 30%;
		}
</style>
