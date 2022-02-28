# ProcessRunningInfo

- [使用说明](#使用说明)
- [属性](#属性)


> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API 8开始支持。


进程运行信息。


## 使用说明


通过appManager来获取。


  
```
import appManager from '@ohos.application.appManager';
appManager.getProcessRunningInfos((error,data) => { 
    console.log("getProcessRunningInfos error: "  + error.code + " data: " + JSON.stringify(data));
});
```


## 属性

  | 名称 | 参数类型 | 可读 | 可写 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| pid | number | 是 | 否 | 进程ID。 | 
| uid | number | 是 | 否 | 用户ID。 | 
| processName | string | 是 | 否 | 进程名称。 | 
| bundleNames | Array&lt;string&gt; | 是 | 否 | 进程中所有运行的包名称。 | 