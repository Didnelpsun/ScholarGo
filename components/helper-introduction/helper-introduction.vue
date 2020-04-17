<template>
	<view>
		<uni-card :extra="area" :title="name" mode="style" :is-shadow="true" :thumbnail="photo"
		 :note="grade">
			{{notes}}
		</uni-card>
	</view>
</template>

<script>
	import uniCard from '@/components/uni-card/uni-card.vue';
	export default {
		name: 'helperIntroduction',
		data () {
			return{};
		},
		props: [
			'name',
			'photo',
			'area',
			'grade',
			'notes'
			],
		components: {
			uniCard
		}
	}
</script>
