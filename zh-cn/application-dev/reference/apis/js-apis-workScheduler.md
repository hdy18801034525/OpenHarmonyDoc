# 延迟任务调度

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```
import workScheduler from '@ohos.workScheduler' 
```

## workScheduler.startWork
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
workScheduler.startWork(work: WorkInfo): boolean

- **说明**：
通知WorkSchedulerService将工作添加到执行队列。

- **参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | work | WorkInfo | 是 | 指示要添加到执行队列的工作。 |

- **返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | 如果工作成功添加到执行队列，则返回true，否则返回false。 |

- **示例**：

  ```
    let workInfo = {
        workId: 1,
        batteryLevel:50,
        batteryStatus:workScheduler.BatteryStatus.BATTERY_STATUS_LOW,
        isRepeat: false,
        isPersisted: true,
        bundleName: "com.example.myapplication",
        abilityName: "MyExtension"
    }
    var res = workScheduler.startWork(workInfo);
    console.info("workschedulerLog res:" + res);
  ```

## workScheduler.stopWork
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
stopWork(work: WorkInfo, needCancel?: boolean): boolean

- **说明**：
通知WorkSchedulerService停止指定工作。

- **参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | work | WorkInfo | 是 | 指示要停止的工作。 |
  |needCancel|boolean|    是|    是否需要取消的工作。|

- **返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | 如果成功，则返回true，否则返回false。 |

- **示例**：

  ```
    let workInfo = {
        workId: 1,
        batteryLevel:50,
        batteryStatus:workScheduler.BatteryStatus.BATTERY_STATUS_LOW,
        isRepeat: false,
        isPersisted: true,
        bundleName: "com.example.myapplication",
        abilityName: "MyExtension"
       }
    var res = workScheduler.stopWork(workInfo, false);
    console.info("workschedulerLog res:" + res);
  ```

## workScheduler.getWorkStatus
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
getWorkStatus(workId: number, callback : AsyncCallback<WorkInfo>): void

- **说明**：
获取工作的最新状态，使用Callback形式返回。

- **参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | workId | number | 是 | work的id。 |
  |callback|AsyncCallback<WorkInfo>|    是|    指定的callback回调方法。如果指定的工作Id有效，则返回从WorkSchedulerService获取的有效工作状态；否则返回null。|


- **示例**：

  ```
    workScheduler.getWorkStatus(50, (err, res) => {
      if (err) {
        console.info('workschedulerLog getWorkStatus failed, because:' + err.data);
      } else {
        for (let item in res) {
          console.info('workschedulerLog getWorkStatus success,' + item + ' is:' + res[item]);
        }
      }
    });
  ```

## workScheduler.getWorkStatus
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
getWorkStatus(workID: number): Promise<WorkInfo>

- **说明**：
获取工作的最新状态，使用Promise形式返回。

- **参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | workId | number | 是 | work的id。 |

- **返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise<WorkInfo> | 指定的Promise回调方法。如果指定的工作ID有效，则返回从WorkSchedulerService获取的有效工作状态；否则返回null。 |

- **示例**：

  ```
    workScheduler.getWorkStatus(50).then((res) => {
      for (let item in res) {
        console.info('workschedulerLog getWorkStatus success,' + item + ' is:' + res[item]);
      }
    }).catch((err) => {
      console.info('workschedulerLog getWorkStatus failed, because:' + err.data);
    })
  ```

## workScheduler.obtainAllWorks
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
obtainAllWorks(callback : AsyncCallback<void>): Array<WorkInfo>

- **说明**：
获取与当前应用程序关联的所有工作，使用Callback形式返回。

- **参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  |callback|AsyncCallback<WorkInfo>|    是|    指定的callback回调方法。返回与应用程序关联的所有工作。|


- **返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Array<WorkInfo> | 返回与应用程序关联的所有工作。 |

- **示例**：

  ```
    workScheduler.obtainAllWorks((err, res) =>{
      if (err) {
        console.info('workschedulerLog obtainAllWorks failed, because:' + err.data);
      } else {
        console.info('workschedulerLog obtainAllWorks success, data is:' + JSON.stringify(res));
      }
    });
  ```

## workScheduler.obtainAllWorks
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
obtainAllWorks(): Promise<Array<WorkInfo>>

- **说明**：
获取与当前应用程序关联的所有工作，使用Promise形式返回。

- **返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise<Array<WorkInfo>> |    指定的Promise回调方法。返回与应用程序关联的所有工作。|

- **示例**：

  ```
    workScheduler.obtainAllWorks().then((res) => {
      console.info('workschedulerLog obtainAllWorks success, data is:' + JSON.stringify(res));
    }).catch((err) => {
      console.info('workschedulerLog obtainAllWorks failed, because:' + err.data);
    })
  ```

## workScheduler.stopAndClearWorks
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
stopAndClearWorks(): boolean

- **说明**：
停止和取消与当前应用程序关联的所有工作。

