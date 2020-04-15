<template>
	<view>
		<view class="search">
			<image src="../../static/image/index/search.png" class="searchimg"></image>
			<input type="text" placeholder="请输入关键字" class="searchinput" confirm-type="search" @focus="startSearch" @blur="startSearch" />
			<view class="calendarholder" @click="TurntoRegister">
				<image src="../../static/image/index/calendar.png" class="calendar"  v-show="calendarShow"></image>
				<text class="calendarnum"  v-show="calendarShow">{{calendarNum}}</text>
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
		<view class="space" style="height: 40px;"/>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				calendarShow: true,
				dataShow: false,
				searchboard: 'searchboard',
				height: 0,
				timer: null
			};
		},
		methods: {
			startSearch: function() {
				this.calendarShow = !this.calendarShow;
				let _this = this;
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
				} else {
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
			TurntoRegister:function(){
				uni.navigateTo({
					url:'/pages/register/register'
				})
			}
		},
		computed: {
			calendarNum: function() {
				let date = new Date();
				return date.getDate();
			}
		},
	}
</script>

<style lang="scss" scoped>
	.search {
		position: fixed;
		background-color: $uni-bg-color-grey;
		width: 100vw;
		height: 8 * $space;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		z-index: 10;
	}

	.searchimg {
		width: 6 * $space;
		height: 5 * $space;
		margin: 0 $space 0;
	}

	.searchinput {
		width: 90vw;
		height: 8 * $space - 2 * $space;
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
		width: 6 * $space;
		height: 6 * $space;
		margin: 0 $space 0;
	}

	.calendarnum {
		position: fixed;
		padding-top: $space - 2px;
		font-size: $uni-font-size-sm;
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
</style>
