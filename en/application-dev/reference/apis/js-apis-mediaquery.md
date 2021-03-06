# Media Query

> ![icon-note.gif](public_sys-resources/icon-note.gif)**NOTE**
> The APIs of this module are supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```
import mediaquery from '@ohos.mediaquery'
```


## Required Permissions

None.


## mediaquery.matchMediaSync

matchMediaSync(condition: string): MediaQueryListener

Sets the media query criteria and returns the corresponding listening handle.

- Parameters
  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | condition | string | Yes| Matching condition of a media event.| 

- Return value
  | Type| Description| 
  | -------- | -------- |
  | MediaQueryListener | Listening handle to a media event, which is used to register or unregister the listening callback.| 

- Example
  ```
  listener = mediaquery.matchMediaSync('(orientation: landscape)'); // Listen for landscape events.
  ```


## MediaQueryListener

Media query handle, including the first query result when the handle is applied for.


### Attributes

| Name| Type| Readable| Writable| Description| 
| -------- | -------- | -------- | -------- | -------- |
| matches | boolean | Yes| No| Whether the match condition is met.| 
| media | string | Yes| No| Matching condition of a media event.| 


### on

on(type: 'change', callback: Callback&lt;MediaQueryResult&gt;): void

Registers a callback with the corresponding query condition by using the handle. This callback is triggered when the media attributes change.

- Parameters
  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | type | string | Yes| Must enter the string **change**.| 
  | callback | Callback&lt;MediaQueryResult&gt; | Yes| Callback registered with media query.| 

- Example
  For details, see [off Example](#off).


### off

off(type: 'change', callback?: Callback&lt;MediaQueryResult&gt;): void

Unregisters a callback with the corresponding query condition by using the handle, so that no callback is triggered when the media attributes change.
- Parameters
  | Name| Type| Mandatory| Description| 
  | -------- | -------- | -------- | -------- |
  | type | boolean | Yes| Must enter the string **change**.| 
  | callback | Callback&lt;MediaQueryResult&gt; | No| Callback to be unregistered. If the default value is used, all callbacks of the handle are unregistered.| 

- Example
  ```
    import mediaquery from '@ohos.mediaquery'
    
    listener = mediaquery.matchMediaSync('(orientation: landscape)'); // Listen for landscape events.
    function onPortrait(mediaQueryResult) {
        if (mediaQueryResult.matches) {
            // do something here
        } else {
            // do something here
        }
    }
    this.listener.on('change', this.onPortrait) // Registration callback.
    this.listener.off('change', this.onPortrait) // Deregistration callback.
  ```


## MediaQueryResult


### Attributes

| Name| Type| Readable| Writable| Description| 
| -------- | -------- | -------- | -------- | -------- |
| matches | boolean | Yes| No| Whether the match condition is met.| 
| media | string | Yes| No| Matching condition of a media event.| 


### Example

```
import mediaquery from '@ohos.mediaquery'

let portraitFunc = null

@Entry
@Component
struct MediaQueryExample {
  @State color: string = '#DB7093'
  @State text: string = 'Portrait'
  listener = mediaquery.matchMediaSync('(orientation: landscape)')

  onPortrait(mediaQueryResult) {
    if (mediaQueryResult.matches) {
      this.color = '#FFD700'
      this.text = 'Landscape'
    } else {
      this.color = '#DB7093'
      this.text = 'Portrait'
    }
  }

  aboutToAppear() {
    portraitFunc = this.onPortrait.bind(this) //bind current js instance
    this.listener.on('change', portraitFunc)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text(this.text).fontSize(24).fontColor(this.color)
    }
    .width('100%').height('100%')
  }
}
```
