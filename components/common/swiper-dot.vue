<template>
	<view class="position-relative">
		<slot></slot>
		<view style="height: 70rpx;position: absolute;bottom: 0;left: 0;right: 0;background-image: linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,0.8));" class="flex align-center text-white rounded-lg px-1">
			<view style="width:80%;" class="text-ellipsis">
				{{info[current]['title']}}
			</view>
			<view style="width:20%;" class="flex align-center justify-end flex-shrink">
				<view  v-for="(item,index) in info" :key="index" style="width: 16rpx;height:16rpx;" :style="current == index?'background:rgba(255,255,255,1)':'background:rgba(255,255,255,0.5)'" class="rounded-circle ml-1"></view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		props:{
			info:Array,
			current:{
				type:Number,
				default:0
			}
		}
	}
</script>

<style>
</style>
