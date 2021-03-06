# CheckboxGroup

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 该组件从API Version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

多选框群组，用于控制多选框全选或者不全选状态。

## 权限列表

无

## 子组件

无

## 接口

CheckboxGroup( group?: string )

创建多选框群组，可以控制群组内的Checkbox全选或者不全选，相同group的Checkbox和CheckboxGroup为同一群组。

- 参数
  | 参数名 | 参数类型 | 必填 | 默认值 | 参数描述 |
  | -------- | -------- | -------- | -------- | -------- |
  | group | string | 否 | - | 群组名称。|


## 属性

| 名称 | 参数类型 | 默认值 | 描述 | 
| -------- | -------- | -------- | -------- |
| selectAll | bool | false | 设置是否全选。 | 
| selectedColor | Color | - | 设置被选中或部分选中状态的颜色。 | 

## 事件

| 名称 | 功能描述 | 
| -------- | -------- |
| onChange (callback: (names: Array&lt;string&gt;, status: SelectStatus) => void ) |CheckboxGroup的选中状态或群组内的Checkbox的选中状态发生变化时，触发回调。<br>- names：群组内所有被选中的多选框名称。<br>- status：选中状态。| 

- SelectStatus枚举说明
  | 名称  | 描述 | 
  | ----- | -------------------- |
  | All   | 群组多选择框全部选择。 |
  | Part  | 群组多选择框部分选择。 |
  | None  | 群组多选择框全部没有选择。 |


## 示例

```
@Entry
@Component
struct CheckboxExample {

  build() {
    Scroll() {
      Column() {
        CheckboxGroup({group : 'checkboxGroup'})
          .selectedColor(0xed6f21)
          .onChange((itemName:CheckboxGroupResult) => {
            console.info("TextPicker::dialogResult is" + JSON.stringify(itemName))
          })
        Checkbox({ name: 'checkbox1', group: 'checkboxGroup' })
          .select(true)
          .selectedColor(0x39a2db)
          .onChange((value: boolean) => {
            console.info('Checkbox1 change is' + value)
          })
        Checkbox({ name: 'checkbox2', group: 'checkboxGroup' })
          .select(false)
          .selectedColor(0x39a2db)
          .onChange((value: boolean) => {
            console.info('Checkbox2 change is' + value)
          })
        Checkbox({ name: 'checkbox3', group: 'checkboxGroup' })
          .select(true)
          .selectedColor(0x39a2db)
          .onChange((value: boolean) => {
            console.info('Checkbox3 change is' + value)
          })
      }
    }
  }
}
```
![](figures/checkboxgroup.gif)
