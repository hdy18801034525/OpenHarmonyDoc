# HUKS开发指导

## 场景介绍

 HUKS（OpenHarmony Universal KeyStore，OpenHarmony通用密钥库系统）向应用提供密钥库能力，包括密钥管理及密钥的密码学操作等功能。HUKS所管理的密钥可以由应用导入或者由应用调用HUKS接口生成。 


## 接口说明

| 接口名                                                       | 描述             |
| ------------------------------------------------------------ | ---------------- |
| function generateKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HksResult>) : void; | 生成密钥/密钥对  |
| function generateKey(keyAlias: string, options: HuksOptions) : Promise<HuksResult>; | 生成密钥/密钥对  |
| function exportKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void; | 导出公钥         |
| function exportKey(keyAlias: string, options: HuksOptions) : Promise<HuksResult>; | 导出公钥         |
| function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>) : void; | 查询密钥是否存在 |
| function isKeyExist(keyAlias: string, options: HuksOptions) : Promise<boolean>; | 查询密钥是否存在 |
| function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void; | 删除密钥         |
| function deleteKey(keyAlias: string, options: HuksOptions) : Promise<HuksResult>; | 删除密钥         |

## 开发步骤

1. 引入HUKS模块

   ```js
   import huks from '@ohos.security.huks'
   ```

2. 使用generateKey接口生成密钥对。

   keyAlias为生成的密钥别名，options为生成密钥时使用到的参数，需根据具体需要到的算法设定options中的参数。

   generateKey接口会返回密钥的生成是否成功。

   ```js
   var alias = 'testAlias';
   var properties = new Array();
   properties[0] = {
     tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
     value: huks.HuksKeyAlg.HUKS_ALG_ECC
   };
   properties[1] = {
     tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
     value: huks.HuksKeySize.HUKS_ECC_KEY_SIZE_224
   };
   properties[2] = {
     tag: huks.HuksTag.HUKS_TAG_PURPOSE,
     value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_AGREE
   };
   properties[3] = {
     tag: huks.HuksTag.HUKS_TAG_DIGEST,
     value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
   };
   var options = {
     properties: properties
   }
   var resultA = await huks.generateKey(alias, options);
   ```

3. 使用Init接口进行init操作。

   Alias为初始化密钥的别名，options为初始化密钥用的参数集合，需根据具体需要到的算法设定options中的参数。

   init接口会返回init操作是否成功。

   ```js
   var alias = 'test001'
   var properties = new Array();
   properties[0] = {
     tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
     value: huks.HksKeyAlg.HKS_ALG_DH
   };
   properties[1] = {
     tag: huks.HksTag.HKS_TAG_PURPOSE,
     value: huks.HksKeyPurpose.HKS_KEY_PURPOSE_AGREE
   };
   properties[2] = {
     tag: huks.HksTag.HKS_TAG_KEY_SIZE
     value: huks.HksKeySize.HKS_DH_KEY_SIZE_4096
   };
   var options = {
     properties: properties
   };
   huks.init(alias, options, function (err, data){}); 
   ```
   
4. 使用Update接口进行update操作。

   handle为更新密钥的session id，options为更新密钥用的参数集合，需根据具体需要到的算法设定options中的参数。

   update接口会返回update操作是否成功。

   ```js
   var properties = new Array();
   properties[0] = {
     tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
     value: huks.HksKeyAlg.HKS_ALG_DH
   };
   properties[1] = {
     tag: huks.HksTag.HKS_TAG_PURPOSE,
     value: huks.HksKeyPurpose.HKS_KEY_PURPOSE_AGREE
   };
   properties[2] = {
     tag: huks.HksTag.HKS_TAG_KEY_SIZE
     value: huks.HksKeySize.HKS_DH_KEY_SIZE_4096
   };
   var options = {
     properties: properties
   };
   huks.update(handle, options, function (err, data){}); 
   ```
   
5. 使用Finish接口进行finish操作。

   handle为 结束密钥的session id，options为结束密钥用的参数集合，需根据具体需要到的算法设定options中的参数。

   finish接口会返回finish操作是否成功。

   ```js
   var properties = new Array();
   properties[0] = {
     tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
     value: huks.HksKeyAlg.HKS_ALG_DH
   };
   properties[1] = {
     tag: huks.HksTag.HKS_TAG_PURPOSE,
     value: huks.HksKeyPurpose.HKS_KEY_PURPOSE_AGREE
   };
   properties[2] = {
     tag: huks.HksTag.HKS_TAG_KEY_SIZE
     value: huks.HksKeySize.HKS_DH_KEY_SIZE_4096
   };
   var options = {
     properties: properties
   };
   huks.finish(handle, options, function (err, data){}); 
   ```


