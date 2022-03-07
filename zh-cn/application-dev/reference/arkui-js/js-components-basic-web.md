# web
展示网页内容的组件。
>![](../../public_sys-resources/icon-note.gif) **说明：** 
>   该组件从API version 6开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## 权限列表
ohos.permission.INTERNET

## 约束
web组件不跟随转场动画。一个页面仅支持一个web组件。

## 子组件
不支持。

## 属性

| 名称 | 参数类型 | 默认值 | 必填 | 描述 |
| -------- | -------- | -------- | -------- | -------- |
| src      | string |   -    |   否     |设置需要显示网页的地址，网址的域名必须为https协议且经过ICP备案。|
| id  | string | -  | 否  |  组件的唯一标识。  |


## 样式
仅支持通用样式中的width<sup>8+</sup>、height<sup>8+</sup>、padding<sup>8+</sup>、margin<sup>8+</sup>、border<sup>8+</sup>。

## 事件
仅支持如下事件：
| 名称 | 参数 | 描述 |
| -------- |  -------- | -------- |
| pagestart      | {url: string} | 加载网页时触发。 |
| pagefinish  | {url: string} |  网页加载结束时触发。  |
| error  | {url: string, errorCode: number, description: string} |  加载网页出现错误时触发或打开网页出错时触发。  |

## 方法
仅支持如下方法：
| 名称 | 参数 | 描述 |
| -------- |  -------- | -------- |
| reload      | - | 重新加载页面。 |

## 示例
```
<!-- xxx.hml -->
<div style="height: 500px; width: 500px; flex-direction: column;">
    <button onclick="reloadWeb">click to reload</button>
    <web src="www.example.com" id="web" onpagestart="pageStart" onpagefinish="pageFinish" on:error="pageError"></web>
</div>
```

```
<!-- xxx.js -->
export default {
    reloadWeb() {
        this.$element('web').reload()
    },

    pageStart: function(e) {
        console.info('web pageStart: ' + e.url)
    },

    pageFinish: function(e) {
        console.info('web pageFinish: ' + e.url)
    },

    pageError: function(e) {
        console.info('web pageError url: ' + e.url)
        console.info('web pageError errorCode: ' + e.errorCode)
        console.info('web pageError description: ' + e.description)
    }
}
```