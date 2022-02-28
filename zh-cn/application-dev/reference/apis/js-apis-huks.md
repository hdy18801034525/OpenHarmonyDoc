# 通用密钥库系统

向应用提供密钥库能力，包括密钥管理及密钥的密码学操作等功能。

HUKS所管理的密钥可以由应用导入或者由应用调用HUKS接口生成。

## 导入模块

```js
import huks from '@ohos.security.huks'
```
## huks.HuksErrorCode

表示错误码的枚举。

| 名称                       | 值    | 说明 |
| -------------------------- | ----- | ---- |
| HUKS_SUCCESS | 0     |表示成功。表示当前设备连接的充电器类型。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_FAILURE | -1    |表示失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_BAD_STATE | -2    |表示错误的状态。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_ARGUMENT | -3    |表示无效的数据。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_NOT_SUPPORTED | -4    |表示不支持。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_NO_PERMISSION | -5    |表示没有许可。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INSUFFICIENT_DATA | -6    |表示数据不足。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_BUFFER_TOO_SMALL | -7    |表示缓冲区太小。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INSUFFICIENT_MEMORY | -8    |表示内存不足。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_COMMUNICATION_FAILURE | -9    |表示通讯失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_STORAGE_FAILURE | -10   |表示存储故障。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_HARDWARE_FAILURE | -11   |表示硬件故障。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_ALREADY_EXISTS | -12   |表示已经存在。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_NOT_EXIST | -13   |表示不存在。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_NULL_POINTER | -14   |表示空指针。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_FILE_SIZE_FAIL | -15   |表示文件大小失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_READ_FILE_FAIL | -16   |表示读取文件失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_PUBLIC_KEY | -17   |表示无效的公钥。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_PRIVATE_KEY | -18   |表示无效的私钥。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_KEY_INFO | -19   |表示无效的密钥信息。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_HASH_NOT_EQUAL | -20   |表示哈希不相等。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_MALLOC_FAIL | -21   |表示MALLOC 失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_WRITE_FILE_FAIL | -22   |表示写文件失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_REMOVE_FILE_FAIL | -23   |表示删除文件失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_OPEN_FILE_FAIL | -24   |表示打开文件失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CLOSE_FILE_FAIL | -25   |表示关闭文件失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_MAKE_DIR_FAIL | -26   |表示创建目录失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_KEY_FILE | -27   |表示无效的密钥文件。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_IPC_MSG_FAIL | -28   |表示IPC 信息失败。**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_REQUEST_OVERFLOWS | -29   |表示请求溢出。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_PARAM_NOT_EXIST | -30   |表示参数不存在。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CRYPTO_ENGINE_ERROR | -31   |表示CRYPTO ENGINE错误。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_COMMUNICATION_TIMEOUT | -32   |表示通讯超时。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_IPC_INIT_FAIL | -33   |表示IPC 初始化失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_IPC_DLOPEN_FAIL | -34   |表示IPC DLOPEN 失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_EFUSE_READ_FAIL | -35   |表示EFUSE 读取失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_NEW_ROOT_KEY_MATERIAL_EXIST | -36   |表示存在新的根密钥材料。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_UPDATE_ROOT_KEY_MATERIAL_FAIL | -37   |表示更新根密钥材料失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_VERIFICATION_FAILED | -38   |表示验证证书链失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_ALG_FAIL | -100  |表示检查获取 ALG 失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_KEY_SIZE_FAIL | -101  |表示检查获取密钥大小失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_PADDING_FAIL | -102  |表示检查获取填充失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_PURPOSE_FAIL | -103  |表示检查获取目的失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_DIGEST_FAIL | -104  |表示检查获取摘要失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_MODE_FAIL | -105  |表示检查获取模式失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_NONCE_FAIL | -106  |表示检查获取随机数失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_AAD_FAIL | -107  |表示检查获取 AAD 失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_IV_FAIL | -108  |表示检查 GET IV 失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_AE_TAG_FAIL | -109  |表示检查获取 AE 标记失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_SALT_FAIL | -110  |表示检查获取SALT失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_CHECK_GET_ITERATION_FAIL | -111  |表示检查获取迭代失败。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_ALGORITHM | -112  |表示无效的算法。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_KEY_SIZE | -113  |表示无效的密钥大小。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_PADDING | -114  |表示无效的填充。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_PURPOSE | -115  |表示无效的目的。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_MODE | -116  |表示无效模式。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_DIGEST | -117  |表示无效的摘要。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_SIGNATURE_SIZE | -118  |表示签名大小无效。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_IV | -119  |表示无效的 IV。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_AAD | -120  |表示无效的 AAD。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_NONCE | -121  |表示无效的随机数。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_AE_TAG | -122  |表示无效的 AE 标签。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_SALT | -123  |表示无效SALT。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_ITERATION | -124  |表示无效的迭代。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INVALID_OPERATION | -125  |表示无效操作。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_INTERNAL_ERROR | -999  |表示内部错误。<br/>**系统能力**：SystemCapability.Security.Huks|
| HUKS_ERROR_UNKNOWN_ERROR | -1000 |表示未知错误。<br/>**系统能力**：SystemCapability.Security.Huks|


## huks.HuksKeyPurpose

表示密钥（密钥对）用途。

