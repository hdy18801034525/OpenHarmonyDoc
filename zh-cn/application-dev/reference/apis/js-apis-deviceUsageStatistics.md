# 设备使用信息统计

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```
import bundleState from '@ohos.bundleState'
```

## bundleState.isIdleState

isIdleState(bundleName: string, callback: AsyncCallback&lt;boolean&gt;): void

判断指定bundleName的应用当前是否是空闲状态，使用Callback形式返回。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | bundleName | string | 是 | 应用的bundleName。|
  | callback | AsyncCallback&lt;boolean&gt; | 是 | 指定的callback回调方法。如果指定的bundleName有效，则返回指定bundleName的应用当前是否是空闲状态；否则返回null。 |

**示例**：

  ```
    bundleState.isIdleState("com.ohos.camera", (err, res) => {
        if (err) {
            console.log('BUNDLE_ACTIVE isIdleState callback failed, because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE isIdleState callback succeeded, result: ' + JSON.stringify(res));
        }
    });
  ```

## bundleState.isIdleState

isIdleState(bundleName: string): Promise&lt;boolean&gt;

判断指定bundleName的应用当前是否是空闲状态，使用Promise形式返回。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | bundleName | string | 是 | 应用的bundleName。|

**返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;boolean&gt; | 指定的Promise回调方法。如果指定的bundleName有效，则返回指定bundleName的应用当前是否是空闲状态；否则返回null。 |

**示例**：

  ```js
    bundleState.isIdleState("com.ohos.camera").then( res => {
        console.log('BUNDLE_ACTIVE isIdleState promise succeeded, result: ' + JSON.stringify(res));
    }).catch( err => {
        console.log('BUNDLE_ACTIVE isIdleState promise failed, because: ' + err.code);
    });
  ```

## bundleState.queryAppUsagePriorityGroup

queryAppUsagePriorityGroup(callback: AsyncCallback&lt;number&gt;): void

查询（返回）当前调用者应用的使用优先级群组，使用Callback形式返回。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;number&gt; | 是 | 指定的callback回调方法。返回当前调用者应用的使用优先级群组。|

**示例**：

  ```js
    bundleState.queryAppUsagePriorityGroup((err, res) => {
        if (err) {
            console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup callback failed. because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup callback succeeded. result: ' + JSON.stringify(res));
        }
    });
  ```

## bundleState.queryAppUsagePriorityGroup

queryAppUsagePriorityGroup(): Promise&lt;number&gt;

查询（返回）当前调用者应用的使用优先级群组，使用Promise形式返回。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;number&gt; | 指定的Promise回调方法。查询（返回）当前调用者应用的使用优先级群组。|

**示例**：

  ```js
    bundleState.queryAppUsagePriorityGroup().then( res => {
        console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup promise succeeded. result: ' + JSON.stringify(res));
    }).catch( err => {
        console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup promise failed. because: ' + err.code);
    });
  ```

## bundleState.queryBundleStateInfos

queryBundleStateInfos(begin: number, end: number, callback: AsyncCallback&lt;BundleActiveInfoResponse&gt;): void

