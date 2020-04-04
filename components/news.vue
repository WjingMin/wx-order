<template>
	<view>
		<uni-list v-for="item in newslist" :key="item.newsid" >
			<uni-list-item   :title="item.newstittle" :note="item.newslitt" :show-badge="true" badge-text="12"></uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue'
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	export default {
		data() {
			return {
				newslist: '',
			};
		},
		
		methods:{
			newsdetail(id){
				// console.log(id);
				uni.navigateTo({
					url:'.././newsdetail/newsdetail',
					fail: (res) => {
						console.log(res)
					}
				})
			}
		},
		components: {
			uniCard,
			uniList,
			uniListItem
		},
		created() {
			uni.request({
				url: 'http://127.0.0.1:8000/api/newquer/',
				success: (res) => {
		
					this.newslist = res.data.data
				}
			})
		}
	}
</script>

<style>

</style>
