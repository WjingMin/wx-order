<template>
	<view>
		<swiper class="swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="500">
			<swiper-item>
				<image class="img" src="../../static/1.png" mode=""></image>
			</swiper-item>
			<swiper-item>
				<image class="img" src="../../static/2.png" mode=""></image>
			</swiper-item>
			<swiper-item>
				<image class="img" src="../../static/3.png" mode=""></image>
			</swiper-item>
		</swiper>
		<uni-grid :column="4" :show-border="false" :square="false">
			<uni-grid-item class="grid">
				<image class="img1" src="../../static/配送车.SVG.png" @click="touch" mode=""></image>
				<text>客户订单提交</text>
			</uni-grid-item>
			<uni-grid-item>
				<image class="img1" src="../../static/农民.SVG.svg" mode=""></image>
				<text>商城</text>
			</uni-grid-item>
			<uni-grid-item>
				<image class="img1" src="../../static/谷物.SVG.svg" mode=""></image>
				<text>我的</text>
			</uni-grid-item>
			<uni-grid-item>
				<image class="img1" src="../../static/果树.SVG.svg" mode=""></image>
				<text>暂未开发</text>
			</uni-grid-item>
		</uni-grid>

		<wuc-tab :tab-list="tabList" :tabCur.sync="TabCur"></wuc-tab>
		<swiper :current="TabCur" class="swiper1" duration="300" :circular="true" indicator-color="rgba(255,255,255,0)"
		 indicator-active-color="rgba(255,255,255,0)" @change="tabChange">
			<swiper-item>
				<news1 @sonvalue="touch1"></news1>
			</swiper-item>
			<swiper-item>
				<news></news>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	import WucTab from '@/components/wuc-tab/wuc-tab.vue';
	import news from '@/components/news.vue'
	import news1 from '@/components/news1.vue'
	
	export default {
		data() {
			return {
				sonva:'',
				TabCur: 0,
				detaillist: [{
					name: "666",

				}],
				tabList: [{
						name: '精选'
					}, {
						name: '订阅'
					},
					{
						name: '热点'
					},
					{
						name: '优惠'
					},
					{
						name: '新闻'
					},
					{
						name: '知识'
					}
				]
			}
		},
		methods: {
			touch(){
				uni.navigateTo({
					url:'../newsdetail/newsdetail?id='+this.sonva
				})
			},
			touch1(data){
				this.sonva=data;
				console.log(this.sonva)
				
			},
		
			tabChange(e) {
				this.TabCur = e.target.current;
				// console.log(e)
				// uni.request({
				// 	url: 'http://127.0.0.1:8000/api/test/',
				// 	success: (res) => {
				// 	console.log(res.data.data)
				// 	this.detaillist=res.data.data

				// 	}
				// })
			}

		},
		components: {
			uniGrid,
			uniGridItem,
			WucTab,
			news1,
			news

		},

	}
</script>

<style lang="scss">
	.img {

		width: 100%;
		height: 100%;
	}

	.swiper {
		height: 400rpx;
		margin-bottom: 0rpx;
	}

	.swiper1 {
		height: 800rpx;
	}

	uni-grid-item {
		/* 	background-color: #007AFF; */
		text-align: center;
	}

	uni-grid {
		margin-left: 50rpx;
	}

	.img1 {
		width: 90rpx;
		height: 90rpx;
		margin: 0 auto;
	}

	text {
		font-size: 25rpx;
	}
</style>
