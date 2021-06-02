<template>
	<view class="row p-2 border-bottom border-light-secondary animate__animated animate__fadeIn animate__faster">
		<view class="span-6">
			<image :src="item.titlePic" mode="aspectFill" class="cover_height" lazy-load="true"></image>
		</view>
		<view class="span-14 pl-2 d-flex flex-column">
			<view class="font-md font-weight">
				{{item.title}}
			</view>
			<view class="font text-light-muted line-h-md mb-auto">
				{{item.des}}
			</view>
			<price>{{item.pprice}}</price>
			<view class="font-sm text-light-muted">
				{{item.comment_num}} 条评论 {{item.good_num}}满意
			</view>
		</view>
	
	</view>
</template>

<script>
	import price from '@/components/price.vue';
	export default {
		components:{
			price
		},
		props:{
			item:Object,
			index:Number
		},
		name:"search-list",
		data() {
			return {
				
			};
		}
	}
</script>

<style>
.cover_height{
	height: 200rpx;
}
</style>
