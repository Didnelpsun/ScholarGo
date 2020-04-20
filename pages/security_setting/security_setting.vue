<template>
	<view class="security">
		<click-card
		title="微信号"
		:subtitle="weixin"
		/>
		<click-card
		title="QQ号"
		:subtitle="qq"
		/>
		<click-card
		title="邮箱"
		:subtitle="email"
		/>
	</view>
</template>

<script>
	import clickCard from '@/components/click-card/click-card.vue'
	export default {
		data() {
			return {
				weixin:'',
				qq:'',
				email:''
			};
		},
		components:{
			clickCard
		}
	}
</script>

<style lang="scss" scoped>
	.security{
		height: 100vh;
		background-color: $uni-bg-color-grey;
	}
</style>
