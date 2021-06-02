<template>
	<view class="d-flex" style="height: 530rpx;">
		<image :src="imgObj.big.src" class="flex-1 mr wh-100" mode="aspectFill" @tap="click(imgObj.big)"
			lazy-load="true"></image>
		<view class="d-flex flex-1 flex-column w-100">
			<image :src="imgObj.top.src" class="flex-1 mb wh-100" mode="aspectFill" @tap="click(imgObj.top)"
				lazy-load="true"></image>
			<image :src="imgObj.bottom.src" class="flex-1 wh-100" mode="aspectFill" @tap="click(imgObj.bottom)"
				lazy-load="true"></image>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			imgObj: Object
		},
		name: "three-adv",
		data() {
			return {

			};
		},
		methods: {
			click(obj) {}
		}
	}
</script>

<style>

</style>
