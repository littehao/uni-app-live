<template>
	<view>
		<!-- #ifdef MP -->
		<!--导航栏-->
		<view class="flex align-center fixed-top" style="height: 44px;">
			<view class="flex align-center flex-1 rounded-circle py-1 px-1 mx-2" style="background-color: #f6f7f8;color:#959fa0;">
				<text class="iconfont iconsousuokuang"></text>
				<text>精彩热搜：浩浩编程</text>
			</view>
		</view>
		<view style="height: 44px;"></view>
		<!-- #endif -->
		
		<card title="热门分类" :showRefresh="false">
			<scroll-view scroll-x="true" class="scroll-row">
				<icon-card v-for="(item,index) in list" :key="index" :item="item"></icon-card>
			</scroll-view>
		</card>
		<view class="f-divider"></view>
		<card title="全部分类" :showRefresh="false">
			<icon-card v-for="(item,index) in list" :key="index" :item="item"></icon-card>
		</card>
	</view>
</template>

<script>
	import card from "@/components/common/card.vue"
	import iconCard from "@/components/common/icon-card.vue"
	export default {
		components:{
			card,
			iconCard
		},
		data() {
			return {
				list:[]
			}
		},
		onLoad(){
			for(let i=0;i<10;i++){
				this.list.push({
					name:'分类',
					cover:"/static/demo/cate/1%20(1).png"
				})
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
