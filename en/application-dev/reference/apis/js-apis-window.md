# Window

> ![icon-note.gif](public_sys-resources/icon-note.gif) **NOTE**
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```
import window from '@ohos.window';
```

## WindowType<sup>7+</sup><a name="windowtype"></a>

Enumerates the window types.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name             | Default Value| Description              |
| ----------------- | ------ | ------------------ |
| TYPE_APP          | 0      | Application subwindow.  |
| TYPE_SYSTEM_ALERT | 1      | System alert window.|

## AvoidAreaType<sup>7+</sup><a name="avoidareatype"></a>

Enumerates the types of the area where the window cannot be displayed.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name       | Default Value| Description              |
| ----------- | ------ | ------------------ |
| TYPE_SYSTEM | 0      | Default area of the system.|
| TYPE_CUTOUT | 1      | Notch.  |

## WindowMode<sup>7+</sup><a name="windowmode"></a>

Enumerates the window modes of an application.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name      | Default Value| Description                         |
| ---------- | ------ | ----------------------------- |
| UNDEFINED  | 1      | The window mode is not defined by the application.      |
| FULLSCREEN | 2      | The application is displayed in full screen.            |
| PRIMARY    | 3      | The application is displayed in the primary window in split-screen mode.  |
| SECONDARY  | 4      | The application is displayed in the secondary window in split-screen mode.  |
| FLOATING   | 5      | The application is displayed in a floating window.|

## SystemBarProperties<a name="systembarproperties"></a>

Describes the properties of the status bar and navigation bar.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name                                  | Type| Readable| Writable| Description                                                        |
| -------------------------------------- | -------- | ---- | ---- | ------------------------------------------------------------ |
| statusBarColor                         | string   | Yes  | Yes  | Background color of the status bar. The value is a hexadecimal RGB or aRGB color value, for example, **\#00FF00** or **\#FF00FF00**.|
| isStatusBarLightIcon<sup>7+</sup>      | boolean  | No  | Yes  | Whether any icon on the status bar is highlighted.                                  |
| statusBarContentColor<sup>8+</sup>     | string   | No  | Yes  | Color of the text on the status bar.                                            |
| navigationBarColor                     | string   | Yes  | Yes  | Background color of the navigation bar. The value is a hexadecimal RGB or aRGB color value, for example, **\#00FF00** or **\#FF00FF00**.|
| isNavigationBarLightIcon<sup>7+</sup>  | boolean  | No  | No  | Whether any icon on the navigation bar is highlighted.                                  |
| navigationBarContentColor<sup>8+</sup> | string   | No  | Yes  | Color of the text on the navigation bar.                                            |

## SystemBarRegionTint<sup>8+</sup><a name="systembartegiontint"></a>

