# Video

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 该组件从API Version 7开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。


视频播放组件。


## 子组件

不支持子组件。


## 接口

Video(value: VideoOption)

- VideoOption类型接口说明
  | 参数名 | 参数类型 | 必填 | 默认值 | 参数描述 |
  | -------- | -------- | -------- | -------- | -------- |
  | src | string | 否 | - | 视频播放源的路径。 |
  | currentProgressRate | number&nbsp;\|&nbsp;PlaybackSpeed<sup>8+</sup> | 否 | 1.0&nbsp;\|&nbsp;PlaybackSpeed.<br>Speed_Forward_1_00_X | 视频播放倍速。<br/>>&nbsp;![icon-note.gif](public_sys-resources/icon-note.gif)&nbsp;**说明：**<br/>>&nbsp;number取值仅支持：0.75，1.0，1.25，1.75，2.0。<br/> |
  | previewUri | string&nbsp;\|&nbsp;PixelMap<sup>8+</sup>&nbsp;\|&nbsp;[Resource](../../ui/ts-types.md#resource类型) | 否 | - | 预览图片的路径。 |
  | controller | [VideoController](#videocontroller) | 否 | - | 控制器。 |


- PlaybackSpeed<sup>8+</sup>类型接口说明
  | 名称 | 描述 | 
  | -------- | -------- |
  | Speed_Forward_0_75_X | 0.75倍速播放。 | 
  | Speed_Forward_1_00_X | 1倍速播放。 | 
  | Speed_Forward_1_25_X | 1.25倍速播放。 | 
  | Speed_Forward_1_75_X | 1.75倍速播放。 | 
  | Speed_Forward_2_00_X | 2倍速播放。 | 


## 属性

| 名称 | 参数类型 | 默认值 | 描述 |
| -------- | -------- | -------- | -------- |
| muted | boolean | false | 是否静音。 |
| autoPlay | boolean | false | 是否自动播放。 |
| controls | boolean | true | 控制视频播放的控制栏是否显示。 |
| objectFit | [ImageFit](ts-basic-components-image.md) | Cover | 设置视频显示模式。 |
| loop | boolean | false | 是否单个视频循环播放。 |


## 事件

| 名称 | 功能描述 | 
| -------- | -------- |
| onStart()&nbsp;=&gt;&nbsp;void | 播放时触发该事件。 | 
| onPause()&nbsp;=&gt;&nbsp;void | 暂停时触发该事件。 | 
| onFinish()&nbsp;=&gt;&nbsp;void | 播放结束时触发该事件。 | 
| onError()&nbsp;=&gt;&nbsp;void | 播放失败时触发该事件。 |
| onPrepared(event?:&nbsp;{&nbsp;duration:&nbsp;number&nbsp;})&nbsp;=&gt;&nbsp;void | 视频准备完成时触发该事件，通过duration可以获取视频时长，单位为秒(s)。 | 
| onSeeking(event?:&nbsp;{&nbsp;time:&nbsp;number&nbsp;})&nbsp;=&gt;&nbsp;void | 操作进度条过程时上报时间信息，单位为s。 | 
| onSeeked(event?:&nbsp;{&nbsp;time:&nbsp;number&nbsp;})&nbsp;=&gt;&nbsp;void | 操作进度条完成后，上报播放时间信息，单位为s。 | 
| onUpdate(event?:&nbsp;{&nbsp;time:&nbsp;number&nbsp;})&nbsp;=&gt;&nbsp;void | 播放进度变化时触发该事件，单位为s，更新时间间隔为250ms。 | 


### VideoController

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 一个VideoController对象可以控制一个或多个video。

| 接口名称 | 描述 |
| -------- | -------- |
| start()&nbsp;:&nbsp;void | 开始播放。 |
| pause()&nbsp;:&nbsp;void | 暂停播放。 |
| stop()&nbsp;:&nbsp;void | 停止播放。 |
| setCurrentTime(value:&nbsp;number) | 指定视频播放的进度位置。 |
| setCurrentTime(value:&nbsp;number,&nbsp;seekMode:&nbsp;SeekMode | 指定视频播放的进度位置，并指定跳转模式。 |

- SeekMode<sup>8+</sup>类型接口说明
  | 名称 | 描述 | 
  | -------- | -------- |
  | PreviousKeyframe | 跳转到前一个最近的关键帧。 | 
  | NextKeyframe | 跳转到后一个最近的关键帧。 | 
  | ClosestKeyframe | 跳转到最近的关键帧。 | 
  | Accurate | 精准跳转，不论是否为关键帧。 | 


## 示例

```
@Entry
@Component
struct VideoCreateComponent {
  @State srcs: string = "/resources/video/video1.mp4";
  @State previewUris: string = "/resources/image/media.JPG";
  @State currentProgressRates: number = 1;
  @State autoPlays: boolean = false;
  @State controlsss: boolean = true;
  myVideoController: VideoController = new VideoController();
  @State startStaus: boolean = true;
  build() {
    Column() {
      Video({
        src: this.srcs,
        previewUri: this.previewUris, 
        currentProgressRate: this.currentProgressRates,
        controller: this.myVideoController
      }).width(700).height(500)
        .autoPlay(this.autoPlays)
        .controls(this.controlsss)
        .onStart(() => {
                  console.error('onStart');
                })
        .onPause(() => {
                  console.error('onPause');
                })
        .onFinish(() => {
                  console.error('onFinish');
                })
        .onError(() => {
                  console.error('onFinish');
                })
        .onPrepared((e) => {
                    console.error('onPrepared is ' + e.duration);
                })
        .onSeeking((e) => {
                    console.error('onSeeking is ' + e.time);
                })
        .onSeeked((e) => {
                    console.error('onSeekedis ' + e.time);
                })
        .onUpdate((e) => {
                    console.error('onUpdateis ' + e.time);
                })
      Row() {
        Button("src").onClick(() => {
          if (this.srcs == "/resources/video/video1.mp4") {
            this.srcs = "/resources/video/video2.mp4";
          } else {
            this.srcs = "/resources/video/video1.mp4";
          }
        });
        Button("previewUri").onClick(() => {
          if (this.previewUris == "/resources/image/media.JPG") {
            this.previewUris = "/resources/image/sinlin.png";
          } else {
            this.previewUris = "/resources/image/media.JPG";
          }
        });
        Button("controlsss").onClick(() => {
          this.controlsss = !this.controlsss;
        });
      }

      Row() {
        Button("start").onClick(() => {
          this.myVideoController.start();
        });
        Button("pause").onClick(() => {
          this.myVideoController.pause();
        });
        Button("stop").onClick(() => {
          this.myVideoController.stop();
        });
      }

      Row() {
        Button("setCurrentTime").onClick(() => {
          this.myVideoController.setCurrentTime(9, SeekMode.Accurate);
        });
      }
    }
  }
}
```