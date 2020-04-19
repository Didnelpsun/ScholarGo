<template>
	<view class="emergency">
		<image class="mainImg" src="../../static/image/user/people.png" />
		<text style="font-size: 15px; margin-top: 10px;">紧急联系人</text>
		<text class="grey">您可以通过下面的搜索框来根据用户的id来查找添加的紧急联系人，在你点击确认后，会自动向该用户发送请求，对方接受则被作为您的紧急联系人，如果拒绝则无法成为。</text>
		<!-- <uni-search-bar/> -->
		<view class="contactBar">
			<view class="contact" style="border: dashed 2px #888; color: #888; font-size: 30px; ">
				<text style="transform: translateY(-2px);">+</text>
			</view>
			<view class="contact" style="border: dashed 2px #888; color: #888; font-size: 40px; ">
				<text style="transform: translateY(-3px);">-</text>
			</view>
		</view>
	</view>
</template>

<script>
	import uniSearchBar from '@/components/uni-search-bar/uni-search-bar.vue'
	export default {
		data() {
			return {
				contactList:[
					{
						name:'',
						img:''
					}
				]
			};
		},
		components:{
			uniSearchBar
		}
	}
</script>

<style lang="scss" scoped>
	.emergency{
		height: 100vh;
		background-color: $uni-bg-color-darkg;
		font-size: $uni-font-size-lg;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.mainImg{
		margin-top: 4 * $space;
		width: 25vw;
		height: 25vw;
	}
	.grey{
		font-size: $uni-font-size-sm;
		color:$uni-text-color-grey;
		margin: 2 * $space;
	}
	.contactBar{
		margin: 2 * $space;
		display: flex;
		flex-direction: row;
		width: 100vw;
		// justify-content: start;
	}
	.contact{
		width: 10vw;
		height: 10vw;
		border-radius: 1vw;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin: 10px;
	}
</style>
