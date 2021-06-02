<template>
	<view class="card">
		<view v-if="title" class="p-2 border-bottom main-border-color">
			<slot name="title">
				<text class="font-md font-weight">{{title}}</text>
			</slot>
		</view>
		<view class="">
			<image v-if='cover' :src="cover" mode="widthFix" lazy-load="true"></image>
			<slot></slot>
		</view>
	</view>
	</view>

</template>

<script>
	export default {
		props: {
			title: String,
			cover: String
		},
		name: "card",
		data() {
			return {

			};
		}
	}
</script>

<style>

</style>
