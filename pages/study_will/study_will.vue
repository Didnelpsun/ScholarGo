<template>
	<view class="index">
		<view class="content">
			<adver/>
			<uni-grid :column="2">
				<view @click="TurntoReward()">
			    <uni-grid-item >
					<view class="indexboard" style="background-color: #7e92dc;">
						<text>发布悬赏贴\n等待帮助者接单</text>
					</view>
			    </uni-grid-item>
				</view>
				<view @click="TurntoFind()">
			    <uni-grid-item>	
					<view class="indexboard" style="background-color: #9477f3;">
			        	<text>自主寻找\n立刻解决问题</text>
						<uni-icons type="contact" size="30"></uni-icons>
					</view>
			    </uni-grid-item>
				</view>
			</uni-grid>
		</view>
	</view>
</template>

<script>
	import adver from '../../components/adver/adver.vue'
	import uniCalendar from '@/components/uni-calendar/uni-calendar.vue'
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	export default {
		data() {
			return {
				calendarShow: true,
				dataShow: false,
				searchboard: 'searchboard',
				height: 0,
				timer: null
			}
		},
		onLoad() {

		},
		components: {
			uniCalendar,
			adver,
			uniGrid,
			uniGridItem
		},
		methods: {
			TurntoReward: function() {
				uni.switchTab({
				    url: '/pages/reward/reward'
				});
			},
			TurntoFind: function() {
				uni.switchTab({
				    url: '/pages/find/find'
				});
			},
		},
		computed: {
			calendarNum: function() {
				let date = new Date();
				return date.getDate();
			}
		},
		mounted() {}
	}
</script>

<style lang="scss">
	.index {
		font-size: $uni-font-size-base;
	}

	.content {
		// height: 150vh;
	}

	.indexboard {
		margin: 40px 20px;
		width: 40vw;
		height: 30vh;
		display: flex;
		justify-content: center;
		align-items: center;
		color: $uni-text-color-inverse;
		font-size: $uni-font-size-llg;
	}

	.indexImg {
		width: 40px;
		height: 40px;
	}
</style>