| 名称                     | 值   | 说明                                                         |
| ------------------------ | ---- | ------------------------------------------------------------ |
| HUKS_KEY_PURPOSE_ENCRYPT | 1    | 表示密钥（密钥对）用于对明文进行加密操作。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_DECRYPT | 2    | 表示密钥（密钥对）用于对密文进行解密操作。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_SIGN    | 4    | 表示密钥对用于对数据进行签名。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_VERIFY  | 8    | 表示密钥对用于验证签名后的数据。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_DERIVE  | 16   | 表示密钥用于派生密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_WRAP    | 32   | 表示密钥用于加密导入。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_UNWRAP  | 64   | 表示密钥加密导出。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_MAC     | 128  | 表示密钥用于生成mac消息验证码。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_PURPOSE_AGREE   | 256  | 表示密钥对用于进行密钥协商。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksKeyDigest

表示摘要算法。

| 名称                   | 值   | 说明                                     |
| ---------------------- | ---- | ---------------------------------------- |
| HUKS_DIGEST_NONE       | 0   | 表示无摘要算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DIGEST_MD5        | 1    | 表示MD5摘要算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DIGEST_SHA1       | 10   | 表示SHA1摘要算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DIGEST_SHA224 | 11   | 表示SHA224摘要算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DIGEST_SHA256 | 12  | 表示SHA256摘要算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DIGEST_SHA384  | 13  | 表示SHA384摘要算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DIGEST_SHA512 | 14  | 表示SHA512摘要算法。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksKeyPadding

表示补齐算法。

| 名称                   | 值   | 说明                                     |
| ---------------------- | ---- | ---------------------------------------- |
| HUKS_PADDING_NONE | 0    | 表示不使用补齐算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_PADDING_OAEP | 1    | 表示使用OAEP补齐算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_PADDING_PSS | 2    | 表示使用PSS补齐算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_PADDING_PKCS1_V1_5 | 3    | 表示使用PKCS1_V1_5补齐算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_PADDING_PKCS5 | 4   | 表示使用PKCS5补齐算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_PADDING_PKCS7 | 5   | 表示使用PKCS7补齐算法。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksCipherMode

表示加密模式。

| 名称          | 值   | 说明                                                         |
| ------------- | ---- | ------------------------------------------------------------ |
| HUKS_MODE_ECB | 1    | 表示使用ECB加密模式。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_MODE_CBC | 2    | 表示使用CBC加密模式。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_MODE_CTR | 3    | 表示使用CTR加密模式。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_MODE_OFB | 4    | 表示使用OFB加密模式。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_MODE_CCM | 31   | 表示使用CCM加密模式。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_MODE_GCM | 32   | 表示使用GCM加密模式。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksKeySize

表示密钥（密钥对）长度。

| 名称                         | 值   | 说明                                                         |
| ---------------------------- | ---- | ------------------------------------------------------------ |
| HUKS_RSA_KEY_SIZE_512        | 512  | 表示使用RSA算法的密钥对长度为512bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_RSA_KEY_SIZE_768        | 768  | 表示使用RSA算法的密钥对长度为768bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_RSA_KEY_SIZE_1024       | 1024 | 表示使用RSA算法的密钥对长度为1024bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_RSA_KEY_SIZE_2048       | 2048 | 表示使用RSA算法的密钥对长度为2048bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_RSA_KEY_SIZE_3072       | 3072 | 表示使用RSA算法的密钥对长度为3072bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_RSA_KEY_SIZE_4096       | 4096 | 表示使用RSA算法的密钥对长度为4096bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ECC_KEY_SIZE_224        | 224  | 表示使用ECC算法的密钥对长度为224bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ECC_KEY_SIZE_256        | 256  | 表示使用ECC算法的密钥对长度为256bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ECC_KEY_SIZE_384        | 384  | 表示使用ECC算法的密钥对长度为384bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ECC_KEY_SIZE_521        | 521  | 表示使用ECC算法的密钥对长度为521bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_AES_KEY_SIZE_128        | 128  | 表示使用AES算法的密钥长度为128bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_AES_KEY_SIZE_192        | 196  | 表示使用AES算法的密钥长度为196bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_AES_KEY_SIZE_256        | 256  | 表示使用AES算法的密钥长度为256bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_AES_KEY_SIZE_512        | 512  | 表示使用AES算法的密钥长度为512bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_CURVE25519_KEY_SIZE_256 | 256  | 表示使用CURVE25519算法的密钥对长度为256bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DH_KEY_SIZE_2048        | 2048 | 表示使用DH算法的密钥对长度为2048bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DH_KEY_SIZE_3072        | 3072 | 表示使用DH算法的密钥对长度为3072bit。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_DH_KEY_SIZE_4096        | 4096 | 表示使用DH算法的密钥对长度为4096bit。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksKeyAlg

表示密钥使用的算法。

