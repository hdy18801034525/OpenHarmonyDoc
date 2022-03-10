# 数据请求

>![](public_sys-resources/icon-note.gif) **说明：** 
>
>本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>本模块所有接口需要设备具有系统能力：SystemCapability.Communication.NetStack

## 导入模块

```
import http from '@ohos.net.http';
```

## 完整示例

```
import http from '@ohos.net.http';

// 每一个httpRequest对应一个http请求任务，不可复用
let httpRequest = http.createHttp();
// 用于订阅http响应头，此接口会比request请求先返回。可以根据业务需要订阅此消息
// 从API 8开始，使用on('headersReceive', Callback)替代on('headerReceive', AsyncCallback)。 8+
httpRequest.on('headersReceive', (data) => {
    console.info('header: ' + data.header);
});
httpRequest.request(
    // 填写http请求的url地址，可以带参数也可以不带参数。URL地址需要开发者自定义。GET请求的参数可以在extraData中指定
    "EXAMPLE_URL",
    {
        method: 'POST', // 可选，默认为“GET”
        // 开发者根据自身业务需要添加header字段
        header: {
            'Content-Type': 'application/json'
        },
        // 当使用POST请求时此字段用于传递内容
 
        extraData: {
            "data": "data to send",
        },
        connectTimeout: 60000, // 可选，默认为60s
        readTimeout: 60000, // 可选，默认为60s
    },(err, data) => {
        if (!err) {
            // data.result为http响应内容，可根据业务需要进行解析
            console.info('Result:' + data.result);
            console.info('code:' + data.responseCode);
            // data.header为http响应头，可根据业务需要进行解析
            console.info('header:' + data.header);
            console.info('cookies:' + data.cookies); // 8+
        } else {
            console.info('error:' + err);
            // 当该请求使用完毕时，调用destroy方法主动销毁。
            httpRequest.destroy();
        }
    }
);
```

## http.createHttp

createHttp\(\): HttpRequest

创建一个http，里面包括发起请求、中断请求、订阅/取消订阅HTTP Response Header 事件。每一个HttpRequest对象对应一个Http请求。如需发起多个Http请求，须为每个Http请求创建对应HttpRequest对象。

**返回值：**

| 类型        | 说明                                                         |
| :---------- | :----------------------------------------------------------- |
| HttpRequest | 返回一个HttpRequest对象，里面包括request、destroy、on和off方法。 |

**示例：**

```
import http from '@ohos.net.http';
let httpRequest = http.createHttp();
```


## HttpRequest

