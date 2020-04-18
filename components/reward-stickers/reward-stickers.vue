<template>
	<view>
		<uni-card
		    title="悬赏贴"
			:extra="name"
		    mode="basic"
		>
				<view v-if="title"><text>主题：{{title}}\n</text></view>
				<view v-if="service"><text>服务类型：{{service}}\n</text></view>
				<view v-if="money"><text>愿意支付金额：{{money}}\n</text></view>
				<view v-if="time"><text>服务时长：{{time}}h\n</text></view>
				<view v-if="is_online"><text>线上or线下：线上\n</text></view>
				<view v-else>
					<text>
						线上or线下：线下
						服务地点（线下）：{{ address }}\n
					</text> 
				</view>
				<text style="color: #007AFF;" @click="open">查看详情</text>
		</uni-card>
		<uni-popup ref="popup" type="center" :mask-click="false" @change="change">
			<view class="uni-tip">
				<text class="uni-tip-title">详情</text>
				<text class="uni-tip-content">{{ details }}</text>
				<view class="uni-tip-group-button">
					<text class="uni-tip-button" @click="cancel">我知道了</text>
				</view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue'
	import uniPopup from "@/components/uni-popup/uni-popup.vue"
	export default {
		name: 'rewardSticker',
		data () {
			return{};
		},
		props: {
			'title': String,
			'name': String,
			'service':String,
			'address':String,
			'money':Number,
			'time':Number,
			'is_online':{
				type:Boolean,
				default:true
			},
			'details':String
		},
		methods:{
			open(){
			    this.$refs.popup.open()
			      },
			cancel() {
				this.$refs.popup.close()
			},
			change(e) {
				console.log('是否打开:' + e.show)
			}
		},
		components: {
			uniCard,
			uniPopup
		}
	}
</script>

<style>
	/* 提示窗口 */
		.uni-tip {
			/* #ifndef APP-NVUE */
			display: flex;
			flex-direction: column;
			/* #endif */
			padding: 15px;
			width: 300px;
			background-color: #fff;
			border-radius: 10px;
		}
	
		.uni-tip-title {
			margin-bottom: 10px;
			text-align: center;
			font-weight: bold;
			font-size: 16px;
			color: #333;
		}
	
		.uni-tip-content {
			/* padding: 15px;
	*/
			font-size: 14px;
			color: #666;
		}
	
		.uni-tip-group-button {
			/* #ifndef APP-NVUE */
			display: flex;
			/* #endif */
			flex-direction: row;
			margin-top: 20px;
		}
	
		.uni-tip-button {
			flex: 1;
			text-align: center;
			font-size: 14px;
			color: #3b4144;
		}
	
</style>