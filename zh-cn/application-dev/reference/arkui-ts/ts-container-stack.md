# Stack

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 该组件从API Version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。


## 权限列表

无


## 子组件

可以包含子组件。


## 接口

Stack(value:{alignContent?: Alignment})

- 参数
  | 参数名 | 参数类型 | 必填 | 默认值 | 参数描述 |
  | -------- | -------- | -------- | -------- | -------- |
  | alignContent | [Alignment](ts-appendix-enums.md#alignment枚举说明) | 否 | Center | 设置子组件在容器内的对齐方式。 |


## 示例

```
@Entry
@Component
struct StackExample {
  build() {
    Stack({ alignContent: Alignment.Bottom }) {
      Text('First child, show in bottom').width('90%').height('100%').backgroundColor(0xd2cab3).align(Alignment.Top)
      Text('Second child, show in top').width('70%').height('60%').backgroundColor(0xc1cbac).align(Alignment.Top)
    }.width('100%').height(150).margin({ top: 5 })
  }
}
```

![zh-cn_image_0000001219982699](figures/zh-cn_image_0000001219982699.jpg)