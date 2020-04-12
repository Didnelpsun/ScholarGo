<template>
	<view class="user">
		<view class="head">
			<text class="fristText">用户中心</text>
			<view class="userBoard">
				<image class="userImg" :src="userimage"></image>
				<view class="userText">
					<text>{{username}}</text>
					<text class="userTel">{{usertel}}</text>
				</view>
				<image style="width: 20px;height: 20px;" src="../../static/image/user/arrow.png"></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				username: '未设置名称',
				usertel: '无',
				userimage: '../../static/image/user/userimage.jpg'
			};
		}
	}
</script>

<style lang="scss">
	.user {
		background-color: $uni-bg-color-darkg;
		height: 100vh;
	}
	.head {
		background-color: #007AFF;
		height: 15vh;
		color: $uni-text-color-inverse;
		padding: 4 * $space;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
	}

	.fristText {
		font-size: $uni-font-size-lg;
	}

	.userBoard {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		margin-top: $space;
	}

	.userImg {
		width: 8 * $space;
		height: 8 * $space;
		border-radius: 1vw;
		border: solid 1px #6cb1fc;
	}

	.userText {
		margin: 2 * $space;
		width: 70vw;
		font-size: $uni-font-size-base;
		display: flex;
		flex-direction: column;
		justify-content: space-around;
	}

	.userTel {
		width: auto;
		border-radius: 2vw;
		margin-top: $space;
	}
</style>
