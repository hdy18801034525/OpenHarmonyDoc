# Display

> ![icon-note.gif](public_sys-resources/icon-note.gif) **NOTE**
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```
import display from '@ohos.display';
```


## DisplayState

Provides the state of a display.

| Name| Default Value| Description|
| -------- | -------- | -------- |
| STATE_UNKNOWN | 0 | Unknown. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| STATE_OFF | 1 | The display is shut down. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| STATE_ON | 2 | The display is powered on. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| STATE_DOZE | 3 | The display is in sleep mode. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| STATE_DOZE_SUSPEND | 4 | The display is in sleep mode, and the CPU is suspended. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| STATE_VR | 5 | The display is in VR mode. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| STATE_ON_SUSPEND | 6 | The display is powered on, and the CPU is suspended. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|


## Display

Describes the attributes of a display.

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| id | number | Yes| No| ID of the display. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| name | string | Yes| No| Name of the display. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| alive | boolean | Yes| No| Whether the display is alive. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| state | [DisplayState](#DisplayState) | Yes| No| State of the display. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| refreshRate | number | Yes| No| Refresh rate of the display. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| rotation | number | Yes| No| Screen rotation angle of the display. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| width | number | Yes| No| Width of the display, in pixels. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| height | number | Yes| No| Height of the display, in pixels. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| densityDPI | number | Yes| No| Screen density of the display, in DPI. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| densityPixels | number | Yes| No| Screen density of the display, in pixels. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| scaledDensity | number | Yes| No| Scaling factor for fonts displayed on the display. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| xDPI | number | Yes| No| Exact physical dots per inch of the screen in the horizontal direction. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|
| yDPI | number | Yes| No| Exact physical dots per inch of the screen in the vertical direction. <br/>**System capabilities**: SystemCapability.WindowManager.WindowManager.Core|


## display.getDefaultDisplay

getDefaultDisplay(callback: AsyncCallback&lt;Display&gt;): void

Obtains the default display object.

**System capabilities**: SystemCapability.WindowManager.WindowManager.Core

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[Display](#Display)&gt; | Yes| Callback used to return the default display object.|

- Example
  ```
  var displayClass = null;
  display.getDefaultDisplay((err, data) => {
      if (err) {
          console.error('Failed to obtain the default display object. Code:  ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in obtaining the default display object. Data:' + JSON.stringify(data));
      displayClass = data;
  });
  ```

## display.getDefaultDisplay

getDefaultDisplay(): Promise&lt;Display&gt;

Obtains the default display object.

**System capabilities**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type| Description|
  | ---------------------------------- | ---------------------------------------------- |
  | Promise&lt;[Display](#Display)&gt; | Promise used to return the default display object.|

- Example

  ```
  let promise = display.getDefaultDisplay();
  promise.then(() => {
      console.log('getDefaultDisplay success');
  }).catch((err) => {
      console.log('getDefaultDisplay fail: ' + JSON.stringify(err));
  });
  ```

## display.getAllDisplay

getAllDisplay(callback: AsyncCallback&lt;Array&lt;Display&gt;&gt;): void

Obtains all the display objects.

**System capabilities**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type| Mandatory| Description|
  | -------- | ---------------------------------------------------- | ---- | ------------------------------- |
  | callback | AsyncCallback&lt;Array&lt;[Display](Display)&gt;&gt; | Yes| Callback used to return all the display objects.|

- Example

  ```
  display.getAllDisplay((err, data) => {
      if (err) {
          console.error('Failed to obtain all the display objects. Code: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in obtaining all the display objects. Data: ' + JSON.stringify(data))
  });
  ```

## display.getAllDisplay

getAllDisplay(): Promise&lt;Array&lt;Display&gt;&gt;

Obtains all the display objects.

**System capabilities**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type| Description|
  | ----------------------------------------------- | ------------------------------------------------------- |
  | Promise&lt;Array&lt;[Display](#Display)&gt;&gt; | Promise used to return an array containing all the display objects.|

- Example

  ```
  let promise = display.getAllDisplay();
  promise.then(() => {
      console.log('getAllDisplay success');
  }).catch((err) => {
      console.log('getAllDisplay fail: ' + JSON.stringify(err));
  });
  ```

## display.on('add'|'remove'|'change')

on(type: 'add'|'remove'|'change', callback: Callback&lt;number&gt;): void

Enables listening.

**System capabilities**: SystemCapability.WindowManager.WindowManager.Core

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Listening type. The available values are as follows: <br/>-&nbsp;**add**: listening for whether a display is added <br/>-&nbsp;**remove**: listening for whether a display is removed <br/>-&nbsp;**change**: listening for whether a display is changed|
  | callback | Callback&lt;number&gt; | Yes| Callback used to return the ID of the display.|

- Example
  ```
  var type = "add";
  var callback = (data) => {
      console.info('Listening enabled. Data: ' + JSON.stringify(data))
  }
  display.on(type, callback);
  ```


## display.off('add'|'remove'|'change')

off(type: 'add'|'remove'|'change', callback?: Callback&lt;number&gt;): void

Disables listening.

**System capabilities**: SystemCapability.WindowManager.WindowManager.Core

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Listening type. The available values are as follows: <br/>-&nbsp;**add**: listening for whether a display is added <br/>-&nbsp;**remove**: listening for whether a display is removed <br/>-&nbsp;**change**: listening for whether a display is changed|
  | callback | Callback&lt;number&gt; | No| Callback used to return the ID of the display.|

- Example
  ```
  var type = "remove";
  display.off(type);
  ```