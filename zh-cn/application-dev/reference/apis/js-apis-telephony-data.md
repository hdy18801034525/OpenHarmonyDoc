# 蜂窝数据

>**说明：** 
>
>本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。 

## 导入模块

```js
import data from '@ohos.telephony.data';
```

## data.getDefaultCellularDataSlotId

getDefaultCellularDataSlotId(callback: AsyncCallback\<number\>): void 

获取默认移动数据的SIM卡，使用callback方式作为异步方法。 

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Telephony.CellularData

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                       |
| -------- | ----------------------- | ---- | ------------------------------------------ |
| callback | AsyncCallback\<number\> | 是   | 回调函数。<br />0：卡槽1。<br />1：卡槽2。 |

**示例：**

```js
data.getDefaultCellularDataSlotId((err, data) => {
    console.log(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## data.getDefaultCellularDataSlotId

getDefaultCellularDataSlotId(): Promise\<number\> 

获取默认移动数据的SIM卡，使用Promise方式作为异步方法。 

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Telephony.CellularData

**返回值：**

| 类型              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| Promise\<number\> | 以Promise形式返回获取默认移动数据的SIM卡。<br />0：卡槽1。<br />1：卡槽2。 |

**示例：**

```js
let promise = data.getDefaultCellularDataSlotId();
promise.then((data) => {
    console.log(`test success, promise: data->${JSON.stringify(data)}`);
}).catch((err) => {
    console.error(`test fail, promise: err->${JSON.stringify(err)}`);
});
```

## data.getCellularDataFlowType

getCellularDataFlowType(callback: AsyncCallback\<DataFlowType\>): void

获取蜂窝数据业务的上下行状态，使用callback方式作为异步方法。

**系统能力**：SystemCapability.Telephony.CellularData

**参数：**

| 参数名   | 类型                                           | 必填 | 说明       |
| -------- | ---------------------------------------------- | ---- | ---------- |
| callback | AsyncCallback\<[DataFlowType](#dataflowtype)\> | 是   | 回调函数。 |

**示例：**

```js
data.getCellularDataFlowType((err, data) => {
    console.log(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## data.getCellularDataFlowType

getCellularDataFlowType(): Promise\<DataFlowType\>

获取蜂窝数据业务的上下行状态，使用Promise方式作为异步方法。

**系统能力**：SystemCapability.Telephony.CellularData

**返回值：**

| 类型                                     | 说明                                            |
| ---------------------------------------- | ----------------------------------------------- |
| Promise\<[DataFlowType](#dataflowtype)\> | 以Promise形式返回获取蜂窝数据业务的上下行状态。 |

**示例：**

```js
let promise = data.getCellularDataFlowType();
promise.then((data) => {
    console.log(`test success, promise: data->${JSON.stringify(data)}`);
}).catch((err) => {
    console.error(`test fail, promise: err->${JSON.stringify(err)}`);
});
```

## data.getCellularDataState

getCellularDataState(callback: AsyncCallback\<DataConnectState\>): void

获取分组交换域（PS域）的连接状态，使用callback方式作为异步方法。

**系统能力**：SystemCapability.Telephony.CellularData

**参数：**

| 参数名   | 类型                                                   | 必填 | 说明       |
| -------- | ------------------------------------------------------ | ---- | ---------- |
| callback | AsyncCallback\<[DataConnectState](#dataconnectstate)\> | 是   | 回调函数。 |

**示例：**

```js
data.getCellularDataState((err, data) => {
    console.log(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## data.getCellularDataState

getCellularDataState(): Promise\<DataConnectState\>

获取分组交换域(PS域)的连接状态，使用Promise方式作为异步方法。

**系统能力**：SystemCapability.Telephony.CellularData

**返回值：**

| 类型                                             | 说明                                  |
| ------------------------------------------------ | ------------------------------------- |
| Promise\<[DataConnectState](#dataconnectstate)\> | 以Promise形式返回获取PS域的连接状态。 |

**示例：**

```js
let promise = data.getCellularDataState();
promise.then((data) => {
    console.log(`test success, promise: data->${JSON.stringify(data)}`);
}).catch((err) => {
    console.error(`test fail, promise: err->${JSON.stringify(err)}`);
});
```

## data.isCellularDataEnabled

isCellularDataEnabled(callback: AsyncCallback\<boolean\>): void

检查蜂窝数据业务是否启用，使用callback方式作为异步方法。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Telephony.CellularData

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                         |
| -------- | ------------------------ | ---- | ------------------------------------------------------------ |
| callback | AsyncCallback\<boolean\> | 是   | 回调函数。<br />true：蜂窝数据业务已启用。<br />false：蜂窝数据业务已禁用。 |

**示例：**

```js
data.isCellularDataEnabled((err, data) => {
    console.log(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## data.isCellularDataEnabled

isCellularDataEnabled(): Promise\<boolean\>

检查蜂窝数据业务是否启用，使用Promise方式作为异步方法。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Telephony.CellularData

**返回值：**

| 类型               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| Promise\<boolean\> | 以Promise形式返回检查蜂窝数据业务是否启用。<br />true：蜂窝数据业务已启用。<br />false：蜂窝数据业务已禁用。 |

**示例：**

```js
let promise = data.isCellularDataEnabled();
promise.then((data) => {
    console.log(`test success, promise: data->${JSON.stringify(data)}`);
}).catch((err) => {
    console.error(`test fail, promise: err->${JSON.stringify(err)}`);
});
```

## data.isCellularDataRoamingEnabled

isCellularDataRoamingEnabled(slotId: number, callback: AsyncCallback\<boolean\>): void

检查蜂窝数据业务是否启用漫游，使用callback方式作为异步方法。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Telephony.CellularData

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                                         |
| -------- | ------------------------ | ---- | ------------------------------------------------------------ |
| slotId   | number                   | 是   | 卡槽ID。<br />0：卡槽1。<br />1：卡槽2。                     |
| callback | AsyncCallback\<boolean\> | 是   | 回调函数。<br />true：蜂窝数据业务已启用漫游。<br />false：蜂窝数据业务已禁用漫游。 |

**示例：**

```js
data.isCellularDataRoamingEnabled(0,(err, data) => {
    console.log(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

## data.isCellularDataRoamingEnabled

isCellularDataRoamingEnabled(slotId: number): Promise\<boolean\>

检查蜂窝数据业务是否启用漫游，使用Promise方式作为异步方法。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Telephony.CellularData

**参数：**

| 参数名 | 类型   | 必填 | 说明                                     |
| ------ | ------ | ---- | ---------------------------------------- |
| slotId | number | 是   | 卡槽ID。<br />0：卡槽1。<br />1：卡槽2。 |

**返回值：**

| 类型               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| Promise\<boolean\> | 以Promise形式返回检查蜂窝数据业务是否启用漫游。<br />true：蜂窝数据业务已启用漫游。<br />false：蜂窝数据业务已禁用漫游。 |

**示例：**

```js
let promise = data.isCellularDataRoamingEnabled(0);
promise.then((data) => {
    console.log(`test success, promise: data->${JSON.stringify(data)}`);
}).catch((err) => {
    console.error(`test fail, promise: err->${JSON.stringify(err)}`);
});
```

## DataFlowType

描述蜂窝数据流类型。 

**系统能力**：以下各项对应的系统能力均为SystemCapability.Telephony.CellularData。

| 名称                   | 值   | 说明                                       |
| ---------------------- | ---- | ------------------------------------------ |
| DATA_FLOW_TYPE_NONE    | 0    | 表示没有上行或下行数据。                   |
| DATA_FLOW_TYPE_DOWN    | 1    | 表示只有下行数据。                         |
| DATA_FLOW_TYPE_UP      | 2    | 表示只有上行数据。                         |
| DATA_FLOW_TYPE_UP_DOWN | 3    | 表示有上下行数据。                         |
| DATA_FLOW_TYPE_DORMANT | 4    | 表示没有上下行数据，底层链路处于休眠状态。 |

## DataConnectState

描述蜂窝数据链路连接状态。 

**系统能力**：以下各项对应的系统能力均为SystemCapability.Telephony.CellularData。

| 名称                    | 值   | 说明                       |
| ----------------------- | ---- | -------------------------- |
| DATA_STATE_UNKNOWN      | -1   | 表示蜂窝数据链路未知。     |
| DATA_STATE_DISCONNECTED | 0    | 表示蜂窝数据链路断开。     |
| DATA_STATE_CONNECTING   | 1    | 表示正在连接蜂窝数据链路。 |
| DATA_STATE_CONNECTED    | 2    | 表示蜂窝数据链路已连接。   |
| DATA_STATE_SUSPENDED    | 3    | 表示蜂窝数据链路被挂起。   |