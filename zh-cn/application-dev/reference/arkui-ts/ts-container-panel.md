# Panel

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 该组件从API Version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


可滑动面板。提供一种轻量的内容展示的窗口，可方便的在不同尺寸中切换，属于弹出式组件。


## 权限列表

无


## 子组件

可以包含子组件。


## 接口

Panel(value:{show：boolean})

- 参数
  | 参数名 | 参数类型 | 必填 | 默认值 | 参数描述 | 
  | -------- | -------- | -------- | -------- | -------- |
  | show | boolean | 是 | - | 控制Panel显示或隐藏。 | 


## 属性

| 名称 | 参数类型 | 默认值 | 描述 |
| -------- | -------- | -------- | -------- |
| type | PanelType | PanelType.Foldable | 设置可滑动面板的类型。 |
| mode | PanelMode | - | 设置可滑动面板的初始状态。 |
| dragBar | boolean | true | 设置是否存在dragbar，true表示存在，false表示不存在。 |
| fullHeight | Length | - | 指定PanelMode.Full状态下的高度。 |
| halfHeight | Length | - | 指定PanelMode.Half状态下的高度，默认为屏幕尺寸的一半。 |
| miniHeight | Length | - | 指定PanelMode.Mini状态下的高度。 |

- PanelType枚举说明
  | 名称 | 描述 | 
  | -------- | -------- |
  | Minibar | 提供minibar和类全屏展示切换效果。 | 
  | Foldable | 内容永久展示类，提供大（类全屏）、中（类半屏）、小三种尺寸展示切换效果。 | 
  | Temporary | 内容临时展示区，提供大（类全屏）、中（类半屏）两种尺寸展示切换效果。 | 

- PanelMode枚举说明
  | 名称 | 描述 | 
  | -------- | -------- |
  | Mini | 类型为minibar和foldable时，为最小状态；类型为temporary，则不生效。 | 
  | Half | 类型为foldable和temporary时，为类半屏状态；类型为minibar，则不生效。 | 
  | Full | 类全屏状态。 | 


## 事件

| 名称 | 功能描述 | 
| -------- | -------- |
| onChange(callback:&nbsp;(width:&nbsp;number,&nbsp;height:&nbsp;number,&nbsp;mode:&nbsp;PanelMode)&nbsp;=&gt;&nbsp;void) | 当可滑动面板发生状态变化时触发，&nbsp;返回的height值为内容区高度值，当dragbar属性为true时，panel本身的高度值为dragbar高度加上内容区高度。 | 


## 示例

```
@Entry
@Component
struct PanelExample {
  @State show: boolean = false

  build() {
    Column() {
      Text('2021-09-30    Today Calendar: 1.afternoon......Click for details')
        .width('90%').height(50).borderRadius(10)
        .backgroundColor(0xFFFFFF).padding({ left: 20 })
        .onClick(() => {
          this.show = !this.show
        })
      Panel(this.show) { // 展示日程
        Column() {
          Text('Today Calendar')
          Divider()
          Text('1. afternoon 4:00 The project meeting')
        }
      }
      .type(PanelType.Foldable).mode(PanelMode.Half)
      .dragBar(true) // 默认开启
      .halfHeight(500) // 默认一半
      .onChange((width: number, height: number, mode: PanelMode) => {
        console.info(`width:${width},height:${height},mode:${mode}`)
      })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

![zh-cn_image_0000001174422896](figures/zh-cn_image_0000001174422896.gif)
