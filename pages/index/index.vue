<template>
	<view class="content">
		<scroll-view scroll-x="true" class="border-bottom scroll-row" style="height: 80rpx;"
			:scroll-into-view="scrollinto" scroll-with-animation="true">
			<view class="scroll-row-item px-3" @tap="changeTab(index)" style="height: 80rpx;line-height: 80rpx;"
				v-for="(item ,index) in tabbars" :key="index" :class="tabIndex===index?'main-text-color':''"
				:id="'tab'+index">
				<text class="font-md">{{item.name}}</text>
			</view>
		</scroll-view>

		<swiper @change="onChangeTab" duration="150" :current="tabIndex" :style="'height:'+scrollH+'px;'">
			<swiper-item v-for="(item,index) in newsItems" :key="index">
				<scroll-view scroll-y="true" style="height: 100%;">
					<block v-for="(listItem,listIndex) in item.list" :key="listIndex">
						<!-- 轮播图 -->
						<swiper-img v-if="listItem.type==='swiper'" :imgs="listItem.data" />
						<!-- 分类 -->
						<template v-else-if="listItem.type==='indexnavs'">
							<index-nav :datas="listItem.data" />
							<divider></divider>
						</template>

						<!-- 三图广告 -->
						<template v-else-if="listItem.type==='threeADV'">
							<three-adv :imgObj="listItem.data"></three-adv>
							<divider></divider>
						</template>

						<!-- 卡片组件 -->
						<!-- 	<card title="测试标题">
							<image src="../../static/images/bg.jpg" mode="widthFix"></image>
						</card> -->
						<!-- 大图广告 -->
						<card v-else-if="listItem.type==='largeAD'" :title="listItem.data.title"
							:cover="listItem.data.cover"></card>

						<!-- 商品列表组件 -->
						<view class="row j-sb " v-else-if="listItem.type==='goods'">
							<block v-for="(item2,index2) in listItem.data" :key="index2">
								<common-list :item="item2" :index="index2"></common-list>
							</block>
						</view>
					</block>
					<!-- 上拉加载更多 -->

				</scroll-view>
			</swiper-item>
		</swiper>



	</view>

</template>

<script>
	// 模拟后端数据
	let demotabBars = [{
			name: "关注",
			list: []
		},
		{
			name: "推荐",
			list: []
		},
		{
			name: "体育",
			list: []
		},
		{
			name: "热点",
			list: []
		},
		{
			name: "财经",
			list: []
		},
		{
			name: "娱乐",
			list: []
		},
		{
			name: "军事",
			list: []
		},
		{
			name: "历史",
			list: []
		},
		{
			name: "本地",
			list: []
		}
	];
	let demo1 = [{
			type: "swiper",
			data: [{
					src: "../../static/images/demo/demo1.jpg"
				},
				{
					src: "../../static/images/demo/demo2.jpg"
				},
				{
					src: "../../static/images/demo/demo3.jpg"
				}
			]
		},
		{
			type: "indexnavs",
			data: [{
					src: '/static/images/indexnav/1.png',
					des: "新品发布"
				},
				{
					src: '/static/images/indexnav/2.gif',
					des: "小米众筹"
				},
				{
					src: '/static/images/indexnav/3.gif',
					des: "以旧换新"
				},
				{
					src: '/static/images/indexnav/4.gif',
					des: "一分拼团"
				}, {
					src: '/static/images/indexnav/5.gif',
					des: "超值特卖"
				},
				{
					src: '/static/images/indexnav/6.gif',
					des: "小米秒杀"
				},
				{
					src: '/static/images/indexnav/7.gif',
					des: "真心想要"
				},
				{
					src: '/static/images/indexnav/8.gif',
					des: "电视热卖"
				},
				{
					src: '/static/images/indexnav/9.gif',
					des: "家电热卖"
				}, {
					src: '/static/images/indexnav/10.gif',
					des: "米粉卡"
				},

			]
		},
		{
			type: "largeAD",
			data: {
				title: "每日精选",
				"cover": "/static/images/demo/demo4.jpg"
			}
		},
		{
			type: "threeADV",
			data: {
				big: {
					src: "/static/images/demo/demo1.jpg"
				},
				top: {
					src: "/static/images/demo/demo2.jpg"
				},
				bottom: {
					src: "/static/images/demo/demo3.jpg"
				}
			}
		},
		{
			type: "goods",
			data: [{
				cover: "/static/images/demo/list/4.jpg",
				title: "米家空调",
				desc: "1.5匹变频空调",
				oprice: 2699,
				pprice: 1399
			}, {
				cover: "/static/images/demo/list/5.jpg",
				title: "米家空调",
				desc: "1.5匹变频空调",
				oprice: 2699,
				pprice: 1399
			}, {
				cover: "/static/images/demo/list/3.jpg",
				title: "米家空调",
				desc: "1.5匹变频空调",
				oprice: 2699,
				pprice: 1399
			}, {
				cover: "/static/images/demo/list/3.jpg",
				title: "米家空调",
				desc: "1.5匹变频空调",
				oprice: 2699,
				pprice: 1399
			}, {
				cover: "/static/images/demo/list/3.jpg",
				title: "米家空调",
				desc: "1.5匹变频空调",
				oprice: 2699,
				pprice: 1399
			}]
		}

	]
	import swiperImg from '@/components/swiper-img.vue';
	import indexNav from '@/components/index-nav.vue';
	import threeAdv from '@/components/three-adv.vue';
	import card from '@/components/card.vue';
	import commonList from '@/components/common-list.vue';

	export default {
		components: {
			swiperImg,
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
				tabbars: [],
				newsItems: [],
			}
		},
		onNavigationBarSearchInputClicked: (e) => {
			uni.navigateTo({
				url:"../serach/serach"
			})
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					this.scrollH = res.windowHeight - uni.upx2px(82)
				}
			})

			// 初始化数据
			this.init()

		},
		methods: {
			init() {
				//获取tabbar
				this.tabbars = demotabBars;
				let arr = []
				for (let i = 0; i < this.tabbars.length; i++) {
					let obj = {
						list: []
					}
					if (i === 0) {
						obj.list = demo1

					}
					arr.push(obj)
				}
				this.newsItems = arr
			},
			changeTab(index) {
				if (this.tabIndex == index) {
					return
				}
				this.tabIndex = index;
				this.scrollinto = 'tab' + index
			},
			onChangeTab(e) {
				this.changeTab(e.detail.current)
				this.addData()
			},
			addData() {
				let index = this.tabIndex;
				this.newsItems[index].list = demo1
			}
		}
	}
</script>

<style>
	.content {}

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
