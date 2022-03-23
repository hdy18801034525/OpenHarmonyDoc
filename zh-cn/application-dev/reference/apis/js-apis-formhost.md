# FormHost

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

卡片使用方相关接口。

## 导入模块

```
import formHost from '@ohos.application.formHost';
```

## 权限

ohos.permission.REQUIRE_FORM

ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

## deleteForm

deleteForm(formId: string, callback: AsyncCallback&lt;void&gt;): void;

删除指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务不再保留有关该卡片的信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.deleteForm(formId, (error, data) => {
      if (error) {
          console.log('formHost deleteForm, error:' + error.code);
      }
  });
  ```

## deleteForm

deleteForm(formId: string): Promise&lt;void&gt;;

删除指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务不再保留有关该卡片的信息。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  ```js
  var formId = "12400633174999288";
  formHost.deleteForm(formId).catch((error) => {
      console.log('formProvider deleteForm, error:' + JSON.stringify(error));
  });
  ```

## releaseForm

releaseForm(formId: string, callback: AsyncCallback&lt;void&gt;): void;

释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，但卡片管理器服务仍然保留有关该卡片的缓存信息和存储信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.releaseForm(formId, (error, data) => {
      if (error) {
          console.log('formHost releaseForm, error:' + error.code);
      }
  });
  ```

## releaseForm

releaseForm(formId: string, isReleaseCache: boolean, callback: AsyncCallback&lt;void&gt;): void;

释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名         | 类型     | 必填 | 说明        |
  | -------------- | ------  | ---- | ----------- |
  | formId         | string  | 是   | 卡片标识     |
  | isReleaseCache | boolean | 是   | 是否释放缓存 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.releaseForm(formId, true, (error, data) => {
      if (error) {
          console.log('formHost releaseForm, error:' + error.code);
      }
  });
  ```

## releaseForm

releaseForm(formId: string, isReleaseCache?: boolean): Promise&lt;void&gt;;

释放指定的卡片。调用此方法后，应用程序将无法使用该卡片，卡片管理器服务保留有关该卡片的存储信息，可以选择是否保留缓存信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名         | 类型     | 必填 | 说明        |
  | -------------- | ------  | ---- | ----------- |
  | formId         | string  | 是   | 卡片标识     |
  | isReleaseCache | boolean | 否   | 是否释放缓存 |


**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.releaseForm(formId, true).catch((error) => {
      console.log('formProvider releaseForm, error:' + JSON.stringify(error));
  });
  ```

## requestForm

requestForm(formId: string, callback: AsyncCallback&lt;void&gt;): void;

请求卡片更新。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.requestForm(formId, (error, data) => {
      if (error) {
          console.log('formHost requestForm, error:' + error.code);
      }
  });
  ```

## requestForm

requestForm(formId: string): Promise&lt;void&gt;;

请求卡片更新。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.requestForm(formId).catch((error) => {
      console.log('formProvider requestForm, error:' + JSON.stringify(error));
  });
  ```

## castTempForm

castTempForm(formId: string, callback: AsyncCallback&lt;void&gt;): void;

将指定的临时卡片转换为普通卡片。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.castTempForm(formId, (error, data) => {
      if (error) {
          console.log('formHost castTempForm, error:' + error.code);
      }
  });
  ```

## castTempForm

castTempForm(formId: string): Promise&lt;void&gt;;

将指定的临时卡片转换为普通卡片。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.castTempForm(formId).catch((error) => {
      console.log('formProvider castTempForm, error:' + JSON.stringify(error));
  });
  ```

## notifyVisibleForms

notifyVisibleForms(formId: string, callback: AsyncCallback&lt;void&gt;): void;

向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.notifyVisibleForms(formId, (error, data) => {
      if (error) {
          console.log('formHost notifyVisibleForms, error:' + error.code);
      }
  });
  ```

## notifyVisibleForms

notifyVisibleForms(formId: string): Promise&lt;void&gt;;

向卡片框架发送通知以使指定的卡片可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.notifyVisibleForms(formId).catch((error) => {
      console.log('formProvider notifyVisibleForms, error:' + JSON.stringify(error));
  });
  ```

## notifyInvisibleForms

notifyInvisibleForms(formId: string, callback: AsyncCallback&lt;void&gt;): void;

