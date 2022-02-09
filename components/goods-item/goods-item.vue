<template>
		<view class="boxes">
			<u-skeleton :loading="loading" :animate="true" :avatar="true" :avatarSize="80" :rows="2" avatarShape="square">
			<view class="goods">
				<view class="goods-img">
					<image class="goods-img__image" :src="goods.image" mode="aspectFill"></image>
					<view class="goods-img__tag">{{goods.tag}}</view>
				</view>
				<view class="goods-content">
					<view class="goods-content__title ellipsis">{{goods.title}}</view>
					<view class="goods-tags">
						<view class="goods-tags__item" v-for="(tag,i) in goods.tags" :key="i">
							<u-tag v-if="i < 4" :text="tag" size="mini" type="error" plain plainFill></u-tag>
						</view>
					</view>
					<view class="goods-subjoin">
						<view class="goods-subjoin__address ellipsis">{{goods.address}}</view>
						<view class="goods-subjoin__distance">附近{{goods.distance}}</view>
					</view>
				</view>
			</view>
			</u-skeleton>
		</view>
</template>

<script>
	export default {
		name:"good-item",
		options: {  
			styleIsolation: 'page-shared'  
		},
		data() {
			return {};
		},
		props:{
			goods: {
				type:Object,
				default:() => {}
			},
			loading: {
				type:Boolean,
				default:false
			}
		}
	}
</script>

<style lang="scss" scoped>
@import '@/style/main.scss';
.boxes {
	width: 100%;
	background-color: #fff;
	padding: 24rpx;
	box-sizing: border-box;
	display: flex;
	::v-deep .u-skeleton {
		overflow: hidden;
	}
}
.goods {
	display: flex;
	
	&-img {
		width: 160rpx;
		height: 160rpx;
		border-radius: 12rpx;
		overflow: hidden;
		position: relative;
		&__image {
			width: 160rpx;
			height: 160rpx;
			border-radius: 12rpx;
		}
		&__tag {
			position: absolute;
			top: 0;
			right: 0;
			z-index: 10;
			border-radius: 0 12rpx 0 12rpx;
			width: 60rpx;
			height: 30rpx;
			background-color: #F0AD4E;
			display: flex;
			justify-content: center;
			align-items: center;
			font-size: 22rpx;
			color: #333;
		}
	}
	&-content {
		flex: 1;
		overflow: hidden;
		margin-left: 12rpx;
		&__title {
			font-size: 32rpx;
			color: #333;
		}
		
	}
	&-tags {
		display: flex;
		width: 100%;
		margin-top: 8rpx;
		&__item {
			margin-right: 12rpx;
		}
	}
	&-subjoin {
		display: flex;
		align-items: center;
		justify-content: space-between;
		margin-top: 20rpx;
		&__address {
			font-size: 24rpx;
			color: #999;
			width: 70%;
		}
		&__distance {
			font-size: 24rpx;
			color: #999;
		}
	}
}
.goods-tags__item ::v-deep .u-tag--mini {
	height: 32rpx;
}
</style>

