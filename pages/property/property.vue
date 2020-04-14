<template>
	<view class="property">
		<view class="backColor"></view>
		<view class="monthData">
			<view class="monthText">您在{{month}}月消费累计{{monthAmount}}人民币</view>
		</view>
		<view class="data">
			<view class="dataView">
				<view class="dataInner" style="background-color: #bc4cfc;">
					<text>￥{{surplus}}</text>
					<text>剩余金额</text>
				</view>
				<view class="button" @click="turnTo('/pages/deposit/deposit')">充值</view>
				<view class="button">提现</view>
			</view>
			<view class="dataView">
				<view class="dataInner" style="background-color: #FFFFFF;">
					<text>￥{{total}}</text>
					<text>总计消费</text>
				</view>
				<view class="button">明细</view>
			</view>
		</view>
		<view class="chart">
			<view class="qiun-charts">
				<canvas canvas-id="canvasLineA" id="canvasLineA" class="charts" @touchstart="touchLineA"></canvas>
			</view>
		</view>
	</view>
</template>

<script>
	import uCharts from '@/components/u-charts/u-charts.js';
	//如果this实例组件中使用图标，必须传入this实例
	var _self;
	var canvaLineA = null;
	export default {
		data() {
			return {
				monthAmount: 0,
				surplus:0,
				total:0,
				cWidth: '',
				cHeight: '',
				pixelRatio: 1,
			};
		},
		computed: {
			month: function() {
				let date = new Date();
				return date.getMonth() + 1;
			}
		},
		onLoad() {
			//将这个变量赋值为this组件对象
			_self = this;
			this.cWidth = uni.upx2px(750);
			this.cHeight = uni.upx2px(500);
			this.getServerData();
		},
		methods: {
			turnTo:(urls)=>{
				uni.navigateTo({
					url:urls
				})
			},
			//获取示例数据
			getServerData() {
				uni.request({
					url: 'https://www.ucharts.cn/data.json',
					data: {},
					success: function(res) {
						// console.log(res.data.data)
						let LineA = {
							categories: [],
							series: []
						};
						//这里我后台返回的是数组，所以用等于，如果您后台返回的是单条数据，需要push进去
						LineA.categories = res.data.data.LineA.categories;
						LineA.series = res.data.data.LineA.series;
						_self.showLineA("canvasLineA", LineA);
					},
					fail: () => {
						_self.tips = "网络错误，小程序端请检查合法域名";
					},
				});
			},
			//展示数据
			showLineA(canvasId, chartData) {
				canvaLineA = new uCharts({
					//将this组件对象传入图表的$this属性
					$this: _self,
					//页面组件id
					canvasId: canvasId,
					//图标类型，line代表为折线图
					type: 'line',
					//全局默认字体
					fontSize: 12,
					legend: {
						show: true
					},
					//不在图标中显示数据表情内容值
					dataLabel: false,
					//显示数据点图形标志
					dataPointShape: true,
					//canvas背景颜色
					background: '#FFFFFF',
					//像素比，出来支付宝大于1，其他都为1
					pixelRatio: _self.pixelRatio,
					//数据类别，饼图和圆环图不用
					categories: chartData.categories,
					//数据列表
					series: chartData.series,
					//开启动画展示
					animation: true,
					xAxis: {
						type: 'grid',
						gridColor: '#CCCCCC',
						gridType: 'dash',
						dashLength: 8
					},
					yAxis: {
						gridType: 'dash',
						gridColor: '#CCCCCC',
						dashLength: 8,
						splitNumber: 5,
						min: 10,
						max: 180,
						format: (val) => {
							return val.toFixed(0) + '元'
						}
					},
					//宽度为upx乘以像素比
					width: _self.cWidth * _self.pixelRatio,
					height: _self.cHeight * _self.pixelRatio,
					extra: {
						line: {
							type: 'straight'
						}
					}
				});

			},
			touchLineA(e) {
				canvaLineA.showToolTip(e, {
					format: function(item, category) {
						return category + ' ' + item.name + ':' + item.data
					}
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
	$width: 95vw;
	$radius: 2vw;

	.property {
		background-color: $uni-bg-color-grey;
		font-size: $uni-font-size-base;
		color: $uni-text-color;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.backColor {
		position: absolute;
		background-color: #bc4cfc;
		width: 200vw;
		height: 200vw;
		transform: translateY(-150vw);
		border-radius: 50%;
	}

	.monthData {
		z-index: 2;
		// width: $width;
		display: flex;
		flex-direction: row;
		margin-top: 10 * $space;
		background-color: $uni-bg-color;
		border-radius: $radius;
		border: solid 1px $uni-bg-color-hover;
	}

	.monthText {
		padding: $space;
		font-size: $uni-font-size-lg;
	}

	.data {
		background-color: $uni-bg-color;
		width: $width;
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-around;
		margin: 2 * $space 0 2 * $space;
		padding: 4 * $space 0 4 * $space;
		border-radius: $radius;
		z-index: 2;
	}

	.dataView {
		background-color: $uni-bg-color;
		background-color: #f2e3fb;
		width: 35vw;
		height: 50vw;
		border-radius: $radius;
		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.dataInner {
		width: 25vw;
		height: 25vw;
		border: solid 1px #f7edfc;
		margin-top: 2 * $space;
		border-radius: $radius;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	.button {
		background-color: #d288fd;
		border-radius: $radius;
		padding: 1px $space 1px;
		margin-top: 2 * $space;
	}

	.qiun-charts {
		width: 750upx;
		height: 500upx;
		background-color: #FFFFFF;
	}

	.charts {
		width: 750upx;
		height: 500upx;
		background-color: #FFFFFF;
	}
</style>
