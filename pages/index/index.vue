<template>
	<view class="content">
		<image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view>
		<view class="menu-box">
			<view class="menu-item" v-for="(item, index) in list" :key="item.id" @click="gotoHref(item.path)">
				<text class="">{{`${index+1}.`}} {{item.name}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello uni-app',
				list: [{
						id: 1,
						path: '/pages/index/index',
						name: '首页 uni-app'
					},
					{
						id: 2,
						path: '/pages/uni-ui/uni-ui',
						name: 'uni-ui'
					},
					{
						id: 3,
						path: '/pages/tabBar/component/component',
						name: 'uni-app框架的内置组件'
					},
					{
						id: 4,
						path: '/pages/tabBar/API/API',
						name: 'uni-app框架的接口'
					},
					{
						id: 5,
						path: '/pages/tabBar/template/template',
						name: 'uni-app框架的模板'
					},
					{
						id: 6,
						path: '/pages/tabBar/extUI/extUI',
						name: 'uni-app框架的扩展组件'
					},
					{
						id: 7,
						path: '/pages/uni-Cloud/uni-Cloud',
						name: 'uniCloud 基础示例'
					},
					{
						id: 8,
						path: '/pages/main/main',
						name: 'uni-app & uniCloud 的前后一体登录模板'
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			gotoHref(path) {
				uni.navigateTo({
					url: path
				})
			}
		}
	}
</script>

<style lang="scss">
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;

		.logo {
			height: 100rpx;
			width: 100rpx;
			margin-top: 20rpx;
			margin-left: auto;
			margin-right: auto;
			margin-bottom: 20rpx;
		}

		.text-area {
			display: flex;
			justify-content: center;

			.title {
				font-size: 36rpx;
				color: #8f8f94;
			}
		}

		.menu-box {
			width: 100%;
			padding: 20rpx;
			color: #999;
			box-sizing: border-box;
			justify-content: start;

			.menu-item {
				text-decoration: underline;
			}
		}
	}
</style>
