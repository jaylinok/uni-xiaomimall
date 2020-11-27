<template>
	<view class="card">
		<!-- 标题 -->
		<view class="p-2 border-bottom main-border-color">
			<slot name="title"><text v-if="headTitle" class="font-md font-weight">{{headTitle}}</text></slot>

		</view>
		<view>
			<image v-if="bodyCover" :src="bodyCover" lazy-load mode="widthFix"></image>
			<slot />
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			headTitle: String,
			bodyCover: String,
			showHead: {
				type: Boolean,
				default: true
			}
		},
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style>

</style>