| 名称             | 值   | 说明                                                         |
| ---------------- | ---- | ------------------------------------------------------------ |
| HUKS_ALG_RSA     | 1    | 表示使用RSA算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_ECC     | 2    | 表示使用ECC算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_DSA     | 3    | 表示使用DSA算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_AES     | 20   | 表示使用AES算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_HMAC    | 50   | 表示使用HMAC算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_HKDF    | 51   | 表示使用HKDF算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_PBKDF2  | 52   | 表示使用PBKDF2算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_ECDH    | 100  | 表示使用ECDH算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_X25519  | 101  | 表示使用X25519算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_ED25519 | 102  | 表示使用ED25519算法。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_ALG_DH      | 103  | 表示使用DH算法。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksKeyGenerateType

表示生成密钥的类型。

| 名称                           | 值   | 说明                                                         |
| ------------------------------ | ---- | ------------------------------------------------------------ |
| HUKS_KEY_GENERATE_TYPE_DEFAULT | 0    | 默认生成的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_GENERATE_TYPE_DERIVE  | 1    | 派生生成的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_GENERATE_TYPE_AGREE   | 2    | 协商生成的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksKeyFlag

表示密钥的产生方式。

| 名称                       | 值   | 说明                           |
| -------------------------- | ---- | ------------------------------ |
| HUKS_KEY_FLAG_IMPORT_KEY   | 1    | 表示通过导入公钥接口导入的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_FLAG_GENERATE_KEY | 2    | 表示通过生成密钥接口生成的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_FLAG_AGREE_KEY    | 3    | 表示通过生成密钥协商接口生成的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_KEY_FLAG_DERIVE_KEY   | 4    | 表示通过生成密钥派生接口生成的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksKeyStorageType

表示密钥存储方式。

| 名称                    | 值   | 说明                                                         |
| ----------------------- | ---- | ------------------------------------------------------------ |
| HUKS_STORAGE_TEMP       | 0    | 表示通过本地直接管理密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_STORAGE_PERSISTENT | 1    | 表示通过HUKS service管理密钥。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksSendType

| 名称                 | 值   | 说明                                                         |
| -------------------- | ---- | ------------------------------------------------------------ |
| HUKS_SEND_TYPE_ASYNC | 0    | 表示异步发送TAG。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_SEND_TYPE_SYNC  | 1    | 表示同步发送TAG。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksTagType

表示Tag的数据类型。

| 名称                  | 值      | 说明                                                         |
| --------------------- | ------- | ------------------------------------------------------------ |
| HUKS_TAG_TYPE_INVALID | 0 << 28 | 表示非法的Tag类型。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_TYPE_INT     | 1 << 28 | 表示该Tag的数据类型为number。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_TYPE_UINT    | 2 << 28 | 表示该Tag的数据类型为number。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_TYPE_ULONG   | 3 << 28 | 表示该Tag的数据类型为bigint。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_TYPE_BOOL    | 4 << 28 | 表示该Tag的数据类型为boolean。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_TYPE_BYTES   | 5 << 28 | 表示该Tag的数据类型为Uint8Array。<br/>**系统能力**：SystemCapability.Security.Huks |

## huks.HuksTag

表示调用参数的Tag。

