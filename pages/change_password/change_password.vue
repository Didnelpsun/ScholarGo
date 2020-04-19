<template>
	<view class="password">
		<view class="grey small">
			不推荐使用账号的id来登入，请使用6位以上的数字、字符组合，不能只包含纯字符，且不能包含特殊字符。如果输入框提示点显示红色则表示密码不符合规范，黄色表示密码符合规范，绿色表示密码安全。
		</view>
		<view class="text grey">
			<text>账号</text>
			<text>{{userId}}</text>
		</view>
		<view class="text">
			<text>原密码</text>
			<input type="text" password v-model="oldPassword" />
		</view>
		<color-pass title="新密码"/>
		<color-pass title="确认密码"/>
		<view class="button">完成</view>
		<text>忘记密码？</text>
	</view>
</template>

<script>
	import colorPass from '@/components/color-pass/color-pass.vue'
	export default {
		data() {
			return {
				userId:'Didnelpsun',
				oldPassword:'',
				newPass1:'',
				newPass2:''
			};
		},
		components:{
			colorPass
		}
	}
</script>

<style lang="scss" scoped>
.password{
	background-color: $uni-bg-color-grey;
	height: 100vh;
	font-size: $uni-font-size-lg;
	padding: 4 * $space 0 4 * $space;
	display: flex;
	flex-direction: column;
	align-items: center;
	overflow: hidden;
}
.grey{
	color: $uni-text-color-grey;
	margin: $space 0 2 * $space;
}
.small{
	font-size: $uni-font-size-sm;
	padding: 0 2 * $space 0;
}
.text{
	display: flex;
	flex-direction: row;
	align-items: center;
	background-color: $uni-bg-color;
	padding: 2 * $space;
	width: 100vw;
	input{
		width: 75vw;
	}
}
text{
	margin: 0 10px 0;
}
.button{
	color: white; 
	background-color: #55D018;
	height: 35px;
	width: 80vw;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;
	border-radius: 1vw;
	margin: 25px 0 15px;
}
</style>
