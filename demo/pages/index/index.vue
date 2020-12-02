<template>
	<view>
		<!-- 轮播图 -->
		<swiper-image :resData="swipers"></swiper-image>
		<!-- 图标导航 -->
		<index-nav :resData="indexnavs"></index-nav>
		<divider />
		<!-- 三图广告 -->
		<three-adv :resData="threeAdvs"></three-adv>
		<divider />
		<!-- 卡片视图 -->
		<!-- 大图广告 -->
		<card headTitle="每日精选" bodyCover="/static/images/demo/cate_banner.png"></card>

		<!-- 公共列表组件750-5 =745  /2 372.5 -->
		<view class="row j-sb">
			<block v-for="(item,index) in commonList" :key="index">
				<common-list :item="item" :index="index"></common-list>
			</block>
		</view>
		<view class="row j-sb">
			<block v-for="(item,index) in commonList" :key="index">
				<common-list :item="item" :index="index"></common-list>
			</block>
		</view>
		<!-- 没有标题的卡片 -->
		<card :showHead="false">
			<image src="/static/images/demo/cate_banner.png" mode="widthFix"></image>
		</card>
	</view>
</template>

<script>
	import swiperImage from "@/components/index/swiper-image.vue"
	import indexNav from "@/components/index/index-nav.vue"
	import threeAdv from "@/components/index/three-adv.vue"
	import card from "@/components/common/card.vue"
	import commonList from "@/components/common/common-list.vue"
	export default {
		components: {
			swiperImage,
			indexNav,
			threeAdv,
			card,
			commonList
		},
		data() {
			return {
				swipers: [{
					src: "../../static/images/demo/demo1.jpg"
				}, {
					src: "../../static/images/demo/demo2.jpg"
				}, {
					src: "../../static/images/demo/demo3.jpg"
				}, {
					src: "../../static/images/demo/demo4.jpg"
				}],
				indexnavs: [{
						src: '/static/images/indexnav/1.png',
						text: '新品分类'
					},
					{
						src: '/static/images/indexnav/2.gif',
						text: '小米众筹'
					},
					{
						src: '/static/images/indexnav/3.gif',
						text: '以旧换新'
					},
					{
						src: '/static/images/indexnav/4.gif',
						text: '1分拼团'
					},
					{
						src: '/static/images/indexnav/5.gif',
						text: '超值特买'
					},
					{
						src: '/static/images/indexnav/6.gif',
						text: '小米秒杀'
					},
					{
						src: '/static/images/indexnav/7.gif',
						text: '真心想要'
					},
					{
						src: '/static/images/indexnav/8.gif',
						text: '电视热卖'
					},
					{
						src: '/static/images/indexnav/9.gif',
						text: '加店热卖'
					},
					{
						src: '/static/images/indexnav/10.gif',
						text: '米粉卡'
					}
				],
				threeAdvs: {
					big: {
						src: '/static/images/demo/demo1.jpg'
					},
					smalltop: {
						src: '/static/images/demo/demo2.jpg'
					},
					smallbottom: {
						src: '/static/images/demo/demo3.jpg'
					}
				},
				commonList: [{
					cover: "/static/images/demo/list/2.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					nprice: 1399
				}, {
					cover: "/static/images/demo/list/2.jpg",
					title: "米家空调",
					desc: "1.5匹变频",
					oprice: 2699,
					nprice: 1399
				}]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
