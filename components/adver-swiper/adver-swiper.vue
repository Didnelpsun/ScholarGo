<template>
	<view class="adver">
		<swiper class="swiper" indicator-dots=true autoplay=true circular=true>
			<swiper-item style="background-image: url('https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1586695678334&di=81f1302551cb97e213d92b5403d2e7b9&imgtype=0&src=http%3A%2F%2Fi1.hdslb.com%2Fbfs%2Farchive%2Faf56a2c9ad2f4c0ba39abb7ed709844240c3afce.jpg');">
			</swiper-item>
			<swiper-item style="background-image: url('https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1586695773884&di=cec81a55f62258a79022ba016dadc1b8&imgtype=0&src=http%3A%2F%2Fi0.hdslb.com%2Fbfs%2Farticle%2Fd43e737a7c2b9f63f5c4e4b5a8a8ab20e8efa41c.png');">
			</swiper-item>
			<swiper-item style="background-image: url('https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1586695843022&di=b4811db03858fcf880c5f1661575a48a&imgtype=0&src=http%3A%2F%2Fi0.hdslb.com%2Fbfs%2Farticle%2Fecae23c3d4417b13ce1edaf01393e418ee4b5b55.jpg');">
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		name: "adver",
		data() {
			return {
			};
		},
		props:[
			
		]
	}
</script>

<style lang="scss" socped>
	swiper {
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
