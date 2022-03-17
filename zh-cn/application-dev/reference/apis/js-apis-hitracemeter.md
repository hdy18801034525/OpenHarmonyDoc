# 性能打点

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```
import hiTraceMeter from '@ohos.hiTraceMeter';
```


## hiTraceMeter.startTrace

startTrace(name: string, taskId: number): void

标记一个预追踪耗时任务的开始，expectedTime是可选参数，标识该任务的期望耗时。

如果有多个相同name的任务需要追踪或者对同一个任务要追踪多次，并且任务同时被执行，则每次调用startTrace的taskId不相同。

如果具有相同name的任务是串行执行的，则taskId可以相同。具体示例可参考[hiTraceMeter.finishTrace](#hitracemeterfinishtrace)中的示例。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 要追踪的任务名称 |
| taskId | number | 是 | 任务id |

**示例：**

```
hiTraceMeter.startTrace("myTestFunc", 1);
hiTraceMeter.startTrace("myTestFunc", 1, 5); //从startTrace到finishTrace流程的耗时期望为5ms
```


## hiTraceMeter.finishTrace

finishTrace(name: string, taskId: number): void

标记一个预追踪耗时任务的结束。

finishTrace的name和taskId必须与流程开始的[startTrace](#hitracemeterstarttrace)对应参数值一致。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 要追踪的任务名称 |
| taskId | number | 是 | 任务id。 |

**示例：**

```
hiTraceMeter.finishTrace("myTestFunc", 1);
```

```
//追踪并行执行的同名任务
hiTraceMeter.startTrace("myTestFunc", 1);
//业务流程...... 
hiTraceMeter.startTrace("myTestFunc", 2);  //第二个追踪的任务开始，同时第一个追踪的同名任务还没结束，出现了并行执行，对应接口的taskId需要不同。
//业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 1);
//业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 2);
```

```
//追踪串行执行的同名任务
hiTraceMeter.startTrace("myTestFunc", 1);
//业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 1);  //第一个追踪的任务结束
//业务流程...... 
hiTraceMeter.startTrace("myTestFunc", 1);   //第二个追踪的同名任务开始，同名的待追踪任务串行执行。
//业务流程...... 
hiTraceMeter.finishTrace("myTestFunc", 1);
```


## hiTraceMeter.traceByValue

traceByValue(name: string, count: number): void

用来标记一个预追踪的数值变量，该变量的数值会不断变化。

**系统能力：** SystemCapability.HiviewDFX.HiTrace

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| name | string | 是 | 要追踪的数值变量名称 |
| count | number | 是 | 变量的值 |

**示例：**
```
let traceCount = 3;
hiTraceMeter.traceByValue("myTestCount", traceCount);
traceCount = 4;
hiTraceMeter.traceByValue("myTestCount", traceCount);
//业务流程......
```