<template>
	<view class="wrapper">
		<view class="status-contents" :style="{ paddingTop: statusBarHeight + 'px'}">
			<view class="status top-view">
				<view>
					<view class="calendarText" @click="open">
						2019-10-30
					</view>
					<view class="calendarBox" v-if="calendarShow" :style="{ top: calendartTop + 'px'}">
						<uni-calendar ref="calendar" :insert="true" @confirm="confirm"></uni-calendar>
					</view>
				</view>
				<view class="headTitle">
					头部文案
				</view>
			</view>
		</view>
		<view class="content">
			fsdfsfsf是的方式发生
		</view>
	</view>
</template>

<script>
	import '@/static/icon/iconfont.css'
	import navigationBar from '@/components/navigation-bar/navigation-bar.vue'
	import uniCalendar from "@/components/uni-calendar/uni-calendar"
	export default {
		components: {
			navigationBar,
			uniCalendar
		},
		data() {
			return {
				//状态栏高度
				statusBarHeight: 0,
				calendarShow: false,
				calendartTop: 0
			};
		},
		//第一次加载
		created() {
			//获取手机状态栏高度
			this.statusBarHeight = uni.getSystemInfoSync()['statusBarHeight'];
			//日历距离顶部高度
			this.calendartTop = this.statusBarHeight + 44;
		},
		methods: {
			open() {
				this.calendarShow = true;
			},
			confirm(e) {
				console.log(e);
			}
		}
	};
</script>

<style lang="scss">
	.wrapper {
		.status-contents {
			height: 88upx;
			background: red;
			position: relative;
		}

		.top-view {
			width: 100%;
			height: 88upx;

			.headTitle {
				display: none;
				align-items: center;
				height: 88upx;
				font-size: 16px;
				color: #000;
				position: absolute;
				bottom: 0;
				left: 50%;
				transform: translateX(-50%);
			}

			.calendarText {
				display: flex;
				align-items: center;
				height: 88upx;
				font-size: 16px;
				color: #000;
				position: absolute;
				bottom: 0;
				left: 50%;
				transform: translateX(-50%);
			}

			.calendarBox {
				position: absolute;
				left: 0;
				right: 0;
			}
		}
	}
</style>
