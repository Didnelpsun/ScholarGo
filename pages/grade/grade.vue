<template>
	<view class="grade">
		<view class="space" />
		<click-card title="帮助者等级:" :subtitle="helpGrade" />
		<click-card title="帮助次数:" :subtitle="helpNum" />
		<view class="textView">
			<text>所享受待遇：</text>
			<text class="textMain">{{text1}}</text>
		</view>
		<view class="space" />
		<click-card title="求助者等级:" :subtitle="helpGrade" />
		<click-card title="求助次数:" :subtitle="helpNum" />
		<view class="textView">
			<text>所享受待遇：</text>
			<text class="textMain">{{text2}}</text>
		</view>
	</view>
</template>

<script>
	import clickCard from '@/components/click-card/click-card.vue'
	export default {
		data() {
			return {
				helpGrade: 0,
				helpNum: 0,
				text1: '',
				askGrage: 0,
				askNum: 0,
				text2: ''
			};
		},
		components: {
			clickCard
		}
	}
</script>

<style lang="scss" socped>
	.grade{
		background-color: $uni-bg-color-grey;
		height: 100vh;
	}
	.space {
		height: 6 * $space;
	}

	.textView {
		background-color: $uni-bg-color;
		font-size: $uni-font-size-base;
		color: $uni-text-color;
		padding: 10px;
		word-wrap: break-word;
		word-break: break-all;
		line-height: 1.5em;
	}

	.textMain {
		color: $uni-text-color-grey;
	}
</style>
