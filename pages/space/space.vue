<template>
	<view>
		<image src="/static/demo/list2/3.jpg" mode="aspectFill"
		style="width: 750rpx;height: 320rpx;"></image>
		<view style="height: 350rpx;" class="border-bottom">
			<view class="flex align-center justify-between px-3">
				<image src="../../static/demo/6.jpg"
				style="width: 130rpx;height: 130rpx;margin-top: -60rpx;"
				class="rounded-circle"></image>
				<view class="flex align-center justify-center rounded bg-main text-white py-1 px-2" hover-class="bg-main-hover">
					<text class="font">关注</text>
				</view>
			</view>
			<view class="px-4 flex align-center py-1">
				<view class="font-lg text-main font-weight-bold">昵称</view>
				<text class="font text-light-muted ml-2">UID:123456</text>
			</view>
			<view class="flex align-center px-4">
				<view class="rounded font-sm bg-main text-white px-1">
					年度大会员
				</view>
			</view>
			<view class="flex align-center px-4 mt-2">
				<view class="font-md text-dark flex align-center">
					21 <text class="ml-2 font-sm text-light-muted">关注</text>
				</view>
				<view class="font-md text-dark flex align-center ml-2">
					21 <text class="ml-2 font-sm text-light-muted">粉丝</text>
				</view>
			</view>
			<view class="px-4 mt-2">
				<view class="text-ellipsis font-sm text-light-muted" style="line-height: 1.5;">年度大会员年度大会员年度大会员年度大会员年度大会员年度大会员年度大会员年度大会员</view>
			</view>
		</view>
		
		<view class="flex align-center" style="height: 44px;">
			<view class="flex-1 flex align-center justify-center"
			v-for="(item,index) in tabBars" :key="index"
			@click="changeTab(index)">
				<text class="font-md font" :class="tabIndex === index ? 'text-main':'' ">{{item.name}}</text>
			</view>
		</view>
		
		<swiper :current="tabIndex" :duration="300" :style="'height:'+scrollHeight+'px;'" @change="changeSwiper">
			<swiper-item v-for="(tab,tabI) in tabBars" :key="tabI">
				<scroll-view scroll-y="true" :style="'height:'+scrollHeight+'px;'">
					<view class="f-divider"></view>
					<media-item v-for="(item,index) in list" :key="index" :item="item" :index="index"></media-item>
				</scroll-view>
			</swiper-item>
		</swiper>
		
			
		
		
	</view>
</template>

<script>
	import mediaItem from '@/components/common/media-item.vue';
	export default {
		components: {
			mediaItem
		},
		data() {
			return {
				tabIndex:0,
				tabBars:[{
					name:"主页"
				},{
					name:"动态"
				},{
					name:"作品"
				},{
					name:"收藏"
				}],
				scrollHeight:0,
				
				list:[{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app第三季实战仿微信教程上线了",
					create_time:"今天06:00",
					play_count:0,
					danmu_count:0
				},{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app第三季实战仿微信教程上线了",
					create_time:"今天06:00",
					play_count:0,
					danmu_count:0
				},{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app第三季实战仿微信教程上线了",
					create_time:"今天06:00",
					play_count:0,
					danmu_count:0
				},{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app第三季实战仿微信教程上线了",
					create_time:"今天06:00",
					play_count:0,
					danmu_count:0
				},{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app第三季实战仿微信教程上线了",
					create_time:"今天06:00",
					play_count:0,
					danmu_count:0
				},{
					cover:"/static/demo/list2/1.jpg",
					title:"Uni-app第三季实战仿微信教程上线了",
					create_time:"今天06:00",
					play_count:0,
					danmu_count:0
				}]
			}
		},
		created() {
			let res = uni.getSystemInfoSync()
			this.scrollHeight = res.windowHeight - 44 - 44 - res.statusBarHeight
		},
		methods: {
			changeSwiper(e){
				this.tabIndex = e.detail.current
			},
			changeTab(index){
				this.tabIndex = index
			}
		}
	}
</script>

<style>

</style>
