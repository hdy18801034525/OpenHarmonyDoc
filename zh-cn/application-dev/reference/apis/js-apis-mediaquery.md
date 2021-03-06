# 媒体查询

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 从API Version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


## 导入模块

```
import mediaquery from '@ohos.mediaquery'
```


## 权限

无


## mediaquery.matchMediaSync

matchMediaSync(condition: string): MediaQueryListener

设置媒体查询的查询条件，并返回对应的监听句柄。

- 参数
  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | condition | string | 是 | 媒体事件的匹配条件。 | 

- 返回值
  | 类型 | 说明 | 
  | -------- | -------- |
  | MediaQueryListener | 媒体事件监听句柄，用于注册和去注册监听回调。 | 

- 示例
  ```
  listener = mediaquery.matchMediaSync('(orientation: landscape)'); //监听横屏事件
  ```


## MediaQueryListener

媒体查询的句柄，并包含了申请句柄时的首次查询结果。


### 属性

| 名称 | 参数类型 | 可读 | 可写 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| matches | boolean | 是 | 否 | 是否符合匹配条件。 | 
| media | string | 是 | 否 | 媒体事件的匹配条件。 | 


### on

on(type: 'change', callback: Callback&lt;MediaQueryResult&gt;): void

通过句柄向对应的查询条件注册回调，当媒体属性发生变更时会触发该回调。

- 参数
  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | type | string | 是 | 必须填写字符串'change'。 | 
  | callback | Callback&lt;MediaQueryResult&gt; | 是 | 向媒体查询注册的回调 | 

- 示例
  详见[off示例](#off)。


### off

off(type: 'change', callback?: Callback&lt;MediaQueryResult&gt;): void

通过句柄向对应的查询条件去注册回调，当媒体属性发生变更时不在触发指定的回调。
- 参数
  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | type | boolean | 是 | 必须填写字符串'change'。 | 
  | callback | Callback&lt;MediaQueryResult&gt; | 否 | 需要去注册的回调，如果参数缺省则去注册该句柄下所有的回调。 | 

- 示例
  ```
    import mediaquery from '@ohos.mediaquery'
    
    let listener = mediaquery.matchMediaSync('(orientation: landscape)'); //监听横屏事件
    function onPortrait(mediaQueryResult) {
        if (mediaQueryResult.matches) {
            // do something here
        } else {
            // do something here
        }
    }
    this.listener.on('change', this.onPortrait) // 注册回调
    this.listener.off('change', this.onPortrait) // 去注册回调
  ```


## MediaQueryResult


### 属性

| 名称 | 参数类型 | 可读 | 可写 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| matches | boolean | 是 | 否 | 是否符合匹配条件。 | 
| media | string | 是 | 否 | 媒体事件的匹配条件。 | 


### 示例

```
import mediaquery from '@ohos.mediaquery'

let portraitFunc = null

@Entry
@Component
struct MediaQueryExample {
  @State color: string = '#DB7093'
  @State text: string = 'Portrait'
  listener = mediaquery.matchMediaSync('(orientation: landscape)')

  onPortrait(mediaQueryResult) {
    if (mediaQueryResult.matches) {
      this.color = '#FFD700'
      this.text = 'Landscape'
    } else {
      this.color = '#DB7093'
      this.text = 'Portrait'
    }
  }

  aboutToAppear() {
    portraitFunc = this.onPortrait.bind(this) //bind current js instance
    this.listener.on('change', portraitFunc)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text(this.text).fontSize(24).fontColor(this.color)
    }
    .width('100%').height('100%')
  }
}
```