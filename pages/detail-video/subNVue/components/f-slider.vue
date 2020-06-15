<template>
	<view style="height: 44px;" class="flex align-center position-relative" @touchstart="touchstart" @touchmove="touchmove" @touchend="touchend" @touchcancel="touchcancel">
		<view class="flex-1 rounded" style="height: 3px;background-color: rgba(255,255,255,0.5);">
			<view class="bg-main" style="height: 3px;" :style="activeStyle"></view>
		</view>
		<view class="position-absolute rounded-circle bg-main-hover" style="width: 15px;height: 15px;" :style="activeDotStyle"></view>
	</view>
</template>

<script>
	export default {
		inject:['v'],
		props: {
			currentTime: {
				type: Number,
				default: 0
			},
			duration:{
				type: Number,
				default: 0
			}
		},
		data() {
			return {
				activeWidth:0,
				width:0,
				moveStatus:false
			}
		},
		created() {
			this.width = this.v.windowWidth - 44 - 44 - 80 - 15
			this.active()
		},
		computed: {
			activeStyle() {
				return `width:${this.activeWidth}px;`
			},
			activeDotStyle(){
				return `left:${this.activeWidth}px;`
			},
			current(){
				return this.width == 0 ? 0 : (this.activeWidth/this.width)*this.duration
			}
		},
		watch: {
			currentTime(newValue, oldValue) {
				if(!this.moveStatus){
					this.active()
				}
			}
		},
		methods: {
			active() {
				this.activeWidth = this.duration == 0 ? 0 : (this.currentTime/this.duration) * this.width
			},
			touchstart(e){
				if(this.duration === 0) return
				this.moveStatus = true
				this.activeWidth = e.changedTouches[0].screenX - 44
			},
			touchmove(e){
				if(this.duration === 0) return
				let d = e.changedTouches[0].screenX - 44
				if(d <= 0){
					this.activeWidth = 0
				} else if(d >= this.width){
					this.activeWidth = this.width
				} else {
					this.activeWidth = d
				}
				this.$emit('update',this.current)
			},
			touchend(e){
				if(this.duration === 0) return
				this.moveStatus = false
				this.$emit('change',this.current)
			},
			touchcancel(e){
				this.touchend(e)
			}
		},
	}
</script>

<style>
</style>
