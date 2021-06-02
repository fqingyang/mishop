<template>
	<!-- 轮播图 -->
	<view>
		<swiper indicator-dots="indicatorDots" duration="300" circular="circular" autoplay="autoplay">
			<block v-for="(item,index) in imgs" :key="index">
				<swiper-item class="swiper-item">
					<view @tap="click(index)">
						<image :src="item.src" lazy-load="true" mode="aspectFill" style="height:400rpx ;"></image>
					</view>
				</swiper-item>

			</block>
		</swiper>
	</view>
</template>

<script>
	export default {
		props: {
			imgs: Array
		},
		name: "swiper-img",
		data() {
			return {

			};
		},
		methods: {
			click(index) {
				console.log("点击了:" + index)
			}
		}
	}
</script>

<style>

</style>
