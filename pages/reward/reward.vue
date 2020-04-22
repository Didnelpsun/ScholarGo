<template>
	<view class="reward">
		<search-bar></search-bar>
		<scroll-view>
			<template v-for="item in list">
				<order-item
				:key='item.id'
				:title='item.title'
				:type='item.type'
				:name='item.user1' 
				:address='item.address' 
				:money='item.money' 
				:online='item.online' 
				:time='item.time' 
				:details='item.details'
				/>
			</template>
		</scroll-view>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue'
	import OrderItem from '@/components/order-item/order-item.vue'
	import searchBar from '../../components/search-bar/search-bar.vue'
	export default {
		data() {
			return {
				list:[
					{
						id:'245655',
						title:'帮我完成实验报告',
						type:'学习',
						user1:'小王',
						address:'八号楼',
						money:'15',
						online:false,
						time:'5',
						details:'帮忙写信息管理学院2019级C语言课程实验报告'
					}
				],
			}
		},
		onLoad: function(option) { //option为object类型，会序列化上个页面传递的参数
			// console.log(option.id); //打印出上个页面传递的参数。
			// console.log(option.name); //打印出上个页面传递的参数。
		},
		components: {
			uniCard,
			OrderItem,
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