向卡片框架发送通知以使指定的卡片不可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.notifyInvisibleForms(formId, (error, data) => {
      if (error) {
          console.log('formHost notifyInvisibleForms, error:' + error.code);
      }
  });
  ```

## notifyInvisibleForms

notifyInvisibleForms(formId: string): Promise&lt;void&gt;;

向卡片框架发送通知以使指定的卡片不可见。该方法调用成功后，会调用onVisibilityChange通知卡片提供方。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.notifyInvisibleForms(formId).catch((error) => {
      console.log('formProvider notifyInvisibleForms, error:' + JSON.stringify(error));
  });
  ```

## enableFormsUpdate

enableFormsUpdate(formId: string, callback: AsyncCallback&lt;void&gt;): void;

向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.enableFormsUpdate(formId, (error, data) => {
      if (error) {
          console.log('formHost enableFormsUpdate, error:' + error.code);
      }
  });
  ```

## enableFormsUpdate

enableFormsUpdate(formId: string): Promise&lt;void&gt;;

向卡片框架发送通知以使指定的卡片可以更新。该方法调用成功后，卡片刷新状态设置为使能，卡片可以接收来自卡片提供方的更新。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.enableFormsUpdate(formId).catch((error) => {
      console.log('formProvider enableFormsUpdate, error:' + JSON.stringify(error));
  });
  ```

## disableFormsUpdate

disableFormsUpdate(formId: string, callback: AsyncCallback&lt;void&gt;): void;

向卡片框架发送通知以使指定的卡片不可以更新。该方法调用成功后，卡片刷新状态设置为去使能，卡片不可以接收来自卡片提供方的更新。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.disableFormsUpdate(formId, (error, data) => {
      if (error) {
          console.log('formHost disableFormsUpdate, error:' + error.code);
      }
  });
  ```

## disableFormsUpdate

disableFormsUpdate(formId: string): Promise&lt;void&gt;;

向卡片框架发送通知以使指定的卡片不可以更新。该方法调用成功后，卡片刷新状态设置为去使能，卡片不可以接收来自卡片提供方的更新。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formId | string | 是   | 卡片标识 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.disableFormsUpdate(formId).catch((error) => {
      console.log('formProvider disableFormsUpdate, error:' + JSON.stringify(error));
  });
  ```

## isSystemReady

isSystemReady(callback: AsyncCallback&lt;void&gt;): void;

检查系统是否准备好。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.isSystemReady((error, data) => {
      if (error) {
          console.log('formHost isSystemReady, error:' + error.code);
      }
  });
  ```

## isSystemReady

isSystemReady(): Promise&lt;void&gt;;

检查系统是否准备好。

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formId = "12400633174999288";
  formHost.isSystemReady().catch((error) => {
      console.log('formProvider isSystemReady, error:' + JSON.stringify(error));
  });
  ```

## getAllFormsInfo

getAllFormsInfo(callback: AsyncCallback&lt;Array&lt;FormInfo&gt;&gt;): void;

