<template>
	<view class="reward">
		<search-bar></search-bar>
		<view>
			<uni-card title="悬赏贴" extra="小红" mode="basic">
				<text>
					服务类型：\n
					愿意支付金额：\n
					服务时长：\n
					线上or线下：\n
					服务地点（线下）：\n
				</text>
			</uni-card>
			<uni-card title="悬赏贴" extra="小明" mode="basic">
				<text>
					服务类型：\n
					愿意支付金额：\n
					服务时长：\n
					线上or线下：\n
					服务地点（线下）：\n
				</text>
			</uni-card>
			<reward-stickers service="学习" name="小王" address="八号楼"></reward-stickers>
		</view>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue'
	import rewardSticker from '@/components/reward-stickers/reward-stickers.vue'
	import searchBar from '../../components/search-bar/search-bar.vue'
	export default {
		data() {
			return {
			}
		},
		onLoad: function(option) { //option为object类型，会序列化上个页面传递的参数
			// console.log(option.id); //打印出上个页面传递的参数。
			// console.log(option.name); //打印出上个页面传递的参数。
		},
		components: {
			uniCard,
			searchBar
		},
		mounted() {}
	}
</script>

<style lang="scss">
	.reward {
		font-size: $uni-font-size-base;
	}
</style>
