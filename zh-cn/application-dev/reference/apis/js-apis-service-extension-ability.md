# ServiceExtensionAbility

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


提供ServiceExtension服务扩展相关接口。


## 导入模块

```
import ServiceExtension from '@ohos.application.ServiceExtensionAbility';
```


## 权限

无


## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 参数类型 | 可读 | 可写 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| context | [ServiceExtensionContext](js-apis-service-extension-context.md)  | 是 | 否 | ServiceExtension的上下文环境，继承自ExtensionContext。 | 


## ServiceExtensionAbility.onCreate

onCreate(want: Want): void;

Extension生命周期回调，在创建时回调，执行初始化业务逻辑操作。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | want |  [Want](js-apis-application-Want.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 | 

**示例：**

  ```js
  class ServiceExt extends ServiceExtension {
    onCreate(want) {
      console.log('onCreate, want:' + want.abilityName);
    }
  }
  ```


## ServiceExtensionAbility.onDestroy

onDestroy(): void;

Extension生命周期回调，在销毁时回调，执行资源清理等操作。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**示例：**

  ```js
  class ServiceExt extends ServiceExtension {
    onDestroy() {
      console.log('onDestroy');
    }
  }
  ```


## ServiceExtensionAbility.onRequest

onRequest(want: Want, startId: number): void;

Extension生命周期回调，如果是startAbility拉起的服务，会在onCreate之后回调。每次拉起服务都会回调，startId会递增。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | want |  [Want](js-apis-application-Want.md) | 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 | 
  | startId | number | 是 | 返回拉起次数。首次拉起初始值返回1，多次之后自动递增。 | 

**示例：**

  ```js
  class ServiceExt extends ServiceExtension {
    onRequest(want, startId) {
      console.log('onRequest, want:' + want.abilityName);
    }
  }
  ```


## ServiceExtensionAbility.onConnect

onConnect(want: Want): rpc.RemoteObject;

Extension生命周期回调，如果是connectAbility拉起的服务，会在onCreate之后回调。返回一个RemoteObject对象，用于和客户端进行通信。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | want |  [Want](js-apis-application-Want.md)| 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 | 

**返回值：**

  | 类型 | 说明 | 
  | -------- | -------- |
  | rpc.RemoteObject | 一个RemoteObject对象，用于和客户端进行通信。 | 

**示例：**

  ```js
  import rpc from '@ohos.rpc'
  class StubTest extends rpc.RemoteObject{
      constructor(des) {
          super(des);
      }
      onRemoteRequest(code, data, reply, option) {
      }
  }
  class ServiceExt extends ServiceExtension {
    onConnect(want) {
      console.log('onConnect , want:' + want.abilityName);
      return new StubTest("test");
    }
  }
  ```


## ServiceExtensionAbility.onDisconnect

onDisconnect(want: Want): void;

Extension的生命周期，断开服务连接时回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | want |[Want](js-apis-application-Want.md)| 是 | 当前Extension相关的Want类型信息，包括ability名称、bundle名称等。 | 

**示例：**

  ```js
  class ServiceExt extends ServiceExtension {
    onDisconnect(want) {
      console.log('onDisconnect, want:' + want.abilityName);
    }
  }
  ```
