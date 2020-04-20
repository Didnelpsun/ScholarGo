<template>
	<view class="currency">
		<click-card title="辅助功能" arrow=true />
		<click-card title="存储空间" arrow=true />
		<click-card title="文件与缓存" arrow=true />
	</view>
</template>

<script>
	import clickCard from '@/components/click-card/click-card.vue'
	export default {
		data() {
			return {
				
			};
		},
		components:{
			clickCard
		}
	}
</script>

<style lang="scss">
.currency{
	background-color: $uni-bg-color-grey;
	height: 100vh;
}
</style>
