<template>
	<view class="color">
		<text :style="'padding: 0 '+ padding +' 0;'">{{title}}</text>
		<input password v-model="password" @input="change"/>
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
				password:''
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
				if(num === CString.length){
					return true;
				}
				else
					return false;
			},
			change(){
				// if(this.password.length >= 6 && this.password != this.userId){
				// }
				console.log(this.check(this.password));
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
input{
}
.dot{
	position: absolute;
	width: 10px;
	height: 10px;
	border-radius: 50%;
}
</style>
