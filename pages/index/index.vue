<template>
	<view class="content">
		<swiper class="swiper" :autoplay="true" :indicator-dots="true" :current="current">
			<swiper-item
				class="swiper-item"
				v-for="(item, index) in images"
				:item-id="index"
				:key="index"
			>
				<image class="swiper-image" :src="item" mode="aspectFill"></image>
			</swiper-item>
		</swiper>
		<view class="main-item" v-for="(item, index) in goods" :key="index">
			<goods-item :loading="loading" :goods="item"></goods-item>
		</view>
		<u-loadmore v-if="goods.length" :status="status" />
	</view>
</template>

<script>
export default {
	data() {
		return {
			current: 0,
			images: [
				'/static/image/src=http___img.zcool.cn_community_01b5555a0d934ca80121985ce63b3b.jpg@1280w_1l_2o_100sh.jpg&refer=http___img.zcool.jpg',
				'/static/image/src=http___img.zcool.cn_community_01f7a95543380c0000019ae9819de6.jpg@1280w_1l_2o_100sh.jpg&refer=http___img.zcool.jpg',
			],
			goods: [{}, {}, {}, {}],
			pages: {
				size: 10,
				page: 1,
			},
			status: 'loadmore',
			loading: false,
			dataList: [
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水千山万水千山万水千山万水千山万水千山万水千山万水千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心山东乳山水产经营中心山东乳山水产经营中心',
					distance: '100m',
				},
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心',
					distance: '100m',
				},
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心',
					distance: '100m',
				},
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心',
					distance: '100m',
				},
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心',
					distance: '100m',
				},
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心',
					distance: '100m',
				},
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心',
					distance: '100m',
				},
				{
					image: '/static/logo.png',
					tag: '热',
					title: '千山万水',
					tags: ['海产', '买一送一', '退险'],
					address: '山东乳山水产经营中心',
					distance: '100m',
				},
			],
		}
	},
	onLoad() {
		this.getData()
	},
	methods: {
		getData(reload = false) {
			if(this.loading || this.status === 'loading') return
			if (this.pages.page === 1) {
				this.loading = true
			} else {
				this.status = 'loading'
			}
			setTimeout(() => {
				if (reload) {
					this.goods = this.dataList
				} else {
					if (this.pages.page === 1) this.goods = this.dataList
					else this.goods.push(...this.dataList)
				}
				this.loading = false
				uni.stopPullDownRefresh()
				this.status = 'loadmore'
			}, 500)
		},
	},
	onPullDownRefresh() {
		this.pages.page = 1
		this.getData(true)
	},
	onReachBottom() {
		this.pages.page += 1
		this.getData()
	},
}
</script>

<style lang="scss">
page {
	height: 100%;
}
.content {
	min-height: 100%;
	background-color: #f8f8f8;
	padding-bottom: 1rpx;
}
.swiper {
	width: 100%;
	height: 300rpx;
	&-item {
		width: 100%;
		height: 300rpx;
	}
	&-image {
		width: 100%;
		height: 300rpx;
	}
}
.main {
	&-item {
		margin-top: 24rpx;
	}
}
</style>
