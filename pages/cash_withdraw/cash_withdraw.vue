<template>
	<view class="cash_withdraw">
		<capitalTurn
		buttonType="提现"
		/>
	</view>
</template>

<script>
	import capitalTurn from "@/components/capital-turn/capital-turn.vue"
	export default {
		data() {
			return {}
		},
		components:{
			capitalTurn
		}
	}
</script>

<style lang="scss" scoped>
.cash_withdraw{
}
</style>
