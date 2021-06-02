<template>
	<!-- 功能导航 -->
	<view class="row  j-center m-2">
		<block v-for="(item,index) in datas">
			<view class="span-4 d-flex flex-column j-center a-center py-1" @tap="click(index)">
				<image :src="item.src" mode="aspectFill" style="width: 60rpx;height: 60rpx;" lazy-load="true">
				</image>
				<text>{{item.des}}</text>
			</view>
		</block>
	</view>
</template>

<script>
	export default {
		name:"index-nav",
		props:{
			datas:Array
		},
		data() {
			return {
				
			};
		},
		methods:{
			click(index){
				console.log(index)
			}
		}
	}
</script>

<style>

</style>
