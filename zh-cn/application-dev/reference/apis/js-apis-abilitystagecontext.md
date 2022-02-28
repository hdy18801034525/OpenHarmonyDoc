# AbilityStageContext

- [使用说明](#使用说明)
- [属性](#属性)


> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API 9开始支持。


AbilityStage的上下文环境，继承自[Context](js-apis-application-context.md)。


## 使用说明


通过AbilityStage实例来获取。


  
```
import AbilityStage from '@ohos.application.AbilityStage';
class MyAbilityStage extends AbilityStage {
    onCreate() {
        let abilityStageContext = this.context;
    }
}
```


## 属性

  | 名称 | 参数类型 | 可读 | 可写 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| currentHapModuleInfo | HapModuleInfo | 是 | 否 | AbilityStage对应的ModuleInfo对象。 | 
| config | [Configuration](js-apis-configuration.md) | 是 | 否 | 环境变化对象。 | 