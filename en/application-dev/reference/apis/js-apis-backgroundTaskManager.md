# Background Task Management

> ![icon-note.gif](public_sys-resources/icon-note.gif) **NOTE**
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```
import backgroundTaskManager from '@ohos.backgroundTaskManager';  
```


## backgroundTaskManager.requestSuspendDelay

requestSuspendDelay(reason: string, callback: Callback&lt;void&gt;): DelaySuspendInfo

Requests delayed suspension after the application switches to the background.

The default duration of delayed suspension is 180000 when the battery level is higher than or equal to the broadcast low battery level and 60000 when the battery level is lower than the broadcast low battery level.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**
| Name     | Type                  | Mandatory  | Description                            |
| -------- | -------------------- | ---- | ------------------------------ |
| reason   | string               | Yes   | Reason for delayed transition to the suspended state.                    |
| callback | Callback&lt;void&gt; | Yes   | Invoked when a delay is about to time out. Generally, this callback is used to notify the application 6 seconds before the delay times out. |

**Return value**
| Type                                   | Description       |
| ------------------------------------- | --------- |
| [DelaySuspendInfo](#delaysuspendinfo) | Information about the suspension delay.|

**Example**

  ```js
  let myReason = 'test requestSuspendDelay';
  let delayInfo = backgroundTaskManager.requestSuspendDelay(myReason, () => {
      console.info("Request suspension delay will time out.");
  })
  
  var id = delayInfo.requestId;
  var time = delayInfo.actualDelayTime;
  console.info("The requestId is: " + id);
  console.info("The actualDelayTime is: " + time);
  ```


## backgroundTaskManager.getRemainingDelayTime

getRemainingDelayTime(requestId: number, callback: AsyncCallback&lt;number&gt;): void

Obtains the remaining duration before the application is suspended. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**
| Name      | Type                         | Mandatory  | Description                                      |
| --------- | --------------------------- | ---- | ---------------------------------------- |
| requestId | number                      | Yes   | ID of the suspension delay request.                              |
| callback  | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the remaining duration before the application is suspended, in milliseconds.|

**Example**

  ```js
  let id = 1;
  backgroundTaskManager.getRemainingDelayTime(id, (err, res) => {
      if(err.data === 0) {
          console.log('callback => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
      } else {
          console.log('callback => Operation getRemainingDelayTime failed. Cause: ' + err.data);
      }
  })
  ```


## backgroundTaskManager.getRemainingDelayTime

getRemainingDelayTime(requestId: number): Promise&lt;number&gt;

Obtains the remaining duration before the application is suspended. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**
| Name      | Type    | Mandatory  | Description        |
| --------- | ------ | ---- | ---------- |
| requestId | number | Yes   | ID of the suspension delay request.|

**Return value**
| Type                   | Description                                      |
| --------------------- | ---------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the remaining duration before the application is suspended, in milliseconds.|

**Example**
  ```js
  let id = 1;
  backgroundTaskManager.getRemainingDelayTime(id).then( res => {
      console.log('promise => Operation getRemainingDelayTime succeeded. Data: ' + JSON.stringify(res));
  }).catch( err => {
      console.log('promise => Operation getRemainingDelayTime failed. Cause: ' + err.data);
  })
  ```


## backgroundTaskManager.cancelSuspendDelay

cancelSuspendDelay(requestId: number): void

Cancels the suspension delay.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

**Parameters**
| Name      | Type    | Mandatory  | Description        |
| --------- | ------ | ---- | ---------- |
| requestId | number | Yes   | ID of the suspension delay request.|

**Example**
  ```js
  backgroundTaskManager.cancelSuspendDelay(id);
  ```


## backgroundTaskManager.startBackgroundRunning<sup>8+</sup>

startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent, callback: AsyncCallback&lt;void&gt;): void

