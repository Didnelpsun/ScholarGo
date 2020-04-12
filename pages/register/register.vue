<template>
	<view class="register">
		<view class="registerText" v-if="!registerIf">
			<icon type="clear" size="10"></icon>
			<text>今日你未签到！</text>
		</view>
		<view class="registerText" v-if="registerIf">
			<icon type="success" size="10"></icon>
			<text>今日你已签到！</text>
		</view>
		<view class="showBoard">
			<view class="registerButton" @click="registerClick" :style="buttonClick">
				<text style="color: #ddd; font-size: 15px;">签到</text>
				<text style="color:#fff; font-size: 18px;margin-top: 5px;">{{hour}}:{{minute}}:{{seconds}}</text>
			</view>
			<uni-calendar></uni-calendar>
		</view>
	</view>
</template>

<script>
	import uniCalendar from '@/components/uni-calendar/uni-calendar.vue'
	export default {
		data() {
			return {
				timer: {},
				seconds: 0,
				minute: 0,
				registerIf : false,
				buttonClick: {
					'background-color':'green'
				},
				orange:{
					'background-color':'#f77103'
				}
			};
		},
		components: {
			uniCalendar
		},
		methods: {
			setSeconds: function() {
				let date = new Date();
				this.seconds = date.getSeconds();
				this.minute = date.getMinutes();
			},
			registerClick: function(){
				if(!this.registerIf){
					this.registerIf = !this.registerIf;
					this.buttonClick = this.orange;
				}
			}
		},
		computed: {
			hour: function() {
				let date = new Date();
				return date.getHours()
			}
		},
		mounted(){
			let _this = this;
			_this.timer = setInterval(()=>_this.setSeconds(),1000);
		},
		beforeDestroy(){
			if(this.timer){
				clearInterval(this.timer)
			}
		}
	}
</script>

<style lang="scss">
	.register {
		padding: 4 * $space;
		font-size: $uni-font-size-base;
	}

	.registerText {
		color: $uni-text-color;

		text {
			margin-left: $space;
			font-weight: bold;
		}
	}

	.showBoard {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding-top: 2 * $space;
	}

	.registerButton {
		width: 120px;
		height: 120px;
		border-radius: 50%;
		background-color: rgba($color: $uni-text-color-placeholder, $alpha:1 - $uni-opacity-disabled);
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
</style>
