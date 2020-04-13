<template>
	<view class="grade">
		<clickCard
		title="帮助者等级:"
		subtitle="15"
		/>
	</view>
</template>

<script>
	import clickCard from '@/components/click-card/click-card.vue'
	export default {
		data() {
			return {
				
			};
		},
		components:{ clickCard }
	}
</script>

<style lang="scss">
.grade{
	background-color: $uni-bg-color-darkg;
	height: 100vh;
}
</style>
