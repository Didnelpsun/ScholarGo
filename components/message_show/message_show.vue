<template>
	<view class="m-item" :id="'message'+index">
		<view class="m-left">
			<image class="head_icon" v-if="abosultPath+user.home.img && message.user=='home'" :src="abosultPath+user.home.img"></image>
		</view>
		<view class="m-content">
			<view class="m-content-head" :class="{'m-content-head-right':message.user=='customer'}">
				<view :class="'m-content-head-'+message.user"> {{ message.content }} </view>
			</view>
		</view>
		<view class="m-right" >
			<image class="head_icon" v-if="abosultPath+user.customer.img && message.user=='customer'" :src="abosultPath+user.customer.img"></image>
		</view>
	</view>
</template>

<script>
	import {
		mapState
	} from 'vuex'

	export default {
		data() {
			return {
				abosultPath: "../../",
				path_1:"'../../'+'user.home.img'"
			}
		},
		props: [
			'message',
			'index'
			],
		computed: mapState(['user'])
	}
</script>

<style>
	.m-item {
		display: flex;
		flex-direction: row;
		padding-top: 40px;
	}
	.m-left {
		display: flex;
		/* width: 40px; */
		justify-content: center;
		align-items: flex-start;
	}
	.m-content {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		word-break: break-all;
	}
	.m-right {
		display: flex;
		/* width: 40px; */
		justify-content: center;
		align-items: flex-start;
	}
	.head_icon {
		width: 40px;
		height: 40px;
	}
	.m-content-head {
		position: relative;
	}
	.m-content-head-right {
		display: flex;
		justify-content: flex-end;
	}
	.m-content-head-home {
		text-align: left;
		background: #1482d1;
		border: 1px #1482d1 solid;
		border-radius: 20px;
		padding: 10px;
		color: white;
		margin-right: 150px;
	}
	/* .m-content-head-home:before {
		border: 15px solid transparent;
		border-right: 15px solid #1482d1;
		left: -26px;
		width: 0;
		height: 0;
		position: absolute;
		content: ' '
	} */
	.m-content-head-customer {
		border: 1px white solid;
		background: white;
		border-radius: 20px;
		padding: 10px;
	}
	/* .m-content-head-customer:after {
		border: 15px solid transparent;
		border-left: 15px solid white;
		top: 20px;
		right: -26px;
		width: 0;
		height: 0;
		position: absolute;
		content: ' '
	} */
</style>
