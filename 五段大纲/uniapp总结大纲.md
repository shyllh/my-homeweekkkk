# 一：uniapp简介

```
是一个使用 Vue.js 开发所有前端应用的框架，开发者编写一套代码，可发布到iOS、Android、Web（响应式）、以及各种小程序（微信/支付宝/百度/头条/QQ/钉钉/淘宝）、快应用等多个平台
```

##### 开发工具：HBuilderX

https://www.dcloud.io/hbuilderx.html

##### 创建uniapp：

https://uniapp.dcloud.io/quickstart-hx?id=%e5%88%9b%e5%bb%bauni-app

##### 目录结构：

```js
┌─cloudfunctions        云函数目录（阿里云为aliyun，腾讯云为tcb，详见uniCloud）
│─components            符合vue组件规范的uni-app组件目录
│  └─comp-a.vue         可复用的a组件
├─hybrid                存放本地网页的目录，详见
├─platforms             存放各平台专用页面的目录，详见
├─pages                 业务页面文件存放的目录
│  ├─index
│  │  └─index.vue       index页面
│  └─list
│     └─list.vue        list页面
├─static                存放应用引用静态资源（如图片、视频等）的目录，注意：静态资源只能存放于此
├─wxcomponents          存放小程序组件的目录，详见
├─main.js               Vue初始化入口文件
├─App.vue               应用配置，用来配置App全局样式以及监听 应用生命周期
├─manifest.json         配置应用名称、appid、logo、版本等打包信息，详见
└─pages.json            配置页面路由、导航条、选项卡等页面类信息，详见
```

注意事项：

```
编译到任意平台时，static 目录下的文件均会被打包进去，非 static 目录下的文件（vue、js、css 等）被引用到才会被包含进去。
static 目录下的 js 文件不会被编译，如果里面有 es6 的代码，不经过转换直接运行，在手机设备上会报错。
css、less/scss 等资源同样不要放在 static 目录下，建议这些公用的资源放在 common 目录下。
```

# 二：代码开发

##### 1，全局配置：

```
pages.json 文件用来对 uni-app 进行全局配置，决定页面文件的路径、窗口样式、原生的导航栏、底部的原生tabbar 等。
类似于小程序的app.json
```

##### 2，页面配置：

```
创建pages文件，
"pages": [ //pages数组中第一项表示应用启动页，参考：https://uniapp.dcloud.io/collocation/pages
		{
			"path": "pages/index/index",
			"style": {
				"navigationBarTitleText": "我是首页",
				"navigationBarBackgroundColor":"#4CD964"//导航栏背景颜色（同状态栏背景色）
			}
		},
		{
			"path": "pages/mytest/mytest",
			"style": {
				"navigationBarTitleText": "uni-app"
			}
		}
	],
```

##### 3，底部tabBar导航配置：

```
	"tabBar":{
		"list":[
				{
			        "pagePath": "pages/index/index",
					"iconPath": "static/icon/1.png",
					"selectedIconPath":"static/icon/2.png",
			        "text": "组件"
			    }, {
			        "pagePath": "pages/mytest/mytest",
					"iconPath":"static/icon/3.png",
					"selectedIconPath":"static/icon/4.png",
			        "text": "接口"
			    }
		]
	},
```

练习：实现底部导航配置，和页面

# 三：uniapp的生命周期

##### 1，应用的生命周期

https://uniapp.dcloud.io/collocation/frame/lifecycle?id=%e5%ba%94%e7%94%a8%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f

![image-20210316154334969](assets/image-20210316154334969.png)

注意：

- ```
  - 应用生命周期仅可在`App.vue`中监听，在其它页面监听无效。
  - onlaunch里进行页面跳转，如遇白屏报错，请参考https://ask.dcloud.net.cn/article/35942
  ```

  

##### 2，页面生命周期

类似小程序斗写在pages里面

https://uniapp.dcloud.io/collocation/frame/lifecycle?id=%e9%a1%b5%e9%9d%a2%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f

![image-20210316154439359](assets/image-20210316154439359.png)

注意：

```
onInit 使用注意

- 仅百度小程序基础库 3.260 以上支持 onInit 生命周期
- 其他版本或平台可以同时使用 onLoad 生命周期进行兼容，注意避免重复执行相同逻辑
- 不依赖页面传参的逻辑可以直接使用 created 生命周期替代

`onReachBottom`使用注意 可在pages.json里定义具体页面底部的触发距离[onReachBottomDistance](https://uniapp.dcloud.io/collocation/pages)，比如设为50，那么滚动页面到距离底部50px时，就会触发onReachBottom事件。

如使用scroll-view导致页面没有滚动，则触底事件不会被触发。scroll-view滚动到底部的事件请参考scroll-view的文档
```

##### 3，组件生命周期：

根目录下创建：components目录，里面都是自定义组件

https://uniapp.dcloud.io/collocation/frame/lifecycle?id=%e7%bb%84%e4%bb%b6%e7%94%9f%e5%91%bd%e5%91%a8%e6%9c%9f

![image-20210316154506424](assets/image-20210316154506424.png)