通过指定起始和结束时间查询应用使用时长统计信息，使用Callback形式返回。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|
  | callback | AsyncCallback&lt;[BundleActiveInfoResponse](#bundleactiveinforesponse)&gt; | 是 | 指定的callback回调方法。返回指定起始和结束时间内应用使用时长统计信息。|

**示例**：

  ```js
    bundleState.queryBundleStateInfos(0, 20000000000000, (err, res) => {
        if (err) {
            console.log('BUNDLE_ACTIVE queryBundleStateInfos callback failed, because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE queryBundleStateInfos callback success.');
            let i = 1;
            for(let key in res){
                console.log('BUNDLE_ACTIVE queryBundleStateInfos callback number : ' + i);
                console.log('BUNDLE_ACTIVE queryBundleStateInfos callback result ' + JSON.stringify(res[key]));
                i++;
            }
        }
    });
  ```

## bundleState.queryBundleStateInfos

queryBundleStateInfos(begin: number, end: number): Promise&lt;BundleActiveInfoResponse&gt;

通过指定起始和结束时间查询应用使用时长统计信息，使用Promise形式返回。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|

**返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;[BundleActiveInfoResponse](#bundleactiveinforesponse)&gt; | 指定的Promise回调方法。返回指定起始和结束时间内应用使用时长统计信息。|

**示例**：

  ```js
    bundleState.queryBundleStateInfos(0, 20000000000000).then( res => {
        console.log('BUNDLE_ACTIVE queryBundleStateInfos promise success.');
        let i = 1;
        for(let key in res){
            console.log('BUNDLE_ACTIVE queryBundleStateInfos promise number : ' + i);
            console.log('BUNDLE_ACTIVE queryBundleStateInfos promise result ' + JSON.stringify(res[key]));
            i++;
        }
    }).catch( err => {
        console.log('BUNDLE_ACTIVE queryBundleStateInfos promise failed, because: ' + err.code);
    });
  ```

## bundleState.queryBundleStateInfoByInterval

queryBundleStateInfoByInterval(byInterval: IntervalType, begin: number, end: number, callback: AsyncCallback&lt;Array&lt;BundleStateInfo&gt;&gt;): void

通过指定时间段间隔（天、周、月、年）查询应用使用时长统计信息，使用Callback形式返回。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | byInterval | [IntervalType](#intervaltype) | 是 | 查询类型。|
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|
  | callback | AsyncCallback&lt;Array&lt;[BundleStateInfo](#bundlestateinfo)&gt;&gt; | 是 | 指定的callback回调方法。返回指定时间段间隔（天、周、月、年）查询应用使用时长统计信息。|

**示例**：

  ```js
    bundleState.queryBundleStateInfoByInterval(0, 0, 20000000000000, (err, res) => {
        if (err) {
            console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback failed, because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback success.');
            for (let i = 0; i < res.length; i++) {
                console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback number : ' + (i + 1));
                console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback result ' + JSON.stringify(res[i]));
            }
        }
    });
  ```

## bundleState.queryBundleStateInfoByInterval

queryBundleStateInfoByInterval(byInterval: IntervalType, begin: number, end: number): Promise&lt;Array&lt;BundleStateInfo&gt;&gt;

通过指定时间段间隔（天、周、月、年）查询应用使用时长统计信息，使用Promise形式返回。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | byInterval | [IntervalType](#intervaltype) | 是 | 查询类型。|
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|

**返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;Array&lt;[BundleStateInfo](#bundlestateinfo)&gt;&gt; | 指定的Promise回调方法。返回指定时间段间隔（天、周、月、年）查询应用使用时长统计信息。|

**示例**：

  ```js
    bundleState.queryBundleStateInfoByInterval(0, 0, 20000000000000).then( res => {
        console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise success.');
        for (let i = 0; i < res.length; i++) {
            console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise number : ' + (i + 1));
            console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise result ' + JSON.stringify(res[i]));
        }
    }).catch( err => {
        console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval promise failed, because: ' + err.code);
    });
  ```

## bundleState.queryBundleActiveStates

queryBundleActiveStates(begin: number, end: number, callback: AsyncCallback&lt;Array&lt;BundleActiveState&gt;&gt;): void

通过指定起始和结束时间查询所有应用的事件集合，使用Callback形式返回。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|
  | callback | AsyncCallback&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | 是 | 指定的callback回调方法。返回指定起始和结束时间查询所有应用的事件集合。|

**示例**：

  ```js
    bundleState.queryBundleActiveStates(0, 20000000000000, (err, res) => {
        if (err) {
            console.log('BUNDLE_ACTIVE queryBundleActiveStates callback failed, because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE queryBundleActiveStates callback success.');
            for (let i = 0; i < res.length; i++) {
                console.log('BUNDLE_ACTIVE queryBundleActiveStates callback number : ' + (i + 1));
                console.log('BUNDLE_ACTIVE queryBundleActiveStates callback result ' + JSON.stringify(res[i]));
            }
        }
    });
  ```

## bundleState.queryBundleActiveStates

queryBundleActiveStates(begin: number, end: number): Promise&lt;Array&lt;BundleActiveState&gt;&gt;

通过指定起始和结束时间查询所有应用的事件集合，使用Promise形式返回。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|

**返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | 指定的Promise回调方法。返回指定起始和结束时间查询所有应用的事件集合。|

**示例**：

  ```js
    bundleState.queryBundleActiveStates(0, 20000000000000).then( res => {
        console.log('BUNDLE_ACTIVE queryBundleActiveStates promise success.');
        for (let i = 0; i < res.length; i++) {
            console.log('BUNDLE_ACTIVE queryBundleActiveStates promise number : ' + (i + 1));
            console.log('BUNDLE_ACTIVE queryBundleActiveStates promise result ' + JSON.stringify(res[i]));
        }
    }).catch( err => {
        console.log('BUNDLE_ACTIVE queryBundleActiveStates promise failed, because: ' + err.code);
    });
  ```

## bundleState.queryCurrentBundleActiveStates

queryCurrentBundleActiveStates(begin: number, end: number, callback: AsyncCallback&lt;Array&lt;BundleActiveState&gt;&gt;): void

通过指定起始和结束时间查询当前应用的事件集合，使用Callback形式返回。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|
  | callback | AsyncCallback&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | 是 | 指定的callback回调方法。返回指定起始和结束时间查询当前应用的事件集合。|

**示例**：

  ```js
    bundleState.queryCurrentBundleActiveStates(0, 20000000000000, (err, res) => {
        if (err) {
            console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback failed, because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback success.');
            for (let i = 0; i < res.length; i++) {
                console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback number : ' + (i + 1));
                console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback result ' + JSON.stringify(res[i]));
            }
        }
    });
  ```

## bundleState.queryCurrentBundleActiveStates

queryCurrentBundleActiveStates(begin: number, end: number): Promise&lt;Array&lt;BundleActiveState&gt;&gt;

通过指定起始和结束时间查询当前应用的事件集合，使用Promise形式返回。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | begin | number | 是 | 起始时间。|
  | end | number | 是 | 结束时间。|

**返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | 指定的Promise回调方法。返回指定起始和结束时间查询当前应用的事件集合。|

**示例**：

  ```js
    bundleState.queryCurrentBundleActiveStates(0, 20000000000000).then( res => {
        console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise success.');
        for (let i = 0; i < res.length; i++) {
            console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise number : ' + (i + 1));
            console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise result ' + JSON.stringify(res[i]));
        }
    }).catch( err => {
        console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates promise failed, because: ' + err.code);
    });
  ```

## bundleState.getRecentlyUsedModules<sup>9+</sup>

getRecentlyUsedModules(maxNum: number): Promise&lt;Array&lt;BundleActiveModuleInfo&gt;&gt;

据maxNum，查询FA使用记录，使用Promise形式返回不超过maxNum条FA使用记录，FA使用记录由近及远排序，maxNum最大为1000。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | maxNum | number | 否 | 返回条目的最大数量，最多支持1000条。若不填写，则默认为1000。|

**返回值**：

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;Array&lt;[BundleActiveModuleInfo](#bundleactivemoduleinfo9)&gt;&gt; | 指定的Promise回调方法。返回不超过maxNum条FA使用记录。|

**示例**：

  ```js
    bundleState.getRecentlyUsedModules(this.maxNum).then( res => {
        console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise succeeded');
        for (let i = 0; i < res.length; i++) {
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise number : ' + (i + 1));
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise result ' + JSON.stringify(res[i]));
        }
    }).catch( err=> {
        console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise failed, because: ' + err.code);
    });

    // 无maxNum参数调用方式
    bundleState.getRecentlyUsedModules().then( res => {
        console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise succeeded');
        for (let i = 0; i < res.length; i++) {
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise number : ' + (i + 1));
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise result ' + JSON.stringify(res[i]));
        }
    }).catch( err=> {
        console.log('BUNDLE_ACTIVE getRecentlyUsedModules promise failed, because: ' + err.code);
    });
  ```

## bundleState.getRecentlyUsedModules<sup>9+</sup>

getRecentlyUsedModules(maxNum: number, callback: AsyncCallback&lt;Array&lt;BundleActiveModuleInfo&gt;&gt;): void

查询FA使用记录。使用CallBack形式返回数量最大不超过maxNum设置的值，FA使用记录由近及远排序，maxNum最大为1000。

**需要权限**：ohos.permission.BUNDLE_ACTIVE_INFO

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | maxNum | number | 否 | 返回条目的最大数量，最多支持1000条。若不填写，则默认为1000。|
  | callback | AsyncCallback&lt;Array&lt;[BundleActiveModuleInfo](#bundleactivemoduleinfo9)&gt;&gt; | 是 | 指定的CallBack回调方法。返回不超过maxNum条FA使用记录。|

**示例**：

  ```js
    bundleState.getRecentlyUsedModules(this.maxNum,(err, res) => {
        if(err) {
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback failed, because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback succeeded.');
                for (let i = 0; i < res.length; i++) {
                    console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback number : ' + (i + 1));
                    console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback result ' + JSON.stringify(res[i]));
                }
        }
    });

    // 无maNum参数调用方式
    stats.getRecentlyUsedModules((err, res) => {
        if(err) {
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback failed, because: ' + err.code);
        } else {
            console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback succeeded.');
                for (let i = 0; i < res.length; i++) {
                    console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback number : ' + (i + 1));
                    console.log('BUNDLE_ACTIVE getRecentlyUsedModules callback result ' + JSON.stringify(res[i]));
                }
            }
    });
  ```

## BundleActiveModuleInfo<sup>9+</sup>
FA的使用信息的属性集合。

**系统能力**：以下各项对应的系统能力均为SystemCapability.ResourceSchedule.UsageStatistics.App

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| deviceId | string | 否 | FA所属deviceId。|
| bundleName | string | 是 | FA所属应用包名。|
| moduleName | string | 是 | FA所属module名。|
| abilityName | string | 否 | FA的MainAbility名。|
| appLabelId | number | 否 | FA的应用labelId。|
| labelId | number | 否 | FA所属module的labelId。|
| descriptionId | number | 否 | FA所属的应用descriptionId。|
| abilityLableId | number | 否 | FA的MainAbility labelId。|
| abilityDescriptionId | number | 否 | FA的MainAbility descriptionId。|
| abilityIconId | number | 否 | FA的MainAbility iconId。|
| launchedCount | number | 是 | FA的启动次数。|
| lastModuleUsedTime | number | 是 | FA的上一次使用时间。|
| formRecords | Array&lt;[BundleActiveFormInfo](#bundleactiveforminfo9)&gt; | 是 | FA中卡片的使用记录。|

## BundleActiveFormInfo<sup>9+</sup>
FA卡片的使用信息的属性集合。

**系统能力**：以下各项对应的系统能力均为SystemCapability.ResourceSchedule.UsageStatistics.App

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| formName | number | 是 | 卡片名称。|
| formDimension | number | 是 | 卡片尺寸。|
| formId | number | 是 | 卡片Id。|
| formLastUsedTime | number | 是 | 卡片的上一次点击时间。|
| count | number | 是 | 卡片的点击次数。|

## BundleStateInfo
提供应用使用时长的具体信息。

### 属性

**系统能力**：以下各项对应的系统能力均为SystemCapability.ResourceSchedule.UsageStatistics.App

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| bundleName | string | 是 | 应用包名。|
| abilityPrevAccessTime | number | 是 | 应用最后一次使用的时间。|
| abilityInFgTotalTime | number | 是 | 应用在前台使用的总时间。|
| id | number | 否 | 用户id。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| abilityPrevSeenTime | number | 否 | 应用最后一次在前台可见的时间。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| abilitySeenTotalTime | number | 否 | 应用在前台可见的总时间。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| fgAbilityAccessTotalTime | number | 否 | 应用访问前台的总时间。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| fgAbilityPrevAccessTime | number | 否 | 应用最后一次访问前台的时间。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| infosBeginTime | number | 否 | BundleActiveInfo对象中第一条应用使用统计的记录时间。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| infosEndTime | number | 否 | BundleActiveInfo对象中最后一条应用使用统计的记录时间。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|

### merge

merge(toMerge: BundleStateInfo): void

合并相同包名的应用使用信息。

本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

**参数**：

  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | toMerge | [BundleStateInfo](#bundlestateinfo) | 是 | 相同包名的应用使用统计信息。|

## BundleActiveState

提供应用事件的具体信息。

**系统能力**：以下各项对应的系统能力均为SystemCapability.ResourceSchedule.UsageStatistics.App

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| bundleName | string | 是 | 应用包名。|
| stateType | number | 是 | 应用事件类型。|
| stateOccurredTime | number | 是 | 应用事件发生的时间戳。|
| appUsagePriorityGroup | number | 否 | 应用程序的使用优先级组。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| indexOfLink | string | 否 | 快捷方式id。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|
| nameOfClass | string | 否 | 类名。<br>本接口在OpenHarmony 3.1 Release版本仅为接口定义，暂不支持使用。接口将在OpenHarmony 3.1 MR版本中提供使用支持。|

## BundleActiveInfoResponse

提供应用使用时长的具体信息。

**系统能力**：SystemCapability.ResourceSchedule.UsageStatistics.App

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| [key: string]: BundleStateInfo | [key: string]: [BundleStateInfo](#bundlestateinfo) | 是 | 不同应用的使用时长统计信息。|

## IntervalType

提供应用使用时长的查询类型。

**系统能力**：以下各项对应的系统能力均为SystemCapability.ResourceSchedule.UsageStatistics.App

|名称    |默认值    |说明|
| -------- | -------- | -------- |
| BY_OPTIMIZED | 0 | 表示系统自行判断最合适的查询类型（天、周、月、年）去查询指定时间段间隔的应用使用时长信息。|
| BY_DAILY | 1 | 表示系统按照天去查询指定时间段间隔的应用使用时长信息。|
| BY_WEEKLY | 2 | 表示系统按照周去查询指定时间段间隔的应用使用时长信息。|
| BY_MONTHLY | 3 | 表示系统按照月去查询指定时间段间隔的应用使用时长信息。|
| BY_ANNUALLY | 4 | 表示系统按照年去查询指定时间段间隔的应用使用时长信息。|