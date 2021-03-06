# 应用打点

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```js
import hiAppEvent from '@ohos.hiAppEvent';
```


## hiAppEvent.write

write(eventName: string, eventType: EventType, keyValues: object, callback: AsyncCallback&lt;void&gt;): void

应用事件打点方法，将事件写入到当天的事件文件中，可接收类型为Json对象的事件参数，使用callback方式作为异步回调。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名    | 类型                      | 必填 | 说明                                                         |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| eventName | string                    | 是   | 应用事件名称。<br/>由开发者自定义。事件名称在48个字符以内，有效的字符是0-9、a-z、下划线，只能以字母开头。 |
| eventType | [EventType](#eventtype)   | 是   | 应用事件类型。                                               |
| keyValues | object                    | 是   | 事件参数键值对，如果是变长参数类型，则依次输入事件的参数名与参数值。如果是Json对象类型，则Json对象的key是事件的参数名，value是事件的参数值。<br/>- key类型只能为string，value类型只能为string、number、boolean、Array（数组数据类型只能为string、number、boolean）。<br/>- 事件的参数个数必须小于等于32。<br/>- 参数名在16个字符以内，有效的字符是0-9、a-z、下划线，只能以字母开头，不能以下划线结尾。<br/>- string类型参数值在8*1024个字符内。<br/>- Array类型参数值的元素个数必须在100个以内，超出时会进行截断处理。 |
| callback  | AsyncCallback&lt;void&gt; | 否   | 回调函数，可以在回调函数中处理接口返回值。<br/>-&nbsp;返回值为0表示事件校验成功，事件正常异步写入事件文件；<br/>-&nbsp;大于0表示事件校验存在异常参数，在忽略异常参数后将事件异步写入事件文件；<br/>-&nbsp;小于0表示事件校验失败，不将事件写入事件文件。 |

**示例：**

```js
hiAppEvent.write("test_event", hiAppEvent.EventType.FAULT, {"int_data":100, "str_data":"strValue"}, (err, value) => {
    if (err) {
        // 事件写入异常：事件存在异常参数时忽略异常参数后继续写入，或者事件校验失败时不执行写入
        console.error(`failed to write event because ${err.code}`);
        return;
    }

    // 事件写入正常
    console.log(`success to write event: ${value}`);
});
```


## hiAppEvent.write

write(eventName: string, eventType: EventType, keyValues: object): Promise&lt;void&gt;

应用事件打点方法，将事件写入到当天的事件文件中，可接收类型为Json对象的事件参数，使用promise方式作为异步回调。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名    | 类型                    | 必填 | 说明                                                         |
| --------- | ----------------------- | ---- | ------------------------------------------------------------ |
| eventName | string                  | 是   | 应用事件名称。<br/>由开发者自定义。事件名称在48个字符以内，有效的字符是0-9、a-z、下划线，只能以字母开头。 |
| eventType | [EventType](#eventtype) | 是   | 应用事件类型。                                               |
| keyValues | object                  | 是   | 事件参数键值对，如果是变长参数类型，则依次输入事件的参数名与参数值。如果是Json对象类型，则Json对象的key是事件的参数名，value是事件的参数值。<br/>- key类型只能为string，value类型只能为string、number、boolean、Array（数组数据类型只能为string、number、boolean）。<br/>- 事件的参数个数必须小于等于32。<br/>- 参数名在16个字符以内，有效的字符是0-9、a-z、下划线，只能以字母开头，不能以下划线结尾。<br/>- string类型参数值在8*1024个字符内。<br/>- Array类型参数值的元素个数必须在100个以内，超出时会进行截断处理。 |

**返回值：**

| 类型                | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise实例，可以在其then()、catch()方法中分别对事件写入成功、写入异常的情况进行回调处理。 |

**示例：**

```js
hiAppEvent.write("test_event", hiAppEvent.EventType.FAULT, {"int_data":100, "str_data":"strValue"})
    .then((value) => {
        // 事件写入正常
        console.log(`success to write event: ${value}`);
    }).catch((err) => {
        // 事件写入异常：事件存在异常参数时忽略异常参数后继续写入，或者事件校验失败时不执行写入
        console.error(`failed to write event because ${err.code}`);
    });
```


## hiAppEvent.configure

configure(config: ConfigOption): boolean

应用事件打点配置方法，可用于配置打点开关、文件目录存储限额大小等功能。

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型                          | 必填 | 说明                     |
| ------ | ----------------------------- | ---- | ------------------------ |
| config | [ConfigOption](#configoption) | 是   | 应用事件打点配置项对象。 |

**返回值：**

| 类型    | 说明                                                        |
| ------- | ----------------------------------------------------------- |
| boolean | 配置结果，true&nbsp;表示配置成功，false&nbsp;表示配置失败。 |

**示例：**
```js
// 配置应用事件打点功能开关
hiAppEvent.configure({
    disable: true
});

// 配置事件文件目录存储限额大小
hiAppEvent.configure({
    maxStorage: '100M'
});
```


## ConfigOption

此接口提供了应用打点的配置选项。

**系统能力：** 以下各项对应的系统能力均为SystemCapability.HiviewDFX.HiAppEvent。

| 参数名     | 类型    | 必填 | 说明                                                         |
| ---------- | ------- | ---- | ------------------------------------------------------------ |
| disable    | boolean | 否   | 应用打点功能开关。配置值为true表示关闭打点功能，false表示不关闭打点功能。 |
| maxStorage | string  | 否   | 打点数据本地存储文件所在目录的配额大小，默认限额为“10M”。所在目录大小超出限额后会对目录进行清理操作，会按从旧到新的顺序逐个删除打点数据文件，直到目录大小不超出限额时停止。 |


## EventType

事件类型枚举。

**系统能力：** 以下各项对应的系统能力均为SystemCapability.HiviewDFX.HiAppEvent。

| 名称      | 默认值 | 说明           |
| --------- | ------ | -------------- |
| FAULT     | 1      | 故障类型事件。 |
| STATISTIC | 2      | 统计类型事件。 |
| SECURITY  | 3      | 安全类型事件。 |
| BEHAVIOR  | 4      | 行为类型事件。 |


## Event

此接口提供了所有预定义事件的事件名称常量。

**系统能力：** 以下各项对应的系统能力均为SystemCapability.HiviewDFX.HiAppEvent。

| 名称                      | 参数类型 | 可读 | 可写 | 说明                 |
| ------------------------- | -------- | ---- | ---- | -------------------- |
| USER_LOGIN                | string   | 是   | 否   | 用户登录事件。       |
| USER_LOGOUT               | string   | 是   | 否   | 用户登出事件。       |
| DISTRIBUTED_SERVICE_START | string   | 是   | 否   | 分布式服务启动事件。 |


## Param

此接口提供了所有预定义参数的参数名称常量。

**系统能力：** 以下各项对应的系统能力均为SystemCapability.HiviewDFX.HiAppEvent。

| 名称                            | 参数类型 | 可读 | 可写 | 说明               |
| ------------------------------- | -------- | ---- | ---- | ------------------ |
| USER_ID                         | string   | 是   | 否   | 用户自定义ID。     |
| DISTRIBUTED_SERVICE_NAME        | string   | 是   | 否   | 分布式服务名称。   |
| DISTRIBUTED_SERVICE_INSTANCE_ID | string   | 是   | 否   | 分布式服务实例ID。 |