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
		</uni-card>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue';
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
			}
			},
		components: {
			uniCard
		}
	}
</script>
