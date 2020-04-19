<template>
	<view class="account">
		<click-card title="账号" :subtitle="userId" />
		<click-card title="手机号" :subtitle="telephone" arrow=true @click.native="turnTo('/pages/change_mobile_phone/change_mobile_phone')"/>
		<click-card title="密码" arrow=true @click.native="turnTo('/pages/change_password/change_password')"/>
		<click-card title="设备管理" arrow=true />
		<click-card title="安全设置" arrow=true />
		<click-card title="紧急联系人" arrow=true />
	</view>
</template>

<script>
	import clickCard from '@/components/click-card/click-card.vue'
	export default {
		data() {
			return {
				userId: '',
				username: '',
				telephone:'',
			};
		},
		components:{
			clickCard
		},
		methods:{
			turnTo:function(url){
				uni.navigateTo({
					url:url
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.account{
	background-color: $uni-bg-color-darkg;
	height: 100vh;
}
</style>
