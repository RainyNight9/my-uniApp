<script>
	import {
		mapState,
		mapMutations
	} from 'vuex'
	
	export default {
		onLaunch: function() {
			console.log('App Launch')
			gotoLogin()
			
			appPlus()
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		globalData: {
			test: ''
		},
		methods: {
			...mapMutations(['login']),
			gotoLogin(){
				let uniIdToken = uni.getStorageSync('uniIdToken')
				if (uniIdToken) {
					this.login(uni.getStorageSync('username'))
				}
			},
			appPlus(){
				// #ifdef APP-PLUS
				// App平台检测升级，服务端代码是通过uniCloud的云函数实现的，详情可参考：https://ext.dcloud.net.cn/plugin?id=2226
				if(plus.runtime.appid !== 'HBuilder'){ // 真机运行不需要检查更新，真机运行时appid固定为'HBuilder'，这是调试基座的appid
					uni.request({
					    url: 'https://7a3e3fa9-7820-41d0-be80-11927ac2026c.bspapp.com/http/update', //检查更新的服务器地址
					    data: {
					        appid: plus.runtime.appid,
					        version: plus.runtime.version,
					        imei: plus.device.imei
					    },
					    success: (res) => {
					        if (res.statusCode == 200 && res.data.isUpdate) {
					            // 提醒用户更新
					            uni.showModal({
					                title: '更新提示',
					                content: res.data.note ? res.data.note : '是否选择更新',
					                success: (ee) => {
					                    if (ee.confirm) {
					                        plus.runtime.openURL(res.data.url);
					                    }
					                }
					            })
					        }
					    }
					})
				}
				// #endif
			}
		}
	}
</script>

<style>
	/*每个页面公共css */
	
	/* 解决头条小程序组件内引入字体不生效的问题 */
	/* #ifdef MP-TOUTIAO */
	@font-face {
		font-family: uniicons;
		src: url('/static/uni.ttf');
	}
	/* #endif */
	
	/* #ifndef APP-PLUS-NVUE */
	/* uni.css - 通用组件、模板样式库，可以当作一套ui库应用 */
	@import './common/uni.css';
	
	/* 以下样式用于 hello uni-app 演示所需 */
	page {
	    background-color: #F4F5F6;
	    height: 100%;
	    font-size: 28rpx;
	    line-height: 1.8;
	}
	
	.uni-header-logo {
	    padding: 30rpx;
	    flex-direction: column;
	    justify-content: center;
	    align-items: center;
	    margin-top: 10rpx;
	}
	
	.uni-header-image {
	    width: 100px;
	    height: 100px;
	}
	
	.uni-hello-text {
	    color: #7A7E83;
	}
	
	.uni-hello-addfile {
	    text-align: center;
	    line-height: 300rpx;
	    background: #FFF;
	    padding: 50rpx;
	    margin-top: 10px;
	    font-size: 38rpx;
	    color: #808080;
	}
	/* #endif*/
	
	
	/* 头条小程序需要把 iconfont 样式放到组件外 */
	@import "components/m-icon/m-icon.css";
	
	/*每个页面公共css */
	page {
		min-height: 100%;
		display: flex;
		font-size: 16px;
	}
	
	/* #ifdef MP-BAIDU */
	page {
		width: 100%;
		height: 100%;
		display: block;
	}
	
	swan-template {
		width: 100%;
		min-height: 100%;
		display: flex;
	}
	
	/* 原生组件模式下需要注意组件外部样式 */
	custom-component {
		width: 100%;
		min-height: 100%;
		display: flex;
	}
	
	/* #endif */
	
	/* #ifdef MP-ALIPAY */
	page {
		min-height: 100vh;
	}
	
	/* #endif */
	
	/* 原生组件模式下需要注意组件外部样式 */
	m-input {
		width: 100%;
		/* min-height: 100%; */
		display: flex;
		flex: 1;
	}
	
	.content {
		display: flex;
		flex: 1;
		flex-direction: column;
		background-color: #efeff4;
		padding: 10px;
	}
	
	.input-group {
		background-color: #ffffff;
		margin-top: 20px;
		position: relative;
	}
	
	.input-group::before {
		position: absolute;
		right: 0;
		top: 0;
		left: 0;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}
	
	.input-group::after {
		position: absolute;
		right: 0;
		bottom: 0;
		left: 0;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}
	
	.input-row {
		display: flex;
		flex-direction: row;
		position: relative;
		font-size: 18px;
		line-height: 40px;
	}
	
	.input-row .title {
		width: 100px;
		padding-left: 15px;
	}
	
	.input-row.border::after {
		position: absolute;
		right: 0;
		bottom: 0;
		left: 8px;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}
	
	.btn-row {
		margin-top: 25px;
		padding: 10px;
	}
	
	button.primary {
		background-color: #0faeff;
	}
</style>
