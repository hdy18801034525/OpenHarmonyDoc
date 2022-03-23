# Device Usage Statistics

> ![icon-note.gif](public_sys-resources/icon-note.gif) **NOTE**
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```
import bundleState from '@ohos.bundleState'
```

## bundleState.isIdleState
isIdleState(bundleName: string, callback: AsyncCallback&lt;boolean&gt;): void<br>
Checks whether the application specified by **bundleName** is in the idle state. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name of an application.|
| callback | AsyncCallback&lt;boolean&gt; | Yes| Callback used to return the result. Returns whether the application specified by **bundleName** is in the idle state if the value of **bundleName** is valid; returns **null** otherwise.|

**Example**

  ```
    bundleState.isIdleState("com.ohos.camera", (err, res) => {
        if(err.code === 0) {
            console.log('BUNDLE_ACTIVE isIdleState callback succeeded, result: ' + JSON.stringify(res));
        } else {
            console.log('BUNDLE_ACTIVE isIdleState callback failed, because: ' + err.code);
        }
    });
  ```

## bundleState.isIdleState
isIdleState(bundleName: string): Promise&lt;boolean&gt;<br>
Checks whether the application specified by **bundleName** is in the idle state. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Bundle name of an application.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;boolean&gt; | Promise used to return the result. Returns whether the application specified by **bundleName** is in the idle state if the value of **bundleName** is valid; returns **null** otherwise.|

**Example**

  ```
    bundleState.isIdleState("com.ohos.camera").then( res => {
        console.log('BUNDLE_ACTIVE isIdleState promise succeeded, result: ' + JSON.stringify(res));
    }).catch( err => {
        console.log('BUNDLE_ACTIVE isIdleState promise failed, because: ' + err.code);
    });
  ```

## bundleState.queryAppUsagePriorityGroup
queryAppUsagePriorityGroup(callback: AsyncCallback&lt;number&gt;): void<br>
Queries the priority group of the current invoker application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;number&gt; | Yes| Callback used to return the result.|

**Example**

  ```
    bundleState.queryAppUsagePriorityGroup((err, res) => {
        if(err.code === 0) {
            console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup callback succeeded. result: ' + JSON.stringify(res));
        } else {
            console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup callback failed. because: ' + err.code);
        }
    });
  ```

## bundleState.queryAppUsagePriorityGroup
queryAppUsagePriorityGroup(): Promise&lt;number&gt;<br>
Queries the priority group of the current invoker application. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.AppGroup

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Example**

  ```
    bundleState.queryAppUsagePriorityGroup().then( res => {
        console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup promise succeeded. result: ' + JSON.stringify(res));
    }).catch( err => {
        console.log('BUNDLE_ACTIVE queryAppUsagePriorityGroup promise failed. because: ' + err.code);
    });
  ```

