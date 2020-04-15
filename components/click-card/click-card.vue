<template>
	<view class="clickCard">
		<view class="view">
			<uniIcons :type="iconType" :color="iconColor" :size="iconSize" v-if="iconType"/>
			<text>
				{{title}}
			</text>
		</view>
		<view class="view">
			<text class="sub" v-if="subtitle!=null">
				{{subtitle}}
			</text>
			<uniBadge :text="messageNum" :type="badgeType" size="small" v-if="messageNum" />
			<view class="dot" v-if="dot"></view>
			<uniIcons type="checkmarkempty" color="#a6e22e" size="20" v-if="check"></uniIcons>
			<uniIcons type="arrowright" color="#999" size="20" v-if="arrow"></uniIcons>
		</view>
	</view>
</template>

<script>
	import uniBadge from "@/components/uni-badge/uni-badge.vue"
	import uniIcons from "@/components/uni-icons/uni-icons.vue"
	export default {
		data() {
			return {};
		},
		props: {
			'iconType':{
				type:String,
				default:null
			},
			'iconSize':{
				type:Number,
				default:25
			},
			'iconColor':{
				type:String,
				default:''
			},
			'title':{
				type:String,
				default:''
			},
			'subtitle':{
				type:String,
				default:null
			},
			'messageNum':{
				type:Number,
				default:0
			},
			'badgeType':{
				type:String,
				default:'error'
			},
			'dot':{
				type:Boolean,
				default:false
			},
			'check':{
				type:Boolean,
				default:false
			},
			'arrow':{
				type:Boolean,
				default:false
			}
		},
		components: {
			uniBadge,
			uniIcons
		}
	}
</script>

<style lang="scss" socped>
	.clickCard {
		background-color: $uni-bg-color;
		width: 100vw;
		height: 45px;
		border: solid 1px $uni-bg-color-grey;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		padding: 0 $space 0;
		color: $uni-text-color;
		align-items: center;
		font-size: $uni-font-size-base;
	}
	.view{
		display: flex;
		flex-direction: row;
		align-items: center;
		padding-right: 10px;
		text{
			margin: 0 10px 0 5px;
			text-align: center;
		}
	}
	.sub {
		color: $uni-text-color-grey;
	}
	.dot{
		width: 8px;
		height: 8px;
		background-color: red;
		border-radius: 50%;
	}
</style>
