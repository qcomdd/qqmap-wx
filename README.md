# qqmap-wx
微信小程序_腾讯地图SDK(在官方基础上增加路径规划功能)
以下为使用方法。

 ```javascript

 // 引入SDK核心类本文件
var QQMapWX = require('xxx/qqmap-wx-jssdk.js'); 
// 实例化API核心类
var demo = new QQMapWX({
    key: '开发密钥（key）' // 必填
});
 
// 调用接口
demo.direction({
    location:{
        latitude: 39.984572,
        longitude: 116.306339
    },
    to:{
        latitude: 39.984060,
        longitude: 116.307520
    },
	mode:"driving",//默认驾车（driving），步行（walking），公交（transit）
	policy: "LEAST_TIME",//REAL_TRAFFIC：[默认]结合路况，最优路线|LEAST_TIME：速度优先|LEAST_FEE：少收费|
	waypoints: "",//途经点39.111,116.112;39.112,116.113
    success: function(res) {
		//返回的内容处理请参考 http://lbs.qq.com/webservice_v1/guide-road.html
        console.log(res);
    },
    fail: function(res) {
        console.log(res);
    },
    complete: function(res) {
        console.log(res);
    }
});
```

js文件中有大量注释。官方文档传送门
 [http://lbs.qq.com/qqmap_wx_jssdk/index.html](http://lbs.qq.com/qqmap_wx_jssdk/index.html)
 做一下简单的使用摘要
 #简介#

腾讯位置服务为微信小程序提供了基础的标点能力、线和圆的绘制接口等地图组件和位置展示、地图选点等地图API位置服务能力支持，使得开发者可以自由地实现自己的微信小程序产品。 在此基础上，腾讯位置服务微信小程序JavaScript SDK是专为小程序开发者提供的LBS数据服务工具包，可以在小程序中调用腾讯位置服务的POI检索、关键词输入提示、地址解析、逆地址解析、行政区划和距离计算等数据服务，让您的小程序更强大！

##使用限制
为了保证我们的服务稳定，我们对每个key的每个服务接口的调用量做了如下限制：

* 日调用量：1万次 / Key
* 并发数：5次 / key / 秒 。
超过日调用量和并发数的开发者，可通过以下途径解决：
 1. 对于多频次的相同请求，可通过缓存结果，并定时访问更新的方式，减少对在线服务调用的依赖；
 2. 对于切实需要大配额来满足应用需求的，请根据[配额申请模板](模板是邮件正文格式，请勿发送附件)，编辑邮件发送至：mapapi@vip.qq.com;mapbd@tencent.com, 我们将对您的申请进行评估，并进行审批（3个工作日内），审批通过后将会获得您申请的配额