1，自定义数组对象，要求包含，姓名，年纪，民族 ，性别，爱好，个人介绍(超出5个字符，用。。。代替), 操作（里面包含删除按钮）完成成列表展示，要求，默认按照年龄排序。

2，按照上面的数据完成列表的新增！使用表单完成提交。两个可以放在一个页面上面

# 四：组件的使用

##### 1，自定义组件实现方式

```
1》创建文件，components
2》import mydiv from '../../components/mydiv/mydiv.vue'
3》components 里面注册
```

##### 2，uniapp内置组件

https://uniapp.dcloud.io/component/README

比如：

```
<button type="default">按钮</button>
```

比如轮播图swiper,可滑动视图

```
  <view class="page-section-spacing">
                    <swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
                        <swiper-item>
                            <view class="swiper-item uni-bg-red">A</view>
                        </swiper-item>
                        <swiper-item>
                            <view class="swiper-item uni-bg-green">B</view>
                        </swiper-item>
                        <swiper-item>
                            <view class="swiper-item uni-bg-blue">C</view>
                        </swiper-item>
                    </swiper>
                </view>
```

##### 3，扩展组件

https://uniapp.dcloud.io/component/README?id=uniui

比如日历组件

使用HBuilderX  导入插件，然后直接使用，不需要注册



练习：使用组件方式，实现选项卡切换，

要求选项一，新闻页面（包含增删改查），

选项二：图文卡片模式（多张图文优美排列）

选项三：轮播图实现，（静态的轮播图）

选项四：实现一个留言板，要求输入框在子组件中，列表在父组件中显示！！（子传父亲）

选项五：写一个表单，要求包含日历，姓名，手机号等信，提交之后在右侧的抽屉里面弹出表单输入的内容。

# 五：页面布局

##### [css引入静态资源](https://uniapp.dcloud.io/frame?id=css引入静态资源)

> `css`文件或`style标签`内引入`css`文件时（scss、less文件同理），可以使用相对路径或绝对路径（`HBuilderX 2.6.6-alpha`）

```css
/* 绝对路径 */
@import url('/common/uni.css');
@import url('@/common/uni.css');
/* 相对路径 */
@import url('../../common/uni.css');
```

![image-20210316163240849](assets/image-20210316163240849.png)



布局推荐使用：flex

单位：rpx

# 六：页面跳转

和小程序一样，

https://uniapp.dcloud.io/component/navigator?id=navigator

```
<navigator url="'/pages/test/test?item'"></navigator>

//跳转到tabar页面
<navigator url="/pages/mytest/mytest" hover-class="navigator-hover" open-type="switchTab">
	<button type="default">跳转到新页面</button>
</navigator>
```

编程式路由：

见uniapp中的api

			uni.navigateTo({
				url:'../kiss/kiss?id=90'
			})
可以看出来如果传参可以在onLoad 中接受和小程序一样

# 七：数据请求

```
uni.request({
    url:"http://120.92.101.187/index.php/index/index/index",
    success: (res) => {
        console.log(res)
    }
})

完整实例：
uni.request({
    url: 'https://www.example.com/request', //仅为示例，并非真实接口地址。
    data: {
        text: 'uni.request'
    },
    header: {
        'custom-header': 'hello' //自定义请求头信息
    },
    success: (res) => {
        console.log(res.data);
        this.text = 'request success';
    }
});
```

如果要封装请自行百度：例如   -》uniapp封装request

或者参考如下api.js，使用知识promise

```
//把配置项单独处理

process.env.NODE_ENV === 'development' ? '192.168.0.1' : 'http://***/api' ; //环境配置

// 全局请求路径，也就是后端的请求基准路径
const BASE_URL =  process.env.NODE_ENV ==='development' ? 'http://120.92.101.187' : 'http://***/api' ;
// 同时发送异步代码的次数，防止一次点击中有多次请求，用于处理
let ajaxTimes=0;
// 封装请求方法，并向外暴露该方法
export const myHttp = (options)=>{
	// 解构请求头参数
	let header = {...options.header};
	// 当前请求不是登录时请求，在header中加上后端返回的token
	if(options.url != 'login'){
	    header["client-identity"] ='后台返回的token';
	}
	ajaxTimes++;
	// 显示加载中 效果
	uni.showLoading({
		title: "加载中",
	    mask: true,
	});
	return new Promise((resolve,reject)=>{

		uni.request({
			url:BASE_URL+options.url,
			method: options.method || 'POST',
			data: options.data || {},
			// header,
			success: (res)=>{
				resolve(res)
				
			},
			fail: (err)=>{
				reject(err)
			
			},
			// 完成之后关闭加载效果
			complete:()=>{
				ajaxTimes--;
				if(ajaxTimes===0){
			        //  关闭正在等待的图标
			        uni.hideLoading();
			    }
			}
		})
	})
}

```

第二步：在main.js中

```
import { myHttp } from './api/api.js'
Vue.prototype.$myHttp = myHttp
```

第三步：使用

```
let res = this.$myHttp({
    url:'/index.php/index/index/index',
    data:{},
}).then(res=>{
	console.log(res.data,'90998')
})
```

八：打包 运行