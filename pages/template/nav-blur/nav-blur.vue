<template>
	<view class="page">
		<view class="img-view" v-if="!showSwiper">
			<image :src="imgUrls[0]"></image>
		</view>
		<swiper v-if="showSwiper" indicator-dots="true">
			<swiper-item v-for="(img,key) in imgUrls" :key="key">
				<image :src="img" />
			</swiper-item>
		</swiper>
		<view class="uni-padding-wrap uni-common-mt">
			<view class="uni-title">
				<view>使用模糊效果时不要设置背景颜色，否则模糊效果会失效，默认值为 none（仅iOS平台支持 HBuilderX 2.4.3+）</view>
			</view>
			<view class="uni-title uni-common-mt">图片类型</view>
		</view>
		<view class="uni-list">
			<radio-group @change="radioChange">
				<label class="uni-list-cell uni-list-cell-pd" v-for="(item,index) in items" :key="index">
					<view>{{item.name}}</view>
					<view>
						<radio :value="item.value" :checked="item.checked" />
					</view>
				</label>
			</radio-group>
		</view>
		<!-- <view style="height: 1000upx;"></view> -->
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showSwiper: false,
				imgUrls: [
                    "https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/cbd.jpg",
					"https://img-cdn-qiniu.dcloud.net.cn/uniapp/images/muwu.jpg",
                    "../../../static/shuijiao.jpg"
				],
				items: [{
						value: "img",
						name: '静态图',
						checked: true
					},
					{
						value: "swiper",
						name: '轮播图',
						checked: false
					}
				]
			}
		},
		methods: {
			radioChange(e) {
				this.showSwiper = e.detail.value === "swiper";
			}
		}
	}
</script>

<style>
	image,
	swiper,
	.img-view {
		width: 750upx;
		height: 500upx;
	}
	.page-section-title{
		margin-top: 50upx;
	}
</style>
