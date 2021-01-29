<template>
	<view class="baseInfos">
		<view class="content">
			<view class="width-100 " v-for="(item, index) in personalArr" :key="index">
				<view class="item-text-wrap">
					<view class="py-4 font-size-16">{{item.text}}</view>
					<view>{{item.desc}}</view>
				</view>
			</view>
		</view>

		<view class="btnLayout">
			<van-icon name="failure" size="24" color="#000" @click="deleteFile" />
			<van-icon name="exchange" size="24" color="#000" />
			<van-icon name="scan" size="24" color="#000" @click="scanner" />
		</view>
	</view>
</template>

<script>
	export default {
		name: "scan",
		/* 声明书 */
		components: {},
		data() {
			return {
				signType: "statement",
				personalArr: [{
					text: "1",
					desc: '介绍描述...',
				}, ],
			}
		},
		methods: {
			scanner() {
				wx.scanCode({
					success: (res) => {
						this.personalArr.push({
							text: this.personalArr.length + 1,
							desc: res.result,
						})
					}
				})
			},
			deleteFile() {
				this.personalArr = [];
			},
			agree(v) {

			}
		}
	}
</script>

<style lang="scss" scoped>
	@import '../../static/myCss/myCss.css';

	.content {
		width: 100vw;
		height: 100%;
		overflow-y: auto;
		// padding: 12rpx 30rpx;
		color: #999999;
	}

	.btnLayout {
		position: fixed;
		width: 100%;
		height: 96rpx;
		bottom: 0;
		z-index: 10;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		background-color: #FFFFFF;
	}

	.item-text-wrap {
		display: flex;
		flex-direction: column;
		flex: 1;
		justify-content: center;
		font-size: 24rpx;
		color: #3C3C46;
		padding: 12rpx 48rpx;
		border-bottom: 1rpx solid #F8F8F8;
		background-color: #FFFFFF;
	}
</style>
