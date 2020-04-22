<template>
	<view class="order">
		<uniSegmentedControl :current="current" :values="title" @clickItem="onClickItem" style-type="button" active-color="#fd7e31"/>
		<view class="content">
			<view v-show="current===0">
				<view ></view>
			</view>
			<view v-show="current===1">
				
			</view>
			<view v-show="current===2">
				
			</view>
			<view v-show="current===3">
				
			</view>
			<view v-show="current===4">
				
			</view>
		</view>
	</view>
</template>

<script>
	import uniSegmentedControl from "@/components/uni-segmented-control/uni-segmented-control.vue"
	import uniCalendar from '@/components/uni-calendar/uni-calendar.vue'
	import clickCard from "../../components/click-card/click-card.vue"
	export default {
		data() {
			return {
				current:0,
				title:[
					"待接受",
					"待付款",
					"被邀请",
					"已接受",
					"已完成"
				],
				list0:[
					
				],
				list1:[
					
				],
				list2:[
					
				],
				list3:[
					
				],
				list4:[
					
				]
			};
		},
		components:{
			 uniSegmentedControl,
			 uniCalendar,
			 clickCard
		},
		 methods: {
		        onClickItem(e) {
		            if (this.current !== e.currentIndex) {
		                this.current = e.currentIndex;
		            }
		        }
		}
	}
</script>

<style lang="scss" scoped>
	.order{
		font-size: $uni-font-size-base;
	}
</style>
