<template>
	<view class="capitalTurn">
		<view style="font-size: 32rpx; margin: 10px;padding-top: 10px;">充值方式：</view>
		<clickCard
		iconType="shop"
		iconColor="#fd4931"
		title="银行卡"
		:subtitle="cardType"
		:check="check.cardCheck"
		arrow=true
		@click.native="showDetail('cardCheck')"
		/>
		<clickCard
		iconType="upload-filled"
		iconColor="#316ffd"
		title="支付宝"
		:check="check.zhifuCheck"
		arrow=true
		@click.native="showDetail('zhifuCheck')"
		/>
		<clickCard
		iconType="weixin"
		iconColor="green"
		title="微信"
		:check="check.weixinCheck"
		arrow=true
		@click.native="showDetail('weixinCheck')"
		/>
		<clickCard
		iconType="qq"
		iconColor="#5cd2f9"
		title="QQ"
		:check="check.qqCheck"
		arrow=true
		@click.native="showDetail('qqCheck')"
		/>
		<view style="height: 20px;"></view>
		<view class="inputNum">
			<text>充值金额</text>
			<view class="inputView">
				<text style="font-weight: bold;">￥</text>
				<input type="digit" focus adjust-position=false :class="style" @focus="focusInput"/>
			</view>
		</view>
		<view class="buttonView">
			<view class="button">{{buttonType}}</view>
		</view>
	</view>
</template>

<script>
	import clickCard from "@/components/click-card/click-card.vue"
	export default {
		data() {
			return {
				cardType:'',
				check:{
					cardCheck:true,
					zhifuCheck:false,
					weixinCheck:false,
					qqCheck:false,
				},
				style:'inputStyle'
			};
		},
		props:{
			'buttonType':{
				type:String,
				default:''
			}
		},
		components:{
			clickCard
		},
		methods:{
			focusInput:function(){
				this.style='inputStyle';
			},
			showDetail:function(type){
				let _this = this;
				for(let key in this.check){
					if(key!==type)
						_this.check[key] = false;
					else
						_this.check[key] = true;
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
.capitalTurn{
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
	margin-top: 3 * $space;
	align-items: center;
	margin-right: 5px;
	font-size: 60rpx;
}
.inputStyle{
	font-size: 60rpx;
	height: 50px;
	font-weight: normal;
	font-family: "Microsoft YaHei";
}
.buttonView{
	width: 100vw; 
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	background-color: white;
}
.button{
	width: 50vw;
	background-color: #55d018;
	font-size: 40rpx;
	color:$uni-text-color-inverse;
	text-align: center;
	margin-top: 2 * $space;
	padding: $space;
	display: flex;
	flex-direction: column;
	justify-content: center;
	border-radius: 1vw;
}
</style>
