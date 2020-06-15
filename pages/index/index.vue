<template>
	<view>
		<!-- #ifdef MP -->
		<!--导航栏-->
		<view class="flex align-center fixed-top" style="height: 44px;">
			<view class="flex align-center flex-1 rounded-circle py-1 px-1 ml-2" style="background-color: #f6f7f8;color:#959fa0;">
				<text class="iconfont iconsousuokuang"></text>
				<text>精彩热搜：浩浩编程</text>
			</view>
			<view class="flex align-center px-2" style="color:#959fa0;">分类</view>
		</view>
		<view style="height: 44px;"></view>
		<!-- #endif -->
		
		<!--轮播图-->
		<view class="px-3 py-2">
			<swiper-dot :info="swipers" :current="current">
				<swiper :current="current" circular :autoplay="true" :interval="3000" :duration="150" style="height: 250rpx;"  @change="changeSwiper">
					<swiper-item v-for="(item,index) in swipers" :key="index">
						<view class="swiper-item">
							<image :src="item.src" mode="aspectFill" style="height: 250rpx;width: 100%;" class="rounded-lg"></image>
						</view>
					</swiper-item>
				</swiper>
			</swiper-dot>
		</view>
		
		<view class="f-divider"></view>
		<card title="为你推荐">
			<view class="f-list">
				<view  v-for="i in 6" :key="i" style="margin-left: 15rpx;margin-right: 15rpx;width: 328rpx;position: relative;" class="rounded-lg border mb-2" @click="videoto">
					<image src="/static/demo/list2/1.jpg" style="width: 100%;height: 220rpx;" class="rounded-top-lg"></image>
					<view style="height: 65rpx;background-image: linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,0.8));position: absolute;left:0;right:0;top:155rpx;" class="text-white flex align-center">
						<text class="iconfont iconbofangshu font-md mx-1"></text>
						<text class="font-sm">203.6万</text>
						<text class="iconfont icondanmushu font-md mx-1"></text>
						<text class="font-sm">6910</text>
					</view>
					<view class="px-1 pb-1">
						<view class="font">标题</view>
						<view class="flex align-center justify-between text-light-muted">
							<text class="font">恶搞</text>
							<text class="iconfont icongengduo"></text>
						</view>
					</view>
				</view>
			</view>
		</card>
		<view class="f-divider"></view>
		<card title="为你推荐">
			<view class="f-list">
				<view v-for="i in 6" :key="i" style="margin-left: 15rpx;margin-right: 15rpx;width: 210rpx;position: relative;" class="rounded-lg mb-2">
					<image src="/static/demo/list3/1.jpg" style="width: 100%;height: 280rpx;" class="rounded-lg"></image>
					<view style="height: 65rpx;background-image: linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,0.8));position: absolute;left:0;right:0;top:215rpx;" class="text-white flex align-center rounded-bottom-lg">
						<text class="iconfont iconbofangshu font-md mx-1"></text>
						<text class="font-sm">203.6万</text>
					</view>
					<view class="font">标题</view>
				</view>
			</view>
		</card>
		<view class="f-divider"></view>
		<card title="为你推荐">
			<view class="f-list">
				<media-item v-for="(item,index) in list" :key="index" :item="item"></media-item>
			</view>
		</card>
	</view>
</template>

<script>
	import swiperDot from "@/components/common/swiper-dot.vue"
	import card from "@/components/common/card.vue"
	import mediaItem from "@/components/common/media-item.vue"
	export default {
		components:{
			swiperDot,
			card,
			mediaItem
		},
		data() {
			return {
				current:0,
				swipers: [
					{
						src:"/static/demo/swiper/1.jpg",
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷 "
					},
					{
						src:"/static/demo/swiper/2.jpg",
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷 "
					},
					{
						src:"/static/demo/swiper/3.jpg",
						title:"近几年来，前端面试的难度上了一个档次，我们前端工程师要刷 "
					}
				],
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
					}
				]
			}
		},
		onLoad() {

		},
		onNavigationBarSearchInputClicked() {
			console.log("点击了搜索框")
		},
		onNavigationBarButtonTap(e){
			console.log("点击了分类按钮"+e)
		},
		methods: {
			changeSwiper(e){
				this.current = e.detail.current
			},
			videoto(){
				uni.navigateTo({
					url:"/pages/detail-video/detail-video"
				})
			}
		}
	}
</script>

<style>
	.f-list{
		display: flex;
		flex-wrap: wrap;
		padding-left: 15rpx;
		padding-right: 15rpx;
	}
</style>
