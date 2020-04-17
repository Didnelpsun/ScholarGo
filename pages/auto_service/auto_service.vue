<template>
	<view>
		<view>
		<uni-grid :column="2">
		    <uni-grid-item>			
				<view class="indexboard" style="background-color: #7e92dc;">
					<view class="indexborder">
						<image src="../../static/image/index/answeer.png" class="indexImg"></image>
					</view>
					<text>我要退款</text>
				</view>
		    </uni-grid-item>
		    <uni-grid-item>	
				<view class="indexboard" style="background-color: #9477f3;">
		        	<view class="indexborder">
		                <image src="../../static/image/index/ask.png" class="indexImg"></image>
					</view>
					<text>催服务</text>
				</view>
		    </uni-grid-item>
		</uni-grid>
		</view>
		<view>
			<uni-list>
			    <uni-list-item title="我的服务进度" :show-badge="true" badge-text="查看所有 "></uni-list-item>
			</uni-list>
		</view>
		<view>
			<uni-list>
			    <uni-list-item title="我们的服务态度"></uni-list-item>
			    <uni-list-item title="常见问题"></uni-list-item>
			    <uni-list-item title="售后问题" badge-text="12"></uni-list-item>
			    <uni-list-item title="我想退款" :show-badge="true" badge-text="12"></uni-list-item>
				<uni-list-item title="服务有问题" :show-badge="true" badge-text="12"></uni-list-item>
				<uni-list-item title="待处理问题" badge-text="12"></uni-list-item>
				<uni-list-item title="活动介绍" badge-text="12"></uni-list-item>
			</uni-list>
		</view>
	</view>
</template>

<script>
	import uniGrid from "@/components/uni-grid/uni-grid.vue"
	import uniGridItem from "@/components/uni-grid-item/uni-grid-item.vue"
	import uniList from "@/components/uni-list/uni-list.vue"
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
	export default {
		components: {
			uniGrid,
			uniGridItem,
			uniList,
			uniListItem
			},
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style lang="scss">
	.indexboard {
		width: 50vw;
		height: 50vh;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		color: $uni-text-color-inverse;
		font-size: $uni-font-size-llg;
	}
	
	.indexborder {
		width: 80px;
		height: 80px;
		background-color: $uni-bg-color;
		border-radius: 50%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		margin-left: 2 * $space;
	}
	
	.indexImg {
		width: 40px;
		height: 40px;
	}

</style>