| 名称                                   | 值                                       | 说明                                                         |
| -------------------------------------- | ---------------------------------------- | ------------------------------------------------------------ |
| HUKS_TAG_INVALID                       | HuksTagType.HUKS_TAG_TYPE_INVALID \| 0   | 表示非法的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ALGORITHM                     | HUKS_TAG_TYPE_UINT \| 1                  | 表示算法的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_PURPOSE                       | HuksTagType.HUKS_TAG_TYPE_UINT \| 2      | 表示密钥（密钥对）用途的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_KEY_SIZE                      | HuksTagType.HUKS_TAG_TYPE_UINT \| 3      | 表示密钥（密钥对）长度的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_DIGEST                        | HuksTagType.HUKS_TAG_TYPE_UINT \| 4      | 表示摘要算法的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_PADDING                       | HuksTagType.HUKS_TAG_TYPE_UINT \| 5      | 表示补齐算法的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_BLOCK_MODE                    | HuksTagType.HUKS_TAG_TYPE_UINT \| 6      | 表示加密模式的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_KEY_TYPE                      | HuksTagType.HUKS_TAG_TYPE_UINT \| 7      | 表示密钥类型的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ASSOCIATED_DATA               | HuksTagType.HUKS_TAG_TYPE_BYTES \| 8     | 表示表示附加身份验证数据的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_NONCE                         | HuksTagType.HUKS_TAG_TYPE_BYTES \| 9     | 表示表示密钥偏移量的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_IV                            | HuksTagType.HUKS_TAG_TYPE_BYTES \| 10    | 表示表示密钥偏移量的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_INFO                          | HuksTagType.HUKS_TAG_TYPE_BYTES \| 11    | 表示密钥派生时的info。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_SALT                          | HuksTagType.HUKS_TAG_TYPE_BYTES \| 12    | 表示密钥派生时的盐值。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_PWD                           | HuksTagType.HUKS_TAG_TYPE_BYTES \| 13    | 表示密钥派生时的password。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ITERATION                     | HuksTagType.HUKS_TAG_TYPE_UINT \| 14     | 表示密钥派生时的迭代次数。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_KEY_GENERATE_TYPE             | HuksTagType.HUKS_TAG_TYPE_UINT \| 15     | 表示生成密钥类型的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_DERIVE_MAIN_KEY               | HuksTagType.HUKS_TAG_TYPE_BYTES \| 16    | 表示密钥派生时的主密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_DERIVE_FACTOR                 | HuksTagType.HUKS_TAG_TYPE_BYTES \| 17    | 表示密钥派生时的派生因子。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_DERIVE_ALG                    | HuksTagType.HUKS_TAG_TYPE_UINT \| 18     | 表示密钥派生时的算法类型。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_AGREE_ALG                     | HuksTagType.HUKS_TAG_TYPE_UINT \| 19     | 表示密钥协商时的算法类型。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS | HuksTagType.HUKS_TAG_TYPE_BOOL \| 20     | 表示密钥协商时的公钥别名<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS       | HuksTagType.HUKS_TAG_TYPE_BYTES \| 21    | 表示密钥协商时的私钥别名<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_AGREE_PUBLIC_KEY              | HuksTagType.HUKS_TAG_TYPE_BYTES \| 22    | 表示密钥协商时的公钥<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_KEY_ALIAS                     | HuksTagType.HUKS_TAG_TYPE_BYTES \| 23    | 表示密钥别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_DERIVE_KEY_SIZE               | HuksTagType.HUKS_TAG_TYPE_UINT \| 24     | 表示派生密钥的大小。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ACTIVE_DATETIME               | HuksTagType.HUKS_TAG_TYPE_ULONG \| 201   | 预留。                                                       |
| HUKS_TAG_ORIGINATION_EXPIRE_DATETIME   | HuksTagType.HUKS_TAG_TYPE_ULONG \| 202   | 预留。                                                       |
| HUKS_TAG_USAGE_EXPIRE_DATETIME         | HuksTagType.HUKS_TAG_TYPE_ULONG \| 203   | 预留。                                                       |
| HUKS_TAG_CREATION_DATETIME             | HuksTagType.HUKS_TAG_TYPE_ULONG \| 204   | 预留。                                                       |
| HUKS_TAG_ALL_USERS                     | ksTagType.HUKS_TAG_TYPE_BOOL \| 301      | 预留。                                                       |
| HUKS_TAG_USER_ID                       | HuksTagType.HUKS_TAG_TYPE_UINT \| 302    | 预留。                                                       |
| HUKS_TAG_NO_AUTH_REQUIRED              | HuksTagType.HUKS_TAG_TYPE_BOOL \| 303    | 预留。                                                       |
| HUKS_TAG_USER_AUTH_TYPE                | HuksTagType.HUKS_TAG_TYPE_UINT \| 304    | 预留。                                                       |
| HUKS_TAG_AUTH_TIMEOUT                  | HuksTagType.HUKS_TAG_TYPE_UINT \| 305    | 预留。                                                       |
| HUKS_TAG_AUTH_TOKEN                    | HuksTagType.HUKS_TAG_TYPE_BYTES \| 306   | 预留。                                                       |
| HUKS_TAG_ATTESTATION_CHALLENGE         | HuksTagType.HUKS_TAG_TYPE_BYTES \| 501   | 表示attestation时的挑战值。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_APPLICATION_ID    | HuksTagType.HUKS_TAG_TYPE_BYTES \| 502   | 表示attestation时的application Id。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_BRAND          | HuksTagType.HUKS_TAG_TYPE_BYTES \| 503   | 表示设备的brand。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_DEVICE         | HuksTagType.HUKS_TAG_TYPE_BYTES \| 504   | 表示设备的device。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_PRODUCT        | HuksTagType.HUKS_TAG_TYPE_BYTES \| 505   | 表示设备的product。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_SERIAL         | HuksTagType.HUKS_TAG_TYPE_BYTES \| 506   | 表示设备的SN号。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_IMEI           | HuksTagType.HUKS_TAG_TYPE_BYTES \| 507   | 表示设备的IMEI号。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_MEID           | HuksTagType.HUKS_TAG_TYPE_BYTES \| 508   | 表示设备的MEID号。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_MANUFACTURER   | HuksTagType.HUKS_TAG_TYPE_BYTES \| 509   | 表示设备的制造商。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_MODEL          | HuksTagType.HUKS_TAG_TYPE_BYTES \| 510   | 表示设备的型号。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_ALIAS          | HuksTagType.HUKS_TAG_TYPE_BYTES \| 511   | 表示attestation时的密钥别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_SOCID          | HuksTagType.HUKS_TAG_TYPE_BYTES \| 512   | 表示设备的SOCID。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_UDID           | HuksTagType.HUKS_TAG_TYPE_BYTES \| 513   | 表示设备的UDID。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO | HuksTagType.HUKS_TAG_TYPE_BYTES \| 514   | 表示attestation时的安全凭据。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_ATTESTATION_ID_VERSION_INFO   | HuksTagType.HUKS_TAG_TYPE_BYTES \| 515   | 表示attestation时的版本号。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_IS_KEY_ALIAS                  | HuksTagType.HUKS_TAG_TYPE_BOOL \| 1001   | 表示是否使用生成key时传入的别名的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_KEY_STORAGE_FLAG              | HuksTagType.HUKS_TAG_TYPE_UINT \| 1002   | 表示密钥存储方式的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_IS_ALLOWED_WRAP               | HuksTagType.HUKS_TAG_TYPE_BOOL \| 1003   | 预留。                                                       |
| HUKS_TAG_KEY_WRAP_TYPE                 | HuksTagType.HUKS_TAG_TYPE_UINT \| 1004   | 预留。                                                       |
| HUKS_TAG_KEY_AUTH_ID                   | HuksTagType.HUKS_TAG_TYPE_BYTES \| 1005  | 预留。                                                       |
| HUKS_TAG_KEY_ROLE                      | HuksTagType.HUKS_TAG_TYPE_UINT \| 1006   | 预留。                                                       |
| HUKS_TAG_KEY_FLAG                      | HuksTagType.HUKS_TAG_TYPE_UINT \| 1007   | 表示密钥标志的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_IS_ASYNCHRONIZED              | HuksTagType.HUKS_TAG_TYPE_UINT \| 1008   | 预留。                                                       |
| HUKS_TAG_SECURE_KEY_ALIAS              | HuksTagType.HUKS_TAG_TYPE_BOOL \| 1009   | 预留。                                                       |
| HUKS_TAG_SECURE_KEY_UUID               | HuksTagType.HUKS_TAG_TYPE_BYTES \| 1010  | 预留。                                                       |
| HUKS_TAG_KEY_DOMAIN                    | HuksTagType.HUKS_TAG_TYPE_UINT \| 1011   | 预留。                                                       |
| HUKS_TAG_PROCESS_NAME                  | HuksTagType.HUKS_TAG_TYPE_BYTES \| 10001 | 表示进程名称的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_PACKAGE_NAME                  | HuksTagType.HUKS_TAG_TYPE_BYTES \| 10002 | 预留。                                                       |
| HUKS_TAG_ACCESS_TIME                   | HuksTagType.HUKS_TAG_TYPE_UINT \| 10003  | 预留。                                                       |
| HUKS_TAG_USES_TIME                     | HuksTagType.HUKS_TAG_TYPE_UINT \| 10004  | 预留。                                                       |
| HUKS_TAG_CRYPTO_CTX                    | HuksTagType.HUKS_TAG_TYPE_ULONG \| 10005 | 预留。                                                       |
| HUKS_TAG_KEY                           | HuksTagType.HUKS_TAG_TYPE_BYTES \| 10006 | 预留。                                                       |
| HUKS_TAG_KEY_VERSION                   | HuksTagType.HUKS_TAG_TYPE_UINT \| 10007  | 表示密钥版本的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_PAYLOAD_LEN                   | HuksTagType.HUKS_TAG_TYPE_UINT \| 10008  | 预留。                                                       |
| HUKS_TAG_AE_TAG                        | HuksTagType.HUKS_TAG_TYPE_BYTES \| 10009 | 预留。                                                       |
| HUKS_TAG_IS_KEY_HANDLE                 | HuksTagType.HUKS_TAG_TYPE_ULONG \| 10010 | 预留。                                                       |
| HUKS_TAG_OS_VERSION                    | HuksTagType.HUKS_TAG_TYPE_UINT \| 10101  | 表示操作系统版本的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_OS_PATCHLEVEL                 | HuksTagType.HUKS_TAG_TYPE_UINT \| 10102  | 表示操作系统补丁级别的Tag。<br/>**系统能力**：SystemCapability.Security.Huks |
| HUKS_TAG_SYMMETRIC_KEY_DATA            | HuksTagType.HUKS_TAG_TYPE_BYTES \| 20001 | 预留。                                                       |
| HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA    | HuksTagType.HUKS_TAG_TYPE_BYTES \| 20002 | 预留。                                                       |
| HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA   | HuksTagType.HUKS_TAG_TYPE_BYTES \| 20003 | 预留。                                                       |

