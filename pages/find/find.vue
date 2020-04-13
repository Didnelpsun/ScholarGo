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
		<view class="cardboard">
			<uni-card
			    extra="擅长领域:"
				title="小红"
			    mode="style"
				:is-shadow="true"
				thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg"
			    note="帮助者等级"
			>
			那是一个秋意盎然、金风送爽的日子，我和父母一起来到了位于上师大旁的康健园。一踏进公园，一股浓郁的桂香扑鼻而来，泌人心脾,让我心旷神怡，只见一朵朵开得正烈的金色桂花，迎风而立，仿佛在向我招手。我们追着这桂香，走进了清幽的公园。
			</uni-card>
			<uni-card
			    extra="擅长领域:"
				title="小明"
			    mode="style"
				:is-shadow="true"
				thumbnail="https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg"
			    note="帮助者等级"
			>
			那是一个秋意盎然、金风送爽的日子，我和父母一起来到了位于上师大旁的康健园。一踏进公园，一股浓郁的桂香扑鼻而来，泌人心脾,让我心旷神怡，只见一朵朵开得正烈的金色桂花，迎风而立，仿佛在向我招手。我们追着这桂香，走进了清幽的公园。
			</uni-card>
		</view>
	</view>
</template>

<script>
	import adverSwiper from '../../components/adver-swiper/adver-swiper.vue'
	import uniCalendar from '@/components/uni-calendar/uni-calendar.vue'
	import uniCard from '@/components/uni-card/uni-card.vue'
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
		onLoad: function (option) { //option为object类型，会序列化上个页面传递的参数
		        console.log(option.id); //打印出上个页面传递的参数。
		        console.log(option.name); //打印出上个页面传递的参数。
		    },
		components: {
			uniCalendar,
			adverSwiper,
			uniCard
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
		// position: fixed;
		background-color: $uni-bg-color-grey;
		width: 100vw;
		height: 6 * $space;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		align-items: center;
		// z-index: 10;
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
		// position: fixed;
		padding-top: $space - 2px;
		font-size: $uni-font-size-sssm;
	}

	.searchboard {
		// position: fixed;
		width: 100vw;
		background-color: $uni-bg-color;
		display: flex;
		flex-direction: column;
		padding-top: 6 * $space;
		z-index: 9;
		margin-bottom: 10px;
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