http请求任务。在调用HttpRequest的方法前，需要先通过[createHttp\(\)](#httpcreatehttp)创建一个任务。

### request

request\(url: string, callback: AsyncCallback\<HttpResponse\>\):void

根据URL地址，发起HTTP网络请求，使用callback方式作为异步方法。

**需要权限**：ohos.permission.INTERNET

**参数：**

| 参数名   | 类型                                                    | 必填 | 说明                    |
| -------- | ------------------------------------------------------- | ---- | ----------------------- |
| url      | string                                                  | 是   | 发起网络请求的URL地址。 |
| callback | AsyncCallback\<[HttpResponse](#httpresponse)\> | 是   | 回调函数。              |

**示例：**

```
let httpRequest = http.createHttp();
httpRequest.request("EXAMPLE_URL", (err, data) => {
  if (!err) {
    console.info('Result:' + data.result);
    console.info('code:' + data.responseCode);
    console.info('header:' + data.header);
    console.info('cookies:' + data.cookies); // 8+
  } else {
    console.info('error:' + err.data);
  }
});
```

### request

request\(url: string, options: HttpRequestOptions, callback: AsyncCallback<HttpResponse\>\):void

根据URL地址和相关配置项，发起HTTP网络请求，使用callback方式作为异步方法。

**需要权限**：ohos.permission.INTERNET

**参数：**

| 参数名   | 类型                                           | 必填 | 说明                                            |
| -------- | ---------------------------------------------- | ---- | ----------------------------------------------- |
| url      | string                                         | 是   | 发起网络请求的URL地址。                         |
| options  | HttpRequestOptions                             | 是   | 参考[HttpRequestOptions](#httprequestoptions)。 |
| callback | AsyncCallback\<[HttpResponse](#httpresponse)\> | 是   | 回调函数。                                      |

**示例：**

```
let httpRequest= http.createHttp();
httpRequest.request("EXAMPLE_URL",
{
  method: 'GET',
  header: {
	'Content-Type': 'application/json'
  },
  readTimeout: 60000,
  connectTimeout: 60000
},(err, data) => {
  if (!err) {
	console.info('Result:' + data.result);
	console.info('code:' + data.responseCode);
	console.info('header:' + data.header);
	console.info('cookies:' + data.cookies); // 8+
	console.info('header['Content-Type']:' + data.header['Content-Type']);
	console.info('header['Status-Line']:' + data.header['Status-Line']);
	console.info('header.Date:' + data.header.Date);
	console.info('header.Server:' + data.header.Server);
  } else {
	console.info('error:' + err.data);
  }
});
```


### request

request\(url: string, options? : HttpRequestOptions\): Promise<HttpResponse\>

根据URL地址，发起HTTP网络请求，使用Promise方式作为异步方法。

**需要权限**：ohos.permission.INTERNET

**参数：**

| 参数名  | 类型               | 必填 | 说明                                               |
| ------- | ------------------ | ---- | -------------------------------------------------- |
| url     | string             | 是   | 发起网络请求的URL地址。                            |
| options | HttpRequestOptions | 是   | 参考[HttpRequestOptions](#httprequestoptions)。 |

**返回值：**

| 类型                  | 说明                              |
| :-------------------- | :-------------------------------- |
| Promise<[HttpResponse](#httpresponse)> | 以Promise形式返回发起请求的结果。 |


**示例：**

```
let httpRequest= http.createHttp();
let promise = httpRequest.request("EXAMPLE_URL", {
  method: "GET",
  connectTimeout: 60000,
  readTimeout: 60000,
  header: {
	'Content-Type': 'application/json'
  }
});
promise.then((value) => {
	console.info('Result:' + value.result);
	console.info('code:' + value.responseCode);
	console.info('header:' + value.header);
	console.info('cookies:' + value.cookies); // 8+
	console.info('header['Content-Type']:' + value.header['Content-Type']);
	console.info('header['Status-Line']:' + value.header['Status-Line']);
	console.info('header.Date:' + value.header.Date);
	console.info('header.Server:' + value.header.Server);
}).catch((err) => {
	console.error(`errCode:${err.code}, errMessage:${err.data}`);
});
```

### destroy

destroy\(\): void

中断请求任务。

**示例：**

```
let httpRequest= http.createHttp();
httpRequest.destroy();
```

### on\('headerReceive'\)

on\(type: 'headerReceive', callback: AsyncCallback<Object\>\):void

订阅HTTP Response Header 事件。

>![](public_sys-resources/icon-note.gif) **说明：** 
> 此接口已废弃，建议使用[on\('headersReceive'\)<sup>8+</sup>](#onheadersreceive8)替代。

**参数：**

| 参数名   | 类型                    | 必填 | 说明                              |
| -------- | ----------------------- | ---- | --------------------------------- |
| type     | string                  | 是   | 订阅的事件类型，'headerReceive'。 |
| callback | AsyncCallback\<Object\> | 是   | 回调函数。                        |

**示例：**

```
let httpRequest= http.createHttp();
httpRequest.on('headerReceive', (err, data) => {
  if (!err) {
	console.info('header: ' + data.header);
  } else {
	console.info('error:' + err.data);
  }
});
```


### off\('headerReceive'\)

off\(type: 'headerReceive', callback?: AsyncCallback<Object\>\):void

取消订阅HTTP Response Header 事件。

>![](public_sys-resources/icon-note.gif) **说明：** 
>
>1. 此接口已废弃，建议使用[off\('headersReceive'\)<sup>8+</sup>](#offheadersreceive8)替代。
>
>2. 可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                  |
| -------- | ----------------------- | ---- | ------------------------------------- |
| type     | string                  | 是   | 取消订阅的事件类型，'headerReceive'。 |
| callback | AsyncCallback\<Object\> | 否   | 回调函数。                            |

**示例：**

```
let httpRequest= http.createHttp();
httpRequest.on('headerReceive', (err, data) => {
  if (!err) {
	console.info('header: ' + data.header);
  } else {
	console.info('error:' + err.data);
  }
});
httpRequest.off('headerReceive');
```

### on\('headersReceive'\)<sup>8+</sup>

on\(type: 'headersReceive', callback: Callback<Object\>\):void

订阅HTTP Response Header 事件。

**参数：**

| 参数名   | 类型               | 必填 | 说明                               |
| -------- | ------------------ | ---- | ---------------------------------- |
| type     | string             | 是   | 订阅的事件类型：'headersReceive'。 |
| callback | Callback\<Object\> | 是   | 回调函数。                         |

**示例：**

```
let httpRequest= http.createHttp();
httpRequest.on('headersReceive', (data) => {
  console.info('header: ' + data.header);
});
```


### off\('headersReceive'\)<sup>8+</sup>

off\(type: 'headersReceive', callback?: Callback<Object\>\):void

取消订阅HTTP Response Header 事件。

>![](public_sys-resources/icon-note.gif) **说明：** 
>可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。

**参数：**

| 参数名   | 类型               | 必填 | 说明                                   |
| -------- | ------------------ | ---- | -------------------------------------- |
| type     | string             | 是   | 取消订阅的事件类型：'headersReceive'。 |
| callback | Callback\<Object\> | 否   | 回调函数。                             |

**示例：**

```
let httpRequest= http.createHttp();
httpRequest.off('headersReceive');
```

### once\('headersReceive'\)<sup>8+</sup>

once\(type: "headersReceive", callback: Callback<Object\>\): void

订阅HTTP Response Header 事件，但是只触发一次。一旦触发之后，订阅器就会被移除。使用callback方式作为异步方法。

**参数：**

| 参数名   | 类型               | 必填 | 说明                               |
| -------- | ------------------ | ---- | ---------------------------------- |
| type     | string             | 是   | 订阅的事件类型：'headersReceive'。 |
| callback | Callback\<Object\> | 是   | 回调函数。                         |

**示例：**

```
let httpRequest= http.createHttp();
httpRequest.once('headersReceive', (data) => {
  console.info('header: ' + data.header);
});
```

## HttpRequestOptions

发起请求可选参数的类型和取值范围。

| 参数           | 类型                                 | 必填 | 说明                                                       |
| -------------- | ------------------------------------ | ---- | ---------------------------------------------------------- |
| method         | [RequestMethod](#requestmethod) | 否   | 请求方式。                                                 |
| extraData      | string \| Object  \| ArrayBuffer<sup>8+</sup> | 否   | 发送请求的额外数据。<br />- 当HTTP请求为POST、PUT等方法时，此字段为HTTP请求的content。<br />- 当HTTP请求为GET、OPTIONS、DELETE、TRACE、CONNECT等方法时，此字段为HTTP请求的参数补充，参数内容会拼接到URL中进行发送。<sup>8+</sup><br />- 开发者传入string对象，开发者需要自行编码，将编码后的string传入。<sup>8+</sup> |
| header         | Object                               | 否   | HTTP请求头字段。默认{'Content-Type': 'application/json'}。 |
| readTimeout    | number                               | 否   | 读取超时时间。单位为毫秒（ms），默认为60000ms。            |
| connectTimeout | number                               | 否   | 连接超时时间。单位为毫秒（ms），默认为60000ms。            |

## RequestMethod

HTTP 请求方法。

| **method 的合法值** | 说明                |
| :------------------ | :------------------ |
| OPTIONS             | HTTP 请求 OPTIONS。 |
| GET                 | HTTP 请求 GET。     |
| HEAD                | HTTP 请求 HEAD。    |
| POST                | HTTP 请求 POST。    |
| PUT                 | HTTP 请求 PUT。     |
| DELETE              | HTTP 请求 DELETE。  |
| TRACE               | HTTP 请求 TRACE。   |
| CONNECT             | HTTP 请求 CONNECT。 |

## ResponseCode

发起请求返回的响应码。

| 变量              | 值   | 说明                                                         |
| ----------------- | ---- | ------------------------------------------------------------ |
| OK                | 200  | 请求成功。一般用于GET与POST请求。                            |
| CREATED           | 201  | 已创建。成功请求并创建了新的资源。                           |
| ACCEPTED          | 202  | 已接受。已经接受请求，但未处理完成。                         |
| NOT_AUTHORITATIVE | 203  | 非授权信息。请求成功。                                       |
| NO_CONTENT        | 204  | 无内容。服务器成功处理，但未返回内容。                       |
| RESET             | 205  | 重置内容。                                                   |
| PARTIAL           | 206  | 部分内容。服务器成功处理了部分GET请求。                      |
| MULT_CHOICE       | 300  | 多种选择。                                                   |
| MOVED_PERM        | 301  | 永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。 |
| MOVED_TEMP        | 302  | 临时移动。                                                   |
| SEE_OTHER         | 303  | 查看其它地址。                                               |
| NOT_MODIFIED      | 304  | 未修改。                                                     |
| USE_PROXY         | 305  | 使用代理。                                                   |
| BAD_REQUEST       | 400  | 客户端请求的语法错误，服务器无法理解。                       |
| UNAUTHORIZED      | 401  | 请求要求用户的身份认证。                                     |
| PAYMENT_REQUIRED  | 402  | 保留，将来使用。                                             |
| FORBIDDEN         | 403  | 服务器理解请求客户端的请求，但是拒绝执行此请求。             |
| NOT_FOUND         | 404  | 服务器无法根据客户端的请求找到资源（网页）。                 |
| BAD_METHOD        | 405  | 客户端请求中的方法被禁止。                                   |
| NOT_ACCEPTABLE    | 406  | 服务器无法根据客户端请求的内容特性完成请求。                 |
| PROXY_AUTH        | 407  | 请求要求代理的身份认证。                                     |
| CLIENT_TIMEOUT    | 408  | 请求时间过长，超时。                                         |
| CONFLICT          | 409  | 服务器完成客户端的PUT请求是可能返回此代码，服务器处理请求时发生了冲突。 |
| GONE              | 410  | 客户端请求的资源已经不存在。                                 |
| LENGTH_REQUIRED   | 411  | 服务器无法处理客户端发送的不带Content-Length的请求信息。     |
| PRECON_FAILED     | 412  | 客户端请求信息的先决条件错误。                               |
| ENTITY_TOO_LARGE  | 413  | 由于请求的实体过大，服务器无法处理，因此拒绝请求。           |
| REQ_TOO_LONG      | 414  | 请求的URI过长（URI通常为网址），服务器无法处理。             |
| UNSUPPORTED_TYPE  | 415  | 服务器无法处理请求的格式。                                   |
| INTERNAL_ERROR    | 500  | 服务器内部错误，无法完成请求。                               |
| NOT_IMPLEMENTED   | 501  | 服务器不支持请求的功能，无法完成请求。                       |
| BAD_GATEWAY       | 502  | 充当网关或代理的服务器，从远端服务器接收到了一个无效的请求。 |
| UNAVAILABLE       | 503  | 由于超载或系统维护，服务器暂时的无法处理客户端的请求。       |
| GATEWAY_TIMEOUT   | 504  | 充当网关或代理的服务器，未及时从远端服务器获取请求。         |
| VERSION           | 505  | 服务器请求的HTTP协议的版本。                                 |

## HttpResponse

request方法回调函数的返回值类型。

| 参数名               | 类型                                         | 必填 | 说明                                                         |
| -------------------- | -------------------------------------------- | ---- | ------------------------------------------------------------ |
| result               | string \| Object \| ArrayBuffer<sup>8+</sup> | 是   | Http请求根据响应头中Content-type类型返回对应的响应格式内容：<br />- application/json：返回JSON格式的字符串，如需Http响应具体内容，需开发者自行解析<br />- application/octet-stream：ArrayBuffer<br />- 其他：string |
| responseCode         | [ResponseCode](#responsecode) \| number      | 是   | 回调函数执行成功时，此字段为[ResponseCode](#responsecode)。若执行失败，错误码将会从AsyncCallback中的err字段返回。错误码如下：<br />- 200：通用错误<br />- 202：参数错误<br />- 300：I/O错误 |
| header               | Object                                       | 是   | 发起http请求返回来的响应头。当前返回的是JSON格式字符串，如需具体字段内容，需开发者自行解析。常见字段及解析方式如下：<br/>- Content-Type：header['Content-Type']；<br />- Status-Line：header['Status-Line']；<br />- Date：header.Date/header['Date']；<br />- Server：header.Server/header['Server']； |
| cookies<sup>8+</sup> | Array\<string\>                              | 是   | 服务器返回的 cookies。                                       |
