<script>
	import chatInput from '../../components/chat_input/chat_input.vue';
	import messageShow from '../../components/message_show/message_show.vue';
	
	export default {
		data() {
			return {
				style: {
					pageHeight: 0,
					contentViewHeight: 0,
					footViewHeight: 90,
					mitemHeight: 0,
				},
				scrollTop: 0,
				messages: [{
					user: 'home',
					type: 'head', //input,content 
					content: '你好!'
				}]
			}
		},
		mounted() {
		    this.scrollToBottom()
		    },
		updated() {
		    this.scrollToBottom()
		    },
		components: {
			chatInput,
			messageShow
		},
		created: function () { 
			const res = uni.getSystemInfoSync();
			this.style.pageHeight = res.windowHeight;
			this.style.contentViewHeight = res.windowHeight - uni.getSystemInfoSync().screenWidth / 750 * (100); //像素
		},
		methods: {
			getInputMessage: function (message) { //获取子组件的输入数据
				// console.log(message);
				this.addMessage('customer', message.content, false);
				this.toRobot(message.content);
			},
			addMessage: function (user, content, hasSub, subcontent) {
				var that = this;
				that.messages.push({
					user: user,
					content: content,
					hasSub: hasSub,
					subcontent: subcontent
				});
			},
			scrollToBottom: function () {
				let that = this
				let query = uni.createSelectorQuery()
				query.select('#scrollview').boundingClientRect()
				query.select('#msglistview').boundingClientRect()
				query.exec((res) => {
					// console.log(res)
					if(res[1].height > res[0].height){
						that.scrollTop = res[1].height - res[0].height
					}
				})
				// var that = this;
				// var query = uni.createSelectorQuery();
				// query.selectAll('.m-item').boundingClientRect();
				// query.select('#scrollview').boundingClientRect();
				// query.exec(function (res) {
				// 	that.style.mitemHeight = 0;
				// 	res[0].forEach(function (rect) {
				// 		// console.info(rect.height);
				// 		that.style.mitemHeight = that.style.mitemHeight + rect.height + 20;
				// 	});
				// 	if (that.style.mitemHeight > that.style.contentViewHeight) {
				// 		that.scrollTop = that.style.mitemHeight - that.style.contentViewHeight;
				// 	}
				// });
			},
			toRobot: function (info) {
				this.addMessage('home', info, false);
				this.scrollToBottom();
				// console.log('request success:' + res.data.text);
				// this.addMessage('home', info, false);
				// var apiUrl = 'http://www.tuling123.com/openapi/api';
				// uni.request({
				// 	url: apiUrl,
				// 	data: {
				// 		"key": 'acfbca724ea1b5db96d2eef88ce677dc',
				// 		"info": info,
				// 		"userid": 'uni-test'
				// 	},
					// success: (res) => {
						// this.addMessage('home', res.data.text, false);
						// this.scrollToBottom();
						// console.log('request success:' + res.data.text);
				// 	},
				// 	fail: (err) => {
				// 		console.log('request fail', err);
				// 		uni.showModal({
				// 			content: err.errMsg,
				// 			showCancel: false
				// 		})
				// 	}
				// });
			}
		}
	}
</script>
<template>
	<view class="uni-column">
		<view class="content" id="content" :style="{height:style.contentViewHeight+'px'}">
			<scroll-view id="scrollview" scroll-y="true" :style="{height:style.contentViewHeight+'px'}" :scroll-with-animation="true"
			    :scroll-top="scrollTop">
				<view id="msglistview">
				<message-show v-for="(message,index) in messages" :key="index" v-bind:message="message" :index="index"></message-show>
				<view id="bottom"></view>
				</view>
			</scroll-view>
		</view>
		<view class="foot">
			<chat-input @send-message="getInputMessage" ></chat-input>
		</view>
	</view>
</template>

<style>
	.uni-column {
		display: flex;
		flex-direction: column;
		background-color: #ede8ee;
	}
	.content {
		display: flex;
		flex: 1;
		margin-bottom: 100px;	 
	}
	.foot {
		position: fixed;
		width: 100%;
		height: 60px;
		min-height: 60px;
		left: 0px;
		bottom: 0px;
		overflow: hidden;
	}
</style>
