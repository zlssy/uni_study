<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view>
			<text class="title">{{title}}</text>
		</view>
		<block v-for="(item,index) in list" :key="index">
			<view>{{item.name}}</view>
		</block>
		<view>
			<text class="f-test-color">测试颜色</text>
		</view>
		<view class="f-container">
			<view class="f-row-2 f-text-center" @tap="goto" :data-id="link1">链接一</view>
			<view class="f-row-2 f-text-center" @tap="goto" :data-id="link2">链接二</view>
		</view>
	</view>
</template>

<script>
	const _c = n=>({
		name:n
	});
	export default {
		data() {
			return {
				title: 'Hello',
				list:[1,2].map(v=>_c(v)),
				link1:'1',
				link2:'2',
			}
		},
		onLoad() {
			console.log('page onload');
		},
		methods: {
			goto(e){
				const {id} = e.currentTarget.dataset;
				uni.navigateTo({
					url:`../list/list?id=${id}`
				});
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin: 200rpx auto 50rpx auto;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
