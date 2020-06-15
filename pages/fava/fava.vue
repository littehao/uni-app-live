<template>
	<view>
		<uni-swipe-action v-for="(item,index) in list" :key="index">
			<uni-swipe-action-item :options="options" @click="bindClick($event,item)">
				<media-item :item="item"></media-item>
			</uni-swipe-action-item>
		</uni-swipe-action>
	</view>
</template>

<script>
	import mediaItem from "@/components/common/media-item.vue"
	import uniSwipeAction from '@/components/uni-ui/uni-swipe-action/uni-swipe-action.vue';
	import uniSwipeActionItem from '@/components/uni-ui/uni-swipe-action-item/uni-swipe-action-item.vue';
	export default {
		components:{
			mediaItem,
			uniSwipeAction,
			uniSwipeActionItem
		},
		data() {
			return {
				options:[
					{
						text: '取消收藏',
						style: {
							backgroundColor: 'rgb(255,58,49)'
						}
					}
				],
				list:[
					{
						id:"1",
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
					{
						id:"2",
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
					{
						id:"3",
						cover:'/static/demo/list2/1.jpg',
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷",
						create_time:"今天06:22",
						day_count:"232",
						danmu_count:"23232"
					},
				]
			}
		},
		methods: {
			bindClick(e,item){
				uni.showToast({
					title: `点击了${e.content.text}按钮`,
					icon: 'none'
				})
				console.log(item.id)
			}
		}
	}
</script>

<style>

</style>
