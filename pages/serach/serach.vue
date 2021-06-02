<template>
	<view>
		<card title="热门搜索" cover="/static/images/demo/search-banner.png"></card>
		<!-- 多色按钮 -->
		<view class="px-1 mb-2">
			<view class="px-2 py-1 border d-inline-block m-1" :style="getStyle" v-for="i in 10" :key="i">
				按钮{{i}}
			</view>
		</view>
		<!-- 常用分类 -->
		<card title="常用分类">
			<view class="px-2 py-1 border d-inline-block m-1" :style="getStyle" v-for="i in 7" :key="i">
				按钮{{i}}
			</view>
			
		</card>
	</view>
</template>

<script>
	import card from '@/components/card.vue';
	export default {
		components: {
			card
		},
		data() {
			return {

			}
		},
		onNavigationBarButtonTap: (e) => {
			if(e.index==0){
				uni.navigateTo({
					url:"../search-list/search-list"
				})
			}
			
		},
		methods: {

		},
		computed: {
			getStyle() {
				let color = {
					borderColor:[],
					background:[]
				}
			}

		},
		onLoad() {
			// console.log(Math.random())
		}
	}
</script>

<style>

</style>
