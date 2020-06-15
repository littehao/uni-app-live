<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	/* #ifndef APP-NVUE */
	/*引入官方样式库*/
	@import url("/common/style/uni.css");
	/*引入animate库*/
	@import url("/common/style/animate.css");
	/* #endif */
	/*引入free样式库*/
	@import url("/common/style/free.css");
	/*引入全局样式库*/
	@import url("/common/style/common.css");
	/* #ifndef APP-NVUE */
	/*引入自定义图标库*/
	@import url("/common/style/iconfont.css");
	/* #endif */
	
</style>
