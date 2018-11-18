# 微信小程序-组件 Toast
### 组件作者：史莱姆
#### 项目介绍
原创Toast 微信小程序组件

#### 安装教程

1. `app.json`:
加入组件索引声明
```javascript
"usingComponents": {
  "msg": "/component/Toast/Toast"
}
```
2. 在需要调用页面的WXML内写入
```html
<msg data="{{toast}}"></msg>
```

#### 使用说明

##### 文字调用
>弹出消息只需要调用setData,同时多次调用则会被加入任务列队，等待上一条Toast消失后显示下一条Toast，如果上一条显示时间为false则会直接显示，短时间内显示多条相同的Toast则会重合为两条
>[预览效果](https://github.com/shi-lai-mu/XCX-Toast/blob/master/images/%E6%96%87%E5%AD%97%E8%B0%83%E7%94%A8.gif)
>```javascript
>this.setData({
>    toast: {
>        text: "消息内容..."
>    }
>});
>```


##### 图标调用
>icon为图标类型 [预览效果](https://github.com/shi-lai-mu/XCX-Toast/blob/master/images/%E5%9B%BE%E6%A0%87%E8%B0%83%E7%94%A8.gif)
>```javascript
>this.setData({
>    toast: {
>        text: "消息内容...",
>        icon: "success"
>    }
>});
>```
>`自带图标类型`:
>- error  错误
>- success  正确
>- warning  警告
>- loading  加载中
>- zhiwen  指纹
>- saoma  扫码


##### 回调函数
>this指向为组件内部，指向page可使用箭头函数 [预览效果](https://github.com/shi-lai-mu/XCX-Toast/blob/master/images/%E5%9B%9E%E8%B0%83%E5%87%BD%E6%95%B0.gif)
>```javascript
>this.setData({
>    toast: {
>        text: "消息内容...",
>        icon: "success",
>        callback: function() {
>            console.log('Toast 消失时回调!');
>        }
>    }
>});
>```

##### 消失时间
>hideTime: 单位ms，默认 1500ms。false时为持续存在，除非下一个Toast出现或tosat值为空对象
>```javascript
>let self = this;
>this.setData({
>    toast: {
>        text: "操作成功!",
>        icon: "success",
>        callback: () => {
>            self.addLog('Toast 回调函数执行成功!');
>        },
>        hideTime: false
>    }
>});
>```

##### 按钮交互
>select: 传入数组,可多个按钮，默认灰色 [预览效果](https://github.com/shi-lai-mu/XCX-Toast/blob/master/images/%E6%8C%89%E9%92%AE%E4%BA%A4%E4%BA%92.gif)
>```javascript
>let self = this;
>this.setData({
>   toast: {
>       text: "操作成功!",
>       icon: "success",
>       callback: () => {
>           self.addLog('Toast 回调函数执行成功!');
>       },
>       hideTime: false,
>       select: [
>           {
>               text: '确定',
>               color: 'red',
>               click: function () {
>                   self.addLog('点击了 确定!');
>               }
>           },
>           {
>               text: '取消',
>               color: 'green',
>               click: function () {
>                   self.addLog('点击了 取消!');
>               }
>           },
>           {
>               text: '收起',
>               click: function () {
>                   self.setData({ toast: {} });
>               }
>           }
>       ]
>   }
>});
>```