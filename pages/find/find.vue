<template>
	<view class="find">
		<search-bar></search-bar>
		<view>
		<view class="cardboard">
			<uni-card extra="擅长领域:" title="小红" mode="style" :is-shadow="true" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg"
			 note="帮助者等级">
				那是一个秋意盎然、金风送爽的日子，我和父母一起来到了位于上师大旁的康健园。一踏进公园，一股浓郁的桂香扑鼻而来，泌人心脾,让我心旷神怡，只见一朵朵开得正烈的金色桂花，迎风而立，仿佛在向我招手。我们追着这桂香，走进了清幽的公园。
			</uni-card>
			<uni-card extra="擅长领域:" title="小明" mode="style" :is-shadow="true" thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg"
			 note="帮助者等级">
				那是一个秋意盎然、金风送爽的日子，我和父母一起来到了位于上师大旁的康健园。一踏进公园，一股浓郁的桂香扑鼻而来，泌人心脾,让我心旷神怡，只见一朵朵开得正烈的金色桂花，迎风而立，仿佛在向我招手。我们追着这桂香，走进了清幽的公园。
			</uni-card>
			<helper-introduction name="王伟" notes="我超级厉害超级厉害超级超级厉害" area="学习"></helper-introduction>
		</view>
			
		</view>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue'
	import searchBar from '../../components/search-bar/search-bar.vue'
	import helperIntroduction from '@/components/helper-introduction/helper-introduction.vue'
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
	.find {
		font-size: $uni-font-size-base;
	}
</style>
