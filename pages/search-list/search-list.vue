<template>
	<view>
		<!-- 筛选 -->
		<view class="d-flex border-top border-bottom" style="height: 100rpx;">
			<view class="flex-1 d-flex a-center j-center">综合</view>
			<view class="flex-1 d-flex a-center j-center">销量</view>
			<view class="flex-1 d-flex a-center j-center">价格</view>
			<view class="flex-1 d-flex a-center j-center" @tap="showDrawer()">筛选</view>
		</view>


		<uni-drawer ref="showRight" mode="right" :mask-click="true">
			<card title="服务">
				<view class="row j-sb">
					<view class="span24-7 p-1  text-center bg-light-secondary box-b m-1 radio-active">
						按钮
					</view>
					<view class="span24-7 p-1  text-center bg-light-secondary box-b m-1">
						按钮
					</view>
					<view class="span24-7 p-1  text-center bg-light-secondary box-b m-1">
						按钮
					</view>
				</view>
			</card>
			<view class=" d-flex position-fixed bottom-0 right-0 w-100">
				<view class="flex-1 main-bg-color text-white font-md py-2 text-center border-top "
					hover-class="main-bg-hover-color">确定</view>
				<view class="flex-1 font-md py-2 text-center border-top ">重置</view>
			</view>
		</uni-drawer>
		<!-- 列表 -->
		<block v-for="(item,index) in list">
			<search-list :item="item" :index="index"></search-list>
		</block>
	</view>
</template>

<script>
	import card from '@/components/card.vue';
	import price from '@/components/price.vue';
	import searchList from '@/components/search-list.vue';
	export default {
		components: {
			card,
			price,
			searchList
		},
		data() {
			return {
				list: [{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					},
					{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					},
					{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					},
					{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					},
					{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					},
					{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					},
					{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					},
					{
						title: "真无线蓝牙耳机",
						titlePic: "/static/images/demo/demo6.jpg",
						des: "雅致简约/分体式入耳/收纳盒充电/触控操作/蓝牙5.0",
						pprice: 100,
						comment_num: 1300,
						good_num: "98%"
					}
				]

			}
		},
		methods: {
			open() {
				console.log("打开抽屉");
			},
			showDrawer() {
				this.$refs.showRight.open();
			},
			closeDrawer() {
				this.$refs.showRight.close();
			}
		}
	}
</script>

<style>
	.radio-active {
		background: #FCE0D5 !important;
		color: #EB7320 !important;
		border-color: #EB7320;
		border: 1px solid #EB7320;
		border-radius: 3px;
	}

	.img-fit {
		object-fit: cover
	}
</style>
