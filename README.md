# 页面构建过程

## html
1. 读取字节
2. 根据编码将字节转换为字符
3. 生成令牌(token)
4. 生成节点(包含attr)
5. 生成DOM树

## CSS
1234同
5. 生成CSSOM树

## Render tree
1. 合并DOM与CSSOM为render tree
2. 渲染树只包含网页所需节点(不包括head标签, script, dis: none节点)
3. 计算元素的位置与大小
4. 绘制到屏幕
	2. 矢量到光栅 : 从具象的形状到屏幕像素

## JS


# 优化
**通用**:  
1. 压缩并缓存
2. 削减非必要呈现在页面中的资源数
3. 

### PC
#### html: 
* 压缩(删除空格,注释)

#### css: 
* 压缩(删除空格,注释)
* 样式表视情况内联(减少请求)
* 删除冗余(不匹配任何元素的)样式
* link正确的添加**media**属性
* 避免使用@import规则

#### js
* 视情况将脚本内联
* 视情况添加**async**属性将脚本变为非阻塞
* 视情况添加**defer**属性将脚本变为延迟脚本
* 将读写样式操作分为读和写, 而不是读写交替
* 缓存DOM方便调用

### MOBILE
*https://www.smashingmagazine.com/2013/04/build-fast-loading-mobile-website/, 去评论区发掘更多*

#### 前端
1. 削减依赖数量
	*  使用css (圆角, 阴影, 渐变) 代替花式效果, 适当使用媒体查询来禁用背景图像.
		* 不管元素dis: none还是vis: hide, 它的bg-image会照样请求
		* 耗费时间**从低到高**: 渐变, 帧动画 < 圆角 < 阴影
	* 视情况内联CSS来减少HTTP请求
	* 使用内联SVG或icon字体来代替图像
	* 雪碧图
	* 避免使用内联FRAME
	* 编写移动端优先的代码
	* 分散页面内容为多页
	* 确保重定向数量最少
2.  削减图片尺寸( 移动端会resize来适应屏幕 )
	* 使用媒体查询响应对应分辨率所需图片
3.  削减客户端处理( js处理 )
	* 削减js大小
	* 避免外链小组件( 比如推特分享按钮 )
	* 使用mobile版jQuery

#### 后端
1. 缓存HTTP重定向来提高再次访问页面所需的加载时间
2. 合并HTTP重定向数量
3. 使用HTTP压缩来减少请求字节数( GZIP啥的 )
