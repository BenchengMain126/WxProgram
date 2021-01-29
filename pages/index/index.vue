<template>
	<scroll-view scroll-y="true">
		<view class="container">
			<van-tabs type="line" border=false sticky style="width: 95%;box-sizing: border-box;">
				<van-tab title="功能展示" style="width: 50%;box-sizing: border-box;">
					<view class="itemLy-outter">
						<view class="itemLy" v-for="(item, index) in personalArr" :key="index" @click="handleclick(item)">
							<view class="item-img-wrap">
								<van-icon name="fire-o" color="#ee0a24" size="42"/>
							</view>
							<view class="item-text-wrap">
								<text class="py-4 font-size-16">{{item.text}}</text>
								<text class="py-4" style="min-height: 42rpx;">{{item.desc}}</text>
							</view>
						</view>
					</view>
				</van-tab>
				<van-tab title="组件展示" style="width: 50%;box-sizing: border-box;">
					<view class="itemLy-outter">
						<view class="itemLy" v-for="(item, index) in groupArr" :key="index" @click="handleclick(item)">
							<view class="item-img-wrap">
								<van-icon name="fire-o" color="#ee0a24" size="42"/>
							</view>
							<view class="item-text-wrap">
								<text class="py-4 font-size-16">{{item.text}}</text>
								<text class="py-4" style="min-height: 42rpx;">{{item.desc}}</text>
							</view>
						</view>
					</view>
				</van-tab>
			</van-tabs>
		</view>
	</scroll-view>
</template>

<script>
	export default {
		data() {
			return {
				personalArr: [
					{
						text: "签到定位",
						desc: '介绍描述...',
						type: 'xcp',
						url: "../sign/signup",
					},
					{
						text: "扫码录入",
						desc: '介绍描述...',
						type: 'xcp',
						url: "../scan/scan",
					},
					/* {
						img: require("../../../../static/index/onlineIcon3.png"),
						text: "证件有效期更新",
						desc: '身份证有效期在线更新。',
						type: 'xcp',
						sencondtype: 'valid',
						url: "",
					},
				
					{
						img: require("../../../../static/index/onlineIcon1.png"),
						text: "借记卡开卡预填单",
						desc: '借记卡开卡预填单，远程预填对接网点超级柜台领取实物卡片。',
						url: "subPackages/debitCard/debitCard",
						type: "xcx",
						appid: 'wxcfa496c3eca687e7'
					},
					{
						img: require("../../../../static/index/onlineIcon2.png"),
						text: "社保卡开卡预填单",
						desc: '社保卡开卡预填单，远程预填对接网点超级柜台领取实物卡片。',
						url: "https://merch.szx.abchina.com/qmall/index?token=nbe1496912830836#preformCommon?type=1",
						type: "h5"
					},
				
 */
				],

				groupArr: [	{
						text: "签名板",
						desc: '介绍描述...',
						type: 'xcp',
						url: "../sign/signatures",
					}
				]
			}
		},
	
		methods: {

			handleclick(params) {
				let that = this
				if (params.type === 'dev') {
					uni.showToast({
						title: '敬请期待',
						icon: "none",
						duration: 2000
					});
					return null;
				} else if (params.type === 'xcp') {
					wx.navigateTo({
						url: params.url,
					})
					return null;

				} else if (params.type === 'xcx') {
					// 跳转小程序
					uni.navigateToMiniProgram({
						appId: params.appid,
						path: params.url,
						extraData: {},
						success(res) {
							// 打开成功
						}
					})
					return null;

				} else if (params.type === 'h5') {
					//H5链接
					let url = params.url;
					if (!url) {
						uni.showToast({
							title: '敬请期待！',
							icon: 'none',
							duration: 2000
						});
						return null;
					}
					console.log('查看线上营业厅跳转链接：   ', url);
				/* 	url = encodeURIComponent(url);
					// 跳转H5
					uni.navigateTo({
						url: '../../../../pages/webView/index?url=' + url,
						animationType: 'pop-in',
						animationDuration: 200,
						fail: (err) => {
							console.log('跳转失败:  ', err);
						}
					}) */
					return null;
				}

			},

		

		},


	}
</script>

<style scoped lang="scss">
	@import '../../static/myCss/myCss.css';


	.itemLy-outter {
		width: 100%;
		display: flex;
		flex-direction: column;
		box-sizing: border-box;
		justify-content: center;
		align-items: center;
		margin: 10rpx 0;
	}

	.itemLy {
		width: 100%;
		display: flex;
		flex-direction: row;
		box-sizing: border-box;
		background-color: white;
		align-items: center;
		border-radius: 15rpx;
		margin: 10rpx 0;
		background-color: white;
	}

	.item-image {
		width: 60rpx;
		height: 50rpx;
		margin: 0 auto;
	}

	.item-img-wrap {
		display: flex;
		flex: 1;
		justify-content: center;
		margin: 20rpx 0;
	}

	.item-text-wrap {
		display: flex;
		flex-direction: column;
		flex: 4;
		justify-content: center;
		padding: 0 12rpx 0 0;
		font-size: 24rpx;
		color: #3C3C46;
		margin: 18rpx 0;
	}

	.flag {
		width: 95%;
		margin-top: 32rpx;
		margin-bottom: 12rpx;
	}

	.item_flag {
		width: 100%;
		height: 260rpx;
		border-radius: 15rpx;
		box-sizing: border-box;
		padding: 0 22rpx;
		position: relative;
	}

	.item1 {
		background-color: #C8EBEC;
		margin-bottom: 21rpx;

		.kongzhong {
			width: 260rpx;
			height: 260rpx;
			position: absolute;
			right: 0;
			bottom: 0;
		}
	}

	.c-com-c-title {
		font-family: 'Source Han Sans CN';
		font-size: 48rpx;
		line-height: 48rpx;
		color: #3C3C46;
		margin-bottom: 8rpx;
		display: block;
		box-sizing: border-box;
		padding: 64rpx 0 0 32rpx;
	}

	.c-com-c-title-desc {
		font-family: 'Source Han Sans CN';
		font-size: 32rpx;
		line-height: 48rpx;
		padding: 32rpx 0 0 96rpx;
		color: #3C3C46;
		margin-bottom: 8rpx;
		display: block;
		box-sizing: border-box;
	}
</style>
