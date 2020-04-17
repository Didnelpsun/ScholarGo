<template>
	<view class="adver">
		<swiper class="swiper" indicator-dots=true autoplay=true circular=true v-if="urlArray" >
			<template v-for="(url,index) in urlArray">
				<swiper-item :style=" 'background-image:url('+url+');' " :key="index"></swiper-item>
			</template>
		</swiper>
	</view>
</template>

<script>
	export default {
		name: "adverSwiper",
		data() {
			return {
			};
		},
		props:{
			urlArray:Array
		},
		// methods:{
		// 	urlTrans:function(array){
		// 		let i = 0;
		// 		for(;i < array.length; i++){
		// 			this.$set(array,i,"background-image: url('" + array[i] + "');");
		// 		}
		// 	}
		// },
		// mounted() {
		// 	this.urlTrans(this.urlArray);
		// }
	}
</script>

<style lang="scss" socped>
	.swiper {
		width: 100vw;
		height: 45vh;
	}
	swiper-item {
		position: relative;
		background-size: cover;
		width: 100%;
		height: 100%;
	}

	.hovertext {
		position: absolute;
	}
</style>
