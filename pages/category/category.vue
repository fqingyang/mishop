<template>
	<view class="d-flex v_height border-top box-b" :style="'height:'+rootHeight+'px;'">
		<scroll-view scroll-y style="flex: 1;height: 100%;" class="border-right">
			<view class="border-bottom border-light-secondary py-1 " v-for="(item,index) in cate"
			@tap="changecate(index)"
			hover-class="bg-light-secondary">
				<view class="py-1 j-center font-md text-muted text-center "
					:class="activeIndex===index?'class-active':''">{{item.name}}
				</view>
			</view>
		</scroll-view>
		
		<scroll-view scroll-y style="flex: 3.5;height: 100%;;">
			<view class="row">
				<view class="span24-8 text-center py-2">
					<image src="../../static/images/demo/cate_03.png" style="height: 120rpx;width: 120rpx;" ></image>
					<text class="d-block">商品一</text>
				</view>
				<view class="span24-8 text-center py-2">
					<image src="../../static/images/demo/cate_03.png" style="height: 120rpx;width: 120rpx;"></image>
					<text class="d-block">商品一</text>
				</view>
				<view class="span24-8 text-center py-2">
					<image src="../../static/images/demo/cate_03.png" style="height: 120rpx;width: 120rpx;"></image>
					<text class="d-block">商品一</text>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				rootHeight: 700,
				cate: [],
				// 当前选中的项目
				activeIndex: 0,
				test:"",
			}
		},
		onLoad() {
			uni.getSystemInfo({
				success: (res) => {
					this.rootHeight = res.windowHeight
				}
			})
			for (let i = 0; i < 20; i++) {
				this.cate.push({
					name: "分类" + i
				})
			}//
		},

		methods: {
			changecate(index){
				this.activeIndex = index
			}
		},
	}
</script>

<style>
	.class-active {
		border-left: 8rpx solid #FD6801;
		color: #FD6801 !important;
	}
</style>
