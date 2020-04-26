<template>
	<view class="user">
		<view class="back" @click="swithTab()">返回用户中心</view>
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
		title="我的二维码"
		arrow="true"
		/>
		<click-card
		title="邀请有礼"
		arrow="true"
		/>
		<click-card
		title="赞助我们"
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
		},
		methods:{
			swithTab(){
				uni.switchTab({
					url:'/pages/user/user',
					fail() {
						uni.navigateBack({
						})
					}
				})
			}
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
		background-color: #007AFF;
		height: 40px;
		display: flex;
		flex-direction: row;
		align-items: center;
		color: $uni-text-color-inverse;
		padding: 2 * $space;
		font-size: $uni-font-size-lg;
	}
</style>
