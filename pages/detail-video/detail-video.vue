<template>
	<view style="line-height: 1;overflow-y: hidden;">
		<!-- #ifndef APP-PLUS -->
		<video :src="detail.src" :poster="detail.poster" style="height: 225px;width: 750rpx;" controls></video>
		<!-- #endif -->
		<scroll-view scroll-y="true" :style="'height:'+scrollH+'px;'">
			<view class="border-bottom border-light-secondary flex align-stretch bg-white" style="height: 80rpx;position: fixed;left: 0;right: 0;z-index: 100;">
				<view class="flex-1 flex align-center justify-center"
				v-for="(item,index) in tabBars" :key="index"
				@click="changeTab(index)">
					<text class="font py-1" 
					:class="tabIndex === index ? 'text-main border-main':''"
					:style="tabIndex === index ? 'border-bottom: 5rpx solid;' : ''">{{item.name}}</text>
				</view>
			</view>
			<view style="height: 80rpx;"></view>
			
			<!-- 简介 -->
			<view v-if="tabIndex === 0" class="animated fadeIn fast">
				<view class="py-2 px-3 flex align-center">
					<image src="/static/demo/6.jpg" style="width: 80rpx;height: 80rpx;" class="mr-3 rounded-circle"></image>
					<view class="flex flex-column">
						<text class="text-main font-md">昵称</text>
						<text class="font-sm text-muted" style="line-height: 1;">369 粉丝</text>
					</view>
					<view class="flex align-center justify-center rounded bg-main text-white py-1 px-2 ml-auto" hover-class="bg-main-hover">
						<text class="font">关注</text>
					</view>
				</view>
				<view class="font-md px-3">
					视频标题
				</view>
				<view class="flex align-center text-muted px-3">
					<text class="iconfont iconbofangshu font-md mr-1"></text>
					<text class="font-sm">203.6万</text>
					<text class="iconfont icondanmushu font-md mx-1"></text>
					<text class="font-sm">6910</text>
					<text class="font-sm ml-1">今日 10:00</text>
				</view>
				<!-- 滚动 -->
				<view class="py-3 border-top border-bottom border-light-secondary">
					<view class="flex align-center px-3">
						<text class="font-md">选集</text>
						<view class="flex align-center text-muted ml-auto"
						@click="openPopup">
							共9集 <text class="iconfont iconjinru ml-1"></text>
						</view>
					</view>
					<scroll-view scroll-x="true" class="scroll-row mt-2">
						<view v-for="i in 10" :key="i" class="scroll-row-item rounded border ml-2 p-2 " :class="i === 0 ? 'text-main border-main' : 'text-muted border-light-secondary'" style="width: 340rpx;">
							<text class="font">第 1 集</text>
							<view class="font-md text-ellipsis">最强发型师</view>
						</view>
					</scroll-view>
				</view>
				<view class="f-list">
					<media-list v-for="(item,index) in list" :key="index"
					:item="item" :index="index"></media-list>
				</view>
				
			</view>
			<!-- 评论 -->
			<view v-else class="animated fadeIn fast px-3 py-1">
				<view class="uni-comment-list">
					<view class="uni-comment-face">
						<image src="/static/demo/6.jpg" style="width: 80rpx;height: 80rpx;" class="rounded-circle"></image>
					</view>
					<view class="uni-comment-body">
						<view class="uni-comment-top">
							<text class="font text-main">昵称</text>
						</view>
						<view class="uni-comment-date">
							<text class="font-sm text-muted">10:10</text>
						</view>
						<view class="uni-comment-content">
							评论内容
						</view>
						<!-- 回复 -->
						<view class="flex flex-wrap p-2 bg-light rounded">
							<text class="font text-main">昵称2：</text>
							回复功能
						</view>
					</view>
				</view>
				
				<view class="position-fixed flex align-center justify-center bg-main rounded-circle animated fast" hover-class="bg-main-hover pulse" style="width: 120rpx;height: 120rpx;right: 50rpx;bottom: 50rpx;" @click="openComment">
					<text class="text-white iconfont iconjia"></text>
				</view>

			</view>
			
		</scroll-view>
		
		<f-popup ref="popup">
			<view class="position-absolute bottom-0 left-0 right-0 bg-white animated faster fadeIn" @click.stop="stop">
				<view style="height: 600rpx;">
					<view class="flex align-center">
						<text class="font-md ml-3">选集</text>
						<view class="flex align-center justify-center ml-auto" style="width: 80rpx;height: 80rpx;" hover-class="bg-light" @click="hidePopup">
							<text class="iconfont iconguanbi text-muted"></text>
						</view>
					</view>
					<scroll-view scroll-y="true" style="height: 520rpx;">
						<view class="flex flex-wrap">
							<view style="width: 50%;box-sizing: border-box;" v-for="i in 10" :key="i" class="p-2">
								<view class="rounded border p-2 " :class="i === 0 ? 'text-main border-main' : 'text-muted border-light-secondary'">
									<text class="font">第 1 集</text>
									<view class="font-md text-ellipsis">最强发型师</view>
								</view>
							</view>
						</view>
					</scroll-view>
				</view>
			</view>
		</f-popup>
		
		<f-popup ref="comment">
			<view class="position-absolute bottom-0 left-0 right-0 bg-white animated faster fadeIn" @click.stop="stop">
				<view style="height: 100rpx;" class="flex align-center px-3">
					<input type="text" value="" class="bg-light rounded mr-3 px-2 flex-1" style="height: 60rpx;" placeholder="说一句话吧"/>
					<view class="flex align-center justify-center rounded bg-main text-white py-1 px-2 ml-auto" hover-class="bg-main-hover">
						<text class="font">关注</text>
					</view>
				</view>
			</view>
		</f-popup>
		
	</view>
</template>

<script>
	import mediaList from '@/components/common/media-item.vue';
	import fPopup from '@/components/common/f-popup.vue';
	export default {
		components: {
			mediaList,
			fPopup
		},
		data() {
			return {
				tabIndex:0,
				tabBars:[{
					name:"简介"
				},{
					name:"评论"
				}],
				
				detail:{
					src:"https://douyinzcmcss.oss-cn-shenzhen.aliyuncs.com/%E8%AF%BE%E6%97%B61.%20%E9%A1%B9%E7%9B%AE%E4%BB%8B%E7%BB%8D.mp4",
					poster:"https://ss2.bdstatic.com/8_V1bjqh_Q23odCf/pacific/1696374343.jpg"
				},
				scrollH:500,
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
				}]
			}
		},
		onLoad() {
			let res = uni.getSystemInfoSync()
			this.scrollH = res.windowHeight - 226
		},
		methods: {
			stop(){ },
			// 切换选项卡
			changeTab(index){
				this.tabIndex = index
			},
			// 弹出选集
			openPopup(){
				this.$refs.popup.show()
			},
			hidePopup(){
				this.$refs.popup.hide()
			},
			openComment(){
				this.$refs.comment.show()
			}
		}
	}
</script>

<style>

</style>
