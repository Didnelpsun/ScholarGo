<template>
	<view class="set">
		<view class="userBoard">
			<view class="user">
				<view style="display: flex;flex-direction: row;align-items: flex-start;">
					<image :src="imgUrl" />
					<text style="margin-top: 5px;">{{username}}</text>
				</view>
				<view class="button">
					<text>退出</text>
					<uni-icons type="arrowdown" size="15" color="#f5f5f5" style="margin-left: 5px;" />
				</view>
			</view>
		</view>
		<click-card title="账号与安全" arrow=true @click.native="turnTo('/pages/account_and_safe/account_and_safe')" />
		<click-card title="隐私" arrow=true />
		<click-card title="通用" arrow=true @click.native="turnTo('/pages/currency/currency')" />
		<click-card title="反馈" arrow=true />
		<click-card title="关于本产品" arrow=true @click.native="turnTo('/pages/about_us/about_us')" />
	</view>
</template>

<script>
	import uniIcons from '@/components/uni-icons/uni-icons.vue'
	import clickCard from '@/components/click-card/click-card.vue'
	export default {
		data() {
			return {
				username: '未设置名称',
				imgUrl: '../../static/image/user/userimage.jpg'
			};
		},
		components: {
			uniIcons,
			clickCard
		},
		methods: {
			turnTo(url) {
				uni.navigateTo({
					url: url
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.set {
		background-color: $uni-bg-color-grey;
		height: 100vh;
	}

	.userBoard {
		background-color: $uni-bg-color-grey;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 20vh;
		font-size: $uni-font-size-base;
	}

	.user {
		height: 15vh;
		width: 80vw;
		background-color: $uni-bg-color;
		border-radius: 3vw;
		color: $uni-text-color-grey;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		padding: $space 2 * $space $space;
	}

	image {
		width: 10vh;
		height: 10vh;
		margin-right: $space;
		border-radius: 1vw;
	}

	.button {
		padding: $space 2 * $space $space;
		border: solid 1px $uni-bg-color-darkg;
		border-radius: 1vw;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
	}
</style>
