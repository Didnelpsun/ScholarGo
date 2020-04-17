<template>
	<view class="account">
		<click-card title="账号" :subtitle="userId" />
		<click-card title="手机号" :subtitle="telphone" arrow=true />
		<click-card title="密码" arrow=true />
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
				telphone:'',
			};
		},
		components:{
			clickCard
		}
	}
</script>

<style lang="scss" scoped>
.account{
	background-color: $uni-bg-color-darkg;
	height: 100vh;
}
</style>
