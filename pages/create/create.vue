<template>
	<view>
		<view class="bg-light position-relative" style="height: 350rpx;" hover-class="bg-hover-light" @tap="upload">
			<image v-if="form.cover" :src="form.cover" mode="aspectFill" style="width: 750rpx;height: 350rpx;"></image>
			<view class="flex flex-column align-center justify-center position-absolute left-0 right-0 top-0 bottom-0" style="background-color: rgba(255,255,255,0.2);">
				<text v-if="!form.cover" class="iconfont iconjia"></text>
				<text class="font text-muted">{{form.cover?'切换添加封面':'点击添加封面'}}</text>
			</view>
		</view>
		
		<form-item label="标题">
			<input type="text" v-model="form.title" placeholder="请填写视频标题" placeholder-class="text-light-muted" value="" class="w-100 pr-5"/>
		</form-item>
		<picker mode="selector" :range="range" @change="change">
			<form-item label="分类" iconshow>
				<input type="text" v-model="form.category" placeholder="请填选择分类" disabled placeholder-class="text-light-muted" value="" class="w-100 pr-5"/>
			</form-item>
		</picker>
		<form-item label="描述">
			<textarea value="" v-model="form.desc" placeholder="请填写视频描述"  style="width: 550rpx;" class="py-3"/>
		</form-item>
		
		<!-- #ifdef MP -->
			<view class="py-2 px-3">
				<main-big-button @tap="submit">发布</main-big-button>
			</view>
		<!-- #endif -->
		
	</view>
</template>

<script>
	import formItem from "@/components/common/form-item.vue"
	import mainBigButton from "@/components/common/mian-big-button.vue"
	export default {
		components:{
			formItem,
			mainBigButton
		},
		data() {
			return {
				form:{
					cover:"",
					title:"",
					category:"",
					desc:""
				},
				range:["分类1","分类2","分类3"]
			}
		},
		onNavigationBarButtonTap(e){
			console.log('发布')
		},
		methods: {
			upload(){
				uni.chooseImage({
				    count: 1, //默认9
				    sizeType: ['compressed'], //可以指定是原图还是压缩图，默认二者都有
				    success: function (res) {
						this.form.cover = res.tempFilePaths[0]
				    }
				});
			},
			change(e){
				this.form.category  = this.range[e.detail.value]
			},
			submit(){
				
			}
		}
	}
</script>

<style>

</style>
