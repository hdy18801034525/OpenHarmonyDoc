# JS API Changes of the Common Event and Notification Framework

The table below lists the APIs changes of the common event and notification framework in OpenHarmony 3.1 Release over OpenHarmony 3.0 LTS.

## API Changes

| Module| Class| Method/Attribute/Enumeration/Constant| Change Type|
|---|---|---|---|
| notificationUserInput | NotificationUserInput | inputKey: string; | Added|
| notificationTemplate | NotificationTemplate | data: {[key: string]: Object}; | Added|
| notificationTemplate | NotificationTemplate | name: string; | Added|
| notificationRequest | DistributedOptions | supportOperateDevices?: Array<string>; | Added|
| notificationRequest | DistributedOptions | supportDisplayDevices?: Array<string>; | Added|
| notificationRequest | DistributedOptions | isDistributed?: boolean; | Added|
| notificationRequest | NotificationRequest | readonly notificationFlags?: NotificationFlags; | Added|
| notificationRequest | NotificationRequest | distributedOption?: DistributedOptions; | Added|
| notificationRequest | NotificationRequest | template?: NotificationTemplate; | Added|
| notificationRequest | NotificationRequest | readonly creatorUserId?: number; | Added|
| notificationRequest | NotificationRequest | groupName?: string; | Added|
| notificationActionButton | NotificationActionButton | userInput?: NotificationUserInput; | Added|
| ohos.notification | notification | function isDistributedEnabled(callback: AsyncCallback<boolean>): void;<br>function isDistributedEnabled(): Promise<boolean>; | Added|
| ohos.notification | notification | function requestEnableNotification(callback: AsyncCallback<void>): void;<br>function requestEnableNotification(): Promise<void>; | Added|
| ohos.notification | notification | function isSupportTemplate(templateName: string, callback: AsyncCallback<boolean>): void;<br>function isSupportTemplate(templateName: string): Promise<boolean>; | Added|
| ohos.notification | notification | function cancelGroup(groupName: string, callback: AsyncCallback<void>): void;<br>function cancelGroup(groupName: string): Promise<void>; | Added|
| ohos.events.emitter | EventPriority | IDLE | Added|
| ohos.events.emitter | EventPriority | LOW | Added|
| ohos.events.emitter | EventPriority | HIGH | Added|
| ohos.events.emitter | EventPriority | IMMEDIATE = 0 | Added|
| ohos.events.emitter | InnerEvent | priority?: EventPriority; | Added|
| ohos.events.emitter | InnerEvent | eventId: number; | Added|
| ohos.events.emitter | EventData | data?: {[key: string]: any}; | Added|
| ohos.events.emitter | emitter | function emit(event: InnerEvent, data?: EventData): void; | Added|
| ohos.events.emitter | emitter | function off(eventId: number): void; | Added|
| ohos.events.emitter | emitter | function once(event: InnerEvent, callback: Callback<EventData>): void; | Added|
| ohos.events.emitter | emitter | function on(event: InnerEvent, callback: Callback<EventData>): void; | Added|
| ohos.commonEvent | Support | COMMON_EVENT_SPLIT_SCREEN = "common.event.SPLIT_SCREEN" | Added|
| ohos.commonEvent | Support | COMMON_EVENT_THERMAL_LEVEL_CHANGED = "usual.event.THERMAL_LEVEL_CHANGED" | Added|