## huks.generateKey

目前有两种方式：

- generateKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

通过Callback方法生成密钥（密钥对）。

**参数：** 

| 参数名   | 类型                                      | 必填 | 说明                                                         |
| -------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| keyAlias | string                                    | 是   | 别名。<br/>**系统能力**：SystemCapability.Security.Huks      |
| options  | [HuksOptions](#huksoptions)               | 是   | 用于存放生成key所需TAG。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HuksResult](#huksresult)> | 是   | 返回HUKS_SUCCESS时表示接口使用成功，其余结果请参考HuksResult进行错误码查询。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var alias = 'alias;
var properties = new Array();
properties[0] = {
  tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
  value: huksHukssKeyAlg.HUKS_ALG_RSA
};
properties[1] = {
  tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
  value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_512
};
properties[2] = {
  tag: huks.HuksTag.HUKS_TAG_PURPOSE,
  value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
};
properties[3] = {
  tag: huks.HuksTag.HUKS_TAG_PADDING,
  value: huks.HuksKeyPadding.HUKS_PADDING_NONE
};
properties[4] = {
  tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
  value: huks.HuksCipherMode.HUKS_MODE_ECB
};
properties[5] = {
  tag: huks.HuksTag.HUKS_TAG_DIGEST,
  value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
};
var options = {
  properties: properties
};
huks.generateKey(alias, options, function (err, data){}); 
```




- generateKey(keyAlias: string, options: HuksOptions) : Promise<HuksResult>

通过Promise方法生成密钥（密钥对）。

**参数：** 

| 参数名   | 类型                        | 必填 | 说明                                                         |
| -------- | --------------------------- | ---- | ------------------------------------------------------------ |
| keyAlias | string                      | 是   | 密钥别名。<br/>**系统能力**：SystemCapability.Security.Huks  |
| options  | [HuksOptions](#huksoptions) | 是   | 用于存放生成key所需TAG。<br/>**系统能力**：SystemCapability.Security.Huks |

**返回值**：（可选，如不涉及可删除）

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| Promise\<[HuksResult](#huksresult)> | 返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var alias = 'alias';
var properties = new Array();
properties[0] = {
  tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
  value: huksHuksKeyAlg.HUKS_ALG_RSA
};
properties[1] = {
  tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
  value: huks.HuksKeySize.HUKS_RSA_KEY_SIZE_512
};
properties[2] = {
  tag: huks.HuksTag.HUKS_TAG_PURPOSE,
  value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
};
properties[3] = {
  tag: huks.HuksTag.HUKS_TAG_PADDING,
  value: huks.HuksKeyPadding.HUKS_PADDING_NONE
};
properties[4] = {
  tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
  value: huks.HuksCipherMode.HUKS_MODE_ECB
};
properties[5] = {
  tag: huks.HuksTag.HUKS_TAG_DIGEST,
  value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
};
var options = {
  properties: properties
};
var result = await huks.generateKey(alias, options);
```

## huks.deleteKey

目前有两种方式：

- deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

针对Callback生成的密钥进行删除。

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                                                         |
| -------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| keyAlias | string                                    | 是   | 密钥别名，应为生成key时传入的别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions)               | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HuksResult](#huksresult)> | 是   | 返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var alias = 'alias';
var emptyOptions = {
  properties: []
};
huks.deleteKey(alias, emptyOptions, function (err, data) {});
```



- deleteKey(keyAlias: string, options: HuksOptions) : Promise<HuksResult>

针对Promise生成的密钥进行删除。

**参数：**

| 参数名   | 类型        | 必填 | 说明                                                  |
| -------- | ----------- | ---- | ----------------------------------------------------- |
| keyAlias | string      | 是   | 密钥别名，应为生成key时传入的别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |

**返回值：**

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| Promise\<[HuksResult](#huksresult)> | 返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var alias = 'alias';
var emptyOptions = {
  properties: []
};
var result = await huks.deleteKey(alias, emptyOptions);
```

## huks.getSdkVersion

getSdkVersion(options: HuksOptions) : string

获取当前系统sdk版本。

**参数：**

| 参数名  | 类型       | 必填 | 说明                      |
| ------- | ---------- | ---- | ------------------------- |
| options | [HuksOptions](#huksoptions) | 是   | 空对象，用于存放sdk版本。<br/>**系统能力**：SystemCapability.Security.Huks |

**返回值：**

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| string | 返回sdk版本。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var emptyOptions = {
  properties: []
};
var result = await huks.getSdkVersion(emptyOptions);
```

## huks.importKey

目前有两种方式：

- importKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

导入Callback方法生成的密钥对 。

**参数：**

| 参数名   | 类型                     | 必填 | 说明                                              |
| -------- | ------------------------ | ---- | ------------------------------------------------- |
| keyAlias | string                   | 是   | 密钥别名，用于存放所需密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | 用于导入时所需TAG和需要导入的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HuksResult](huksresult)> | 是   | 返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var properties = new Array();
properties[0] = {
  tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
  value: huks.HuksKeyAlg.HUKS_ALG_DSA
};
properties[1] = {
  tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
  value: 1024
};
properties[2] = {
  tag: huks.HuksTag.HUKS_TAG_PURPOSE,
  value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
};
properties[3] = {
  tag: huks.HuksTag.HUKS_TAG_PADDING,
  value: huks.HuksKeyPadding.HUKS_PADDING_NONE
};
properties[4] = {
  tag: huks.HuksTag.HUKS_TAG_DIGEST,
  value: HUKS_DIGEST_SHA1
};
var options = {
  properties: properties,
  inData: importText
};
huks.importKey(keyAlias, options, function (err, data){});
```



- importKey(keyAlias: string, options: HuksOptions) : Promise<HuksResult>

导入Promise方法生成的密钥对

**参数：**

| 参数名   | 类型        | 必填 | 说明                                 |
| -------- | ----------- | ---- | ------------------------------------ |
| keyAlias | string      | 是   | 密钥别名，用于存放所需密钥。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | 用于导入时所需TAG和需要导入的密钥。<br/>**系统能力**：SystemCapability.Security.Huks |

**返回值：**

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| Promise\<[HuksResult](#huksresult)> | 返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var properties = new Array();
properties[0] = {
  tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
  value: huks.HuksKeyAlg.HUKS_ALG_DSA
};
properties[1] = {
  tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
  value: 1024
};
properties[2] = {
  tag: huks.HuksTag.HUKS_TAG_PURPOSE,
  value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_VERIFY
};
properties[3] = {
  tag: huks.HuksTag.HUKS_TAG_PADDING,
  value: huks.HuksKeyPadding.HUKS_PADDING_NONE
};
properties[4] = {
  tag: huks.HuksTag.HUKS_TAG_DIGEST,
  value: HUKS_DIGEST_SHA1
};
var options = {
  properties: properties,
  inData: importText
};
var result = await huks.importKey(keyAlias, options);
```

## huks.exportKey

目前有两种方式：

- exportKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

导出Callback方法生成的密钥对。

**参数：**

| 参数名   | 类型                                     | 必填 | 说明                                                         |
| -------- | ---------------------------------------- | ---- | ------------------------------------------------------------ |
| keyAlias | string                                   | 是   | 密钥别名，应与所用密钥生成时使用的别名相同。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions)              | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HuksResult](huksresult)> | 是   | 返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。outData：返回从密钥中导出的公钥。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var emptyOptions = {
  properties: []
};
huks.exportKey(keyAlias, emptyOptions, function (err, data){});
```



- exportKey(keyAlias: string, options: HuksOptions) : Promise<HuksResult>

导出Promise方法生成的密钥对。

**参数：**

| 参数名   | 类型        | 必填 | 说明                                                         |
| -------- | ----------- | ---- | ------------------------------------------------------------ |
| keyAlias | string      | 是   | 密钥别名，应与所用密钥生成时使用的别名相同。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |

**返回值：**

| 类型                                | 说明                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| Promise\<[HuksResult](#huksresult)> | 返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。outData：返回从密钥中导出的公钥。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var emptyOptions = {
  properties: []
};
var result = await huks.exportKey(keyAlias, emptyOptions);
```

## huks.getKeyProperties

目前有两种方式：

- getKeyProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

获取Callback方法生成的密钥属性。

**参数：**

| 参数名   | 类型                                      | 必填 | 说明                                                         |
| -------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| keyAlias | string                                    | 是   | 密钥别名，应与所用密钥生成时使用的别名相同。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions)               | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HuksResult](#huksresult)> | 是   | errorCode：返回HUKS_SUCCESS时表示接口使用成功，其他时为错误properties：返回值为从生成key时传入的别名。中导出的生成密钥时所需参数。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var emptyOptions = {
  properties: []
};
huks.getKeyProperties(keyAlias, emptyOptions, function (err, data){});
```



- getKeyProperties(keyAlias: string, options: HuksOptions) : Promise<HuksResult>

获取Promise方法生成的密钥属性。

**参数：**

| 参数名   | 类型        | 必填 | 说明                                                         |
| -------- | ----------- | ---- | ------------------------------------------------------------ |
| keyAlias | string      | 是   | 密钥别名，应与所用密钥生成时使用的别名相同。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |

**返回值：**

| 类型               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| Promise\<[HuksResult](#huksoptions)> | errorCode：返回HUKS_SUCCESS时表示接口使用成功，其他时为错误。properties：返回值为从生成key时传入的别名。中导出的生成密钥时所需参数。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var emptyOptions = {
  properties: []
};
var result = await huks.getKeyProperties(keyAlias, emptyOptions);
```

## huks.isKeyExist

目前有两种方式：

- isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback<boolean>) : void

判断Callback方法生成的密钥是否存在 。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| keyAlias | string                 | 是   | 所需查找的密钥的别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[boolean](#boolean)> | 是   | FALSE代表密钥不存在，TRUE代表密钥存在。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var emptyOptions = {
  properties: []
};
huks.isKeyExist(keyAlias, emptyOptions, function (err, data){});
```



- isKeyExist(keyAlias: string, options: HuksOptions) : Promise<boolean>

判断Promise方法生成的密钥是否存在 。

**参数：**

| 参数名   | 类型        | 必填 | 说明                             |
| -------- | ----------- | ---- | -------------------------------- |
| keyAlias | string      | 是   | 所需查找的密钥的别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | 空对象（此处传空即可）。<br/>**系统能力**：SystemCapability.Security.Huks |

**返回值：**

| 类型                          | 说明                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| Promise\<[boolean](#boolean)> | FALSE代表密钥不存在，TRUE代表密钥存在。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

```js
var keyAlias = 'keyAlias';
var emptyOptions = {
  properties: []
};
var result = await huks.isKeyExist(keyAlias, emptyOptions);
```


## huks.init

Init操作接口，目前有两种方式：
- init(keyAlias: string, options: HuksOptions, callback: AsyncCallback<HuksHandle>) : void

使用callback回调异步返回结果 。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| keyAlias | string                 | 是   | Init操作密钥的别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Init操作的参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HuksHandle](#HuksHandle)> | 是   | 将Init操作操作返回的handle添加到密钥管理系统的回调。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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
huks.init(alias, options, function(err, data) {
    if (err.code !== 0) {
        console.log("test init err information: " + JSON.stringify(err));
    } else {
        console.log(`test init data: ${JSON.stringify(data)}`);
    }
})
```

- init(keyAlias: string, options: HuksOptions) : Promise<HuksHandle>

使用Promise方式异步返回结果。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| keyAlias | string                 | 是   | Init操作密钥的别名。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Init参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| promise | Promise\<[HuksHandle](#HuksHandle)> | 是   | 将Init操作返回的handle添加到密钥管理系统的回调。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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
  value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
};
var options = {
  properties: properties
};
huks.init(alias, options).then((data) => {
    console.log(`test init data: ${JSON.stringify(data)}`);
    handle1 = data.handle1;
    handle2 = data.handle2;
    handle = {
        "handle1": handle1,
        "handle2": handle2
    };
}).catch((err) => {
    console.log("test init err information: " + JSON.stringify(err))
}) 
```


## huks.update

update操作接口，目前有两种方式：
- update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

使用callback回调异步返回结果 。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| handle | number           | 是   | Update操作的handle。<br/>**系统能力**：SystemCapability.Security.Huks |
| token | Uint8Array | 否 | Update操作的token。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Update的参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HksResult](#HksResult)> | 是 | 将Update操作的结果添加到密钥管理系统的回调。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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

- update(handle: number, token?: Uint8Array, options: HuksOptions) : Promis<HuksResult>

使用Promise方式异步返回结果。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| handle | number           | 是   | Update操作的handle。<br/>**系统能力**：SystemCapability.Security.Huks |
| token | Uint8Array | 否 | Update操作的token。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Update操作的参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| promise | Promise\<[HuksResult](#HuksResult)> | 是 | 将Update操作的结果添加到密钥管理系统的回调。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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
  value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
};
var options = {
  properties: properties
};
var result = huks.update(handle, options)
```

## huks.finish

finish操作接口，目前有两种方式：
- finish(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

使用callback回调异步返回结果 。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| handle | number           | 是   | Finish操作的handle。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Finish的参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HksResult](#HksResult)> | 是 | 将Finish操作的结果添加到密钥管理系统的回调。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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

- finish(handle: number, options: HuksOptions) : Promise<HuksResult>

使用Promise方式异步返回结果。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| handle | number           | 是   | Finish操作的handle。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Finish操作的参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| promise | Promise\<[HuksResult](#HuksResult)> | 是 | promise实例，用于获取异步返回结果。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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
  value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
};
var options = {
  properties: properties
};
var result = huks.finish(handle, options)
```


## huks.abort

abort操作接口，目前有两种方式：
- abort(handle: number, options: HuksOptions, callback: AsyncCallback<HuksResult>) : void

使用callback回调异步返回结果 。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| handle | number           | 是   | Abort操作的handle。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Abort操作的参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| callback | AsyncCallback\<[HksResult](#HksResult)> | 是 | 将Abort操作的结果添加到密钥管理系统的回调。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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
huks.abort(handle, options, function (err, data){}); 
```

- abort(handle: number, options: HuksOptions) : Promise<HuksResult>;

使用Promise方式异步返回结果。

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                  |
| -------- | ---------------------- | ---- | ------------------------------------- |
| handle | number           | 是   | Abort操作的handle。<br/>**系统能力**：SystemCapability.Security.Huks |
| options  | [HuksOptions](#huksoptions) | 是   | Abort操作的参数集合。<br/>**系统能力**：SystemCapability.Security.Huks |
| promise | Promise\<[HuksResult](#HuksResult)> | 是 | 将Abort操作的结果添加到密钥管理系统的回调。<br/>**系统能力**：SystemCapability.Security.Huks |

**示例：**

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
  value: huks.HuksKeyDigest.HUKS_DIGEST_NONE
};
var options = {
  properties: properties
};
var result = huks.abort(handle, options);
```

##  huks.HuksParam

调用接口使用的options中的properties数组中的param。

**参数：**

| 参数名 | 类型                                | 必填 | 说明                                                        |
| ------ | ----------------------------------- | ---- | ----------------------------------------------------------- |
| tag    | HuksTag                             | 是   | 标签<br/>**系统能力**：SystemCapability.Security.Huks       |
| value  | boolean\|number\|bigint\|Uint8Array | 是   | 标签对应值<br/>**系统能力**：SystemCapability.Security.Huks |

##  huks.HuksOptions

调用接口使用的options。

**参数：**

| 参数名     | 类型             | 必填 | 说明                                                         |
| ---------- | ---------------- | ---- | ------------------------------------------------------------ |
| properties | Array<HuksParam> | 否   | 属性,存HuksParam的数组。<br/>**系统能力**：SystemCapability.Security.Huks |
| inData     | Uint8Array       | 否   | 输入数据。<br/>**系统能力**：SystemCapability.Security.Huks  |

##  huks.HuksHandle

huks Handle结构体。

**参数：**

| 参数名     | 类型             | 必填 | 说明     |
| ---------- | ---------------- | ---- | -------- |
| errorCode  | number           | 是   | 错误码<br/>**系统能力**：SystemCapability.Security.Huks |
| handle    | number       | 是 | handle值<br/>**系统能力**：SystemCapability.Security.Huks |
| token | Uint8Array | 否 | 预留字段<br/>**系统能力**：SystemCapability.Security.Huks |


##  huks.HuksResult

调用接口返回的result。

**参数：**

| 参数名     | 类型             | 必填 | 说明                                                      |
| ---------- | ---------------- | ---- | --------------------------------------------------------- |
| errorCode  | number           | 是   | 错误码<br/>**系统能力**：SystemCapability.Security.Huks   |
| outData    | Uint8Array       | 否   | 输出数据<br/>**系统能力**：SystemCapability.Security.Huks |
| properties | Array<HuksParam> | 否   | 属性<br/>**系统能力**：SystemCapability.Security.Huks     |
| certChains | Array<string>    | 否   | 证书链<br/>**系统能力**：SystemCapability.Security.Huks   |
