<template>
	<view>
		<scroll-view scroll-x class="border-bottom scroll-row" style="height: 80upx;" :scroll-into-view="scrollinto"
		 :scroll-with-animation="true">
			<view class="scroll-row-item px-3" style="height: 80upx;line-height: 80upx;" v-for="(item,index) in tabBars" :key="index"
			 :class="tabIndex===index?'main-text-color':''" @click="changeTab(index)" :id="'tab'+index">
				<text class="font-md">{{item.name}}</text>
			</view>
		</scroll-view>

		<swiper :current="tabIndex" :style="'height:'+scrollH+'px;'" :duration="150" @change="onChangeTab">
			<swiper-item v-for="(item ,index ) in newsitems" :key="index">
				<scroll-view scroll-y :style="'height:'+scrollH+'px;'" @scrolltolower="loadMore(index)">
					<block v-for="(list,listIndex) in item.list" :key="listIndex">


						<template v-if="list.type==='indexnavs'">
							<!-- 图标导航 -->
							<index-nav :resData="list.data" />
							<divider />
						</template>
						<template v-else-if="list.type==='threeAdv'">
							<!-- 三图广告 -->
							<three-adv :resData="list.data" />
							<divider />
						</template>
						<template v-else-if="list.type==='list'">

							<!-- 卡片视图 -->
							<!-- 大图广告 -->
							<card headTitle="每日精选" bodyCover="/static/images/demo/cate_banner.png"></card>

							<!-- 公共列表组件750-5 =745  /2 372.5 -->
							<view class="row j-sb">
								<block v-for="(item2,index2) in list.data" :key="index2">
									<common-list :item="item2" :index="index2"></common-list>
								</block>
							</view>

							<!-- 没有标题的卡片 -->
							<card :showHead="false">
								<image src="/static/images/demo/cate_banner.png" mode="widthFix"></image>
							</card>
						</template>
						<!-- 轮播图 -->
						<swiper-image v-else-if="list.type==='swipers'" :resData="list.data" />
					</block>
					<!-- 上拉加载更多 -->
					<divider />
					<view class="d-flex a-center j-center text-light-muted font-md py-3">{{item.loadText}}</view>
				</scroll-view>
			</swiper-item>

		</swiper>

	</view>
</template>

<script>
	let demoTabbars = [{
			name: '推荐'
		},
		{
			name: '家电'
		},
		{
			name: '智能'
		},
		{
			name: '摄影'
		},
		{
			name: '厨房'
		},
		{
			name: '家居'
		},
		{
			name: '生活'
		},
		{
			name: '饮料'
		},
		{
			name: '调料'
		},
		{
			name: '学习'
		},
		{
			name: '音乐'
		}
	];

	let demo1 = [{
		type: 'swipers',
		data: [{
			src: "../../static/images/demo/demo1.jpg"
		}, {
			src: "../../static/images/demo/demo2.jpg"
		}, {
			src: "../../static/images/demo/demo3.jpg"
		}, {
			src: "../../static/images/demo/demo4.jpg"
		}]
	}, {
		type: 'indexnavs',
		data: [{
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
		]
	}, {
		type: 'threeAdv',
		data: {
			big: {
				src: '/static/images/demo/demo1.jpg'
			},
			smalltop: {
				src: '/static/images/demo/demo2.jpg'
			},
			smallbottom: {
				src: '/static/images/demo/demo3.jpg'
			}
		}
	}, {
		type: 'list',
		data: [{
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
		}, {
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
		}, {
			cover: "/static/images/demo/list/2.jpg",
			title: "米家空调",
			desc: "1.5匹变频",
			oprice: 2699,
			nprice: 1399
		}]
	}];
	let demo2 = [{
		type: 'swipers',
		data: [{
			src: "../../static/images/demo/demo1.jpg"
		}, {
			src: "../../static/images/demo/demo2.jpg"
		}, {
			src: "../../static/images/demo/demo3.jpg"
		}, {
			src: "../../static/images/demo/demo4.jpg"
		}]
	}, {
		type: 'indexnavs',
		data: [{
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
		]
	}, {
		type: 'threeAdv',
		data: {
			big: {
				src: '/static/images/demo/demo1.jpg'
			},
			smalltop: {
				src: '/static/images/demo/demo2.jpg'
			},
			smallbottom: {
				src: '/static/images/demo/demo3.jpg'
			}
		}
	}, {
		type: 'list',
		data: [{
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
		}, {
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
		}, {
			cover: "/static/images/demo/list/2.jpg",
			title: "米家空调",
			desc: "1.5匹变频",
			oprice: 2699,
			nprice: 1399
		}]
	}];
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
				scrollinto: "",
				scrollH: 500,
				tabIndex: 0,
				tabBars: [],
				newsitems: []
			}
		},
		onLoad() {
			//获取可视区域高度
			uni.getSystemInfo({
				success: (res) => {
					// console.log("res: " + JSON.stringify(res));
					this.scrollH = res.windowHeight - uni.upx2px(82);
				}
			})
			//初始化事件
			this.__init()
		},
		methods: {
			__init() {
				this.tabBars = demoTabbars
				let arr = []
				for (var i = 0; i < this.tabBars.length; i++) {
					let obj = {
						list: [],
						//1上拉加载更多,2,3
						loadText: "上拉加载更多"
					}
					if (i === 0) {
						obj.list = demo1
					}
					arr.push(obj)
					this.newsitems = arr
				}
			},
			//切换选项卡
			changeTab(index) {
				if (this.tabIndex === index) {
					return;
				}
				this.tabIndex = index
				this.scrollinto = 'tab' + index
				this.addData()
			},
			//监听滑动
			onChangeTab(e) {
				this.changeTab(e.detail.current)
			},
			//家在数据
			addData() {
				let index = this.tabIndex
				this.newsitems[index].list = demo2
			},
			loadMore(index) {
				let item = this.newsitems[index]
				if (item.loadText !== '上拉加载更多') {
					return;
				}
				item.loadText = '加载中...'
				setTimeout(() => {
					item.list = [
						...item.list,
						...demo2
					];
					item.loadText = '上拉加载更多'
				}, 2000)
			}
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
