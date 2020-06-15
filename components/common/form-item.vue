<template>
	<view class="flex border-bottom border-light-secondary" style="min-height:100rpx;">
		<view class="font-md flex align-center justify-center" style="width: 120rpx;height: 100rpx;">{{label}}</view>
		<view class="flex-1 flex align-center">
			<slot></slot>
		</view>
		<view  v-if="iconshow" class="flex align-center justify-center" style="height: 100rpx;width: 80rpx;">
			<text class="iconfont iconjinru text-muted"></text>
		</view>
	</view>
</template>


<script>
	export default {
		props:{
			label:{
				type:String,
				default:"标题"
			},
			iconshow:{
				type:Boolean,
				default:false
			}
		}
	}
</script>

<style>
</style>
