<template>
	<view class="footer">
		<view class="footer-center">
			<input class="input-text" type="text" v-model="inputValue"></input>
		</view>
		<view class="footer-right" @tap="sendMessge">
			<view id='msg-type'>发送</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "chatInput",
		data() {
			return {
				inputValue: ''
			}
		},
		methods: {
			sendMessge: function () {
				var that = this;
				if (that.inputValue.trim() == '') {
					that.inputValue = '';
				} else {
					//点击发送按钮时，通知父组件用户输入的内容
					this.$emit('send-message', {
						type: 'text',
						content: that.inputValue
					});
					that.inputValue = '';
				}
			}
		}
	}
</script>

<style>

	.footer {
		display: flex;
		flex-direction: row;
		width: 100%;
		height: 60px;
		min-height: 60px;
		border-top: solid 1px #bbb;
		overflow: hidden;
		background-color: #fafafa;
	}
	.footer-right {
		width: 80px;
		height: 60px;
		display: flex;
		justify-content: center;
		align-items: center;
		color: #1482D1;
	}
	.footer-center {
		flex: 1;
		height: 60px;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.footer-center .input-text {
		flex: 1;
		background: #fff;
		border: solid 1px #ddd;
		padding: 3px !important;
		font-family: verdana !important;
		overflow: hidden;
		border-radius: 15px;
		margin-left: 10px;
	}
</style>