Describes the callback for a single system bar.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name           | Type                 | Readable| Writable| Description                                                        |
| --------------- | ------------------------- | ---- | ---- | ------------------------------------------------------------ |
| type            | [WindowType](#windowtype) | Yes  | Yes  | Type of the system bar whose properties are changed. Only the navigation bar and status bar are supported.|
| isEnable        | boolean                   | Yes  | Yes  | Whether the system bar is displayed.                                        |
| region          | [Rect](#rect)             | Yes  | Yes  | Current position and size of the system bar.                                    |
| backgroundColor | string                    | Yes  | Yes  | Background color of the system bar. The value is a hexadecimal RGB or aRGB color value, for example, **\#00FF00** or **\#FF00FF00**.|
| contentColor    | string                    | Yes  | Yes  | Color of the text on the system bar.                                            |

## SystemBarTintState<sup>8+</sup><a name="systembartintstate"></a>

Describes the callback for the current system bar.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name      | Type                                          | Readable| Writable| Description                      |
| ---------- | -------------------------------------------------- | ---- | ---- | -------------------------- |
| displayId  | number                                             | Yes  | No  | ID of the current physical screen.          |
| regionTint | Array<[SystemBarRegionTint](#systembartegiontint)> | Yes  | Yes  | All system bar information changed.|

## Rect<sup>7+</sup><a name="rect"></a>

Describes a rectangle.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name  | Type| Readable| Writable| Description              |
| ------ | -------- | ---- | ---- | ------------------ |
| left   | number   | Yes  | Yes  | Left boundary of the rectangle.|
| top    | number   | Yes  | Yes  | Top boundary of the rectangle.|
| width  | number   | Yes  | Yes  | Width of the rectangle.  |
| height | number   | Yes  | Yes  | Height of the rectangle.  |

## AvoidArea<sup>7+</sup><a name="avoidarea"></a>

Describes the area where the window cannot be displayed.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name      | Type     | Readable| Writable| Description              |
| ---------- | ------------- | ---- | ---- | ------------------ |
| leftRect   | [Rect](#rect) | Yes  | Yes  | Rectangle on the left of the screen.|
| topRect    | [Rect](#rect) | Yes  | Yes  | Rectangle at the top of the screen.|
| rightRect  | [Rect](#rect) | Yes  | Yes  | Rectangle on the right of the screen.|
| bottomRect | [Rect](#rect) | Yes  | Yes  | Rectangle at the bottom of the screen.|

## Size<sup>7+</sup><a name="size"></a>

Describes the window size.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name  | Type| Readable| Writable| Description      |
| ------ | -------- | ---- | ---- | ---------- |
| width  | number   | Yes  | Yes  | Window width.|
| height | number   | Yes  | Yes  | Window height.|

## WindowProperties<a name="windowproperties"></a>

Describes the window properties.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name                           | Type                 | Readable| Writable| Description                                                        |
| ------------------------------- | ------------------------- | ---- | ---- | ------------------------------------------------------------ |
| windowRect<sup>7+</sup>         | [Rect](#rect)             | Yes  | Yes  | Window size.                                                  |
| type<sup>7+</sup>               | [WindowType](#windowtype) | Yes  | Yes  | Window type.                                                  |
| isFullScreen                    | boolean                   | Yes  | Yes  | Whether the window is displayed in full screen mode. The default value is **false**.                                     |
| isLayoutFullScreen<sup>7+</sup> | boolean                   | Yes  | Yes  | Whether the window layout is in full-screen mode (whether the window is immersive). The default value is **false**.                             |
| focusable<sup>7+</sup>          | boolean                   | Yes  | No  | Whether the window can gain focus. The default value is **true**.                                |
| touchable<sup>7+</sup>          | boolean                   | Yes  | No  | Whether the window is touchable. The default value is **true**.                                |
| brightness                      | number                    | Yes  | Yes  | Screen brightness. The value ranges from 0 to 1. The value **1** indicates the maximum brightness.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| dimBehindValue<sup>7+</sup>     | number                    | Yes  | Yes  | Dimness of the window that is not on top. The value ranges from 0 to 1. The value **1** indicates the maximum dimness.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| isKeepScreenOn                  | boolean                   | Yes  | Yes  | Whether the screen is always on. The default value is **false**.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| isPrivacyMode<sup>7+</sup>      | boolean                   | Yes  | Yes  | Whether the window is in privacy mode. The default value is **false**.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| isRoundCorner<sup>7+</sup>      | boolean                   | Yes  | Yes  | Whether the window has rounded corners.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|
| isTransparent<sup>7+</sup>      | boolean                   | Yes  | Yes  | Whether the window is transparent. The default value is **false**.<br>This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.|

## ColorSpace<sup>8+</sup><a name="colorspace"></a>

Describes the color gamut mode.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

| Name      | Default Value| Description          |
| ---------- | ------ | -------------- |
| DEFAULT    | 0      | Default color gamut mode.|
| WIDE_GAMUT | 1      | Wide color gamut mode.  |

## window.create<sup>7</sup><a name="window-create"></a>

create(id: string, type: WindowType, callback: AsyncCallback&lt;Window&gt;): void

Creates a subwindow. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                  | Mandatory| Description                      |
  | -------- | -------------------------------------- | ---- | -------------------------- |
  | id       | string                                 | Yes  | Window ID.                  |
  | type     | [WindowType](#windowtype)              | Yes  | Window type.                |
  | callback | AsyncCallback&lt;[Window](#window)&gt; | Yes  | Callback used to return the subwindow created.|

- Example

  ```
   var windowClass = null;
   window.create("first", window.WindowType.TYPE_APP, (err, data) => {
      if (err.code) {
          console.error('Failed to create the subWindow. Cause: ' + JSON.stringify(err));
          return;
      }
      windowClass = data;
      console.info('SubWindow created. Data: ' + JSON.stringify(data))
      windowClass.resetSize(500, 1000);
  });
  ```

## window.create<sup>7</sup>

create(id: string, type: WindowType): Promise&lt;Window&gt;

Creates a subwindow. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type                     | Mandatory| Description      |
  | ------ | ------------------------- | ---- | ---------- |
  | id     | string                    | Yes  | Window ID.  |
  | type   | [WindowType](#windowtype) | Yes  | Window type.|

- Return value

  | Type                            | Description                                             |
  | -------------------------------- | ------------------------------------------------- |
  | Promise&lt;[Window](#window)&gt; | Promise used to return the subwindow created.|

- Example

  ```
   var windowClass = null;
   let promise = window.create("first", window.WindowType.TYPE_APP);
   promise.then((data)=> {
   	windowClass = data;
      console.info('SubWindow created. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to create the subWindow. Cause: ' + JSON.stringify(err));
   });
  ```

## window.create<sup>8+</sup>

create(ctx: Context, id: string, type: WindowType, callback: AsyncCallback&lt;Window&gt;): void

Creates a system window when the context is [ServiceExtensionContext](https://gitee.com/openharmony/docs/blob/master/en/application-dev/reference/apis/js-apis-service-extension-context.md). This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                                        | Mandatory| Description                                                 |
  | -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
  | ctx      | [Context](https://gitee.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis/js-apis-Context.md) | Yes  | Current application context, which is the base class of **ServiceExtensionContext**.|
  | id       | string                                                       | Yes  | Window ID.                                             |
  | type     | [WindowType](#windowtype)                                    | Yes  | Window type.                                           |
  | callback | AsyncCallback&lt;[Window](#window)&gt;                       | Yes  | Callback used to return the system window created.                               |

- Example

  ```
   var windowClass = null;
   window.create(this.context, "alertWindow", window.WindowType.TYPE_SYSTEM_ALERT, (err, data) => {
      if (err.code) {
          console.error('Failed to create the Window. Cause: ' + JSON.stringify(err));
          return;
      }
      windowClass = data;
      console.info('Window created. Data: ' + JSON.stringify(data))
      windowClass.resetSize(500, 1000);
  });
  ```

## window.create<sup>8+</sup>

create(ctx: Context, id: string, type: WindowType): Promise&lt;Window&gt;

Creates a system window when the context is [ServiceExtensionContext](https://gitee.com/openharmony/docs/blob/master/en/application-dev/reference/apis/js-apis-service-extension-context.md). This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type                                                        | Mandatory| Description                                                 |
  | ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
  | ctx    | [Context](https://gitee.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis/js-apis-Context.md) | Yes  | Current application context, which is the base class of **ServiceExtensionContext**.|
  | id     | string                                                       | Yes  | Window ID.                                             |
  | type   | [WindowType](#windowtype)                                    | Yes  | Window type.                                           |

- Return value

  | Type                            | Description                                           |
  | -------------------------------- | ----------------------------------------------- |
  | Promise&lt;[Window](#window)&gt; | Promise used to return the system window created.|

- Example

  ```
   var windowClass = null;
   let promise = window.create(this.context, "alertWindow", window.WindowType.TYPE_SYSTEM_ALERT);
   promise.then((data)=> {
   	windowClass = data;
      console.info('Window created. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to create the Window. Cause: ' + JSON.stringify(err));
   });
  ```

## window.find<sup>7+</sup><a name="window-find"></a>

find(id: string, callback: AsyncCallback&lt;Window&gt;): void

Finds a window based on the ID. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                  | Mandatory| Description                        |
  | -------- | -------------------------------------- | ---- | ---------------------------- |
  | id       | string                                 | Yes  | Window ID.                    |
  | callback | AsyncCallback&lt;[Window](#window)&gt; | Yes  | Callback used to return the window found.|

- Example

  ```
   var windowClass = null;
   window.find("alertWindow", (err, data) => {
     if (err.code) {
         console.error('Failed to find the Window. Cause: ' + JSON.stringify(err));
         return;
     }
     windowClass = data;
     console.info('window found. Data: ' + JSON.stringify(data))
  });
  ```

## window.find<sup>7+</sup>

find(id: string): Promise&lt;Window&gt;

Finds a window based on the ID. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type  | Mandatory| Description    |
  | ------ | ------ | ---- | -------- |
  | id     | string | Yes  | Window ID.|

- Return value

  | Type                            | Description                                           |
  | -------------------------------- | ----------------------------------------------- |
  | Promise&lt;[Window](#window)&gt; | Promise used to return the window found.|

- Example

  ```
   var windowClass = null;
   let promise = window.find("alertWindow");
   promise.then((data)=> {
   	windowClass = data;
      console.info('window found. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to find the Window. Cause: ' + JSON.stringify(err));
   });
  ```

## window.getTopWindow<a name="window-gettopwindow"></a>

getTopWindow(callback: AsyncCallback&lt;Window&gt;): void

Obtains the top window of the current application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                  | Mandatory| Description                                  |
  | -------- | -------------------------------------- | ---- | -------------------------------------- |
  | callback | AsyncCallback&lt;[Window](#window)&gt; | Yes  | Callback used to return the top window obtained.|

- Example

  ```
  var windowClass = null;
  window.getTopWindow((err, data) => {
      if (err.code) {
          console.error('Failed to obtain the top window. Cause: ' + JSON.stringify(err));
          return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
  });
  ```

## window.getTopWindow

getTopWindow(): Promise&lt;Window&gt;

Obtains the top window of the current application. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type                            | Description                                                     |
  | -------------------------------- | --------------------------------------------------------- |
  | Promise&lt;[Window](#window)&gt; | Promise used to return the top window obtained.|

- Example

  ```
   var windowClass = null;
   let promise = window.getTopWindow();
   promise.then((data)=> {
   	windowClass = data;
      console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to obtain the top window. Cause: ' + JSON.stringify(err));
   })
  ```

## window.getTopWindow<sup>8+</sup>

getTopWindow(ctx: Context, callback: AsyncCallback&lt;Window&gt;): void

Obtains the top window of the current application. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                                        | Mandatory| Description                                  |
  | -------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
  | ctx      | [Context](https://gitee.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis/js-apis-Context.md) | Yes  | Current application context.                  |
  | callback | AsyncCallback&lt;[Window](#window)&gt;                       | Yes  | Callback used to return the top window obtained.|

- Example

  ```
  var windowClass = null;
  window.getTopWindow(this.context, (err, data) => {
      if (err.code) {
          console.error('Failed to obtain the top window. Cause: ' + JSON.stringify(err));
          return;
      }
      windowClass = data;
      console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data));
  });
  ```

## window.getTopWindow<sup>8+</sup>

getTopWindow(ctx: Context): Promise&lt;Window&gt;

Obtains the top window of the current application. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type                                                        | Mandatory| Description                |
  | ------ | ------------------------------------------------------------ | ---- | -------------------- |
  | ctx    | [Context](https://gitee.com/openharmony/docs/blob/master/zh-cn/application-dev/reference/apis/js-apis-Context.md) | Yes  | Current application context.|

- Return value

  | Type                            | Description                                                     |
  | -------------------------------- | --------------------------------------------------------- |
  | Promise&lt;[Window](#window)&gt; | Promise used to return the top window obtained.|

- Example

  ```
   var windowClass = null;
   let promise = window.getTopWindow(this.context);
   promise.then((data)=> {
   	windowClass = data;
      console.info('Succeeded in obtaining the top window. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to obtain the top window. Cause: ' + JSON.stringify(err));
   })
  ```

## on('systemBarTintChange')<sup>8+</sup>

on(type: 'systemBarTintChange', callback: Callback&lt;SystemBarTintState&gt;): void

Enables listening for the properties changes of the status bar and navigation bar.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                                     | Mandatory| Description                                                        |
  | -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                                                    | Yes  | Listening type.<br>Set it to **systemBarTintChange**, which indicates listening for properties changes of the status bar and navigation bar.|
  | callback | Callback&lt;[SystemBarTintState](#systembartintstate)&gt; | Yes  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'systemBarTintChange';
  windowClass.on(type, (data) => {
      console.info('Succeeded in enabling the listener for systemBarTint changes. Data: ' + JSON.stringify(data));
  });
  ```

## off('systemBarTintChange')<sup>8+</sup>

off(type: 'systemBarTintChange', callback?: Callback&lt;SystemBarTintState &gt;): void

Disables listening for the properties changes of the status bar and navigation bar.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                                     | Mandatory| Description                                                        |
  | -------- | --------------------------------------------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                                                    | Yes  | Listening type.<br>Set it to **systemBarTintChange**, which indicates listening for properties changes of the status bar and navigation bar.|
  | callback | Callback&lt;[SystemBarTintState](#systembartintstate)&gt; | No  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'systemBarTintChange';
  windowClass.off(type);
  ```

## Window

In the following API examples, you must use [getTopWindow()](#window-gettopwindow), [create()](#window-create), or [find()](#window-find) to obtain a **Window** instance and then call a method in this instance.

### hide<sup>7+</sup>

hide (callback: AsyncCallback&lt;void&gt;): void

Hides this window. This API uses an asynchronous callback to return the result.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description      |
  | -------- | ------------------------- | ---- | ---------- |
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.|

- Example

  ```
  windowClass.hide((err, data) => {
      if (err.code) {
          console.error('Failed to hide the window. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('window hidden. data: ' + JSON.stringify(data))
  })
  ```

### hide<sup>7+</sup>

hide(): Promise&lt;void&gt;

Hides this window. This API uses a promise to return the result.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
   let promise = windowClass.hide();
   promise.then((data)=> {
      console.info('window hidden. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to hide the window. Cause: ' + JSON.stringify(err));
   })
  ```

### show<sup>7+</sup>

show(callback: AsyncCallback&lt;void&gt;): void

Shows this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description      |
  | -------- | ------------------------- | ---- | ---------- |
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.|

- Example

  ```
  windowClass.show((err, data) => {
      if (err.code) {
          console.error('Failed to show the window. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in showing the window. Data: ' + JSON.stringify(data))
  })
  ```

### show<sup>7+</sup>

show(): Promise&lt;void&gt;

Shows this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
   let promise = windowClass.show();
   promise.then((data)=> {
      console.info('Succeeded in showing the window. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to show the window. Cause: ' + JSON.stringify(err));
   })
  ```

### destroy<sup>7+</sup>

destroy(callback: AsyncCallback&lt;void&gt;): void

Destroys this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description      |
  | -------- | ------------------------- | ---- | ---------- |
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.|

- Example

  ```
  windowClass.destroy((err, data) => {
      if (err.code) {
          console.error('Failed to destroy the window. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in destroying the window. Data: ' + JSON.stringify(data))
  })
  ```

### destroy<sup>7+</sup>

destroy(): Promise&lt;void&gt;

Destroys this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
   let promise = windowClass.destroy();
   promise.then((data)=> {
      console.info('Succeeded in destroying the window. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to destroy the window. Cause: ' + JSON.stringify(err));
   })
  ```

### moveTo<sup>7+</sup>

moveTo(x: number, y: number, callback: AsyncCallback&lt;void&gt;): void

Moves the position of this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description                                   |
  | -------- | ------------------------- | ---- | --------------------------------------- |
  | x        | number                    | Yes  | Distance that the window moves along the x-axis. A positive value indicates that the window moves to the right.|
  | y        | number                    | Yes  | Distance that the window moves along the y-axis. A positive value indicates that the window moves downwards.|
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                             |

- Example

  ```
  windowClass.moveTo(300, 300, (err, data)=>{
      if (err.code) {
          console.error('Failed to move the window. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Window moved. Data: ' + JSON.stringify(data))
  
  });
  ```

### moveTo<sup>7+</sup>

moveTo(x: number, y: number): Promise&lt;void&gt;

Moves the position of this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type  | Mandatory| Description                                   |
  | ------ | ------ | ---- | --------------------------------------- |
  | x      | number | Yes  | Distance that the window moves along the x-axis. A positive value indicates that the window moves to the right.|
  | y      | number | Yes  | Distance that the window moves along the y-axis. A positive value indicates that the window moves downwards.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
   let promise = windowClass.moveTo(300, 300);
   promise.then((data)=> {
      console.info('Window moved. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to move the window. Cause: ' + JSON.stringify(err));
   })
  ```

### resetSize<sup>7+</sup>

resetSize(width: number, height: number, callback: AsyncCallback&lt;void&gt;): void

Changes the size of this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description            |
  | -------- | ------------------------- | ---- | ---------------- |
  | width    | number                    | Yes  | New width of the window.|
  | height   | number                    | Yes  | New height of the window.|
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.      |

- Example

  ```
  windowClass.resetSize(500, 1000, (err, data) => {
      if (err.code) {
          console.error('Failed to change the window size. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Window size changed. Data: ' + JSON.stringify(data))
  });
  ```

### resetSize<sup>7+</sup>

resetSize(width: number, height: number): Promise&lt;void&gt;

Changes the size of this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type  | Mandatory| Description            |
  | ------ | ------ | ---- | ---------------- |
  | width  | number | Yes  | New width of the window.|
  | height | number | Yes  | New height of the window.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
   let promise = windowClass.resetSize(500, 1000);
   promise.then((data)=> {
      console.info('Window size changed. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to change the window size. Cause: ' + JSON.stringify(err));
   });
  ```

### setWindowType<sup>7+</sup>

setWindowType(type: WindowType, callback: AsyncCallback&lt;void&gt;): void

Sets the type of this window. This API uses an asynchronous callback to return the result.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description      |
  | -------- | ------------------------- | ---- | ---------- |
  | type     | [WindowType](#windowtype) | Yes  | Window type.|
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.|

- Example

  ```
  var type = window.TYPE_APP;
  windowClass.setWindowType(type, (err, data) => {
    if (err.code) {
        console.error('Failed to set the window type. Cause: ' + JSON.stringify(err));
        return;
    }
    console.info('Succeeded in setting the window type. Data: ' + JSON.stringify(data))
  });
  ```

### setWindowType<sup>7+</sup>

setWindowType(type: WindowType): Promise&lt;void&gt;

Sets the type of this window. This API uses a promise to return the result.

This is a system API and cannot be called by third-party applications.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type                     | Mandatory| Description      |
  | ------ | ------------------------- | ---- | ---------- |
  | type   | [WindowType](#windowtype) | Yes  | Window type.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
   var type = window.TYPE_APP;
   let promise = windowClass.setWindowType(type);
   promise.then((data)=> {
      console.info('Succeeded in setting the window type. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to set the window type. Cause: ' + JSON.stringify(err));
   });
  ```

### getProperties

getProperties(callback: AsyncCallback&lt;WindowProperties&gt;): void

Obtains the properties of this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                                      | Mandatory| Description              |
  | -------- | ---------------------------------------------------------- | ---- | ------------------ |
  | callback | AsyncCallback&lt;[WindowProperties](#windowproperties)&gt; | Yes  | Callback used to return the window properties.|

- Example

  ```
  windowClass.getProperties((err, data) => {
      if (err.code) {
          console.error('Failed to obtain the window properties. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in obtaining the window properties. Data: ' + JSON.stringify(data));
  });
  ```

### getProperties

getProperties(): Promise&lt;WindowProperties&gt;

Obtains the properties of this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type                                                | Description                                 |
  | ---------------------------------------------------- | ------------------------------------- |
  | Promise&lt;[WindowProperties](#windowproperties)&gt; | Promise used to return the window properties.|

- Example

  ```
   let promise = windowClass.getProperties();
   promise.then((data)=> {
      console.info('Succeeded in obtaining the window properties. Data: ' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to obtain the window properties. Cause: ' + JSON.stringify(err));
   });
  ```

### getAvoidArea<sup>7+</sup>

getAvoidArea(type: AvoidAreaType, callback: AsyncCallback&lt;AvoidArea&gt;): void

Obtains the area where this window cannot be displayed, for example, the system bar area and notch. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                        | Mandatory| Description                                                        |
  | -------- | -------------------------------------------- | ---- | ------------------------------------------------------------ |
  | type     | [AvoidAreaType](#avoidareatype)              | Yes  | Type of the area.**TYPE_SYSTEM** indicates the default area of the system. **TYPE_CUTOUT** indicates the notch.|
  | callback | AsyncCallback&lt;[AvoidArea](#avoidarea)&gt; | Yes  | Callback used to return the area.                                  |

- Example

  ```
  var type = window.AvoidAreaType.TYPE_SYSTEM;
  windowClass.getAvoidArea(type, (err, data) => {
      if (err.code) {
          console.error('Failed to obtain the area. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in obtaining the area. Data:' + JSON.stringify(data));
  });
  ```

### getAvoidArea<sup>7+</sup>

getAvoidArea(type: AvoidAreaType): Promise&lt;AvoidArea&gt;

Obtains the area where this window cannot be displayed, for example, the system bar area and notch. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type                           | Mandatory| Description                                                        |
  | ------ | ------------------------------- | ---- | ------------------------------------------------------------ |
  | type   | [AvoidAreaType](#avoidareatype) | Yes  | Type of the area.**TYPE_SYSTEM** indicates the default area of the system. **TYPE_CUTOUT** indicates the notch.|

- Return value

  | Type                                  | Description                                         |
  | -------------------------------------- | --------------------------------------------- |
  | Promise&lt;[AvoidArea](#avoidarea)&gt; | Promise used to return the area.|

- Example

  ```
   let promise = windowClass.getAvoidArea();
   promise.then((data)=> {
      console.info('Succeeded in obtaining the area. Data:' + JSON.stringify(data))
   }).catch((err)=>{
      console.error('Failed to obtain the area. Cause:' + JSON.stringify(err));
   });
  ```

### setFullScreen

setFullScreen(isFullScreen: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether to enable the full-screen mode for this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name      | Type                     | Mandatory| Description                                          |
  | ------------ | ------------------------- | ---- | ---------------------------------------------- |
  | isFullScreen | boolean                   | Yes  | Whether to enable the full-screen mode, in which the status bar and navigation bar are hidden.|
  | callback     | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                                    |

- Example

  ```
  var isFullScreen = true;
  windowClass.setFullScreen(isFullScreen, (err, data) => {
      if (err.code) {
          console.error('Failed to enable the full-screen mode. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in enabling the full-screen mode. Data: ' + JSON.stringify(data))
  });
  ```

### setFullScreen

setFullScreen(isFullScreen: boolean): Promise&lt;void&gt;

Sets whether to enable the full-screen mode for this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name      | Type   | Mandatory| Description                                          |
  | ------------ | ------- | ---- | ---------------------------------------------- |
  | isFullScreen | boolean | Yes  | Whether to enable the full-screen mode, in which the status bar and navigation bar are hidden.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var isFullScreen = true;
  let promise = windowClass.setFullScreen(isFullScreen);
  promise.then((data)=> {
      console.info('Succeeded in enabling the full-screen mode. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to enable the full-screen mode. Cause: ' + JSON.stringify(err));
  });
  ```

### setLayoutFullScreen<sup>7+</sup>

setLayoutFullScreen(isLayoutFullScreen: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether the window layout is in full-screen mode. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name            | Type                     | Mandatory| Description                                                        |
  | ------------------ | ------------------------- | ---- | ------------------------------------------------------------ |
  | isLayoutFullScreen | boolean                   | Yes  | Whether the window layout is in full-screen mode, in which the status bar and navigation bar are displayed.|
  | callback           | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                                                  |

- Example

  ```
  var isLayoutFullScreen= true;
  windowClass.setLayoutFullScreen(isLayoutFullScreen, (err, data) => {
      if (err.code) {
          console.error('Failed to set the window layout to full-screen mode. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the window layout to full-screen mode. Data: ' + JSON.stringify(data))
  });
  ```

### setLayoutFullScreen<sup>7+</sup>

setLayoutFullScreen(isLayoutFullScreen: boolean): Promise&lt;void&gt;

Sets whether the window layout is in full-screen mode. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name            | Type   | Mandatory| Description                                                        |
  | ------------------ | ------- | ---- | ------------------------------------------------------------ |
  | isLayoutFullScreen | boolean | Yes  | Whether the window layout is in full-screen mode, in which the status bar and navigation bar are displayed.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var isLayoutFullScreen = true;
  let promise = windowClass.setLayoutFullScreen(isLayoutFullScreen);
  promise.then((data)=> {
      console.info('Succeeded in setting the window layout to full-screen mode. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the window layout to full-screen mode. Cause:' + JSON.stringify(err));
  });
  ```

### setSystemBarEnable<sup>7+</sup>

setSystemBarEnable(names: Array<'status' | 'navigation'>, callback: AsyncCallback&lt;void&gt;): void

Sets whether to display the status bar and navigation bar in this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description                                                        |
  | -------- | ------------------------- | ---- | ------------------------------------------------------------ |
  | names    | Array                     | Yes  | Whether to display the status bar and navigation bar. For example, to display the status bar and navigation bar, set this parameter to **["status", "navigation"]**. By default, they are not displayed.|
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                                                  |

- Example

  ```
  var names = ["status", "navigation"];
  windowClass.setSystemBarEnable(names, (err, data) => {
      if (err.code) {
          console.error('Failed to set the system bar to be visible. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the system bar to be visible. Data: ' + JSON.stringify(data))
  });
  ```

### setSystemBarEnable<sup>7+</sup>

setSystemBarEnable(names: Array<'status' | 'navigation'>): Promise&lt;void&gt;

Sets whether to display the status bar and navigation bar in this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type | Mandatory| Description                                                        |
  | ------ | ----- | ---- | ------------------------------------------------------------ |
  | names  | Array | Yes  | Whether to display the status bar and navigation bar. For example, to display the status bar and navigation bar, set this parameter to **["status", "navigation"]**. By default, they are not displayed.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var names = ["status", "navigation"];
  let promise = windowClass.setSystemBarEnable(names);
  promise.then((data)=> {
      console.info('Succeeded in setting the system bar to be visible. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the system bar to be visible. Cause:' + JSON.stringify(err));
  });
  ```

### setSystemBarProperties

setSystemBarProperties(systemBarProperties: SystemBarProperties, callback: AsyncCallback&lt;void&gt;): void

Sets the properties of the status bar and navigation bar in this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name             | Type                                       | Mandatory| Description                |
  | ------------------- | ------------------------------------------- | ---- | -------------------- |
  | SystemBarProperties | [SystemBarProperties](#systembarproperties) | Yes  | Properties of the status bar and navigation bar.|
  | callback            | AsyncCallback&lt;void&gt;                   | Yes  | Callback used to return the execution result.          |

- Example

  ```
  var SystemBarProperties={
      statusBarColor: '#ff00ff',
      navigationBarColor: '#00ff00',
      // The following properties are supported since API version 7.
      isStatusBarLightIcon: true,
      isNavigationBarLightIcon:false,
      // The following properties are supported since API version 8.
      statusBarContentColor:'#ffffff',
      navigationBarContentColor:'#00ffff'
  };
  windowClass.setSystemBarProperties(SystemBarProperties, (err, data) => {
      if (err.code) {
          console.error('Failed to set the system bar properties. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the system bar properties. Data: ' + JSON.stringify(data))
  });
  ```

### setSystemBarProperties

setSystemBarProperties(systemBarProperties: SystemBarProperties): Promise&lt;void&gt;

Sets the properties of the status bar and navigation bar in this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name             | Type                                       | Mandatory| Description                |
  | ------------------- | ------------------------------------------- | ---- | -------------------- |
  | SystemBarProperties | [SystemBarProperties](#systembarproperties) | Yes  | Properties of the status bar and navigation bar.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var SystemBarProperties={
      statusBarColor: '#ff00ff',
      navigationBarColor: '#00ff00',
      // The following properties are supported since API version 7.
      isStatusBarLightIcon: true,
      isNavigationBarLightIcon:false,
      // The following properties are supported since API version 8.
      statusBarContentColor:'#ffffff',
      navigationBarContentColor:'#00ffff'
  };
  let promise = windowClass.setSystemBarProperties(SystemBarProperties);
  promise.then((data)=> {
      console.info('Succeeded in setting the system bar properties. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the system bar properties. Cause: ' + JSON.stringify(err));
  });
  ```

### loadContent<sup>7+</sup>

loadContent(path: string, callback: AsyncCallback&lt;void&gt;): void

Loads content to this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description                |
  | -------- | ------------------------- | ---- | -------------------- |
  | path     | string                    | Yes  | Path of the page to which the content will be loaded.|
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.          |
  
- Example

  ```
  windowClass.loadContent("pages/page2/page2", (err, data) => {
     if (err.code) {
           console.error('Failed to load the content. Cause:' + JSON.stringify(err));
           return;
     }
    console.info('Succeeded in loading the content. Data: ' + JSON.stringify(data))
  });
  ```

### loadContent<sup>7+</sup>

loadContent(path: string): Promise&lt;void&gt;

Loads content to this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type  | Mandatory| Description                |
  | ------ | ------ | ---- | -------------------- |
  | path   | string | Yes  | Path of the page to which the content will be loaded.|
  
- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  let promise = windowClass.loadContent("pages/page2/page2");
  promise.then((data)=> {
      console.info('Succeeded in loading the content. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to load the content. Cause: ' + JSON.stringify(err));
  });
  ```

### isShowing<sup>7+</sup>

isShowing(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether this window is displayed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                        | Mandatory| Description                            |
  | -------- | ---------------------------- | ---- | -------------------------------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return whether the window is displayed.|

- Example

  ```
  windowClass.isShowing((err, data) => {
      if (err.code) {
          console.error('Failed to check whether the window is showing. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in checking whether the window is showing. Data: ' + JSON.stringify(data))
  });
  ```

### isShowing<sup>7+</sup>

isShowing(): Promise&lt;boolean&gt;

Checks whether this window is displayed. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type                  | Description                                                 |
  | ---------------------- | ----------------------------------------------------- |
  | Promise&lt;boolean&gt; | Promise used to return whether the window is displayed.|

- Example

  ```
  let promise = windowClass.isShowing();
  promise.then((data)=> {
      console.info('Succeeded in checking whether the window is showing. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to check whether the window is showing. Cause: ' + JSON.stringify(err));
  });
  ```

### on('windowSizeChange')<sup>7+</sup>

on(type:  'windowSizeChange', callback: Callback&lt;Size&gt;): void

Enables listening for window size changes.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                         | Mandatory| Description                                                        |
  | -------- | ----------------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                        | Yes  | Listening type.<br>Set it to **windowSizeChange**, which indicates listening for window size changes.|
  | callback | Callback&lt;[Size](#size)&gt; | Yes  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'windowSizeChange';
  windowClass.on(type, (data) => {
      console.info('Succeeded in enabling the listener for window size changes. Data: ' + JSON.stringify(data));
  });
  ```

### off('windowSizeChange')<sup>7+</sup>

off(type: 'windowSizeChange', callback?: Callback&lt;Size &gt;): void

Disables listening for window size changes.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                         | Mandatory| Description                                                        |
  | -------- | ----------------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                        | Yes  | Listening type.<br>Set it to **windowSizeChange<sup>7+</sup>**, which indicates listening for window size changes.|
  | callback | Callback&lt;[Size](#size)&gt; | No  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'windowSizeChange';
  windowClass.off(type);
  ```

### on('systemAvoidAreaChange')<sup>7+</sup>

on(type: 'systemAvoidAreaChange', callback: Callback&lt;AvoidArea&gt;): void

Enables listening for changes to the area where the window cannot be displayed.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                   | Mandatory| Description                                                        |
  | -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                                  | Yes  | Listening type.<br>Set it to **systemAvoidAreaChange**, which indicates listening for changes to the area where the window cannot be displayed.|
  | callback | Callback&lt;[AvoidArea](#avoidarea)&gt; | Yes  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'systemAvoidAreaChange';
  windowClass.on(type, (data) => {
      console.info('Succeeded in enabling the listener for system avoid area changes. Data: ' + JSON.stringify(data));
  });
  ```

### off('systemAvoidAreaChange')<sup>7+</sup>

off(type: 'systemAvoidAreaChange', callback?: Callback&lt;AvoidArea&gt;): void

Disables listening for changes to the area where the window cannot be displayed.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                   | Mandatory| Description                                                        |
  | -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                                  | Yes  | Listening type.<br>Set it to **systemAvoidAreaChange**, which indicates listening for changes to the area where the window cannot be displayed.|
  | callback | Callback&lt;[AvoidArea](#avoidarea)&gt; | No  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'systemAvoidAreaChange';
  windowClass.off(type);
  ```

### on('keyboardHeightChange')<sup>7+</sup>

on(type: 'keyboardHeightChange', callback: Callback&lt;number&gt;): void

Enables listening for keyboard height changes.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                   | Mandatory| Description                                                        |
  | -------- | --------------------------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                                  | Yes  | Listening type.<br>Set it to **keyboardHeightChange**, which indicates listening for keyboard height changes.|
  | callback | Callback&lt;[AvoidArea](#avoidarea)&gt; | Yes  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'keyboardHeightChange';
  windowClass.on(type, (data) => {
      console.info('Succeeded in enabling the listener for keyboard height changes. Data: ' + JSON.stringify(data));
  });
  ```

### off('keyboardHeightChange')<sup>7+</sup>

off(type: 'keyboardHeightChange', callback?: Callback&lt;number&gt;): void

Disables listening for keyboard height changes.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                  | Mandatory| Description                                                        |
  | -------- | ---------------------- | ---- | ------------------------------------------------------------ |
  | type     | string                 | Yes  | Listening type.<br>Set it to **keyboardHeightChange**, which indicates listening for keyboard height changes.|
  | callback | Callback&lt;number&gt; | No  | Callback used to return the listened information.                                      |

- Example

  ```
  var type = 'keyboardHeightChange';
  windowClass.off(type);
  ```

### isSupportWideGamut<sup>8+</sup>

isSupportWideGamut(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether this window supports the wide color gamut mode. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                        | Mandatory| Description                            |
  | -------- | ---------------------------- | ---- | -------------------------------- |
  | callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return whether the wide color gamut mode is supported.|

- Example

  ```
  windowClass.isSupportWideGamut((err, data) => {
      if (err.code) {
          console.error('Failed to check whether the window support WideGamut. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in checking whether the window support WideGamut Data: ' + JSON.stringify(data))
  })
  ```

### isSupportWideGamut<sup>8+</sup>

isSupportWideGamut(): Promise&lt;boolean&gt;

Checks whether this window supports the wide color gamut mode. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type                  | Description                                                        |
  | ---------------------- | ------------------------------------------------------------ |
  | Promise&lt;boolean&gt; | Promise used to return whether the wide color gamut mode is supported.|

- Example

  ```
  let promise = windowClass.isSupportWideGamut();
  promise.then((data)=> {
      console.info('Succeeded in checking whether the window support WideGamut. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to check whether the window support WideGamut. Cause: ' + JSON.stringify(err));
  });
  ```

### setColorSpace<sup>8+</sup>

setColorSpace(colorSpace:ColorSpace, callback: AsyncCallback&lt;void&gt;): void

Sets this window to the wide or default color gamut mode. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name    | Type                     | Mandatory| Description        |
  | ---------- | ------------------------- | ---- | ------------ |
  | colorSpace | [ColorSpace](#colorspace) | Yes  | Color gamut mode.|
  | callback   | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.  |

- Example

  ```
  windowClass.setColorSpace(window.ColorSpace.WIDE_GAMUT, (err, data) => {
      if (err.code) {
          console.error('Failed to set window colorspace. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting window colorspace. Data: ' + JSON.stringify(data))
  })
  ```

### setColorSpace<sup>8+</sup>

setColorSpace(colorSpace:ColorSpace): Promise&lt;void&gt;

Sets this window to the wide or default color gamut mode. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name    | Type                     | Mandatory| Description        |
  | ---------- | ------------------------- | ---- | ------------ |
  | colorSpace | [ColorSpace](#colorspace) | Yes  | Color gamut mode.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  let promise = windowClass.isSupportWideGamut(window.ColorSpace.WIDE_GAMUT);
  promise.then((data)=> {
      console.info('Succeeded in setting window colorspace. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set window colorspacet. Cause: ' + JSON.stringify(err));
  });
  ```

### getColorSpace<sup>8+</sup>

getColorSpace(callback: AsyncCallback&lt;ColorSpace&gt;): void

Obtains the color gamut mode of this window. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                                          | Mandatory| Description                      |
  | -------- | ---------------------------------------------- | ---- | -------------------------- |
  | callback | AsyncCallback&lt;[ColorSpace](#colorspace)&gt; | Yes  | Callback used to return the color gamut mode obtained.|

- Example

  ```
  windowClass.getColorSpace((err, data) => {
      if (err.code) {
          console.error('Failed to get window color space. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in getting window color space. Cause:' + JSON.stringify(data))
  })
  ```

### getColorSpace<sup>8+</sup>

getColorSpace(): Promise&lt;ColorSpace&gt;

Obtains the color gamut mode of this window. This API uses a promise to return the result.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Return value

  | Type                                    | Description                                     |
  | ---------------------------------------- | ----------------------------------------- |
  | Promise&lt;[ColorSpace](#colorspace)&gt; | Promise used to return the color gamut mode obtained.|

- Example

  ```
  let promise = windowClass.getColorSpace();
  promise.then((data)=> {
      console.info('Succeeded in getting window color space. Cause:' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set window colorspacet. Cause: ' + JSON.stringify(err));
  });
  ```

### setBackgroundColor

setBackgroundColor(color: string, callback: AsyncCallback&lt;void&gt;): void

Sets the background color for this window. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name  | Type                     | Mandatory| Description                                                        |
  | -------- | ------------------------- | ---- | ------------------------------------------------------------ |
  | color    | string                    | Yes  | Background color to set. The color is a hexadecimal value, for example, #00FF00 or #FF00FF00.|
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                                                  |

- Example

  ```
  var color = '#00ff33';
  windowClass.setBackgroundColor(color, (err, data) => {
      if (err.code) {
          console.error('Failed to set the background color. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the background color. Data: ' + JSON.stringify(data));
  });
  ```

### setBackgroundColor

setBackgroundColor(color: string): Promise&lt;void&gt;

Sets the background color for this window. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name| Type  | Mandatory| Description                                                        |
  | ------ | ------ | ---- | ------------------------------------------------------------ |
  | color  | string | Yes  | Background color to set. The color is a hexadecimal value, for example, #00FF00 or #FF00FF00.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var color = '#00ff33';
  let promise = windowClass.setBackgroundColor(color);
  promise.then((data)=> {
      console.info('Succeeded in setting the background color. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the background color. Cause: ' + JSON.stringify(err));
  });
  ```

### setBrightness

setBrightness(brightness: number, callback: AsyncCallback&lt;void&gt;): void

Sets the screen brightness for this window. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name    | Type                     | Mandatory| Description                                |
  | ---------- | ------------------------- | ---- | ------------------------------------ |
  | brightness | number                    | Yes  | Brightness to set, which ranges from 0 to 1. The value **1** indicates the brightest.|
  | callback   | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                          |

- Example

  ```
  var brightness = 1;
  windowClass.setBrightness(brightness, (err, data) => {
      if (err.code) {
          console.error('Failed to set the brightness. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the brightness. Data: ' + JSON.stringify(data));
  });
  ```

### setBrightness

setBrightness(brightness: number): Promise&lt;void&gt;

Sets the screen brightness for this window. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name    | Type  | Mandatory| Description                                |
  | ---------- | ------ | ---- | ------------------------------------ |
  | brightness | number | Yes  | Brightness to set, which ranges from 0 to 1. The value **1** indicates the brightest.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var brightness = 1;
  let promise = windowClass.setBrightness(brightness);
  promise.then((data)=> {
      console.info('Succeeded in setting the brightness. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the brightness. Cause: ' + JSON.stringify(err));
  });
  ```

### setDimBehind<sup>7+</sup>

setDimBehind(dimBehindValue: number, callback: AsyncCallback&lt;void&gt;): void

Sets the dimness of the window that is not on top. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name        | Type                     | Mandatory| Description                                              |
  | -------------- | ------------------------- | ---- | -------------------------------------------------- |
  | dimBehindValue | number                    | Yes  | Dimness of the window to set. The value ranges from 0 to 1. The value **1** indicates the dimmest.|
  | callback       | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                                        |

- Example

  ```
  windowClass.setDimBehind(0.5, (err, data) => {
      if (err.code) {
          console.error('Failed to set the dimness. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the dimness. Data:' + JSON.stringify(data));
  });
  ```

### setDimBehind<sup>7+</sup>

setDimBehind(dimBehindValue: number): Promise&lt;void&gt;

Sets the dimness of the window that is not on top. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name        | Type  | Mandatory| Description                                              |
  | -------------- | ------ | ---- | -------------------------------------------------- |
  | dimBehindValue | number | Yes  | Dimness of the window to set. The value ranges from 0 to 1. The value **1** indicates the dimmest.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  let promise = windowClass.setDimBehind(0.5);
  promise.then((data)=> {
      console.info('Succeeded in setting the dimness. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the dimness. Cause: ' + JSON.stringify(err));
  });
  ```

### setFocusable<sup>7+</sup>

setFocusable(isFocusable: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether this window can gain focus. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name     | Type                     | Mandatory| Description                        |
  | ----------- | ------------------------- | ---- | ---------------------------- |
  | isFocusable | boolean                   | Yes  | Whether the window can gain focus.|
  | callback    | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.                  |

- Example

  ```
  var isFocusable= true;
  windowClass.setFocusable(isFocusable, (err, data) => {
      if (err.code) {
          console.error('Failed to set the window to be focusable. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the window to be focusable. Data: ' + JSON.stringify(data));
  });
  ```

### setFocusable<sup>7+</sup>

setFocusable(isFocusable: boolean): Promise&lt;void&gt;

Sets whether this window can gain focus. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name     | Type   | Mandatory| Description                        |
  | ----------- | ------- | ---- | ---------------------------- |
  | isFocusable | boolean | Yes  | Whether the window can gain focus.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var isFocusable= true;
  let promise = windowClass.setFocusable(isFocusable);
  promise.then((data)=> {
      console.info('Succeeded in setting the window to be focusable. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the window to be focusable. Cause: ' + JSON.stringify(err));
  });
  ```

### setKeepScreenOn

setKeepScreenOn(isKeepScreenOn: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether to keep the screen always on. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name        | Type                     | Mandatory| Description                    |
  | -------------- | ------------------------- | ---- | ------------------------ |
  | isKeepScreenOn | boolean                   | Yes  | Whether to keep the screen always on.|
  | callback       | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.              |

- Example

  ```
  var isKeepScreenOn = true;
  windowClass.setKeepScreenOn(isKeepScreenOn, (err, data) => {
      if (err.code) {
          console.error('Failed to set the screen to be always on. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the screen to be always on. Data: ' + JSON.stringify(data));
  });
  ```

### setKeepScreenOn

setKeepScreenOn(isKeepScreenOn: boolean): Promise&lt;void&gt;

Sets whether to keep the screen always on. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name        | Type   | Mandatory| Description                    |
  | -------------- | ------- | ---- | ------------------------ |
  | isKeepScreenOn | boolean | Yes  | Whether to keep the screen always on.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var isKeepScreenOn= true;
  let promise = windowClass.setKeepScreenOn(isKeepScreenOn);
  promise.then((data)=> {
      console.info('Succeeded in setting the screen to be always on. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the screen to be always on. Cause: ' + JSON.stringify(err));
  });
  ```

### setOutsideTouchable<sup>7+</sup>

setOutsideTouchable(touchable: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether the area outside the subwindow is touchable. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name   | Type                     | Mandatory| Description            |
  | --------- | ------------------------- | ---- | ---------------- |
  | touchable | boolean                   | Yes  | Whether the area outside the subwindow is touchable. The value **true** means that such an area is touchable, and **false** means the opposite.|
  | callback  | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.      |

- Example

  ```
  windowClass.setOutsideTouchable(true, (err, data) => {
      if (err.code) {
          console.error('Failed to set the area to be touchable. Cause: ' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the area to be touchable. Data: ' + JSON.stringify(data))
  })
  ```

### setOutsideTouchable<sup>7+</sup>

setOutsideTouchable(touchable: boolean): Promise&lt;void&gt;

Sets whether the area outside the subwindow is touchable. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name   | Type   | Mandatory| Description            |
  | --------- | ------- | ---- | ---------------- |
  | touchable | boolean | Yes  | Whether the area outside the subwindow is touchable. The value **true** means that such an area is touchable, and **false** means the opposite.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  let promise = windowClass.setOutsideTouchable(true);
  promise.then((data)=> {
      console.info('Succeeded in setting the area to be touchable. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the area to be touchable. Cause: ' + JSON.stringify(err));
  });
  ```

### setPrivacyMode<sup>7+</sup>

setPrivacyMode(isPrivacyMode: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether this window is in privacy mode. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name       | Type                     | Mandatory| Description                |
  | ------------- | ------------------------- | ---- | -------------------- |
  | isPrivacyMode | boolean                   | Yes  | Whether the window is in privacy mode.|
  | callback      | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.          |

- Example

  ```
  var isPrivacyMode = true;
  windowClass.setPrivacyMode(isPrivacyMode, (err, data) => {
      if (err.code) {
          console.error('Failed to set the window to privacy mode. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the window to privacy mode. Data:' + JSON.stringify(data));
  
  });
  ```

### setPrivacyMode<sup>7+</sup>

setPrivacyMode(isPrivacyMode: boolean): Promise&lt;void&gt;

Sets whether this window is in privacy mode. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name       | Type   | Mandatory| Description                |
  | ------------- | ------- | ---- | -------------------- |
  | isPrivacyMode | boolean | Yes  | Whether the window is in privacy mode.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var isPrivacyMode = true;
  let promise = windowClass.setPrivacyMode(isPrivacyMode);
  promise.then((data)=> {
      console.info('Succeeded in setting the window to privacy mode. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the window to privacy mode. Cause: ' + JSON.stringify(err));
  });
  ```

### setTouchable<sup>7+</sup>

setTouchable(isTouchable: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets whether this window is touchable. This API uses an asynchronous callback to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name     | Type                     | Mandatory| Description                |
  | ----------- | ------------------------- | ---- | -------------------- |
  | isTouchable | boolean                   | Yes  | Whether the window is touchable.|
  | callback    | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the execution result.          |

- Example

  ```
  var isTouchable = true;
  windowClass.setTouchable(isTouchable, (err, data) => {
      if (err.code) {
          console.error('Failed to set the window to be touchable. Cause:' + JSON.stringify(err));
          return;
      }
      console.info('Succeeded in setting the window to be touchable. Data:' + JSON.stringify(data));
  
  });
  ```

### setTouchable<sup>7+</sup>

setTouchable(isTouchable: boolean): Promise&lt;void&gt;

Sets whether this window is touchable. This API uses a promise to return the result.

This API is defined but not implemented in OpenHarmony 3.1 Release. It will be available for use in OpenHarmony 3.1 MR.

**System capability**: SystemCapability.WindowManager.WindowManager.Core

- Parameters

  | Name     | Type   | Mandatory| Description                |
  | ----------- | ------- | ---- | -------------------- |
  | isTouchable | boolean | Yes  | Whether the window is touchable.|

- Return value

  | Type               | Description                                           |
  | ------------------- | ----------------------------------------------- |
  | Promise&lt;void&gt; | Promise used to return the execution result.|

- Example

  ```
  var isTouchable = true;
  let promise = windowClass.setTouchable(isTouchable);
  promise.then((data)=> {
      console.info('Succeeded in setting the window to be touchable. Data: ' + JSON.stringify(data))
  }).catch((err)=>{
      console.error('Failed to set the window to be touchable. Cause: ' + JSON.stringify(err));
  });
  ```

### 