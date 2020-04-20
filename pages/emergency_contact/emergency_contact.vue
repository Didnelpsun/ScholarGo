<template>
	<view class="emergency">
		<image class="mainImg" src="../../static/image/user/people.png" />
		<text style="font-size: 15px; margin-top: 10px;">紧急联系人</text>
		<text class="grey">您可以通过下面的搜索框来根据用户的id来查找添加的紧急联系人，在你点击确认后，
		会自动向该用户发送请求，对方接受则被作为您的紧急联系人，如果拒绝则无法成为。且下面的联系人的昵称只会显示前5个字符，多出的字符将被截断。</text>
		<view class="contactBar">
			<template v-for="contact in contactList">
				<view class="item" :key="contact.id" v-if="contact.id.trim()">
					<image class="contact" :src="contact.img"/>
					<text>{{contact.name.substring(0,5)}}</text>
					<view v-show="sub" style="transform: translate(16px,-54px);">
						<uni-icons type="clear" color="red" size="16"></uni-icons>
					</view>
				</view>
			</template>
			<view class="contact item" style="border: dashed 2px #888; color: #888; font-size: 30px; " @click="popupOpen">
				<text style="transform: translateY(-2px);">+</text>
			</view>
			<view class="contact item" style="border: dashed 2px #888; color: #888; font-size: 40px; " @click="subContact">
				<text style="transform: translateY(-3px);">-</text>
			</view>
			<uni-popup ref="popup" type="center" maskClick="false">
				<view class="searchBoard">
					<view style="height: 10px;"></view>
					<uni-search-bar placeholder="请输入用户id" radius="25" clearButton="always" cancelButton="none" />
					<scroll-view class="searchResult">
						<template>
							
						</template>
					</scroll-view>
					<view class="cancel" @click="popupClose">取消</view>
				</view>
			</uni-popup>
		</view>
	</view>
</template>

<script>
	import uniSearchBar from '@/components/uni-search-bar/uni-search-bar.vue'
	import uniPopup from '@/components/uni-popup/uni-popup.vue'
	import uniIcons from '@/components/uni-icons/uni-icons.vue'
	export default {
		data() {
			return {
				contactList:[
					{
						id:'gdfdfghhghghghf',
						name:'hegdfdfdgdgdf0',
						img:'data:image/gif;base64,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'
					}
				],
				sub:false
			};
		},
		components:{
			uniSearchBar,
			uniPopup,
			uniIcons
		},
		methods:{
			popupOpen(){
				this.$refs.popup.open();
			},
			popupClose(){
				this.$refs.popup.close();
			},
			subContact(){
				this.sub = !this.sub;
			}
		}
	}
</script>

<style lang="scss" scoped>
	.emergency{
		height: 100vh;
		background-color: $uni-bg-color-grey;
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
	.item{
		font-size: $uni-font-size-sm;
		margin: 10px;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.contact{
		width: 35px;
		height: 35px;
		border-radius: 1vw;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.searchBoard{
		width: 100vw;
		height: 100vh;
		background-color: $uni-bg-color;
	}
	.searchResult{
		margin: 2 * $space;
	}
	.cancel{
		background-color: red;
		width: 40px;
		height: 25px;
		color: $uni-text-color-inverse;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		border-radius: 1vw;
		position: absolute;
		right: 20px;
		bottom: 20px;
	}
</style>
