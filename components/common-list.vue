<template>
	<view style="width: 372rpx;">
		<image :src="item.cover" mode="widthFix" lazy-load="lazy-load"></image>
		<view class="p-2 pt-1">
			<view class="font-md">{{item.title}}</view>
			<text class="d-block font">{{item.desc}}</text>
			<view class="d-flex  my-1">
				<price>{{item.pprice}}</price>
				<view class="font-sm text-light-muted line-through a-self-end ml-1 line-h">¥{{item.oprice}}
				</view>
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
		name: "common-list",
		data() {
			return {

			};
		}
	}
</script>

<style>

</style>
