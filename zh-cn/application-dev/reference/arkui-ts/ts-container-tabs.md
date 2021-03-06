# Tabs

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 该组件从API Version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


一种可以通过页签进行内容视图切换的容器组件，每个页签对应一个内容视图。


## 权限列表

无


## 子组件

包含子组件[TabContent](ts-container-tabcontent.md)。


## 接口说明

Tabs(value: {barPosition?: BarPosition, index?: number, controller?: [TabsController](#tabscontroller)})

- 参数
  | 参数名 | 参数类型 | 必填 | 默认值 | 参数描述 |
  | -------- | -------- | -------- | -------- | -------- |
  | barPosition | BarPosition | 否 | BarPosition.Start | 指定页签位置来创建Tabs容器组件。 |
  | index | number | 否 | 0 | 指定初次初始页签索引。 |
  | controller | [TabsController](#tabscontroller) | 否 | - | 设置Tabs控制器。 |

- BarPosition枚举说明
  | 名称 | 描述 | 
  | -------- | -------- |
  | Start | vertical属性方法设置为true时，页签位于容器左侧；vertical属性方法设置为false时，页签位于容器顶部。 | 
  | End | vertical属性方法设置为true时，页签位于容器右侧；vertical属性方法设置为false时，页签位于容器底部。 | 


## 属性

不支持触摸热区设置。

| 名称 | 参数类型 | 默认值 | 描述 |
| -------- | -------- | -------- | -------- |
| vertical | boolean | 是否为纵向Tab，默认为false。 | 是否为纵向Tab，默认为false。 |
| scrollable | boolean | 是否可以通过左右滑动进行页面切换，默认为true。 | 是否可以通过左右滑动进行页面切换，默认为true。 |
| barMode | BarMode  | TabBar布局模式。 | TabBar布局模式。 |
| barWidth | number | TabBar的宽度值，不设置时使用系统主题中的默认值。 | TabBar的宽度值，不设置时使用系统主题中的默认值。 |
| barHeight | number | TabBar的高度值，不设置时使用系统主题中的默认值。 | TabBar的高度值，不设置时使用系统主题中的默认值**。** |
| animationDuration | number | 200 | TabContent滑动动画时长。 |

- BarMode枚举说明
  | 名称 | 描述 | 
  | -------- | -------- |
  | Scrollable | TabBar使用实际布局宽度,&nbsp;超过总长度后可滑动。 | 
  | Fixed | 所有TabBar平均分配宽度。 | 


## 事件

| 名称 | 功能描述 | 
| -------- | -------- |
| onChange(callback:&nbsp;(index:&nbsp;number)&nbsp;=&gt;&nbsp;void) | Tab页签切换后触发的事件。 | 

## TabsController

Tabs组件的控制器，用于控制Tabs组件进行页签切换。

### 导入对象

```
controller: TabsController = new TabsController()

```

### changeIndex

changeIndex(value: number): void

控制Tabs切换到指定页签。

- 参数
  | 参数名 | 参数类型 | 必填 | 默认值 | 参数描述 | 
  | -------- | -------- | -------- | -------- | -------- |
  | value | number | 是 | - | 页签在Tabs里的索引值，索引值从0开始。 |


## 示例

```
@Entry
@Component
struct TabsExample {
  private controller: TabsController = new TabsController()

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.Start, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar('pink')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Yellow)
        }.tabBar('yellow')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar('blue')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar('green')
      }
      .vertical(true).scrollable(true).barMode(BarMode.Fixed)
      .barWidth(70).barHeight(150).animationDuration(400)
      .onChange((index: number) => {
        console.info(index.toString())
      })
      .width('90%').backgroundColor(0xF5F5F5)
    }.width('100%').height(150).margin({ top: 5 })
  }
}
```

![zh-cn_image_0000001174264360](figures/zh-cn_image_0000001174264360.gif)
