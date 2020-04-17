<template>
	<view class="index">
		<search-bar></search-bar>
		<view class="content">
			<adver-swiper/>
			<navigator url="../want_help/want_help" hover-class="navigator-hover">
				<view class="indexboard" style="background-color: #7e92dc;">
					<text>我要求助</text>
					<view class="indexborder">
						<image src="../../static/image/index/answeer.png" class="indexImg"></image>
					</view>
				</view>
			</navigator>
			<navigator url="../will_help/will_help" hover-class="navigator-hover">
				<view class="indexboard" style="background-color: #9477f3;">
					<text>我愿帮助</text>
					<view class="indexborder">
						<image src="../../static/image/index/ask.png" class="indexImg"></image>
					</view>
				</view>
			</navigator>
		</view>
	</view>
</template>

<script>
	import adverSwiper from '../../components/adver-swiper/adver-swiper.vue'
	import searchBar from '../../components/search-bar/search-bar.vue'
	export default {
		data() {
			return {}
		},
		onLoad: function(option) { //option为object类型，会序列化上个页面传递的参数
			// console.log(option.id); //打印出上个页面传递的参数。
			// console.log(option.name); //打印出上个页面传递的参数。
		},
		components: {
			adverSwiper,
			searchBar
		},
		methods: {

			TurntoRegister: function() {
				uni.navigateTo({
					url: '/pages/register/register'
				})
			}
		},

		mounted() {}
	}
</script>

<style lang="scss" socped>
	.index {
		font-size: $uni-font-size-base;
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
