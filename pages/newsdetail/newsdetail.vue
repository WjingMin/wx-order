<template>
	<view>
		<view class="tittle">
			<text>{{newslist.newstittle}}</text>
		</view>

		<view class="writer">
			<view class="imgtoux">
				<image src="../../static/农民.SVG.svg" mode=""></image>
			</view>
			<view class="time">
				<text>作者：7Years</text>
				<text>时间：2020/4/5</text>
			</view>

			<view class="button">
				<button type="warn" @click="changebt">{{butvalu}}</button>
			</view>

		</view>


		<view class="mian">
			<text>
				{{newslist.newsdetail}}
			</text>
		</view>
		
		
		<!-- <view class="count">
			<text>评论区</text>
			<uni-list >
				<uni-list-item title="好文章" note="2020/3/4/5" 
				></uni-list-item>
				<uni-list-item title="好文章" note="2020/3/4/5"
				></uni-list-item>
				<uni-list-item title="好文章" note="2020/3/4/5"
				></uni-list-item>
				<uni-list-item title="好文章" note="2020/3/4/5"
				></uni-list-item>
			</uni-list>
		</view> -->
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	export default {
		
			
		components:{
			uniList,uniListItem
		},
		data() {
			return {
			newslist:'',
			butvalu:'关注'
			}
		},
		methods: {
			changebt(){
				this.butvalu="已关注"
			}

		},
		onLoad(id) {
			console.log(id.id)
			uni.request({
				url:'http://127.0.0.1:8000/api/newbyid/'+id.id,
				success: (res) => {
					console.log(res.data.data)
					this.newslist=res.data.data[0]
				}
			})
		}
	}
</script>

<style lang="scss" scoped>
	.tittle {
		text-align: center;
		margin-top: 15rpx;
		padding: 10rpx;

		text {
			font-size: 40rpx;
		}
	}

	.writer {
		display: flex;
		align-items: center;

		button {
			width: 150rpx;
			height: 50rpx;
			font-size: 20rpx;
			margin-left: 120rpx;
		}

		image {
			width: 80rpx;
			height: 80rpx;
			
		}

		.time {
			font-size: 25rpx;

			text {
				margin-right: 30rpx;
			}
		}
		.mian{
			text{
				font-size: 30rpx;
				text-align: left;
			}
		}
	.count{
		margin-top: 50rpx
		;
		text{
			font-size: 50rpx;
		}
	}
	
	
	

	}
</style>
