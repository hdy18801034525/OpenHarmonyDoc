# Context

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


提供开发者运行代码的上下文环境，包括应用信息、ResourceManager等信息。


## 使用说明


通过AbilityContext等继承实现。


## 属性

**系统能力**：以下各项对应的系统能力均为SystemCapability.Ability.AbilityRuntime.Core

  | 名称 | 参数类型 | 可读 | 可写 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| resourceManager | ResourceManager | 是 | 否 | ResourceManager对象。 | 
| applicationInfo | ApplicationInfo | 是 | 否 | 当前应用信息。 | 
| cacheDir | string | 是 | 否 | 应用在内部存储上的缓存路径。 | 
| tempDir | string | 是 | 否 | 应用的临时文件路径。 | 
| filesDir | string | 是 | 否 | 应用在内部存储上的文件路径。 | 
| databaseDir | string | 是 | 否 | 获取本地数据存储路径。 | 
| storageDir | string | 是 | 否 | 获取轻量级数据存储路径。 | 
| bundleCodeDir | string | 是 | 否 | 应用安装路径。 | 
| distributedFilesDir | string | 是 | 否 | 应用的分布式文件路径。 | 
| eventHub | [EventHub](js-apis-eventhub.md) | 是 | 否 | 事件中心信息。| 
| area | [AreaMode](#areamode) | 是 | 是 | 文件分区。| 


## Context.createBundleContext

createBundleContext(bundleName: string): Context;

创建指定应用上下文。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

  | 参数名 | 类型 | 必填 | 说明 | 
  | -------- | -------- | -------- | -------- |
  | bundleName | string | 是 | 应用bundle名。 | 

**返回值：**

  | 类型 | 说明 | 
  | -------- | -------- |
  | Context | 对应创建应用的上下文context。 | 

**示例：**
    
  ```js
  let test = "com.example.test";
  let context = this.context.createBundleContext(test);
  ```


## Context.getApplicationContext

getApplicationContext(): ApplicationContext;

获取当前applicationContext。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| ApplicationContext | 当前ApplicationContext对象信息。 |

**示例：**
    
  ```js
  // 必选项。
  let applicationContext = this.context.getApplicationContext();
  ```


## AreaMode

访问的文件分区，每个文件分区有对应自己的内容。

**系统能力**：以下各项对应的系统能力均为SystemCapability.Ability.AbilityRuntime.Core

| 变量            | 值    | 描述            |
| --------------- | ---- | --------------- |
| EL1             | 0    | 设备级加密区。   |
| EL2             | 1    | 用户凭据加密区。默认为EL2。 |
