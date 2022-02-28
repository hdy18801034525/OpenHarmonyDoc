# ConfigurationConstant

- [导入模块](#导入模块)
- [ColorMode](#ColorMode)
- [Direction](#Direction)
- [ScreenDensity](#ScreenDensity)


> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 8开始支持。


配置信息枚举值定义。


## 导入模块

  
```
import ConfigurationConstant from '@ohos.application.ConfigurationConstant';
```


## ColorMode

使用时通过ConfigurationConstant.ColorMode获取，示例：ConfigurationConstant.ColorMode.COLOR_MODE_LIGHT。


  | 名称 | 值 | 说明 | 
| -------- | -------- | -------- |
| COLOR_MODE_NOT_SET | -1 | 未设置颜色模式。 | 
| COLOR_MODE_DARK | 0 | 深色模式。 | 
| COLOR_MODE_LIGHT | 1 | 浅色模式。 | 


## Direction

使用时通过ConfigurationConstant.Direction获取，示例：ConfigurationConstant.Direction.DIRECTION_VERTICAL。


  | 名称 | 值 | 说明 | 
| -------- | -------- | -------- |
| DIRECTION_NOT_SET | -1 | 未设置方向。 | 
| DIRECTION_VERTICAL | 0 | 垂直方向。 | 
| DIRECTION_HORIZONTAL | 1 | 水平方向。 | 


## ScreenDensity

使用时通过ConfigurationConstant.ScreenDensity获取，示例：ConfigurationConstant.ScreenDensity.SCREEN_DENSITY_NOT_SET。


  | 名称 | 值 | 说明 | 
| -------- | -------- | -------- |
| SCREEN_DENSITY_NOT_SET | 0 | 未设置屏幕分辨率。 | 
| SCREEN_DENSITY_SDPI | 120 | 屏幕分辨率为"sdpi"。 | 
| SCREEN_DENSITY_MDPI | 160 | 屏幕分辨率为"mdpi"。 | 
| SCREEN_DENSITY_LDPI | 240 | 屏幕分辨率为"ldpi"。 | 
| SCREEN_DENSITY_XLDPI | 320 | 屏幕分辨率为"xldpi"。 | 
| SCREEN_DENSITY_XXLDPI | 480 | 屏幕分辨率为"xxldpi"。 | 
| SCREEN_DENSITY_XXXLDPI | 640 | 屏幕分辨率为"xxxldpi"。 | 