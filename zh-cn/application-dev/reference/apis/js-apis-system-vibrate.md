# 振动


> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> - 本模块首批接口从API version 4开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 从API Version 8开始，该接口不再维护，推荐使用新接口[vibrator](js-apis-vibrator.md)。
> - 该功能使用需要对应硬件支持，仅支持真机调试。


## 导入模块


```
import vibrator from '@system.vibrator';
```


## vibrator.vibrate

vibrate(Object): void

触发设备振动。

**参数：**

| 参数名 | 类型 | 必填 | 说明 | 
| -------- | -------- | -------- | -------- |
| mode | string | 否 | 振动的模式，其中long表示长振动，short表示短振动，默认值为long。 |

**示例：**

```
vibrator.vibrate({
  mode: 'short',
  success: function(ret) {
    console.log('vibrate is successful');
  },
  fail: function(ret) {
    console.log('vibrate is failed');
  },
  complete: function(ret) {
    console.log('vibrate is completed');
  }
});
```
