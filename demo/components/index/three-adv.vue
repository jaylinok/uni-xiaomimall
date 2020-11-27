<template>
	<view class="d-flex">
		<image :src="resData.big.src" mode="" lazy-load style="width: 373rpx;height: 530rpx;border-right: 2rpx solid #F5F5F5;"
		 @tap="event(resData.big)"></image>
		<view class="d-flex flex-column">
			<image :src="resData.smalltop.src" mode="" lazy-load style="width: 375rpx;height: 264rpx; border-bottom: 2rpx solid #F5F5F5;"
			 @tap="event(resData.smalltop)"></image>
			<image :src="resData.smallbottom.src" mode="" lazy-load style="width: 375rpx;height: 265rpx;" @tap="event(resData.smallbottom)"></image>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			resData: Object
		},
		data() {
			return {

			}
		},
		methods: {
			event(item) {
				console.log("点击了adv图片", item)
			}

		}
	}
</script>

<style>

</style>