## bundleState.queryBundleStateInfos
queryBundleStateInfos(begin: number, end: number, callback: AsyncCallback&lt;BundleActiveInfoResponse&gt;): void<br>
Queries the application usage duration statistics based on the specified start time and end time. This API uses an asynchronous callback to return the result.<br>
**Required permissions**: ohos.permission.BUNDLE_ACTIVE_INFO

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|
| callback | AsyncCallback&lt;[BundleActiveInfoResponse](#bundleactiveinforesponse)&gt; | Yes| Callback used to return the result.|

**Example**

  ```
    bundleState.queryBundleStateInfos(0, 20000000000000, (err, res) => {
        if(err.code == 0) {
            console.log('BUNDLE_ACTIVE queryBundleStateInfos callback success.');
            let i = 1;
            for(let key in res){
                console.log('BUNDLE_ACTIVE queryBundleStateInfos callback number : ' + i);
                console.log('BUNDLE_ACTIVE queryBundleStateInfos callback result ' + JSON.stringify(res[key]));
                i++;
            }
        } else {
            console.log('BUNDLE_ACTIVE queryBundleStateInfos callback failed, because: ' + err.code);
        }
    });
  ```

## bundleState.queryBundleStateInfos
queryBundleStateInfos(begin: number, end: number): Promise&lt;BundleActiveInfoResponse&gt;<br>
Queries the application usage duration statistics based on the specified start time and end time. This API uses a promise to return the result.<br>
**Required permissions**: ohos.permission.BUNDLE_ACTIVE_INFO

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[BundleActiveInfoResponse](#bundleactiveinforesponse)&gt; | Promise used to return the result.|

**Example**

  ```
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
queryBundleStateInfoByInterval(byInterval: IntervalType, begin: number, end: number, callback: AsyncCallback&lt;Array&lt;BundleStateInfo&gt;&gt;): void<br>
Queries the application usage duration statistics in the specified time frame at the specified interval (daily, weekly, monthly, or annually). This API uses an asynchronous callback to return the result.<br>
**Required permissions**: ohos.permission.BUNDLE_ACTIVE_INFO

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| byInterval | [IntervalType](#intervaltype) | Yes| Interval type.|
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|
| callback | AsyncCallback&lt;Array&lt;[BundleStateInfo](#bundlestateinfo)&gt;&gt; | Yes| Callback used to return the result.|

**Example**

  ```
    bundleState.queryBundleStateInfoByInterval(0, 0, 20000000000000, (err, res) => {
        if(err.code == 0) {
            console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback success.');
            for (let i = 0; i < res.length; i++) {
                console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback number : ' + (i + 1));
                console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback result ' + JSON.stringify(res[i]));
            }
        } else {
            console.log('BUNDLE_ACTIVE queryBundleStateInfoByInterval callback failed, because: ' + err.code);
        }
    });
  ```

## bundleState.queryBundleStateInfoByInterval
queryBundleStateInfoByInterval(byInterval: IntervalType, begin: number, end: number): Promise&lt;Array&lt;BundleStateInfo&gt;&gt;<br>
Queries the application usage duration statistics in the specified time frame at the specified interval (daily, weekly, monthly, or annually). This API uses a promise to return the result.<br>
**Required permissions**: ohos.permission.BUNDLE_ACTIVE_INFO

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| byInterval | [IntervalType](#intervaltype) | Yes| Interval type.|
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[BundleStateInfo](#bundlestateinfo)&gt;&gt; | Promise used to return the result.|

**Example**

  ```
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
queryBundleActiveStates(begin: number, end: number, callback: AsyncCallback&lt;Array&lt;BundleActiveState&gt;&gt;): void<br>
Queries events of all applications based on the specified start time and end time. This API uses an asynchronous callback to return the result.<br>
**Required permissions**: ohos.permission.BUNDLE_ACTIVE_INFO

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|
| callback | AsyncCallback&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | Yes| Callback used to return the result.|

**Example**

  ```
    bundleState.queryBundleActiveStates(0, 20000000000000, (err, res) => {
        if(err.code == 0) {
            console.log('BUNDLE_ACTIVE queryBundleActiveStates callback success.');
            for (let i = 0; i < res.length; i++) {
                console.log('BUNDLE_ACTIVE queryBundleActiveStates callback number : ' + (i + 1));
                console.log('BUNDLE_ACTIVE queryBundleActiveStates callback result ' + JSON.stringify(res[i]));
            }
        } else {
            console.log('BUNDLE_ACTIVE queryBundleActiveStates callback failed, because: ' + err.code);
        }
    });
  ```

## bundleState.queryBundleActiveStates
queryBundleActiveStates(begin: number, end: number): Promise&lt;Array&lt;BundleActiveState&gt;&gt;<br>
Queries events of all applications based on the specified start time and end time. This API uses a promise to return the result.<br>
**Required permissions**: ohos.permission.BUNDLE_ACTIVE_INFO

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | Promise used to return the result.|

**Example**

  ```
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
queryCurrentBundleActiveStates(begin: number, end: number, callback: AsyncCallback&lt;Array&lt;BundleActiveState&gt;&gt;): void<br>
Queries events of this application based on the specified start time and end time. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|
| callback | AsyncCallback&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | Yes| Callback used to return the result.|

**Example**

  ```
    bundleState.queryCurrentBundleActiveStates(0, 20000000000000, (err, res) => {
        if(err.code == 0) {
            console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback success.');
            for (let i = 0; i < res.length; i++) {
                console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback number : ' + (i + 1));
                console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback result ' + JSON.stringify(res[i]));
             }
        } else {
            console.log('BUNDLE_ACTIVE queryCurrentBundleActiveStates callback failed, because: ' + err.code);
        }
    });
  ```

## bundleState.queryCurrentBundleActiveStates
queryCurrentBundleActiveStates(begin: number, end: number): Promise&lt;Array&lt;BundleActiveState&gt;&gt;<br>
Queries events of this application based on the specified start time and end time. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| begin | number | Yes| Start time.|
| end | number | Yes| End time.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Array&lt;[BundleActiveState](#bundleactivestate)&gt;&gt; | Promise used to return the result.|

**Example**

  ```
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

## BundleStateInfo
Provides the usage duration information of an application.

### Attributes
**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Application bundle name.|
| abilityPrevAccessTime | number | Yes| Last time when the application was used.|
| abilityInFgTotalTime | number | Yes| Total time that the application runs in the foreground.|
| id | number | No| User ID.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| abilityPrevSeenTime | number | No| Last time when the application was visible in the foreground.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| abilitySeenTotalTime | number | No| Total time when the application is visible in the foreground.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| fgAbilityAccessTotalTime | number | No| Total time that the application accesses the foreground.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| fgAbilityPrevAccessTime | number | No| Last time when the application accessed the foreground.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| infosBeginTime | number | No| Time logged in the first application usage record in the **BundleActiveInfo** object.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| infosBeginTime | number | No| Time logged in the last application usage record in the **BundleActiveInfo** object.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|

### merge
merge(toMerge: BundleStateInfo): void

Merges the application usage information that has the same bundle name.<br>
This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| toMerge | [BundleStateInfo](#bundlestateinfo) | Yes| Application usage information to merge.|

## BundleActiveState
Provides information about an application event.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| bundleName | string | Yes| Application bundle name.|
| stateType | number | Yes| Application event type.|
| stateOccurredTime | number | Yes| Timestamp when the application event occurs.|
| appUsagePriorityGroup | number | No| Usage priority group of the application.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| indexOfLink | string | No| Shortcut ID.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| nameOfClass | string | No| Class name.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|

## BundleActiveInfoResponse
Provides the usage duration information of applications.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| [key: string]: BundleStateInfo | [BundleStateInfo](#bundlestateinfo) | Yes| Usage duration information by application.|

## IntervalType
Enumerates the interval types for querying the application usage duration.

**System capability**: SystemCapability.ResourceSchedule.UsageStatistics.App

|Name   |Default Value    |Description|
| -------- | -------- | -------- |
| BY_OPTIMIZED | 0 | The system obtains the application usage duration statistics in the specified time frame at the interval the system deems appropriate.|
| BY_DAILY | 1 | The system obtains the application usage duration statistics in the specified time frame on a daily basis.|
| BY_WEEKLY | 2 | The system obtains the application usage duration statistics in the specified time frame on a weekly basis.|
| BY_MONTHLY | 3 | The system obtains the application usage duration statistics in the specified time frame on a monthly basis.|
| BY_ANNUALLY | 4 | The system obtains the application usage duration statistics in the specified time frame on an annual basis.|