- **示例**：

  ```
    let res = workScheduler.stopAndClearWorks();
    console.info("workschedulerLog res:" + res);
  ```

## workScheduler.isLastWorkTimeOut
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
isLastWorkTimeOut(workId: number, callback : AsyncCallback<void>): boolean

- **说明**：
检查指定工作的最后一次执行是否为超时操作，使用Callback形式返回。

- **参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | workId | number | 是 | work的id。 |
  |callback|AsyncCallback<WorkInfo>|    是|    指定的callback回调方法。如果指定工作的最后一次执行是超时操作，则返回true；否则返回false。|

- **返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | 指定的callback回调方法。如果指定工作的最后一次执行是超时操作，则返回true；否则返回false。 |

- **示例**：

  ```
    workScheduler.isLastWorkTimeOut(500, (err, res) =>{
      if (err) {
        console.info('workschedulerLog isLastWorkTimeOut failed, because:' + err.data);
      } else {
        console.info('workschedulerLog isLastWorkTimeOut success, data is:' + res);
      }
    });
  ```

## workScheduler.isLastWorkTimeOut
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

- **接口**：
isLastWorkTimeOut(workId: number): Promise<boolean>

- **说明**：
检查指定工作的最后一次执行是否为超时操作，使用Promise形式返回。

- **参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | workId | number | 是 | work的id。 |

- **返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise<boolean> | 指定的Promise回调方法。如果指定工作的最后一次执行是超时操作，则返回true；否则返回false。|

- **示例**：

  ```
    workScheduler.isLastWorkTimeOut(500)
      .then(res => {
        console.info('workschedulerLog isLastWorkTimeOut success, data is:' + res);
      })
      .catch(err =>  {
        console.info('workschedulerLog isLastWorkTimeOut failed, because:' + err.data);
      });
    })
  ```

## workScheduler.WorkInfo
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

提供工作的具体信息。

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  |workId    |number    |是    |当前工作的ID。|
  |bundleName    |string    |是|    延迟任务包名。|
  |abilityName | string| 是| 延迟任务回调通知的组件名（必填）|
  |networkType | NetworkType| 否| 网络条件 |
  |isCharging | bool| 否|是否充电 |
  |chargerType | ChargingType| 否|充电类型 |
  |batteryLevel | number| 否|电量|
  |batteryStatus| BatteryStatus| 否|电池状态|
  |storageRequest|StorageRequest| 否|存储状态|
  |isRepeat|boolean|否|是否循环任务|
  |repeatCycleTime |number|否|循环间隔|
  |repeatCount    |number|否|循环次数|

## workScheduler.NetworkType
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

触发工作的网络类型。

  |名称    |默认值    |说明|
  | -------- | -------- | -------- |
  |NETWORK_TYPE_ANY    |0    |表示这个触发条件是任何类型的网络连接。|
  |NETWORK_TYPE_MOBILE    |1|    表示这个触发条件是Mobile网络连接。|
  |NETWORK_TYPE_WIFI    |2    |表示这个触发条件是Wifi类型的网络连接。|
  |NETWORK_TYPE_BLUETOOTH    |3    |表示这个触发条件是Bluetooth网络连接。|
  |NETWORK_TYPE_WIFI_P2P    |4    |表示这个触发条件是Wifi P2P网络连接。|
  |NETWORK_TYPE_ETHERNET    |5    |表示这个触发条件是有线网络连接。|

## workScheduler.ChargingType
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

触发工作的充电类型。

  |名称    |默认值    |说明|
  | -------- | -------- | -------- |
  |CHARGING_PLUGGED_ANY    |0|    表示这个触发条件是任何类型的充电器连接。|
  |CHARGING_PLUGGED_AC    |1    |表示这个触发条件是直流充电器连接。|
  |CHARGING_PLUGGED_USB    |2    |表示这个触发条件是USB充连接。|
  |CHARGING_PLUGGED_WIRELESS    |3|    表示这个触发条件是无线充电器连接。|

## workScheduler.BatteryStatus
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

触发工作的电池状态。

  |名称    |默认值    |说明|
  | -------- | -------- | -------- |
  |BATTERY_STATUS_LOW    |0    |表示这个触发条件是低电告警。|
  |BATTERY_STATUS_OKAY    |1|    表示这个触发条件是从低电恢复到正常电量。|
  |BATTERY_STATUS_LOW_OR_OKAY    |2    |表示这个触发条件是从低电恢复到正常电量或者低电告警。|

## workScheduler.StorageRequest
- **系统能力**：
SystemCapability.ResourceSchedule.WorkScheduler

触发工作的存储状态。

  |名称    |默认值    |说明|
  | -------- | -------- | -------- |
  |STORAGE_LEVEL_LOW    |0    |表示这个触发条件是存储空间不足。
  |STORAGE_LEVEL_OKAY    |1    |表示这个触发条件是从存储空间不足恢复到正常。
  |STORAGE_LEVEL_LOW_OR_OKAY    |2    |表示这个触发条件是从存储空间不足恢复到正常或者存储空间不足。