<template>
	<view class="detail">
		<view class="detailBoard">
			<text>订单编号：{{itemId}}</text>
			<view class="row">
				<text>订单开始时间：{{startDate}}</text>
				<text v-if="endDate">订单完成时间：{{endDate}}</text>
			</view>
			<view class="row">
				<text class="bold">主题：{{title}}</text>
				<text v-if="fee">收费：￥{{fee}}</text>
				<text class="bold">交易额：￥{{money}}</text>
			</view>
			<view class="row">
				<text>发起者：{{userId1}}</text>
				<text v-if="userId2">接受者：{{userId2}}</text>
			</view>
			<view class="row">
				<text>服务类型：{{type}}</text>
				<text v-if="online">开展类型：线上</text>
				<text v-if="!online">开展类型：线下</text>
			</view>
			<text v-if="!online">地址：{{address}}</text>
			<text style="color: #f77103;" @click="open" v-if="details">查看详情</text>
			<uni-popup ref="popup" type="center">
				<view class="popup">
					<view class="bold" style="text-align: center;">具体内容</view>	
					{{details}}
				</view>
			</uni-popup>
		</view>
	</view>
</template>

<script>
	import uniPopup from '@/components/uni-popup/uni-popup.vue'
	export default {
		data() {
			return {
			};
		},
		props:{
			'itemId' : String,
			'title' : String,
			'type' : String,
			'money' :Number,
			'complete' : {
				type : Boolean,
				default : false 
			},
			'fee' : Number, 
			'startDate' : String,
			'endDate' : String, 
			'userId1' : String,
			'userId2' : String,
			'abuserId' : Array,
			'online' : {
				type : Boolean,
				default : true
			},
			'address' : String, 
			'details' : String
		},
		components:{
			uniPopup
		},
		methods:{
			open(){
				this.$refs.popup.open()
			}
		}
	}
</script>

<style lang="scss">
	.detail{
		font-size: $uni-font-size-base;
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
	.popup{
		padding: 2 * $space;
		background-color: $uni-bg-color;
		border-radius: 1vw;
		width: 80vw;
	}
</style>
