# FormProvider

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

卡片提供方相关接口。

## 导入模块

```
import formProvider from '@ohos.application.formProvider';
```

## 权限

无

## setFormNextRefreshTime

setFormNextRefreshTime(formId: string, minute: number, callback: AsyncCallback<void>): void;

设置指定卡片的下一次更新时间。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明                                   |
  | ------ | ------ | ---- | ------------------------------------- |
  | formId | string | 是   | 卡片标识                               |
  | minute | number | 是   | 指定多久之后更新，单位分钟，大于等于5     |

**示例：**

  ```js
  var formId = "12400633174999288";
  formProvider.setFormNextRefreshTime(formId, 5, (error, data) => {
      if (error) {
          console.log('formProvider setFormNextRefreshTime, error:' + error.code);
      }
  });
  ```

## setFormNextRefreshTime

setFormNextRefreshTime(formId: string, minute: number): Promise<void>;

设置指定卡片的下一次更新时间，以promise方式返回。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型    | 必填 | 说明                                   |
  | ------ | ------ | ---- | ------------------------------------- |
  | formId | string | 是   | 卡片标识                               |
  | minute | number | 是   | 指定多久之后更新，单位分钟，大于等于5     |

**示例：**

  ```js
  var formId = "12400633174999288";
  formProvider.setFormNextRefreshTime(formId, 5).catch((error) => {
      console.log('formProvider setFormNextRefreshTime, error:' + JSON.stringify(error));
  });
  ```

## updateForm

updateForm(formId: string, formBindingData: formBindingData.FormBindingData, callback: AsyncCallback<void>): void;

更新指定的卡片。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型                                                                    | 必填 | 说明             |
  | ------ | ---------------------------------------------------------------------- | ---- | ---------------- |
  | formId | string                                                                 | 是   | 请求更新的卡片标识 |
  | formBindingData | [FormBindingData](js-apis-formbindingdata.md#formbindingdata) | 是   | 用于更新的数据    |

**示例：**

  ```js
  import formBindingData from '@ohos.application.formBindingData';
  var formId = "12400633174999288";
  let obj = formBindingData.createFormBindingData({temperature:"22c", time:"22:00"});
  formProvider.updateForm(formId, obj, (error, data) => {
      if (error) {
          console.log('formProvider updateForm, error:' + error.code);
      }
  });
  ```

## updateForm

updateForm(formId: string, formBindingData: formBindingData.FormBindingData): Promise<void>;

更新指定的卡片，以promise方式返回。

**系统能力：**

SystemCapability.Ability.Form

**参数：**

  | 参数名 | 类型                                                                    | 必填 | 说明             |
  | ------ | ---------------------------------------------------------------------- | ---- | ---------------- |
  | formId | string                                                                 | 是   | 请求更新的卡片标识 |
  | formBindingData | [FormBindingData](js-apis-formbindingdata.md#formbindingdata) | 是   | 用于更新的数据    |

**示例：**

  ```js
  import formBindingData from '@ohos.application.formBindingData';
  var formId = "12400633174999288";
  let obj = formBindingData.createFormBindingData({temperature:"22c", time:"22:00"});
  formProvider.updateForm(formId, obj).catch((error) => {
      console.log('formProvider updateForm, error:' + JSON.stringify(error));
  });
  ```