<template>
	<view class="mobile">
		<view class="imageBoard">
			<image src="../../static/image/user/phone.png" style="width: 70px; height: 120px;"/>
			<uni-icons size="50" type="clear" color="red" v-if="!telephone.trim()"/>
			<uni-icons size="50" type="checkbox-filled" color="#55d018" v-if="telephone.trim()"/>
		</view>
		<text v-if="telephone.trim()" style="transform: translateY(-25px);">绑定的手机号：{{telephone}}</text>
		<text v-else style="color: #999;transform: translateY(-25px);" @click.native="turnTo()">您未绑定手机号，点击跳转</text>
		<view class="button">更换手机号</view>
	</view>
</template>

<script>
	import uniIcons from '@/components/uni-icons/uni-icons.vue'
	export default {
		data() {
			return {
				telephone:'137575443'
			};
		},
		components:{
			uniIcons
		},
		methods:{
			turnTo(url){
				uni.navigateTo({
					url:url
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.mobile{
	display: flex;
	flex-direction: column;
	align-items: center;
	height: 100vh;
	background-color: $uni-bg-color-grey;
	color: $uni-text-color;
	font-size: $uni-font-size-lg;
}
.imageBoard{
	margin-top: 8 * $space;
}
uni-icons{
	display: flex;
	flex-direction: column;
	align-items: center;
	transform: translate(25px,-55px);
}
.button{
	font-size: $uni-font-size-llg;
	width: 80vw;
	height: 35px;
	background-color: $green;
	color: white;
	display: flex;
	flex-direction: column;
	justify-content: center;
	align-items: center;	
	border-radius: 1vw;
}
</style>
