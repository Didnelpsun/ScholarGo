<template>
	<view class="index">
		<view class="search">
			<image src="../../static/image/index/search.png" class="searchimg"></image>
			<input type="text" placeholder="请输入关键字" class="searchinput" confirm-type="search" @focus="startSearch" @blur="startSearch" />
			<view class="calendarholder" v-show="calendarShow" @click="TurntoRegister">
				<image src="../../static/image/index/calendar.png" class="calendar"></image>
				<text class="calendarnum">{{calendarNum}}</text>
			</view>
		</view>
		<view class="searchboard" ref="searchboard" v-bind:style="{height:height+'vh'}">
			<view v-show="dataShow">
				<view class="hot">
					<image src="../../static/image/index/fire.png" class="hotImg"></image>
					<image src="../../static/image/index/hot.png" class="hotImg"></image>
				</view>
				<view class="history">
					<text class="historyText">搜索记录：</text>
				</view>
			</view>
		</view>
		<view class="content">
			<adverSwiper/>
			<view class="indexboard" style="background-color: #7e92dc;">
				<text>我要求助</text>
				<view class="indexborder">
					<image src="../../static/image/index/answeer.png" class="indexImg"></image>
				</view>
			</view>
			<view class="indexboard" style="background-color: #9477f3;">
				<text>我愿帮助</text>
				<view class="indexborder">
					<image src="../../static/image/index/ask.png" class="indexImg"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import adverSwiper from '../../components/adver-swiper/adver-swiper.vue'
	import uniCalendar from '@/components/uni-calendar/uni-calendar.vue'
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
			adverSwiper
		},
		methods: {
			startSearch: function() {
				let _this = this;
				_this.calendarShow = !_this.calendarShow;
				let height = _this.height;
				if (height < 100) {
					_this.timer = setInterval(function() {
						if (height <= 100) {
							height += 10;
							_this.height = height;
							// console.log(_this.height);
						} else
							clearInterval(_this.timer)
					}, 10)
					_this.dataShow = !_this.dataShow;
				} 
				else {
					_this.dataShow = !_this.dataShow;
					if (height >= 100) {
						_this.timer = setInterval(function() {
							if (height >= 0) {
								height -= 10;
								_this.height = height;
								// console.log(_this.height);
							} else
								clearInterval(_this.timer)
						}, 10)
					}
				}
			},
			TurntoRegister: function() {
				uni.navigateTo({
					url: '/pages/register/register'
				})
			}
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

	.search {
		position: fixed;
		background-color: $uni-bg-color-grey;
		width: 100vw;
		height: 6 * $space;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		z-index: 10;
	}

	.searchimg {
		width: 4 * $space;
		height: 4 * $space;
		margin: 0 $space 0;
	}

	.searchinput {
		width: 90vw;
		height: 6 * $space - 2 * $space;
		background-color: $uni-bg-color;
		border-radius: 2vw;
		padding-left: $space;
		margin: 0 $space 0;
		border: solid 1px #eee;
	}

	.calendarholder {
		position: relative;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.calendar {
		width: 4 * $space;
		height: 4 * $space;
		margin: 0 $space 0;
	}

	.calendarnum {
		position: fixed;
		padding-top: $space - 2px;
		font-size: $uni-font-size-sssm;
	}

	.searchboard {
		position: fixed;
		width: 100vw;
		background-color: $uni-bg-color;
		display: flex;
		flex-direction: column;
		padding-top: 6 * $space;
		z-index: 9;
	}

	.hot {
		// background-color: blue;
		margin: 4 * $space 4 * $space 0;
		display: flex;
		flex-direction: row;
	}

	.hotImg {
		width: 4 * $space;
		height: 4 * $space;
		margin-right: $space;
	}

	.history {
		margin: 4 * $space 4 * $space 0;
	}

	.historyText {
		font-size: $uni-font-size-lg;
		font-weight: bold;
	}

	.content {
		// height: 150vh;
	}

	.indexboard {
		width: 100vw;
		height: 50vh;
		display: flex;
		flex-direction: row;
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
		flex-direction: row;
		justify-content: center;
		align-items: center;
		margin-left: 2 * $space;
	}

	.indexImg {
		width: 40px;
		height: 40px;
	}
</style>