获取设备上所有应用提供的卡片信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | callback | AsyncCallback&lt;Array&lt;[FormInfo](./js-apis-formInfo.md#forminfo-1)&gt;&gt; | 是 | callback形式返回查询到的卡片信息 |

**示例：**

  ```js
  formHost.getAllFormsInfo((error, data) => {
      if (error) {
          console.log('formHost getAllFormsInfo, error:' + error.code);
      }
  });
  ```

## getAllFormsInfo

getAllFormsInfo(): Promise&lt;Array&lt;FormInfo&gt;&gt;;

获取设备上所有应用提供的卡片信息。

**系统能力：**

SystemCapability.Ability.Form

**返回值：**

| 类型          | 说明                                |
| :------------ | :---------------------------------- |
| Promise&lt;Array&lt;[FormInfo](./js-apis-formInfo.md#forminfo-1)&gt;&gt; | Promise实例，用于获取异步返回查询到的卡片信息 |

**示例：**

  ```js
  formHost.getAllFormsInfo().catch((error) => {
      console.log('formProvider getAllFormsInfo, error:' + JSON.stringify(error));
  });
  ```

## getFormsInfo

getFormsInfo(bundleName: string, callback: AsyncCallback&lt;Array&lt;FormInfo&gt;&gt;): void;

获取设备上指定应用程序提供的卡片信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | bundleName | string | 是 |  要查询的应用程序包名称 |
  | callback | AsyncCallback&lt;Array&lt;[FormInfo](./js-apis-formInfo.md#forminfo-1)&gt;&gt; | 是 | callback形式返回查询到的卡片信息 |

**示例：**

  ```js
  formHost.getFormsInfo("com.example.ohos.accountjsdemo", (error, data) => {
      if (error) {
          console.log('formHost getFormsInfo, error:' + error.code);
      }
  });
  ```

## getFormsInfo

getFormsInfo(bundleName: string, moduleName: string, callback: AsyncCallback&lt;Array&lt;FormInfo&gt;&gt;): void;

获取设备上指定应用程序提供的卡片信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | bundleName | string | 是 |  要查询的应用程序包名称 |
  | moduleName | string | 是 |  要查询的模块名称 |
  | callback | AsyncCallback&lt;Array&lt;[FormInfo](./js-apis-formInfo.md#forminfo-1)&gt;&gt; | 是 | callback形式返回查询到的卡片信息 |

**示例：**

  ```js
  formHost.getFormsInfo("com.example.ohos.accountjsdemo", (error, data) => {
      if (error) {
          console.log('formHost getFormsInfo, error:' + error.code);
      }
  });
  ```

## getFormsInfo

getFormsInfo(bundleName: string, moduleName?: string): Promise&lt;Array&lt;FormInfo&gt;&gt;;

获取设备上所有应用提供的卡片信息。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | bundleName | string | 是 |  要查询的应用程序包名称 |
  | moduleName | string | 否 |  要查询的模块名称 |

**返回值：**

| 类型          | 说明                                |
| :------------ | :---------------------------------- |
| Promise&lt;Array&lt;[FormInfo](./js-apis-formInfo.md#forminfo-1)&gt;&gt; | Promise实例，用于获取异步返回查询到的卡片信息 |

**示例：**

  ```js
  formHost.getAllFormsInfo().catch((error) => {
      console.log('formProvider getAllFormsInfo, error:' + JSON.stringify(error));
  });
  ```

## deleteInvalidForms

deleteInvalidForms(formIds: Array&lt;string&gt;, callback: AsyncCallback&lt;number&gt;): void;

根据列表删除应用程序的无效卡片。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formIds | Array&lt;string&gt; | 是   | 卡片标识列表 |
  | callback | AsyncCallback&lt;number&gt; | 是 | callback形式返回删除的卡片个数 |

**示例：**

  ```js
  var formIds = new Array("12400633174999288", "12400633174999289");
  formHost.deleteInvalidForms(formIds, (error, data) => {
      if (error) {
          console.log('formHost deleteInvalidForms, error:' + error.code);
      }
  });
  ```

## deleteInvalidForms

function deleteInvalidForms(formIds: Array&ltstring&gt): Promise&lt;number&gt;;

根据列表删除应用程序的无效卡片。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formIds | Array&lt;string&gt; | 是   | 卡片标识列表 |

**返回值：**

| 类型          | 说明                                |
| :------------ | :---------------------------------- |
| Promise&lt;number&gt; | Promise实例，用于获取异步返回删除的卡片个数 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var formIds = new Array("12400633174999288", "12400633174999289");
  formHost.deleteInvalidForms(formIds).catch((error) => {
      console.log('formProvider deleteInvalidForms, error:' + JSON.stringify(error));
  });
  ```

## acquireFormState

acquireFormState(want: Want, callback: AsyncCallback&lt;FormStateInfo&gt;): void;

获取卡片状态

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | want | [Want](js-apis-featureAbility.md#want) | 是   | 查询卡片状态时携带的want信息 |
  | callback | AsyncCallback&lt;[FormStateInfo](./js-apis-formInfo.md#formstateinfo)&gt; | 是 | callback形式返回卡片状态 |

**示例：**

  ```js
  var want = {
  	"deviceId": "",
  	"bundleName": "com.extreme.test",
  	"abilityName": "com.extreme.test.MainAbility"
  };
  formHost.acquireFormState(want, (error, data) => {
      if (error) {
          console.log('formHost acquireFormState, error:' + error.code);
      }
  });
  ```

## acquireFormState

function acquireFormState(formIds: Array&ltstring&gt): Promise&lt;formInfo.FormStateInfo&gt;;

根据列表删除应用程序的无效卡片。

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formIds | Array&lt;string&gt; | 是   | 卡片标识列表 |

**返回值：**

| 类型          | 说明                                |
| :------------ | :---------------------------------- |
| Promise&lt;[FormStateInfo](./js-apis-formInfo.md#formstateinfo)&gt; | Promise实例，用于返回卡片状态 |

**系统能力：**

SystemCapability.Ability.Form

**示例：**

  ```js
  var want = {
  	"deviceId": "",
  	"bundleName": "com.extreme.test",
  	"abilityName": "com.extreme.test.MainAbility"
  };
  formHost.acquireFormState(want).catch((error) => {
      console.log('formProvider acquireFormState, error:' + JSON.stringify(error));
  });
  ```

## on("formUninstall")

on(type: "formUninstall", callback: Callback&lt;string&gt;): void;

获取卡片状态

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | type | string | 是   | 填写"formUninstall"，表示卡片卸载事件 |
  | callback | Callback&lt;string&gt; | 是 | 接口本身调用的回调方法 |

**示例：**

  ```js
  formHost.on("formUninstall", (error, data) => {
      if (error) {
          console.log('formHost on formUninstall, error:' + error.code);
      }
  });
  ```

## off("formUninstall")

off(type: "formUninstall", callback: Callback&lt;string&gt;): void;

获取卡片状态

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | type | string | 是   | 填写"formUninstall"，表示卡片卸载事件 |
  | callback | Callback&lt;string&gt; | 是 | 接口本身调用的回调方法 |

**示例：**

  ```js
  formHost.off("formUninstall", (error, data) => {
      if (error) {
          console.log('formHost off formUninstall, error:' + error.code);
      }
  });
  ```

## notifyFormsVisible

notifyFormsVisible(formIds: Array&lt;string&gt;, isVisible: boolean, callback: AsyncCallback&lt;void&gt;): void;

通知卡片是否可见。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formIds | Array&lt;string&gt; | 是   | 卡片标识列表 |
  | isVisible | boolean | 是   | 是否可见 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formIds = new Array("12400633174999288", "12400633174999289");
  formHost.notifyFormsVisible(formIds, true, (error, data) => {
      if (error) {
          console.log('formHost notifyFormsVisible, error:' + error.code);
      }
  });
  ```

## notifyFormsVisible

notifyFormsVisible(formIds: Array&lt;string&gt;, isVisible: boolean): Promise&lt;void&gt;;

通知卡片是否可见。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formIds | Array&lt;string&gt; | 是   | 卡片标识列表 |
  | isVisible | boolean | 是   | 是否可见 |

**示例：**

  ```js
  var formIds = new Array("12400633174999288", "12400633174999289");
  formHost.notifyFormsVisible(formIds, true).catch((error) => {
      console.log('formProvider notifyFormsVisible, error:' + JSON.stringify(error));
  });
  ```

## notifyFormsEnableUpdate

notifyFormsEnableUpdate(formIds: Array&lt;string&gt;, isEnableUpdate: boolean, callback: AsyncCallback&lt;void&gt;): void;

通知卡片是否启用更新状态。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formIds | Array&lt;string&gt; | 是   | 卡片标识列表 |
  | isEnableUpdate | boolean | 是   | 是否使能更新 |
  | callback | AsyncCallback&lt;void&gt; | 是 | callback形式返回启动结果 |

**示例：**

  ```js
  var formIds = new Array("12400633174999288", "12400633174999289");
  formHost.notifyFormsEnableUpdate(formIds, true, (error, data) => {
      if (error) {
          console.log('formHost notifyFormsEnableUpdate, error:' + error.code);
      }
  });
  ```

## notifyFormsEnableUpdate

notifyFormsEnableUpdate(formIds: Array&lt;string&gt;, isEnableUpdate: boolean): Promise&lt;void&gt;;

通知卡片是否启用更新状态。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明    |
  | ------ | ------ | ---- | ------- |
  | formIds | Array&lt;string&gt; | 是   | 卡片标识列表 |
  | isEnableUpdate | boolean | 是   | 是否使能更新 |

**示例：**

  ```js
  var formIds = new Array("12400633174999288", "12400633174999289");
  formHost.notifyFormsEnableUpdate(formIds, true).catch((error) => {
      console.log('formProvider notifyFormsEnableUpdate, error:' + JSON.stringify(error));
  });
  ```