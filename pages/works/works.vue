<template>
	<view>
		<view class="flex flex-column" v-for="(item,index) in list" :key="index">
			<media-item :item="item"></media-item>
			<view class="flex" style="height: 100rpx;">
				<view class="flex-1 flex align-center justify-center" hover-class="bg-light">修改</view>
				<view class="flex-1 flex align-center justify-center" hover-class="bg-light" @click="navigateTo('video-list')">视频</view>
				<view class="flex-1 flex align-center justify-center" hover-class="bg-light">删除</view>
			</view>
			<view class="f-divider"></view>
		</view>
	</view>
</template>

<script>
	import mediaItem from "@/components/common/media-item.vue"
	export default {
		components:{
			mediaItem
		},
		data() {
			return {
				list:[
					{
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
					{
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
					{
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
					{
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
					{
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
					{
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					}
				]
			}
		},
		methods: {
			navigateTo(url){
				uni.navigateTo({
					url:"/pages/"+url+"/"+url
				})
			}
		}
	}
</script>

<style>

</style>
