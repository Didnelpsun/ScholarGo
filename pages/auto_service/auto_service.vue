<template>
	<view>
		<view>
		<uni-grid :column="2">
		    <uni-grid-item>			
				<view class="indexboard" style="background-color: #7e92dc;">
					<view class="indexborder">
						<image src="../../static/image/index/answeer.png" class="indexImg"></image>
					</view>
					<text>我要退款</text>
				</view>
		    </uni-grid-item>
		    <uni-grid-item>	
				<view class="indexboard" style="background-color: #9477f3;">
		        	<view class="indexborder">
		                <image src="../../static/image/index/ask.png" class="indexImg"></image>
					</view>
					<text>催服务</text>
				</view>
		    </uni-grid-item>
		</uni-grid>
		</view>
		<view style="margin-bottom: 10px;">
			<click-card
			:title="schedule.Title"
			:subtitle="schedule.Subtitle"
			:badgeType="schedule.BadgeType"
			:messageNum="schedule.MessageNum"
			:dot="schedule.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
		</view>
		<view>
			<click-card
			:title="serviceAttitude.Title"
			:subtitle="serviceAttitude.Subtitle"
			:badgeType="serviceAttitude.BadgeType"
			:messageNum="serviceAttitude.MessageNum"
			:dot="serviceAttitude.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
			<click-card 
			:title="trouble.Title"
			:subtitle="trouble.Subtitle"
			:badgeType="trouble.BadgeType"
			:messageNum="trouble.MessageNum"
			:dot="trouble.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
			<click-card
			:title="afterSalesQuestion.Title"
			:subtitle="afterSalesQuestion.Subtitle"
			:badgeType="afterSalesQuestion.BadgeType"
			:messageNum="afterSalesQuestion.MessageNum"
			:dot="afterSalesQuestion.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
			<click-card
			:title="refund.Title"
			:subtitle="refund.Subtitle"
			:badgeType="refund.BadgeType"
			:messageNum="refund.MessageNum"
			:dot="refund.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
			<click-card 
			:title="serviceQuestion.Title"
			:subtitle="serviceQuestion.Subtitle"
			:badgeType="serviceQuestion.BadgeType"
			:messageNum="serviceQuestion.MessageNum"
			:dot="serviceQuestion.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
			<click-card 
			:title="pendingIssue.Title"
			:subtitle="pendingIssue.Subtitle"
			:badgeType="pendingIssue.BadgeType"
			:messageNum="pendingIssue.MessageNum"
			:dot="pendingIssue.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
			<click-card
			:title="activityDescription.Title"
			:subtitle="activityDescription.Subtitle"
			:badgeType="activityDescription.BadgeType"
			:messageNum="activityDescription.MessageNum"
			:dot="activityDescription.Dot"
			@click.native="turnTo('/pages/real_name/real_name')"
			arrow=true
			/>
		</view>
	</view>
</template>

<script>
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	import clickCard from "@/components/click-card/click-card.vue"
	export default {
		components: {
			uniGrid,
			uniGridItem,
			uniList,
			uniListItem
			},
		data() {
			return {
				schedule:{
					Title:"服务进度",
					Subtitle: null,
					BadgeType:'success',
					MessageNum:null,
					Dot:false,
				},serviceAttitude:{
					Title:"服务态度",
					Subtitle: null,
					BadgeType:'success',
					MessageNum:null,
					Dot:false,
				},trouble:{
					Title:"常见问题",
					Subtitle: null,
					BadgeType:'success',
					MessageNum: null,
					Dot:false,
				},afterSalesQuestion:{
					Title:"售后问题",
					Subtitle: null,
					BadgeType:'success',
					MessageNum: null,
					Dot:false,
				},refund:{
					Title:"退款",
					Subtitle: null,
					BadgeType:'success',
					MessageNum: 1,
					Dot:false,
				},serviceQuestion:{
					Title:"服务问题",
					Subtitle: null,
					BadgeType:'success',
					MessageNum: null,
					Dot:false,
				},pendingIssue:{
					Title:"待处理问题",
					Subtitle: null,
					BadgeType:'success',
					MessageNum: 1,
					Dot:false,
				},activityDescription:{
					Title:"活动介绍",
					Subtitle: null,
					BadgeType:'success',
					MessageNum: 2,
					Dot:false,
				}	
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.indexboard {
		width: 50vw;
		height: 50vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		color: $uni-text-color-inverse;
		font-size: $uni-font-size-llg;
	}
	
	.indexborder {
		width: 80px;
		height: 80px;
		background-color: $uni-bg-color;
		border-radius: 50%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin-left: 2 * $space;
	}
	
	.indexImg {
		width: 40px;
		height: 40px;
	}

</style>
