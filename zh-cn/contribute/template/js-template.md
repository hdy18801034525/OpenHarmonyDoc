# API接口说明模板

> *写作说明*
>
> 0.1 - 所有的写作说明，在完成写作后，都要删除。
>
> 0.2 - 上传路径：docs/zh-cn/application-dev/reference/apis，图片放到对应的figures文件夹中。上传后可通过提issue的方式，触发翻译。
>
> 0.3 - 一个d.ts文件对应一个js api接口文档。**文件名称：js-apis-模块名.md**。示例：
> 	媒体@ohos.multimedia.audio，文件命名为：js-apis-audio.md
> 	电话@ohos.telephony.sms，文件命名为：js-apis-sms.md
>
> 0.4 - 新增文件，需要修改对应的Readme，即docs/zh-cn/application-dev/reference/apis/Readme-CN.md。
>
> 0.5 - **文档标题**：使用中文短语概括本模块功能。但如果部分概念使用英文更便于开发者理解，不必强求，比方说，Ability、SIM卡等概念可以直接使用。
>
> 0.6 - 文档标题为一级标题；namespace下的属性字段、function、class、interface、enum、type为二级标题；class下的属性、function为三级标题。
>
> **版本说明**
>
> 0.7 - **对已有模块的新增接口标记起始版本：使用\<sup>标签，标记对应的版本号。**
> 	示例：API 6已有的模块，在API 7新增了一个属性字段，则在属性后加标记，即newAttribute<sup>7+</sup>。
> 	如果新增了一个方法，则在方法标题后增加标记，即 sim.getSimIccId<sup>7+</sup>，interface、class、枚举等同理。
>
> 0.8 - **废弃内容**：不能直接在文档上删去，在废弃内容后面加上标标注deprecated，并使用“>”引用语法建议使用的替代方式，加上对应的链接。
> 	示例：abandonmentMethod<sup>(deprecated) </sup>
>
> > 从API Version 7 开始不再维护，建议使用[newMethod](#newMethod)替代。
>
> 0.9 - **MR版本才能实现的空接口**，在接口的描述说明中，添加：
> 本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。
>
> **权限、syscap、系统API**
>
> 0.10 - **权限**：与代码保持一致，下沉到各个方法、枚举、属性字段中。采用格式：
>      （所有应用可申请）**需要权限：** ohos.permission.xxxx   
>      （仅系统应用可申请）**需要权限：** ohos.permission.xxxx，仅系统应用可用。
>
> 0.11 - **syscap**：
>   每个function需要进行描述：**系统能力**：SystemCapability.xxx.xxx
>   每个表格（属性、枚举、常量、变量）可统一进行说明，分两种情况：
>   每个表格下系统能力无差异的：
>   以下各项对应的系统能力均为SystemCapability.xxx.xxx。
>   有差异的：
>   以下各项对应的系统能力有所不同，详见下表。
>
> 0.12 - **系统API**：系统API需要增加描述：此接口为系统接口，三方应用不支持调用。
> 下面进入具体每个API的写作。

***
> *写作说明*
>
> 1.1 - 使用markdown的引用语法“>”对接口的起始版本进行说明。
>
> 1.2 - 一个模块只会有一个起始版本。
>
> 1.3 - 采用标准句式：“本模块首批接口从API version x开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。”x需要修改为对应的版本号。



> **说明**
>
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

模块说明。此处对该模块提供的功能、使用场景和使用建议进行简要描述。



## 导入模块

> *写作说明*
>
> 2.1 - 根据实际情况填写导入模块。采用代码段的样式，给出import语句。
>
> 2.2 - 如果没有导入模块，将“导入模块”修改为“使用说明”。
> 	使用说明案例：	
> 	在使用AbilityContext的功能前，需要通过[getContext()](链接到对应的接口说明文件中.md)先获取Context对象。
>
> ```js
> import ability_featureAbility from '@ohos.ability.featureAbility';
> var context = ability_featureAbility.getContext();
> ```

```js
import call from '@ohos.telephony.call';
```


## 属性

> *写作说明*
>
> 4.1 - 可选，如果没有属性可删除此二级标题。
>
> 4.2 - 类型如果为自定义类型，需要建立链接到对应的interface或enum中。
>
> 4.3 - 对于可读属性：如果取值为有特殊含义的有限值，需要进行枚举。
>
> 4.4 - 对于可写属性：如果仅支持固定字段，需要进行说明。
>
> 4.5 - 如果各项系统能力有差异，描述改为：以下各项对应的系统能力有所不同，详见下表。然后在各项里进行描述。参考[枚举的说明](#枚举)

**系统能力：** 以下各项对应的系统能力均为SystemCapability.xxx.xxx。（必选）

| 名称             | 类型                                      | 可读 | 可写 | 说明                                       |
| ---------------- | ----------------------------------------- | ---- | ---- | ------------------------------------------ |
| pluggedType      | [BatteryPluggedType](#BatteryPluggedType) | 是   | 否   | 表示当前设备连接的充电器类型。             |
| isBatteryPresent | boolean                                   | 是   | 否   | 表示当前设备是否支持电池或者电池是否在位。 |

## 枚举

> *写作说明*
>
> 5.1 - 可选，如果没有可删除。如果有多个枚举，请分多个二级内容描述，并使用“##”自行新建二级标题。
>
> 5.2 - 二级标题名为实际枚举名，比方说 BatteryHealthState 。

在此处给出该枚举类型的简要描述。如：表示连接的充电器类型的枚举。

**系统能力：** 以下各项对应的系统能力有所不同，详见下表。（必选）

| 名称 | 值   | 说明                                                         |
| ---- | ---- | ------------------------------------------------------------ |
| NONE | 1    | 表示连接的充电器类型未知。<br>**系统能力**：SystemCapability.xxx.xxx（必选） |

## 方法

> *写作说明*
>
> 6.1 - 可选，如果没有可删除。如果有多个方法，请分多个二级内容描述，并使用“##”自行新建二级标题。
>
> 6.2 - 二级标题名为方法名，采用导入类.方法名，如果是订阅方法，需要在方法名加上对应的订阅事件。
> 	示例： sim.getSimIccId
> 	订阅方法：sim.on('exampleEvent')
>
> 6.3 - **方法具体调用形式**：和d.ts保持一致，需要包括参数类型、参数名、返回值类型。
> 	示例：getNetworkState(slotId: number, callback: AsyncCallback\<NetworkState>): void
> 	注意：尖括号<>可能会被识别为标签，导致界面显示失效，可增加一个\，以保证界面正常显示，如“\\<>”或使用转义字符\&lt; \&gt; 。
>
> 6.4.1  - **方法描述**：对方法实现的功能进行描述，包括其使用的前提条件（*如：在xx方法调用后才能调用、需要确保网络已连接……*）、使用之后的影响（*如：调用该接口后再进行xx将不起效*）、**权限限制**、**系统能力**等。
>
> 6.4.2 - **异步方法描述**：存在大量异步方法，其返回方式需要在方法描述处进行说明。通过注册回调函数获取？还是通过Promise获取？
>
> 6.4.3 - **表格内换行**：markdown语法中，换行采用特殊标记\<br>

在此处给出方法的具体调用形式：（如果是静态方法需说明） 方法名称(参数1名称：参数1类型，参数2名称：参数2类型，……)：返回值类型

在此处给出方法描述。说明请参考6.4.1和6.4.2。

**需要权限**：ohos.permission.xxx（如不涉及可删除，如果是系统权限要说明）

**系统能力**：SystemCapability.xxx.xxx（必选）

**参数：** （可选，如不涉及可删除）

| 参数名       | 类型                                          | 必填 | 说明                                                         |
| ------------ | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| parameterOne | number \| string \| [CustomType](#CustomType) | 是   | 参数描述。给出取值范围、建议值。如果有固定格式，需要给出格式样例，尤其是URI。<br>自定义类型需要进行建链说明。 |
| callback     | Callback\<Array<[CustomType](#CustomType)>>   | 否   | 参数描述。可选参数需要说明不填写该参数的后果。<br>如：不填该参数则取消该type对应的所有回调。 |

**返回值**：（可选，如不涉及可删除）

| 类型                                       | 说明                                         |
| ------------------------------------------ | -------------------------------------------- |
| string                                     | 返回值描述。取到返回值之后，可以用来做什么。 |
| Promise\<Array<[CustomType](#CustomType)>> | 返回值描述。通过Promise获取了什么。          |

**示例：**

```js
// 必选项。
// 所有的示例代码需要进行自检。
// 不能出现缺符号、变量前后不一致等低错。
// 所有的使用到的变量要进行声明。
// 不允许直接写参数名，必须是可使用、易替代的实际用例。
// 如果非用户自定义填写，需通过注释进行说明。
// 示例：var result = xxx.createExample(parameterOne); // parameterOne由扫描自动获取
```

## Class/Interface

> *写作说明*
>
> 7.1 -  可选，如果没有可删除。如果有多个，请分多个二级内容描述，并使用“##”自行新建二级标题。
>
> 7.2 - 二级标题名为class、interface的名称。
>
> 7.3 - 如果该API中，既有属性，又有方法，需要先进行属性的写作，并使用“###”三级标题。
> 	如果该API中，只有属性，那么不需要新建三级标题，直接使用表格陈列属性，具体示例参考[CustomType](#CustomType)。

类描述/interface描述。如果有使用限制，需要在这个地方说明。比方说，是否有前提条件，是否需要通过什么方法先构造一个实例。 

### 属性

> *写作说明*
>
> 除标题使用三级标题外，其余要求同[属性](#属性)。

### Class/Interface中的方法

> *写作说明*
>
> 7.4 - 标题名为方法名，使用三级标题，**没有前缀**。如果是订阅方法，需要在方法名加上对应的订阅事件。
> 	示例： getSimIccId
> 	订阅方法：on('exampleEvent')
> 其余要求请参考[方法](#方法)中的说明。

在此处给出方法的具体调用形式。说明请参考6.3。

在此处给出方法描述。说明请参考6.4.1和6.4.2。

**需要权限**：ohos.permission.xxx（如不涉及可删除，如果是系统权限要说明）

**系统能力**：SystemCapability.xxx.xxx（必选）

**参数：** （可选，如不涉及可删除）

| 参数名       | 类型                                          | 必填 | 说明                                                         |
| ------------ | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| parameterOne | number \| string \| [CustomType](#CustomType) | 是   | 参数描述。给出取值范围、建议值。如果有固定格式，需要给出格式样例，尤其是URI。<br>自定义类型需要进行建链说明。 |
| callback     | Callback\<Array<[CustomType](#CustomType)>>   | 否   | 参数描述。可选参数需要说明不填写该参数的后果。<br>如：不填该参数则取消该type对应的所有回调。 |

**返回值**：（可选，如不涉及可删除）

| 类型                                       | 说明                                         |
| ------------------------------------------ | -------------------------------------------- |
| string                                     | 返回值描述。取到返回值之后，可以用来做什么。 |
| Promise\<Array<[CustomType](#CustomType)>> | 返回值描述。通过Promise获取了什么。          |

**示例：**

```js
// 必选项。
// 所有的示例代码需要进行自检。
// 不能出现缺符号、变量前后不一致等低错。
// 所有的使用到的变量要进行声明。
// 不允许直接写参数名，必须是可使用、易替代的实际用例。
// 如果非用户自定义填写，需通过注释进行说明。
// 示例：var result = xxx.createExample(parameterOne); // parameterOne由扫描自动获取
```

## CustomType

仅有k-v键值对的自定义类型示例。
**系统能力：** 以下各项对应的系统能力均为SystemCapability.xxx.xxx。（必选）

| 名称         | 类型                | 可读 | 可写 | 说明                                                         |
| ------------ | ------------------- | ---- | ---- | ------------------------------------------------------------ |
| parameterUrl | string              | 是   | 是   | 媒体输出URI。支持：<br/>1. 协议类型为“internal”的相对路径，示例如下：<br/>临时目录：internal://cache/test.mp4<br/><br/>2. 文件的绝对路径，示例如下：<br/>file:///data/data/ohos.xxx.xxx/files/test.mp4<br/> |
| parameterOne | [CustomEnum](#枚举) | 是   | 是   | 属性描述，要求与参数说明类似。                               |