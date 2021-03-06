# 延迟任务调度回调

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 9开始支持。API 9当前为Canary版本，仅供试用，不保证接口可稳定调用。


## 导入模块

```
import WorkSchedulerExtensionAbility from '@ohos.WorkSchedulerExtensionAbility'
```

## WorkSchedulerExtensionAbility.onWorkStart

onWorkStart(work: workScheduler.WorkInfo): void

延迟任务调度开始回调。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名  | 类型                    | 必填   | 说明             |
| ---- | --------------------- | ---- | -------------- |
| work | [workScheduler.WorkInfo](js-apis-workScheduler.md#workinfo) | 是    | 指示要添加到执行队列的工作。 |

**示例：** 

  ```
    export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
        onWorkStart(workInfo) {
            console.log('MyWorkSchedulerExtensionAbility onWorkStart' + JSON.stringify(workInfo));
        }
    }
  ```

## WorkSchedulerExtensionAbility.onWorkStop

onWorkStop(work: workScheduler.WorkInfo): void

延迟任务调度结束回调。

**系统能力：** SystemCapability.ResourceSchedule.WorkScheduler

**参数**：

| 参数名  | 类型                    | 必填   | 说明             |
| ---- | --------------------- | ---- | -------------- |
| work | [workScheduler.WorkInfo](js-apis-workScheduler.md#workinfo) | 是    | 指示要添加到执行队列的工作。 |


**示例：** 

  ```
    export default class MyWorkSchedulerExtensionAbility extends WorkSchedulerExtensionAbility {
        onWorkStop(workInfo) {
            console.log('MyWorkSchedulerExtensionAbility onWorkStop' + JSON.stringify(workInfo));
        }
    }
  ```