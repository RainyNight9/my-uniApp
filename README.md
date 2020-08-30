## uni-app

### 开发准备

1.下载 HBuilder App开发版 [!下载地址](https://www.dcloud.io/hbuilderx.html)

2.下载 微信开发者工具 [!下载地址](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html)

3.下载 谷歌浏览器Chrome [!下载地址](https://www.google.cn/chrome/)

4.官方文档学习 [!uni-app官网](https://uniapp.dcloud.io/)

### 开发初始了解

1.vue语法 + 小程序组件
	
	1.vue必须会，小程序可会可不会（可能有点绝对，特例可忽略，哈哈）
	
2.uni-app 生命周期 这边 多了两类：
	
	1.应用的生命周期
	2.页面的生命周期 (只能写在页面里边，不能写在组件里边)
	3.组件的生命周期（等同于原生vue生命周期）
	
3.组件的使用
	
	1.自定义组件的命名规范(驼峰法)，可以直接使用，不需要(import)引用
	2.组件不建议使用class为属性传递，也不建议用class与style绑定样式（H5除外），组件不接该参数就不报错
	3.都放在 components 文件夹下，这样引入插件也很方便，直接安装在该文件夹下，可以根据需求自己改插件
	
4.style使用
	
	1.rpx 是基于750设计稿
	2.支持less 或 scss 预编译
	
5.uniCloud 
	
	1.DCloud 联合阿里云、腾讯云（暂时免费，需要实名认证）
	2.用熟悉的js，轻松搞定前后台整体业务
	3.创建关联服务空间，初始化云数据库，上传所有云函数和公共模块
	
6.条件编译

	1.以 #ifdef 或 #ifndef 加 %PLATFORM% 开头，以 #endif 结尾，跨平台。
	