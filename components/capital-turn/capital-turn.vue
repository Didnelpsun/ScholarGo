<template>
	<view class="capitalTurn">
		<view style="font-size: 32rpx; margin: 10px;padding-top: 10px;">充值方式：</view>
		<clickCard
		iconType="shop"
		iconColor="#fd4931"
		title="银行卡"
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
			<view class="button" @click="showPass">{{buttonType}}</view>
		</view>
		<uniPopup ref="showDetail" type="bottom">
			<view class="popBoard">
				<view style="height: 10px;"/>
				<text>选择{{capitalType.value}}</text>
				<view style="height: 10px;"/>
				<template v-for="(account, index) in showCheck">
					<clickCard
					:key = "index"
					:title = "'账号'+(index+1)+'：'"
					:subtitle="account[0]"
					:check="account[1]"
					@click.native="changeDetailCheck(index)"
					/>
				</template>
				<clickCard
				iconType="plus-filled"
				iconColor="#888"
				:title="'使用新的'+capitalType.value+'支付'"
				/>
			</view>
		</uniPopup>
		<uni-popup ref="pass" type="center">
			<view class="passwordBoard">
				<input type="password" v-model="password" @blur="cleanPass"/>
				<view class="button">确认</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import clickCard from "@/components/click-card/click-card.vue"
	import uniPopup from "@/components/uni-popup/uni-popup.vue"
	export default {
		data() {
			return {
				check:{
					cardCheck:false,
					zhifuCheck:false,
					weixinCheck:false,
					qqCheck:false,
				},
				style:'inputStyle',
				capitalType:{
					name:'',
					value:''
				},
				showCheck:[],
				cardCheck:[
					['123',false],
					['155',true]
				],
				zhifuCheck:[
					['345',false]
				],
				weixinCheck:[
					['567',false]
				],
				qqCheck:[
					['890',false]
				],
				password:''
			};
		},
		props:{
			'buttonType':{
				type:String,
				default:''
			},
		},
		components:{
			clickCard,
			uniPopup
		},
		mounted()
		{
			//初始化capitalType值
			let trueNum = 0;
			let i = 0;
			let _check = this.check;
			for(let key in _check){
				if(_check[key] === true){
					trueNum++;
					i++;
					if(trueNum === 1){
						this.capitalType.name = key;
						this.capTypeValue(key,this.capitalType.value);
					}
					if(trueNum > 1){
						_check[key] = false;
					}
				}
				if(trueNum === 0){
					for(key in _check){
						this.capitalType.name = key;
						this.capTypeValue(key,this.capitalType.value);
						_check[key] = true;
						break;
					}
				}
			}
		},
		methods:{
			//辅助方法
			focusInput:function(){
				this.style='inputStyle';
			},
			//检查参数布尔值
			checkBoolProps:function(array){
				let trueNum = 0;
				let i = 0;
				for(;i < array.length; i++){
					if(array[i][1] === true){
						trueNum++;
						if(trueNum > 1)
							array[i][1] = false;
					}
				}
				if(trueNum === 0){
					array[0][1] = true;
				}
			},
			//根据capitalType.name补充capitalType.value
			capTypeValue:function(name,value){
				switch(name){
					case 'cardCheck':
						value = "银行卡";
						break;
					case 'zhifuCheck':
						value = "支付宝账号";
						break;
					case 'weixinCheck':
						value = "微信账号";
						break;
					case 'qqCheck':
						value = "QQ账号";
						break;
				}
			},
			//
			showDetail:function(type){
				this.capitalType.name = type;
				for(let key in this.check){
					if(key!==type)
						this.check[key] = false;
					else
						this.check[key] = true;
				}
				this.showCheck = this[type];
				this.capTypeValue(type,this.capitalType.value);
				this.checkBoolProps(this.showCheck);
				this.$refs.showDetail.open();
			},
			changeDetailCheck:function(index){
				this.$set(this.showCheck[index],1,true);
				let i = 0;
				for(;i < this.showCheck.length; i++){
					if(i != index)
						this.$set(this.showCheck[i],1,false);
				}
			},
			showPass:function(){
				this.$refs.pass.open();
			},
			cleanPass:function(){
				this.password = '';
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
.popBoard{
	background-color: $uni-bg-color;
	border-radius: 1vw;
	font-size: $uni-font-size-lg;
	text{
		margin: 10px;
	}
}
.passwordBoard{
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	background-color: $uni-bg-color;
	font-size: 40rpx;
	padding: 4 * $space;
	border-radius: 1vw;
	input{
		width: 50vw;
		border: solid 1px #c8c7cc;
		border-radius: 0.5vw;
	}
}
</style>
