<template>
	<view class="cash_detail">
		<template v-for="item in array">
			<view class="detail" :key="item.id">
				<view class="space"/>
				<view class="detailBoard">
					<text>订单编号：{{item.id}}</text>
					<view class="row">
						<text>订单开始时间：{{item.startDate}}</text>
						<text>订单完成时间：{{item.endDate}}</text>
					</view>
					<view class="row">
						<text class="bold">主题：{{item.title}}</text>
						<text>收费：￥{{item.fee}}</text>
						<text class="bold">交易额：￥{{item.money}}</text>
					</view>
					<view class="row">
						<text>发起者：{{item.userId1}}</text>
						<text>接受者：{{item.userId2}}</text>
					</view>
					<view class="row">
						<text>服务类型：{{item.type}}</text>
						<text v-if="online">开展类型：线上</text>
						<text v-if="!online">开展类型：线下</text>
					</view>
					<text v-if="!online">地址：{{item.address}}</text>
				</view>
			</view>
		</template>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				array:[
					{
						id:'12535675',
						title:'帮忙学习',
						startDate:'2020-04-16',
						endDate:'2020-04-17',
						userId1:'Didnelpsun',
						userId2:'LSY',
						type:'补习',
						money:12,
						fee:0.7,
						online: true,
						address:'湖北省武汉市华中师范大学八号楼1035室'
					}
				]
			};
		}
	}
</script>

<style lang="scss" scoped>
	.cash_detail{
		display: flex;
		flex-direction: column;
		color: $uni-text-color;
	}
	.detail{
		font-size: $uni-font-size-base;
	}
	.space{
		height: 2 * $space;
		background-color: $uni-bg-color-grey;
	}
	.detailBoard{
		padding: 2 * $space;
		display: flex;
		flex-direction: column;
	}
	.row{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		color: $uni-text-color-grey;
		font-size: $uni-font-size-sm;
		margin: 1px 0 1px;
	}
	.bold{
		font-size: $uni-font-size-lg;
		color: #000;
		font-weight: bold;
		padding: $space 0 $space;
	}
</style>
