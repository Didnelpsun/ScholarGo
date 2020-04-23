<template>
	<view class="cash_detail">
		<template v-for="item in array">
			<view class="space" :key="item.itemId"></view>
			<order-items
			:key="item.itemId"
			:itemId="item.itemId"
			:title="item.title"
			:startDate="item.startDate"
			:endDate="item.endDate"
			:userId1="item.userId1"
			:userId2="item.userId2"
			:type="item.type"
			:money="item.money"
			:fee="item.fee"
			:online= "item.online"
			:address="item.address"
			:details="item.details"
			/>
		</template>
	</view>
</template>

<script>
	import orderItems from '@/components/order-items/order-items.vue'
	export default {
		data() {
			return {
				array:[
					{
						itemId:'12535675',
						title:'帮忙学习',
						startDate:'2020-04-16',
						endDate:'2020-04-17',
						userId1:'Didnelpsun',
						userId2:'LSY',
						type:'补习',
						money:12,
						fee:0.7,
						online: true,
						address:'湖北省武汉市华中师范大学八号楼1035室',
						details:'打架'
					}
				]
			};
		},
		components:{
			orderItems
		}
	}
</script>

<style lang="scss" scoped>
	.cash_detail{
		display: flex;
		flex-direction: column;
		color: $uni-text-color;
	}
	.space{
		background-color: $uni-bg-color-grey;
		height: 3 * $space;
	}
</style>
