<template>
	<view class="position-fixed right-0 left-0 bottom-0 top-0 animated faster fadeIn" style="background-color: rgba(0,0,0,0.5);z-index: 1000;" @click.stop="hide"
	v-if="status">
		<slot></slot>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				status:false
			}
		},
		methods:{
			hide(){
				this.status = false
			},
			show(){
				this.status = true
			}
		}
	}
</script>

<style>
</style>
