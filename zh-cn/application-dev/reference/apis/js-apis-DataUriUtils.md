# DataUriUtils模块

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```js
import dataUriUtils from '@ohos.ability.dataUriUtils';
```

## dataUriUtils.getId

getId(uri: string): number

获取附加到给定uri的路径组件末尾的ID。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 名称 | 类型   | 必填 | 描述                        |
| ---- | ------ | ---- | --------------------------- |
| uri  | string | 是   | 指示要从中获取ID的uri对象。 |

**返回值：**

| 类型   | 说明                     |
| ------ | ------------------------ |
| number | 附加到路径组件末尾的ID。 |

**示例：**

```js
dataUriUtils.getIdSync("com.example.dataUriUtils/1221")
```



## dataUriUtils.attachId

attachId(uri: string, id: number): string

将给定ID附加到给定uri的路径组件的末尾。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 名称 | 类型   | 必填 | 描述                        |
| ---- | ------ | ---- | --------------------------- |
| uri  | string | 是   | 指示要从中获取ID的uri对象。 |
| id   | number | 是   | 指示要附加的ID。            |

**返回值：**

| 类型   | 说明                  |
| ------ | --------------------- |
| string | 附加给定ID的uri对象。 |

**示例：**

```js
var idint = 1122;
dataUriUtils.attachId(
    "com.example.dataUriUtils",
	idint,
)
```



## dataUriUtils.deleteId

deleteId(uri: string): string

从给定uri的路径组件的末尾删除ID。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 名称 | 类型   | 必填 | 描述                        |
| ---- | ------ | ---- | --------------------------- |
| uri  | string | 是   | 指示要从中删除ID的uri对象。 |

**返回值：**

| 类型   | 说明                |
| ------ | ------------------- |
| string | ID已删除的uri对象。 |

**示例：**

```js
dataUriUtils.deleteId("com.example.dataUriUtils/1221")
```



## dataUriUtils.updateId

updateId(uri: string, id: number): string

更新指定uri中的ID。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 名称 | 类型   | 必填 | 描述                |
| ---- | ------ | ---- | ------------------- |
| uri  | string | 是   | 指示要更新的uri对象 |
| id   | number | 是   | 指示新ID            |

**返回值：**

| 类型   | 说明            |
| ------ | --------------- |
| string | 更新的uri对象。 |

**示例：**

```js
var idint = 1122;
dataUriUtils.updateId(
    "com.example.dataUriUtils",
	idint
)
```

