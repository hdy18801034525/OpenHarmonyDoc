# 组合按键


> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口均为系统接口，三方应用不支持调用。


## 导入模块


```
import inputConsumer from '@ohos.multimodalInput.inputConsumer';
```


## inputConsumer.on

on(type: "key", keyOption: KeyOption, callback: Callback&lt;KeyOption&gt;): void

开始监听组合按键事件, 当满足条件的组合按键输入事件发生时，将KeyOption回调到入参callback表示的回调函数上。

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：** 

| 参数 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| type | string | 是 | 监听输入事件类型，只支持“key”。 | 
| keyOption | [KeyOption](#keyoption) | 是 | 组合键选项，用来指定组合键输入时应该符合的条件。 | 
| callback | Callback&lt;KeyOption&gt; | 是 | 回调函数。当满足条件的按键输入产生时，回调到此函数，以传入的keyOption为入参。 | 

**示例：** 

```
let keyOption = {preKeys: [], finalKey: 3, isFinalKeyDown: true, finalKeyDownDuration: 0}
let callback = function(keyOption) {
    console.info("preKeys: " + keyOption.preKeys, "finalKey: " + keyOption.finalKey, 
                 "isFinalKeyDown: " + keyOption.isFinalKeyDown, "finalKeyDownDuration: " + keyOption.finalKeyDownDuration)
}
inputConsumer.on('key', keyOption, callback);
```


## inputConsumer.off

off(type: "key", keyOption: KeyOption, callback: Callback&lt;KeyOption&gt;): void

停止监听组合按键事件。

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**参数：** 

| 参数 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| type | string | 是 | 监听输入事件类型，只支持“key”。 | 
| keyOption | [KeyOption](#keyoption) | 是 | 开始监听时传入的KeyOption。 | 
| callback | Callback&lt;KeyOption&gt; | 是 | 开始监听时与KeyOption一同传入的回调函数&nbsp;。 | 

**示例：** 

```
let keyOption = {preKeys: [], finalKey: 3, isFinalKeyDown: true, finalKeyDownDuration: 0}
let callback = function(keyOption) {
    console.info("preKeys: " + keyOption.preKeys, "finalKey: " + keyOption.finalKey, 
                 "isFinalKeyDown: " + keyOption.isFinalKeyDown, "finalKeyDownDuration: " + keyOption.finalKeyDownDuration)
}
inputConsumer.off('key', keyOption, callback);
```


## KeyOption

组合键输入事件发生时，组合键满足的选项。

**系统能力：** 以下各项对应系统能力均为SystemCapability.MultimodalInput.Input.InputConsumer

  | 参数 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| preKeys | Array | 是 | 组合键前置按键集合，可为空，前置按键无顺序要求。 | 
| finalKey | Number | 是 | 组合键最后按键，不能为空。 | 
| isFinalKeyDown | boolean | 是 | 组合键最后按键是按下还是抬起，默认是按下。 | 
| finalKeyDownDuration | Number | 是 | 组合键最后按键按下持续时长，默认无时长要求。 | 
