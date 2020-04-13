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
				<uniIcons type="arrowright" color="#fff" size="25"></uniIcons>
			</view>
		</view>
		<view class="content">
			<clickCard style="margin-bottom: 15px;"
			:title="realNameTitle"
			:subtitle="realNameSubtitle"
			:badgeType="realNameBadgeType"
			:messageNum="realNameMessageNum"
			:dot="realNameDot"
			arrow=true
			/>
			<clickCard style="margin-bottom: 15px;"
			iconType="contact-filled"
			iconSize="25"
			iconColor="#3193fd"
			title="等级"
			subtitle="100积分待领取"
			dot= true
			@click.native="turnTo('/pages/grade/grade')"
			arrow=true
			/>
			<clickCard
			iconType="cart-filled"
			iconSize="22"
			iconColor="#fd7e31"
			title="订单"
			arrow=true
			/>
			<clickCard
			iconType="list"
			iconSize="22"
			iconColor="#a79af4"
			 title="资产"
			arrow=true
			/>
			<clickCard 
			iconType="home-filled"
			iconSize="22"
			iconColor="#fce94c"
			title="个人信息"
			subtitle="查看详情"
			arrow=true
			/>
			<clickCard 
			iconType="gear-filled"
			iconSize="22"
			iconColor="#bc4cfc"
			title="设置"
			arrow=true
			/>
		</view>
	</view>
</template>

<script>
	import clickCard from '@/components/click-card/click-card.vue'
	import uniIcons from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {
				username: '未设置名称',
				usertel: '无',
				userimage: '../../static/image/user/userimage.jpg',
				realNameTitle: '请完成实名认证,体验更多服务',
				realNameSubtitle: null,
				realNameBadgeType:'error',
				realNameMessageNum: 1,
				realNameDot:false
			};
		},
		components:{ clickCard, uniIcons },
		methods:{
			turnTo:(urls)=>{
				uni.navigateTo({
					url:urls
				})
				console.log('hello')
			}
		}
	}
</script>

<style lang="scss" socped>
	.user {
		background-color: $uni-bg-color-darkg;
		height: 100vh;
	}
	.head {
		background-color: #007AFF;
		height: 12vh;
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
	.content{
		display: flex;
		flex-direction: column;
	}
</style>