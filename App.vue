<template>
	<view id="app">
		<van-loading type="spinner" color="white" size="3rem" />
	</view>
</template>
<script>
	export default {
		onLaunch: function() {
			const that = this
			// 检查版本更新
			const updateManager = uni.getUpdateManager()
			updateManager.onCheckForUpdate(function(res) {
				// 请求完新版本信息的回调
				if (res.hasUpdate) {
					updateManager.onUpdateReady(function(res2) {
						uni.showModal({
							title: '更新提示',
							content: '发现新版本，是否重启应用?',
							cancelColor: '#eeeeee',
							confirmColor: '#FF0000',
							success(res2) {
								if (res2.confirm) {
									// 新的版本已经下载好，调用 applyUpdate 应用新版本并重启
									updateManager.applyUpdate()
									console.log('版本更新已完成')
								}
							}
						})
					})
				}
			})
			updateManager.onUpdateFailed(function(res) {
				// 新的版本下载失败
				uni.showModal({
					title: '提示',
					content: '检查到有新版本，但下载失败，请检查网络设置',
					success(res) {
						if (res.confirm) {
							// 新的版本已经下载好，调用 applyUpdate 应用新版本并重启
							updateManager.applyUpdate()
						}
					}
				})
			})
		},
		onError(err){
			console.log(err)
		},
	}
</script>

<style lang="scss">
	/*每个页面公共css */
	@import '/wxcomponents/vant/dist/common/index.wxss';

	page {
		width: 100%;
		height: 100%;
		background: #f4f4f5;
	}
	.boxShadow {
		box-shadow:1px 1px 7px 1px #ccc;
	}	
	
	.wrapper {
	  display: flex;
	  align-items: center;
	  justify-content: center;
	  height: 100%;
	}
	
	.block {
	  width: 120px;
	  height: 120px;
	  background-color: #fff;
	}
</style>
