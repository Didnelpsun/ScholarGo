<template>
	<view class="deposit">
		<capital-turn 
		buttonType="充值"
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
</style>
