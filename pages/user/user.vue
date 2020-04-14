<template>
	<view class="user">
		<view class="head" @click="turnTo('/pages/user_main/user_main')">
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
			:title="realName.Title"
			:subtitle="realName.Subtitle"
			:badgeType="realName.BadgeType"
			:messageNum="realName.MessageNum"
			:dot="realName.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
			<clickCard style="margin-bottom: 15px;"
			iconType="contact-filled"
			iconSize="25"
			iconColor="#3193fd"
			title="等级"
			:subtitle="grade.Subtitle"
			:badgeType="grade.BadgeType"
			:messageNum="grade.MessageNum"
			:dot= "grade.Dot"
			@click.native="turnTo('/pages/grade/grade')"
			arrow=true
			/>
			<clickCard
			iconType="cart-filled"
			iconSize="22"
			iconColor="#fd7e31"
			title="订单"
			:subtitle="order.Subtitle"
			:badgeType="order.BadgeType"
			:messageNum="order.MessageNum"
			:dot= "order.Dot"
			@click.native="turnTo('/pages/order/order')"
			arrow=true
			/>
			<clickCard
			iconType="list"
			iconSize="22"
			iconColor="#bc4cfc"
			title="资产"
			:subtitle="property.Subtitle"
			:badgeType="property.BadgeType"
			:messageNum="property.MessageNum"
			:dot= "property.Dot"
			@click.native="turnTo('/pages/property/property')"
			arrow=true
			/>
			<clickCard 
			iconType="gear-filled"
			iconSize="22"
			iconColor="#f9e263"
			title="设置"
			:subtitle="set.Subtitle"
			:badgeType="set.BadgeType"
			:messageNum="set.MessageNum"
			:dot= "set.Dot"
			@click.native="turnTo('/pages/set/set')"
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
				realName:{
					Title: '请完成实名认证,体验更多服务',
					Subtitle: null,
					BadgeType:'error',
					MessageNum: 1,
					Dot:false,
				},
				grade:{
					Subtitle: '100积分待领取',
					BadgeType:null,
					MessageNum: null,
					Dot:true,
				},
				order:{
					Subtitle: null,
					BadgeType:null,
					MessageNum: null,
					Dot:null,
				},
				property:{
					Subtitle: null,
					BadgeType:null,
					MessageNum: null,
					Dot:null,
				},
				set:{
					Subtitle: null,
					BadgeType:null,
					MessageNum: null,
					Dot:null,
				}
			};
		},
		components:{ clickCard, uniIcons },
		methods:{
			turnTo:(urls)=>{
				uni.navigateTo({
					url:urls
				})
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