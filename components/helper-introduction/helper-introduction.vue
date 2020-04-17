<template>
	<view>
		<uni-card :extra="'擅长领域：' + area" :title="name" mode="style" :is-shadow="true" :thumbnail="photo"
		 :note="'帮助者等级：' + grade">
			{{notes}}
		</uni-card>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue';
	export default {
		name: 'helperIntroduction',
		data :function() {
			return{};
		},
		props: {
			'name':String,
			'photo':String,
			'area':String,
			'grade':String,
			'notes':{
				Type:String,
				default:''
			}
		},
		components: {
			uniCard
		}
	}
</script>