Requests a continuous task from the system. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**
| Name      | Type                                | Mandatory  | Description                      |
| --------- | ---------------------------------- | ---- | ------------------------ |
| context   | [Context](js-apis-Context.md)      | Yes   | Application context.               |
| bgMode    | [BackgroundMode](#backgroundmode8) | Yes   | Background mode requested.             |
| wantAgent | [WantAgent](js-apis-wantAgent.md)  | Yes   | Notification parameter, which is used to specify the target page that is redirected to when a continuous task notification is clicked.|
| callback  | AsyncCallback&lt;void&gt;          | Yes   | Callback used to return the result.  |

**Example**
```js
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import featureAbility from '@ohos.ability.featureAbility';
import wantAgent from '@ohos.wantAgent';

function callback(err, data) {
    if (err) {
        console.error("Operation startBackgroundRunning failed Cause: " + err);
    } else {
        console.info("Operation startBackgroundRunning succeeded");
    }
}

let wantAgentInfo = {
    wants: [
        {
            bundleName: "com.example.myapplication",
            abilityName: "com.example.myapplication.MainAbility"
        }
    ],
    operationType: wantAgent.OperationType.START_ABILITY,
    requestCode: 0,
    wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj) => {
    backgroundTaskManager.startBackgroundRunning(featureAbility.getContext(),
        backgroundTaskManager.BackgroundMode.DATA_TRANSFER, wantAgentObj, callback)
});

```

## backgroundTaskManager.startBackgroundRunning<sup>8+</sup>

startBackgroundRunning(context: Context, bgMode: BackgroundMode, wantAgent: WantAgent): Promise&lt;void&gt;

Requests a continuous task from the system. This API uses a promise to return the result.

**Required permissions**: ohos.permission.KEEP_BACKGROUND_RUNNING

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**

| Name       | Type                                 | Mandatory   | Description                      |
| --------- | ---------------------------------- | ---- | ----------------------- |
| context   | [Context](js-apis-Context.md)      | Yes    | Application context.               |
| bgMode    | [BackgroundMode](#backgroundmode8) | Yes    | Background mode requested.             |
| wantAgent | [WantAgent](js-apis-wantAgent.md)  | Yes    | Notification parameter, which is used to specify the target page that is redirected to when a continuous task notification is clicked. |

**Return value**
| Type             | Description               |
| -------------- | ---------------- |
| Promise\<void> | Promise used to return the result. |

**Example**
```js
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import featureAbility from '@ohos.ability.featureAbility';
import wantAgent from '@ohos.wantAgent';

let wantAgentInfo = {
    wants: [
        {
            bundleName: "com.example.myapplication",
            abilityName: "com.example.myapplication.MainAbility"
        }
    ],
    operationType: wantAgent.OperationType.START_ABILITY,
    requestCode: 0,
    wantAgentFlags: [wantAgent.WantAgentFlags.UPDATE_PRESENT_FLAG]
};

wantAgent.getWantAgent(wantAgentInfo).then((wantAgentObj) => {
    backgroundTaskManager.startBackgroundRunning(featureAbility.getContext(),
        backgroundTaskManager.BackgroundMode.DATA_TRANSFER, wantAgentObj).then(() => {
        console.info("Operation startBackgroundRunning succeeded");
    }).catch((err) => {
        console.error("Operation startBackgroundRunning failed Cause: " + err);
    });
});

```

## backgroundTaskManager.stopBackgroundRunning<sup>8+</sup>

stopBackgroundRunning(context: Context, callback: AsyncCallback&lt;void&gt;): void

Requests to cancel a continuous task. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**
| Name       | Type                            | Mandatory   | Description                      |
| -------- | ----------------------------- | ---- | ---------------------- |
| context   | [Context](js-apis-Context.md) | Yes    | Application context.              |
| callback | AsyncCallback&lt;void&gt;     | Yes    | Callback used to return the result. |

**Example**
```js
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import featureAbility from '@ohos.ability.featureAbility';

function callback(err, data) {
    if (err) {
        console.error("Operation stopBackgroundRunning failed Cause: " + err);
    } else {
        console.info("Operation stopBackgroundRunning succeeded");
    }
}

backgroundTaskManager.stopBackgroundRunning(featureAbility.getContext(), callback);

```

## backgroundTaskManager.stopBackgroundRunning<sup>8+</sup>

stopBackgroundRunning(context: Context): Promise&lt;void&gt;

Requests to cancel a continuous task. This API uses a promise to return the result.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

**Parameters**
| Name       | Type                            | Mandatory   | Description        |
| ------- | ----------------------------- | ---- | --------- |
| context | [Context](js-apis-Context.md) | Yes    | Application context. |

**Return value**
| Type             | Description               |
| -------------- | ---------------- |
| Promise\<void> | Promise used to return the result. |

**Example**
```js
import backgroundTaskManager from '@ohos.backgroundTaskManager';
import featureAbility from '@ohos.ability.featureAbility';

backgroundTaskManager.stopBackgroundRunning(featureAbility.getContext()).then(() => {
    console.info("Operation stopBackgroundRunning succeeded");
}).catch((err) => {
    console.error("Operation stopBackgroundRunning failed Cause: " + err);
});

```

## DelaySuspendInfo

Provides the information about the suspension delay.

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.TransientTask

| Name            | Type    | Mandatory  | Description                                      |
| --------------- | ------ | ---- | ---------------------------------------- |
| requestId       | number | Yes   | ID of the suspension delay request.                              |
| actualDelayTime | number | Yes   | Actual suspension delay duration of the application, in milliseconds.<br>The default duration is 180000 when the battery level is higher than or equal to the broadcast low battery level and 60000 when the battery level is lower than the broadcast low battery level.|


## BackgroundMode<sup>8+</sup>

**System capability**: SystemCapability.ResourceSchedule.BackgroundTaskManager.ContinuousTask

| Name                 | Value| Description                        |
| ----------------------- | ------ | ---------------------------- |
| DATA_TRANSFER           | 1      | Data transfer.                    |
| AUDIO_PLAYBACK          | 2      | Audio playback.                    |
| AUDIO_RECORDING         | 3      | Audio recording.                        |
| LOCATION                | 4      | Positioning and navigation.                    |
| BLUETOOTH_INTERACTION   | 5      | Bluetooth-related task.                    |
| MULTI_DEVICE_CONNECTION | 6      | Multi-device connection.                  |
| WIFI_INTERACTION        | 7      | WLAN-related (reserved).        |
| VOIP                    | 8      | Voice and video call (reserved).      |
| TASK_KEEPING            | 9      | Computing task (effective only for specific devices).|
