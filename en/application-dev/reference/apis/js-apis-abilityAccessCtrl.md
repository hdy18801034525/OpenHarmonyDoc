#  	Ability Access Control

> ![icon-note.gif](public_sys-resources/icon-note.gif) **NOTE**
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```
import abilityAccessCtrl from '@ohos.abilityAccessCtrl'
```

## System Capabilities
SystemCapability.Security.AccessToken

## abilityAccessCtrl.createAtManager

createAtManager(): AtManager

Creates an **AtManager** instance, which is used for ability access control.

**Return value**

| Type| Description|
| -------- | -------- |
| [AtManager](#atmanager) | **AtManager** instance obtained.|

**Example**

```
var AtManager = abilityAccessCtrl.createAtManager();
```

## AtManager

Implements ability access control.

### verifyAccessToken

verifyAccessToken(tokenID: number, permissionName: string): Promise&lt;GrantStatus&gt;

Checks whether an application has been granted the specified permission. This method uses a promise to return the result.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------------------  | ---- | ------------------------------------------ |
| tokenID   |  number   | Yes| ID of the application.|
| permissionName | string | Yes| Name of the permission to verify.|

**Return value**

| Type| Description|
| :------------ | :---------------------------------- |
| Promise&lt;GrantStatus&gt; | Promise instance used to return the result.|

**Example**

```
const AtManager = abilityAccessCtrl.createAtManager();
let tokenID = 0;
let promise = AtManager.verifyAccessToken(tokenID, "ohos.permission.GRANT_SENSITIVE_PERMISSIONS");
promise.then(data => {
    console.log(`promise: data->${JSON.stringify(data)}`);
});
```

### grantUserGrantedPermission

grantUserGrantedPermission(tokenID: number, permissionName: string, permissionFlag: number): Promise&lt;number&gt;

Grants a user granted permission to an application. This method uses a promise to return the result.

Required permission: ohos.permission.GRANT_SENSITIVE_PERMISSIONS

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ------------------- | ---- | ------------------------------------------------------------ |
| tokenID      | number              | Yes| ID of the application.|
| permissionName | string              | Yes| Name of the permission to grant.|
| permissionFlag  | number | Yes| Permission flag. The value **1** means that a dialog box will still be displayed after the user grants or denies the permission. The value **2** means that no dialog box will be displayed after the user grants or denies the permission. The value **3** means a system permission that cannot be changed.|

**Return value**

| Type| Description|
| :------------ | :---------------------------------- |
| Promise&lt;number&gt; | Promise instance used to return the result.|

**Example**

```
const AtManager = abilityAccessCtrl.createAtManager();
let tokenID = 0;
let promise = AtManager.grantUserGrantedPermission(tokenID, "ohos.permission.GRANT_SENSITIVE_PERMISSIONS");
promise.then(data => {
    console.log(`promise: data->${JSON.stringify(data)}`);
});
```



### grantUserGrantedPermission

grantUserGrantedPermission(tokenID: number, permissionName: string, permissionFlag: number, callback: AsyncCallback&lt;number&gt;): void

Grants a user granted permission to an application. This method uses an asynchronous callback to return the result.

Required permission: ohos.permission.GRANT_SENSITIVE_PERMISSIONS

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ------------------- | ---- | ------------------------------------------------------------ |
| tokenID      | number              | Yes| ID of the application.|
| permissionName | string              | Yes| Name of the permission to grant.|
| permissionFlag  | number | Yes| Permission flag. The value **1** means that a dialog box will still be displayed after the user grants or denies the permission. The value **2** means that no dialog box will be displayed after the user grants or denies the permission. The value **3** means a system permission that cannot be changed.|
| callback | AsyncCallback&lt;number&gt; | Yes| Callback used to return the result.|

**Example**

```
const AtManager = abilityAccessCtrl.createAtManager();
let tokenID = 0;
let permissionFlag = 1;
AtManager.grantUserGrantedPermission(tokenID, "ohos.permission.GRANT_SENSITIVE_PERMISSIONS",permissionFlag, data => {
    console.log(`callback: data->${JSON.stringify(data)}`);
});
```

### revokeUserGrantedPermission

revokeUserGrantedPermission(tokenID: number, permissionName: string, permissionFlag: number): Promise&lt;number&gt;

Revokes a user granted permission given to an application. This method uses a promise to return the result.

Required permission: ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ------------------- | ---- | ------------------------------------------------------------ |
| tokenID      | number              | Yes| ID of the application.|
| permissionName | string              | Yes| Name of the permission to revoke.|
| permissionFlag  | number | Yes| Permission flag. The value **1** means that a dialog box will still be displayed after the user grants or denies the permission. The value **2** means that no dialog box will be displayed after the user grants or denies the permission. The value **3** means a system permission that cannot be changed.|

**Return value**

| Type| Description|
| :------------ | :---------------------------------- |
| Promise&lt;number&gt; | Promise instance used to return the result.|

**Example**

```
const AtManager = abilityAccessCtrl.createAtManager();
let tokenID = 0;
let permissionFlag = 1;
let promise = AtManager.revokeUserGrantedPermission(tokenID, "ohos.permission.GRANT_SENSITIVE_PERMISSIONS", permissionFlag);
promise.then(data => {
    console.log(`promise: data->${JSON.stringify(data)}`);
});
```

### revokeUserGrantedPermission

revokeUserGrantedPermission(tokenID: number, permissionName: string, permissionFlag: number, callback: AsyncCallback&lt;number&gt;): void

Revokes a user granted permission given to an application. This method uses an asynchronous callback to return the result.

Required permission: ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ------------------- | ---- | ------------------------------------------------------------ |
| tokenID      | number              | Yes| ID of the application.|
| permissionName | string              | Yes| Name of the permission to revoke.|
| permissionFlag  | number | Yes| Permission flag. The value **1** means that a dialog box will still be displayed after the user grants or denies the permission. The value **2** means that no dialog box will be displayed after the user grants or denies the permission. The value **3** means a system permission that cannot be changed.|
| callback | AsyncCallback&lt;number&gt; | Yes| Callback used to return the result.|

**Example**

```
const AtManager = abilityAccessCtrl.createAtManager();
let tokenID = 0;
AtManager.revokeUserGrantedPermission(tokenID, "ohos.permission.GRANT_SENSITIVE_PERMISSIONS",permissionFlag, data => {
    console.log(`callback: data->${JSON.stringify(data)}`);
});
```

### getPermissionFlags

getPermissionFlags(tokenID: number, permissionName: string): Promise&lt;number&gt;

Obtains the flags of the specified permission of a given application. This method uses a promise to return the result.

**Parameters**

| Name| Type| Mandatory| Description|
| --------- | ------------------- | ---- | ------------------------------------------------------------ |
| tokenID      | number              | Yes| ID of the application.|
| permissionName | string              | Yes| Name of the permission to query.|

**Return value**

| Type| Description|
| :------------ | :---------------------------------- |
| Promise&lt;number&gt; | Promise instance used to return the result.|

**Example**

```
const AtManager = abilityAccessCtrl.createAtManager();
let tokenID = 0;
let promise = AtManager.getPermissionFlags(tokenID, "ohos.permission.GRANT_SENSITIVE_PERMISSIONS");
promise.then(data => {
    console.log(`promise: data->${JSON.stringify(data)}`);
});
```