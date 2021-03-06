# FA Model Overview

## Overall Architecture
The development of an OpenHarmony application is essentially the development of one or more abilities. By scheduling abilities and managing their lifecycle, OpenHarmony implements application scheduling.

The Feature Ability (FA) model applies to application development using API 8 and earlier versions. In this model, there are Page, Service, Data, and Form abilities.  
- The Page ability implements the ArkUI and provides the capability of interacting with users.
- The Service ability does not have a UI. It runs in the background and provides custom services for other abilities to invoke. 
- The Data ability does not have a UI. It also runs in the background and enables other abilities to insert, delete, and query data.
- The Form ability provides a widget, which is a UI display mode.

## Application Package Structure
**The following figure shows the application package structure.**

![fa-package-info](figures/fa-package-info.png)

For details about the application package structure, see [Description of the Application Package Structure Configuration File](../quick-start/package-structure.md).

## Lifecycle

Among all abilities, the Page ability has the most complex lifecycle, because it has a UI and is the interaction entry of applications.
**The following figure shows the lifecycle of the Page ability.**

![fa-pageAbility-lifecycle](figures/fa-pageAbility-lifecycle.png)

The other abilities do not involve the foreground/background switchover and the **onShow** callback.
You can override the lifecycle callbacks in **app.js/app.ets** to process application logic.

Currently, the **app.js** file provides only the **onCreate** and **onDestroy** callbacks, and the **app.ets** file provides the full lifecycle callbacks.


## Process and Thread Model
An application exclusively uses an independent process, and an ability exclusively uses an independent thread. An application process is created when an ability is started for the first time, and a thread is created for this ability too. After the application is started, other abilities in the application are started, and a thread is created for every of these started abilities. Each ability is bound to an independent JSRuntime instance. Therefore, abilities are isolated from each other.

![fa-threading-nodel](figures/fa-threading-model.png)
