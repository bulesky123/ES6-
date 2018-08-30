# ES6
学习ES6的总结

```
一、暂时是死区：
case 1：
var a=123;
if(true){
  a = 'abc';//Uncaught ReferenceError: a is not defined
  let a;
  console.log(a);
}

注：在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）


case 2：
typeof x;
let x ; //Uncaught ReferenceError: x is not defined

//暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量。

二、块级作用域

case 1:
function a(){
  let name = 'xiaomao';
  if(true){
    let name = 'xiaogou';
    console.log(name);//xiaogou
  }
  console.log(name);//xiaomao
}

case 2:
{{{{
  {let insane = 'Hello World'}
  console.log(insane); // 报错  insane is not defined
}}}};

//const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，const只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了。因此，将一个对象声明为常量必须非常小心

case 3:
const foo = {};
// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123
// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only

三、变量的解构赋值



















```




# DataAcquisition 简介
一、页面访问量采集 ACQ01<br /><br />
二、按钮点击上报ACQ02<br /><br />
三、输入框采集ACQ03<br /><br />
四、代码异常采集 ACQ05<br /><br />
五、请求异常采集标记 ACQ16<br /><br />
六、页面时间采集标记、性能监控 ACQ17<br /><br />
## 目录结构简介
1、代码无任何依赖，直接导入即可使用，需要放在里面的最开始部分<br /><br />
defaultConfig.js----里面为初始配置项<br /><br />
```
const Config={//公共参数配置
    sessionId: generateSessionId(),
    ch_biz: 'zzbuyapp',
    appid: com.getAppId(),
    zuid: com.getStoreUuid(),
    appver: com.getAppver(),
    ch: com.getCh(),
    ch_sub: com.getChannelSub(),
    version: '1.0',//上报项版本
    district: 'cn',//国内：cn 印度尼西亚：id 越南：vn
    swv: com.getAppver(),//这个是客户端上报的字段（现在都统一加上）
    tokenId:createTokenId(),
    bizType:0,
    ugid:localStorage.getItem(config.USERGID_KEY)
}
```
# 统一配置项
```
store:{ //配置项
        storeVer     : '1.0.2',     //版本号
        storePage    : "ACQ01",    //页面采集标记
        storeInput   : "ACQ02",   //输入采集标记
        storeClick   : "ACQ03",    //点击事件采集标记
        storeCodeErr : "ACQ05",    //代码异常采集标记
        storeReqErr  : "ACQ16",    //请求异常采集标记 暂定 ACQ16
        storeTiming  : "ACQ17",    //页面时间采集标记 暂定 ACQ17
        referId      : "acquisitionPageReferId",  //上一页面eleId
        btnId        : "acquisitionPageBtnId",    ////上一页面跳转按钮eleId
        sendUrl      : url,   //log采集地址（需配置）
        selector     : "*[id^='zb_aci']",     //通过控制输入框的选择器来限定监听范围$("*[id^='qyd_aci']");
        acRange      : ['text','tel'],   //输入框采集范围
        userSha      : 'userSha',   //用户标识
        // classTag     : '',          //自动埋点,数据大
        idTag        : 'zb_acb',   //主动埋点标识
        maxDays      : 5,           //cookie期限
        acbLength    : 2,           //点击元素采集层数
        useStorage   : (typeof window.localStorage != 'undefined') ,       //自动检测是否使用storage，不要手动更改
        openInput    : true,        //是否开启输入数据采集
        openCodeErr  : true,        //是否开启代码异常采集
        openClick    : true,        //是否开启点击数据采集
        openAjaxData : true,        //是否采集接口异常时的参数params
        openAjaxHock : true,        //自动检测是否开启ajax异常采集,未使用jquery情况下自动关闭
        openPerformance : true      //是否开启页面性能采集
    }
```
