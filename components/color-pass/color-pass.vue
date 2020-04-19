<template>
	<view class="color">
		<text :style="'padding: 0 '+ padding +' 0;'">{{title}}</text>
		<input :password="inputType" v-model="password" @input="change" maxlength="20"/>
		<image :style="'right: ' + eye +';'" v-show="show" src="../../static/image/user/eye-open.png" @click="showPass"/>
		<image :style="'right: ' + eye +';'" v-show="!show" src="../../static/image/user/eye-close.png" @click="showPass"/>
		<view class="dot" :style="'background-color: '+dotColor+' ; right: ' + padding +';'"></view>
	</view>
</template>

<script>
	export default {
		name:'colorPass',
		data() {
			return {
				dotColor:'red',
				userId:'',
				inputType:'password',
				show:false
			};
		},
		props:{
			title:{
				type:String,
				default:'密码'
			},
			padding:{
				type:String,
				default:'10px'
			}
		},
		computed:{
			eye(){
				let string = this.padding;
				let num = parseInt(string);
				num *= 2.5;
				let i = 0;
				for(;i < string.length;){
					if(string[i]>='0' && string[i]<='9'){
						i++
					}
					else
						break;
				}
				let unit = string.substring(i);
				return num+unit;
			}
		},
		methods:{
			check(CString){
				let i = 0;
				let num = 0;
				let nNum = 0;
				for(;i < CString.length; i++){
					if((CString[i] >= 'A' && CString[i] <= 'Z') || (CString[i] >= 'a' && CString[i] <= 'z'))
						num++;
					if(CString[i] >= '0' && CString[i] <= '9') {
						num++;
						nNum++;
					}
				}
				if(num === CString.length && nNum < num){
					return num - nNum;
				}
				else
					return 0;
			},
			change(){
				let len = this.password.length;
				let num = this.check(this.password);
				if(len >= 6 && this.password != this.userId && num){
					this.dotColor = '#f0c84e'
					if(this.password.length > 10 && num > 3)
						this.dotColor = '#73ab4a'
				}
				else
					this.dotColor = 'red'
			},
			showPass(){
				this.show = !this.show;
				if(this.show)
					this.inputType=false;
				else
					this.inputType=true;
			}
		}
	}
</script>

<style lang="scss" scoped>
.color{
	color: $uni-text-color;
	font-size: $uni-font-size-lg;
	background-color: $uni-bg-color;
	display: flex;
	flex-direction: row;
	align-items: center;
	width: 100vw;
	padding: 10px;
}
image{
	position: absolute;
	width: 20px;
	height: 20px;
}
.dot{
	position: absolute;
	width: 10px;
	height: 10px;
	border-radius: 50%;
	border:solid 1px $uni-bg-color-darkg;
}
</style>
