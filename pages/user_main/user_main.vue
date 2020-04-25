<template>
	<view class="user">
		<view class="back">返回用户中心</view>
		<click-card
		title="个人主页"
		arrow="true"
		/>
		<click-card
		title="手机号码"
		:subtitle="telephone"
		arrow="true"
		/>
		<click-card
		title="手机号码"
		:subtitle="telephone"
		arrow="true"
		/>
		<click-card
		title="手机号码"
		:subtitle="telephone"
		arrow="true"
		/>
	</view>
</template>

<script>
	import clickCard from '@/components/click-card/click-card.vue'
	export default {
		data() {
			return {
				telephone:'136454546',
				class1: "background-color:red"
			};
		},
		components:{
			clickCard
		}
	}
</script>

<style lang="scss" scoped>
	.user{
		background-color: $uni-bg-color-grey;
		font-size: $uni-font-size-base;
		height: 100vh;
	}
	.back{
		
	}
	
</style>
