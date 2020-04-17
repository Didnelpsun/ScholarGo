<template>
	<view class="index">
		<view class="content">
			<adver-swiper/>
			<uni-grid :column="2">
			    <uni-grid-item>
					<navigator url="../want_help/want_help" hover-class="navigator-hover">
					<view class="indexboard" style="background-color: #7e92dc;">
						<text>学习</text>
						<view class="indexborder">
							<image src="../../static/image/index/answeer.png" class="indexImg"></image>
						</view>
					</view>
					</navigator>
			    </uni-grid-item>
			    <uni-grid-item>	
					<navigator url="../want_help/want_help" hover-class="navigator-hover">
					<view class="indexboard" style="background-color: #9477f3;">
			        	<text>生活</text>
			        	<view class="indexborder">
		                    <image src="../../static/image/index/ask.png" class="indexImg"></image>
						</view>
					</view>
					</navigator>
			    </uni-grid-item>
			</uni-grid>
		</view>
	</view>
</template>

<script>
	import adverSwiper from '../../components/adver-swiper/adver-swiper.vue'
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
			adverSwiper,
			uniGrid,
			uniGridItem
		},
		methods: {
			TurntoRegister: function() {
				uni.navigateTo({
					url: '/pages/register/register'
				})
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
		width: 50vw;
		height: 70vh;
		display: flex;
		justify-content: center;
		align-items: center;
		color: $uni-text-color-inverse;
		font-size: $uni-font-size-llg;
	}

	.indexborder {
		width: 60px;
		height: 60px;
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
