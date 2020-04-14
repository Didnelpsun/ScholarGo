<template>
	<view class="deposit">
		<view style="font-size: 32rpx; margin: 10px;padding-top: 10px;">充值方式：</view>
		<clickCard
		iconType="shop"
		iconColor="#fd4931"
		title="银行卡"
		:subtitle="cardType"
		arrow=true
		/>
		<clickCard
		iconType="upload-filled"
		iconColor="#316ffd"
		title="支付宝"
		arrow=true
		/>
		<clickCard
		iconType="weixin"
		iconColor="green"
		title="微信"
		arrow=true
		/>
		<clickCard
		iconType="qq"
		iconColor="#5cd2f9"
		title="QQ"
		arrow=true
		/>
		<view style="height: 20px;"></view>
		<view class="inputNum">
			<text>充值金额</text>
			<scroll-view class="inputView">
				<text style="font-weight: bold;">￥</text>
				<input type="digit" focus adjust-position=false @focus="focusInput"/>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	import clickCard from "@/components/click-card/click-card.vue"
	export default {
		data() {
			return {
				cardType:''
			};
		},
		components:{
			clickCard
		},
		methods:{
			focusInput:function(){
				
			}
		}
	}
</script>

<style lang="scss" scoped>
.deposit{
	color: $uni-text-color;
	font-size: $uni-font-size-base;
	background-color: $uni-bg-color-grey;
}
.inputNum{
	padding: 2* $space 4 * $space 2 * $space;
	background-color: $uni-bg-color;
	border-radius: 1vw;
}
.inputView{
	display: flex;
	flex-direction: row;
	font-size: 60rpx;
	margin-top: 3 * $space;
	align-items: center;
	margin-right: 5px;
}
</style>
