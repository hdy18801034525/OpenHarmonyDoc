# File Management

> ![icon-note.gif](public_sys-resources/icon-note.gif) **Note:**
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import fileio from '@ohos.fileio';
```


## Required Permissions

None


## Note

Before using this module to perform operations on a file or directory, obtain the absolute path of the file or directory. For details, see [getOrCreateLocalDir of the Context module](js-apis-Context.md).

Absolute file or directory path = Application directory + File name or directory name

For example, if the application directory obtained by using **getOrCreateLocalDir** is **dir** and the file name is **xxx.txt**, the absolute path of the file is as follows:

```js
let path = dir + "/xxx.txt";
```


The file descriptor is as follows:


```js
let fd = fileio.openSync(path);
```


## fileio.stat

stat(path: string): Promise&lt;Stat&gt;

Asynchronously obtains file information. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Stat](#stat)&gt; | Promise used to return the file information obtained.|

- Example
  ```js
  fileio.stat(path).then(function(stat){
      console.info("getFileInfo successfully:"+ JSON.stringify(stat));
  }).catch(function(err){
      console.info("getFileInfo failed with error:"+ err);
  });
  ```


## fileio.stat

stat(path:string, callback:AsyncCallback&lt;Stat&gt;): void

Asynchronously obtains file information. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | callback | AsyncCallback&lt;[Stat](#stat)&gt; | Yes| Callback invoked to return the file information obtained.|

- Example
  ```js
  fileio.stat(path, function (err, stat) {
      // Example code in Stat
  });
  ```


## fileio.statSync

statSync(path:string): Stat

Synchronously obtains file information.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|


- Return value
  | Type| Description|
  | -------- | -------- |
  | [Stat](#stat) | File information obtained.|

- Example
  ```js
  let stat = fileio.statSync(path);
  // Example code in Stat
  ```


## fileio.opendir

opendir(path: string): Promise&lt;Dir&gt;

Asynchronously opens a directory. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to open.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Dir](#dir)&gt; | A **Dir** instance corresponding to the directory.|

- Example
  ```js
  fileio.opendir(path).then(function(dir){
      console.info("opendir successfully:"+ JSON.stringify(dir));
  }).catch(function(err){
      console.info("opendir failed with error:"+ err);
  });
  ```


## fileio.opendir

opendir(path: string, callback: AsyncCallback&lt;Dir&gt;): void

Asynchronously opens a directory. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to open.|
  | callback | AsyncCallback&lt;[Dir](#dir)&gt; | Yes| Callback invoked when the directory is open asynchronously.|

- Example
  ```js
  fileio.opendir(path, function (err, dir) { 
      // Example code in Dir struct
      // Use read/readSync/close
  });
  ```


## fileio.opendirSync

opendirSync(path: string): Dir

Synchronously opens a directory.


- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to open.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | [Dir](#dir) | A **Dir** instance corresponding to the directory.|

- Example
  ```js
  let dir = fileio.opendirSync(path);
  // Example code in Dir struct
  // Use read/readSync/close.
  ```


## fileio.access

access(path: string, mode?: number): Promise&lt;void&gt;

Asynchronously checks whether the current process can access a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | number | No| Options for accessing the file. You can specify multiple options, separated with a bitwise OR operator (&#124;). The default value is **0**. <br/>The options are as follows:<br/>-&nbsp;**0**: check whether the file exists. <br/>-&nbsp;**1**: check whether the current process has the execute permission on the file. <br/>-&nbsp;**2**: check whether the current process has the write permission on the file. <br/>-&nbsp;**4**: check whether the current process has the read permission on the file.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.access(path).then(function() {
      console.info("access successfully");
  }).catch(function(err){
      console.info("access failed with error:"+ err);
  });
  ```


## fileio.access

access(path: String, mode?: number, callback: AsyncCallback&lt;void&gt;): void

Asynchronously checks whether the current process can access a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | number | No| Options for accessing the file. You can specify multiple options, separated with a bitwise OR operator (&#124;). The default value is **0**. <br/>The options are as follows:<br/>-&nbsp;**0**: check whether the file exists. <br/>-&nbsp;**1**: check whether the current process has the execute permission on the file. <br/>-&nbsp;**2**: check whether the current process has the write permission on the file. <br/>-&nbsp;**4**: check whether the current process has the read permission on the file.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is asynchronously checked.|

- Example
  ```js
  fileio.access(path, function (err) {
      // Do something.
  });
  ```


## fileio.accessSync

accessSync(path: string, mode?: number): void

Synchronously checks whether the current process can access the specified file.


- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | number | No| Options for accessing the file. You can specify multiple options, separated with a bitwise OR operator (&#124;). The default value is **0**. <br/>The options are as follows:<br/>-&nbsp;**0**: check whether the file exists. <br/>-&nbsp;**1**: check whether the current process has the execute permission on the file. <br/>-&nbsp;**2**: check whether the current process has the write permission on the file. <br/>-&nbsp;**4**: check whether the current process has the read permission on the file.|

- Example
  ```js
  try {
      fileio.accessSync(path);
  } catch(err) {
      console.info("accessSync failed with error:"+ err);
  }
  ```


## fileio.close<sup>7+</sup>

close(fd: number):Promise&lt;void&gt;

Asynchronously closes a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to close.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  let fd = fileio.openSync(path);
  fileio.close(fd).then(function(){
      console.info("close file successfully");
  }).catch(function(err){
      console.info("close file failed with error:"+ err);
  });
  ```


## fileio.close<sup>7+</sup>

close(fd: number, callback:AsyncCallback&lt;void&gt;): void

Asynchronously closes a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to close.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is closed asynchronously.|

- Example
  ```js
  let fd = fileio.openSync(path);
  fileio.close(fd, function (err) {
      // Do something.
  });
  ```


## fileio.closeSync

closeSync(fd: number): void

Synchronously closes a file.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to close.|

- Example
  ```js
  fileio.closeSync(fd);
  ```


## fileio.close<sup>7+</sup>

close(): Promise&lt;void&gt;

Asynchronously closes the stream. This method uses a promise to return the result.

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.close().then(function(){
      console.info("close file stream successfully");
  }).catch(function(err){
      console.info("close file stream failed with error:"+ err);
  });
  ```


## fileio.close<sup>7+</sup>

close(callback: AsyncCallback&lt;void&gt;): void

Asynchronously closes the stream. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the stream is closed asynchronously.|

- Example
  ```js
  fileio.close(function(err){
      // Do something.
  });
  ```


## fileio.copyFile

copyFile(src:string | number, dest:string | number, mode?:number):Promise&lt;void&gt;

Asynchronously copies a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | src | string&nbsp;\|&nbsp;number | Yes| Path or file descriptor of the file to copy.|
  | dest | string&nbsp;\|&nbsp;number | Yes| Path or file descriptor of the new file.|
  | mode | number | No| Option for overwriting the file of the same name in the destination path. The default value is **0**, which is the only value supported. <br/>**0**: Completely overwrite the file with the same name and truncate the part that is not overwritten.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.copyFile(src, dest).then(function(){
      console.info("copyFile successfully");
  }).catch(function(err){
      console.info("copyFile failed with error:"+ err);
  });
  ```


## fileio.copyFile

copyFile(src:string | number, dest:string | number, mode?: number, callback: AsyncCallbak&lt;void&gt;): void

Asynchronously copies a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | src | string&nbsp;\|&nbsp;number | Yes| Path or file descriptor of the file to copy.|
  | dest | string&nbsp;\|&nbsp;number | Yes| Path or file descriptor of the new file.|
  | mode | number | No| Option for overwriting the file of the same name in the destination path. The default value is **0**, which is the only value supported. <br/>**0**: Completely overwrite the file with the same name and truncate the part that is not overwritten.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is copied asynchronously.|

- Example
  ```js
  fileio.copyFile(src, dest, function (err) {
      // Do something.
  });
  ```


## fileio.copyFileSync

fileio.copyFileSync(src:string | number, dest:string | number, mode?:number): void

Synchronously copies a file.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | src | string&nbsp;\|&nbsp;number | Yes| Path or file descriptor of the file to copy.|
  | dest | string&nbsp;\|&nbsp;number | Yes| Path or file descriptor of the new file.|
  | mode | number | No| Option for overwriting the file of the same name in the destination path. The default value is **0**, which is the only value supported. <br/>**0**: Completely overwrite the file with the same name and truncate the part that is not overwritten.|

- Example
  ```js
  fileio.copyFileSync(src, dest);
  ```


## fileio.mkdir

mkdir(path:string, mode?: number): Promise&lt;void&gt;

Asynchronously creates a directory. This method uses a promise to return the result.


- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to create.|
  | mode | number | No| Permission on the directory to create. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). The default value is **0o775**. <br/>-&nbsp;**0o775**: The owner has the read, write, and execute permissions, and other users have the read and execute permissions. <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.mkdir(path).then(function() {
      console.info("mkdir successfully");
  }).catch(function (error){
      console.info("mkdir failed with error:"+ error);
  });
  ```


## fileio.mkdir

mkdir(path:string, mode?:number, callback:AsyncCallbak&lt;void&gt;): void

Asynchronously creates a directory. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to create.|
  | mode | number | No| Permission on the directory to create. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). The default value is **0o775**. <br/>-&nbsp;**0o775**: The owner has the read, write, and execute permissions, and other users have the read and execute permissions. <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the directory is created asynchronously.|

- Example
  ```js
  fileio.mkdir(path, function(err) {
      if (!err) {
          // Do something.
      }
  });
  ```


## fileio.mkdirSync

fileio.mkdirSync(path: string, mode?: number): void

Synchronously creates a directory.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to create.|
  | mode | number | No| Permission on the directory to create. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). The default value is **0o775**. <br/>-&nbsp;**0o775**: The owner has the read, write, and execute permissions, and other users have the read and execute permissions. <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|

- Example
  ```js
  fileio.mkdirSync(path);
  ```


## fileio.open<sup>7+</sup>

open(path: string, flags?: number, mode?: number): Promise&lt;number&gt;

Asynchronously opens a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | flags | number | No| Option for opening a file. You must specify one of the following options. By default, the file is opened in read-only mode. <br/>-&nbsp;**0o0**: Open the file in read-only mode. <br/>-&nbsp;**0o1**: Open the file in write-only mode. <br/>-&nbsp;**0o2**: Open the file in read/write mode. <br/>You can also specify the following options, separated using a bitwise OR operator (&#124;). By default, no extra option is specified. <br/>-&nbsp;**0o100**: If the file does not exist, create it. If you use this option, you must also specify **mode**. <br/>-&nbsp;**0o200**: If **0o100** is added and the file already exists, throw an exception. <br/>-&nbsp;**0o1000**: If the file exists and is open in write-only or read/write mode, truncate the file length to 0. <br/>-&nbsp;**0o2000**: Open the file in append mode. New data will be appended to the file (added to the end of the file). <br/>-&nbsp;**0o4000**: If **path** points to a named pipe (also known as a FIFO), block special file, or character special file, perform non-blocking operations on the open file and in subsequent I/Os. <br/>-&nbsp;**0o200000**: If **path** points to a directory, throw an exception. <br/>-&nbsp;**0o400000**: If **path** points to a symbolic link, throw an exception. <br/>-&nbsp;**0o4010000**: Open the file in synchronous I/O mode.|
  | mode | number | No| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). The default value is **0o666**. <br/>-&nbsp;**0o666**: The owner, user group, and other users have the read and write permissions on the file. <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise used to return the file descriptor of the file opened.|

- Example
  ```js
  fileio.open(path, 0o1, 0o0200).then(function(number){
      console.info("open file successfully");
  }).catch(function(error){
      console.info("open file failed with error:"+ err);
  });
  ```


## fileio.open<sup>7+</sup>

open(path: string, flags: number, mode: number, callback: AsyncCallback&lt;number&gt;): void

Asynchronously opens a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | flags | number | Yes| Option for opening a file. You must specify one of the following options. By default, the file is opened in read-only mode. <br/>-&nbsp;**0o0**: Open the file in read-only mode. <br/>-&nbsp;**0o1**: Open the file in write-only mode. <br/>-&nbsp;**0o2**: Open the file in read/write mode. <br/>You can also specify the following options, separated using a bitwise OR operator (&#124;). By default, no extra option is specified. <br/>-&nbsp;**0o100**: If the file does not exist, create it. If you use this option, you must also specify **mode**. <br/>-&nbsp;**0o200**: If **0o100** is added and the file already exists, throw an exception. <br/>-&nbsp;**0o1000**: If the file exists and is open in write-only or read/write mode, truncate the file length to 0. <br/>-&nbsp;**0o2000**: Open the file in append mode. New data will be appended to the file (added to the end of the file). <br/>-&nbsp;**0o4000**: If **path** points to a named pipe (also known as a FIFO), block special file, or character special file, perform non-blocking operations on the open file and in subsequent I/Os. <br/>-&nbsp;**0o200000**: If **path** points to a directory, throw an exception. <br/>-&nbsp;**0o400000**: If **path** points to a symbolic link, throw an exception. <br/>-&nbsp;**0o4010000**: Open the file in synchronous I/O mode.|
  | mode | number | Yes| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). The default value is **0o666**. <br/>-&nbsp;**0o666**: The owner, user group, and other users have the read and write permissions on the file. <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|
  | callback | AsyncCallback&nbsp;&lt;void&gt; | Yes| Callback invoked when the file is open asynchronously.|

- Example
  ```js
  fileio.open(path, 0, function(err, fd) {
      // Do something.
  });
  ```


## fileio.openSync

openSync(path:string, flags?:number, mode?:number): number

Synchronously opens a file.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | flags | number | No| Option for opening a file. You must specify one of the following options. By default, the file is opened in read-only mode. <br/>-&nbsp;**0o0**: Open the file in read-only mode. <br/>-&nbsp;**0o1**: Open the file in write-only mode. <br/>-&nbsp;**0o2**: Open the file in read/write mode. <br/>You can also specify the following options, separated using a bitwise OR operator (&#124;). By default, no extra option is specified. <br/>-&nbsp;**0o100**: If the file does not exist, create it. If you use this option, you must also specify **mode**. <br/>-&nbsp;**0o200**: If **0o100** is added and the file already exists, throw an exception. <br/>-&nbsp;**0o1000**: If the file exists and is open in write-only or read/write mode, truncate the file length to 0. <br/>-&nbsp;**0o2000**: Open the file in append mode. New data will be appended to the file (added to the end of the file). <br/>-&nbsp;**0o4000**: If **path** points to a named pipe (also known as a FIFO), block special file, or character special file, perform non-blocking operations on the open file and in subsequent I/Os. <br/>-&nbsp;**0o200000**: If **path** points to a directory, throw an exception. <br/>-&nbsp;**0o400000**: If **path** points to a symbolic link, throw an exception. <br/>-&nbsp;**0o4010000**: Open the file in synchronous I/O mode.|
  | mode | number | No| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). The default value is **0o666**. <br/>-&nbsp;**0o666**: The owner, user group, and other users have the read and write permissions on the file. <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.<br/>The file permissions of newly created files are affected by **umask**, which is set as the process starts. Currently, the modification of **umask** is not open.

- Return value
  | Type| Description|
  | -------- | -------- |
  | number | File descriptor of the file opened.|

- Example
  ```js
  let fd = fileio.openSync(path);
  ```


## fileio.read

read(fd: number, buffer: ArrayBuffer, options?: Object): Promise&lt;Readout&gt;

Asynchronously reads data from a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to read.|
  | buffer | ArrayBuffer | Yes| Buffer used to store the file data read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to be read. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): position of the data to be read in the file. By default, data is read from the current position.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Readout](#readout)&gt; | Promise used to return the data read.|

- Example
  ```js
  let fd = fileio.openSync(path, 0o2);
  let buf = new ArrayBuffer(4096);
  fileio.read(fd, buf).then(function(readout){
      console.info("read file data successfully:"+ JSON.stringify(readout));
  }).catch(function(error){
      console.info("read file data failed with error:"+ error);
  });
  ```


## fileio.read

read(fd: number, buffer: ArrayBuffer, options?: Object, callback: AsyncCallback&lt;Readout&gt;): void

Asynchronously reads data from a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to read.|
  | buffer | ArrayBuffer | Yes| Buffer used to store the file data read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to be read. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): position of the data to be read in the file. By default, data is read from the current position.|
  | callback | AsyncCallback&lt;[Readout](#readout)&gt; | Yes| Callback invoked when the data is read asynchronously.|

- Example
  ```js
  let fd = fileio.openSync(path, 0o2);
  let buf = new ArrayBuffer(4096);
  fileio.read(fd, buf, function (err, readOut) {
      if (!err) {
          console.log(String.fromCharCode.apply(null, new Uint8Array(readOut.buffer)))
      }
  });
  ```


## fileio.readSync

readSync(fd: number, buffer: ArrayBuffer, options?: Object): number

Synchronously reads data from a file.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to read.|
  | buffer | ArrayBuffer | Yes| Buffer used to store the file data read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to be read. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): position of the data to be read in the file. By default, data is read from the current position.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | number | Length of the data read.|

- Example
  ```js
  let fd = fileio.openSync(path, 0o2);
  let buf = new ArrayBuffer(4096);
  let num = fileio.readSync(fd, buf);
  ```


## fileio.rmdir<sup>7+</sup>

rmdir(path: string): Promise&lt;void&gt;

Asynchronously deletes a directory. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to delete.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.rmdir(path).then(function() {
      console.info("rmdir successfully");
  }).catch(function(err){
      console.info("rmdir failed with error:"+ err);
  });
  ```


## fileio.rmdir<sup>7+</sup>

rmdir(path: string, callback:AsyncCallback&lt;void&gt;): void

Asynchronously deletes a directory. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to delete.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the directory is deleted asynchronously.|

- Example
  ```js
  fileio.rmdir(path, function(err){
      // Do something.
  });
  ```


## fileio.rmdirSync

rmdirSync(path:string)

Synchronously deletes a directory.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the directory to delete.|

- Example
  ```js
  fileio.rmdirSync(path);
  ```


## fileio.unlink

unlink(path:string): Promise&lt;void&gt;

Asynchronously deletes a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the file to delete.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.unlink(path).then(function(){
      console.info("remove file successfully");
  }).catch(function(error){
      console.info("remove file failed with error:"+ error);
  });
  ```


## fileio.unlink

unlink(path:string, callback:AsyncCallback&lt;void&gt;): void

Asynchronously deletes a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the file to delete.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is deleted asynchronously.|

- Example
  ```js
  fileio.unlink(path, function(err) {
      if (!err) {
          // Do something.
      }
  });
  ```


## fileio.unlinkSync

unlinkSync(path: string): void

Synchronously deletes a file.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the file to delete.|

- Example
  ```js
  fileio.unlinkSync(path);
  ```


## fileio.write

write(fd: number, buffer: ArrayBuffer | string, options?: Object): Promise&lt;number&gt;

Asynchronously writes data into a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to write.|
  | buffer | ArrayBuffer&nbsp;\|&nbsp;string | Yes| Data to write. It can be a string or data from a buffer.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position of the data to write in reference to the start address of the data. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to write. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): start position to write the data in the file. By default, data is written from the current position. <br/>-&nbsp;**encoding** (string): format of the string to be encoded. The default value is **utf-8**, which is the only value supported.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise used to return the length of the data written in the file.|

- Example
  ```js
  let fd = fileio.openSync(fpath, 0o100 | 0o2, 0o666);
  fileio.write(fd, "hello, world").then(function(number){
       console.info("write data to file successfully:"+ number);
  }).catch(function(err){
      console.info("write data to file failed with error:"+ err);
  });
  ```


## fileio.write

write(fd:number, buffer:ArrayBuffer | string,options?:Object, callback:AsyncCallback&lt;number&gt;): void

Asynchronously writes data into a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to write.|
  | buffer | ArrayBuffer&nbsp;\|&nbsp;string | Yes| Data to write. It can be a string or data from a buffer.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position of the data to write in reference to the start address of the data. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to write. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): start position to write the data in the file. By default, data is written from the current position. <br/>-&nbsp;**encoding** (string): format of the string to be encoded. The default value is **utf-8**, which is the only value supported.|
  | callback | AsyncCallback&lt;number&gt; | Yes| Callback invoked when the data is written asynchronously.|

- Example
  ```js
  let fd = fileio.openSync(path, 0o100 | 0o2, 0o666);
  fileio.write(fd, "hello, world", function (err, bytesWritten) {
      if (!err) {
         console.log(bytesWritten)
      }
  });
  ```


## fileio.writeSync

writeSync(fd: number, buffer: ArrayBuffer | string, options?:Object): number

Synchronously writes data into a file.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to write.|
  | buffer | ArrayBuffer&nbsp;\|&nbsp;string | Yes| Data to write. It can be a string or data from a buffer.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position of the data to write in reference to the start address of the data. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to write. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): start position to write the data in the file. By default, data is written from the current position. <br/>-&nbsp;**encoding** (string): format of the string to be encoded. The default value is **utf-8**, which is the only value supported.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | number | Length of the data written in the file.|

- Example
  ```js
  let fd = fileio.openSync(path, 0o100 | 0o2, 0o666);
  let num = fileio.writeSync(fd, "hello, world");
  ```


## fileio.hash

hash(path: string, algorithm: string): Promise&lt;string&gt;

Asynchronously calculates the hash value of a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | algorithm | string | Yes| Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**.**sha256** is recommended for security purposes.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;string&gt; | Promise used to return the hash value of the file. The hash value is a hexadecimal string consisting of digits and uppercase letters.|

- Example
  ```js
  fileio.hash(path, "sha256").then(function(str){
      console.info("calculate file hash successfully:"+ str);
  }).catch(function(error){
      console.info("calculate file hash failed with error:"+ err);
  });
  ```


## fileio.hash

hash(psth:string, algorithm:string, callback:AsyncCallback&lt;string&gt;): void

Asynchronously calculates the hash value of a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | algorithm | string | Yes| Algorithm used to calculate the hash value. The value can be **md5**, **sha1**, or **sha256**.**sha256** is recommended for security purposes.|
  | callback | AsyncCallback&lt;string&gt; | Yes| Callback used to return the hash value. The hash value is a hexadecimal string consisting of digits and uppercase letters.|

- Example
  ```js
  fileio.hash(fpath, "sha256", function(err, hashStr) {
      if (!err) {
          console.log(hashStr)
      }
  });
  ```


## fileio.chmod<sup>7+</sup>

chmod(path: string, mode: number):Promise&lt;void&gt;

Asynchronously changes the file permissions based on its path. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | number | Yes| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.chmod(path, mode).then(function() {
      console.info("chmod successfully");
  }).catch(function(err){
      console.info("chmod failed with error:"+ err);
  });
  ```


## fileio.chmod<sup>7+</sup>

chmod(path: string, mode: number, callback: AsyncCallback&lt;void&gt;): void

Asynchronously changes the file permissions based on its path. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | number | Yes| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file permissions are changed asynchronously.|

- Example
  ```js
  fileio.chmod(path, mode, function (err) {
      // Do something.
  });
  ```


## fileio.chmodSync<sup>7+</sup>

chmodSync(path: string, mode: number): void

Synchronously changes the file permissions based on its path.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | number | Yes| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|

- Example
  ```js
  fileio.chmodSync(fpath, mode);
  ```


## fileio.fstat<sup>7+</sup>

fstat(fd: number): Promise&lt;Stat&gt;

Asynchronously obtains file status information based on the file descriptor. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Stat](#stat)&gt; | Promise used to return the file status information.|

- Example
  ```js
  fileio.fstat(fd).then(function(stat){
      console.info("fstat successfully:"+ JSON.stringify(stat));
  }).catch(function(err){
      console.info("fstat failed with error:"+ err);
  });
  ```


## fileio.fstat<sup>7+</sup>

fstat(fd: number, callback: AsyncCallback&lt;Stat&gt;): void

Asynchronously obtains file status information based on the file descriptor. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | callback | AsyncCallback&lt;[Stat](#stat)&gt; | Yes| Callback invoked when the file status information is obtained asynchronously.|

- Example
  ```js
  let fd = fileio.openSync(path);
  fileio.fstat(fd, function (err) {
      // Do something.
  });
  ```


## fileio.fstatSync<sup>7+</sup>

fstatSync(fd: number): Stat

Synchronously obtains file status information based on the file descriptor.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | [Stat](#stat) | File status information obtained.|

- Example
  ```js
  let fd = fileio.openSync(path);
  let stat = fileio.fstatSync(fd);
  ```


## fileio.ftruncate<sup>7+</sup>

ftruncate(fd: number, len: number): Promise&lt;void&gt;

Asynchronously truncates a file based on the file descriptor. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to truncate.|
  | len | number | Yes| File length, in bytes, after truncation.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  let fd = fileio.openSync(path);
  fileio.ftruncate(fd, 5).then(function(err) {    
      console.info("File truncated successfully");
  }).catch(function(err){
      console.info("Failed to truncate the file. Error:"+ err);
  });
  ```


## fileio.ftruncate<sup>7+</sup>

ftruncate(fd: number, len: number, callback:AsyncCallback&lt;void&gt;): void

Asynchronously truncates a file based on the file descriptor. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to truncate.|
  | len | number | Yes| File length, in bytes, after truncation.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is truncated asynchronously.|

- Example
  ```js
  fileio.ftruncate(fd, len, function(err){
      // Do something.
  });
  ```


## fileio.ftruncateSync<sup>7+</sup>

ftruncateSync(fd: number, len?: number): void

Synchronously truncates a file based on the file descriptor.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to truncate.|
  | len | number | No| File length, in bytes, after truncation.|

- Example
  ```js
  fileio.ftruncate(fd, len);
  ```


## fileio.truncate<sup>7+</sup>

truncate(path: string, len: number): Promise&lt;void&gt;

Asynchronously truncates a file based on its path. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the file to truncate.|
  | len | number | Yes| File length, in bytes, after truncation.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.truncate(path, len).then(function(){
      console.info("File truncated successfully");
  }).catch(function(err){
      console.info("Failed to truncate the file. Error:"+ err);
  });
  ```


## fileio.truncate<sup>7+</sup>

truncate(path: string, len: number, callback:AsyncCallback&lt;void&gt;): void

Asynchronously truncates a file based on its path. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the file to truncate.|
  | len | number | Yes| File length, in bytes, after truncation.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is truncated asynchronously.|

- Example
  ```js
  fileio.truncate(path, len, function(err){
      // Do something.
  });
  ```


## fileio.truncateSync<sup>7+</sup>

truncateSync(fpath: string, len?: number): void

Synchronously truncates a file based on the file path.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the file to truncate.|
  | len | number | No| File length, in bytes, after truncation.|

- Example
  ```js
  fileio.ftruncate(path, len);
  ```


## fileio.readText<sup>7+</sup>

readText(filePath: string, options?:Object): Promise&lt;string&gt;

Asynchronously reads the text of a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | filePath | string | Yes| Absolute path of the file to read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**position** (number): position of the data to read in the file. By default, data is read from the current position. <br/>-&nbsp;**length** (number): length of the data to be read. The default value is the buffer length minus the offset. <br/>-&nbsp;**encoding** (string): format of the data (string) to be encoded. The default value is **utf-8**, which is the only value supported.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;string&gt; | Promise used to return the content of the file read.|

- Example
  ```js
  fileio.readText(path).then(function(str) {
      console.info("readText successfully:"+ str);
  }).catch(function(err){
      console.info("readText failed with error:"+ err);
  });
  ```


## fileio.readText<sup>7+</sup>

readText(filePath: string, options?:Object, callback:AsyncCallback&lt;string&gt;): void

Asynchronously reads the text of a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | filePath | string | Yes| Absolute path of the file to read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**position** (number): position of the data to read in the file. By default, data is read from the current position. <br/>-&nbsp;**length** (number): length of the data to be read. The default value is the buffer length minus the offset. <br/>-&nbsp;**encoding** (string): format of the data (string) to be encoded. The default value is **utf-8**, which is the only value supported.|
  | callback | AsyncCallback&lt;string&gt; | Yes| Callback invoked when the file is read asynchronously.|

- Example
  ```js
  fileio.readText(path, function(err, str){
      // Do something.
  });
  ```


## fileio.readTextSync<sup>7+</sup>

readTextSync(filePath: string, options?:Object): string

Synchronously reads the text of a file. 

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | filePath | string | Yes| Absolute path of the file to read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**position** (number): position of the data to read in the file. By default, data is read from the current position. <br/>-&nbsp;**length** (number): length of the data to be read. The default value is the buffer length minus the offset. <br/>-&nbsp;**encoding** (string): format of the data (string) to be encoded. The default value is **utf-8**, which is the only value supported.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | string| Content of the file read.|

- Example
  ```js
  let str = fileio.readTextSync(path, {position: 1, length: 3});
  ```


## fileio.lstat<sup>7+</sup>

lstat(path: string): Promise&lt;Stat&gt;

Asynchronously obtains link status information. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file, pointing to the link status.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Stat](#stat)&gt; | Promise used to return the link status.|

- Example
  ```js
  fileio.lstat(path).then(function(stat){
      console.info("Link status obtained:"+ number);
  }).catch(function(err){
      console.info("Failed to obtain the link status. Error:"+ err);
  });
  ```


## fileio.lstat<sup>7+</sup>

lstat(path:string, callback:AsyncCallback&lt;Stat&gt;): void

Asynchronously obtains link status information. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file, pointing to the link status.|
  | callback | AsyncCallback&lt;[Stat](#stat)&gt; | Yes| Callback invoked when the link status information is obtained asynchronously.|

- Example
  ```js
  fileio.lstat(path, function (err, stat) {
      // Do something.
  ));
  ```


## fileio.lstatSync<sup>7+</sup>

lstatSync(path:string): Stat

Synchronously obtains link status information.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file, pointing to the link status.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | [Stat](#stat) | Link status information.|

- Example
  ```js
  let stat = fileio.lstatSync(path);
  ```


## fileio.read<sup>7+</sup>

read(buffer: ArrayBuffer, options?: Object): Promise&lt;Readout&gt;

Asynchronously reads data from a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer | Yes| Buffer used to store the file data read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to be read. It is optional. The default value is the buffer length minus the offset.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Readout](#readout)&gt; | Promise used to return the data read.|

- Example
  ```js
  fileio.read(new ArrayBuffer(4096)).then(function(readout){
      console.info("File data read successfully:"+ String.fromCharCode.apply(null, new Uint8Array(readout.buffer)));
  }).catch(function(err){
      console.info("Failed to read file data. Error:"+ err);
  });
  ```


## fileio.read<sup>7+</sup>

read(buffer: ArrayBuffer, options?: Object, callback: AsyncCallback&lt;Readout&gt;): void

Asynchronously reads data from a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer | Yes| Buffer used to store the file data read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to be read. It is optional. The default value is the buffer length minus the offset.|
  | callback | AsyncCallback&lt;[Readout](#readout)&gt; | Yes| Callback invoked when the data is read asynchronously from the file.|

- Example
  ```js
  let buf = new ArrayBuffer(4096);
  fileio.read(buf, function (err, readOut) {
      if (!err) {
          console.log(String.fromCharCode.apply(null, new Uint8Array(readOut.buffer)))
      }
  });
  ```


## fileio.rename<sup>7+</sup>

rename(oldPath: string, newPath: string): Promise&lt;void&gt;

Asynchronously renames a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | oldPath | string | Yes| Absolute path of the file to rename.|
  | Newpath | String | Yes| Absolute path of the file renamed.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.rename(oldPath, Newpath).then(function() {
      console.info("rename successfully");
  }).catch(function(err){
      console.info("rename failed with error:"+ err);
  });
  ```


## fileio.rename<sup>7+</sup>

rename(oldPath: string, newPath: string, callback: AsyncCallback&lt;void&gt;): void

Asynchronously renames a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | oldpath | string | Yes| Absolute path of the file to rename.|
  | Newpath | String | Yes| Absolute path of the file renamed.|
  | Callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is asynchronously renamed.|

- Example
  ```js
  fileio.rename(oldpath, Newpath, function(err){
  });
  ```


## fileio.renameSync<sup>7+</sup>

renameSync(oldPath: string, newPath: string): void

Synchronously renames a file.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | oldPath | string | Yes| Absolute path of the file to rename.|
  | Newpath | String | Yes| Absolute path of the file renamed.|

- Example
  ```js
  fileio.renameSync(oldpath, newpath);
  ```


## fileio.fsync<sup>7+</sup>

fsync(fd: number): Promise&lt;void&gt;

Asynchronously synchronizes a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to synchronize.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  fileio.fsync(fd).then(function(){
      console.info("sync data successfully");
  }).catch(function(err){
      console.info("sync data failed with error:"+ err);
  });
  ```


## fileio.fsync<sup>7+</sup>

fsync(fd: number, callback: AsyncCallback&lt;void&gt;): void

Asynchronously synchronizes a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to synchronize.|
  | Callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file is synchronized in asynchronous mode.|

- Example
  ```js
  fileio.fsync(fd, function(err){
      // Do something.
  });
  ```


## fileio.fsyncSync<sup>7+</sup>

fsyncSync(fd: number): void

Synchronizes a file in synchronous mode.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to synchronize.|

- Example
  ```js
  fileio.fyncsSync(fd);
  ```


## fileio.fdatasync<sup>7+</sup>

fdatasync(fd: number): Promise&lt;void&gt;

Asynchronously synchronizes data in a file. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to synchronize.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result asynchronously. An empty value is returned.|

- Example
  ```js
  fileio.fdatasync(fd).then(function(err) {
      console.info("sync data successfully");
  }).catch(function(err){
      console.info("sync data failed with error:"+ err);
  });
  ```


## fileio.fdatasync<sup>7+</sup>

fdatasync(fd: number, callback:AsyncCallback&lt;void&gt;): void

Asynchronously synchronizes data in a file. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to synchronize.|
  | callback | AsyncCallback&nbsp;&lt;void&gt; | Yes| Callback invoked when the file data is synchronized in asynchronous mode.|

- Example
  ```js
  fileio.fdatasync (fd, function (err) {
      // Do something.
  });
  ```


## fileio.fdatasyncSync<sup>7+</sup>

fdatasyncSync(fd: number): void

Synchronizes data in a file in synchronous mode.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the file to synchronize.|

- Example
  ```js
  let stat = fileio.fdatasyncSync(fd);
  ```


## fileio.symlink<sup>7+</sup>

symlink(target: string, srcPath: string): Promise&lt;void&gt;

Asynchronously creates a symbolic link based on a path. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | target | string | Yes| Absolute path of the symbolic link.|
  | srcPath | string | Yes| Absolute path of the referenced file or directory contained in the symbolic link.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result asynchronously. An empty value is returned.|

- Example
  ```js
  fileio.symlink(target, srcPath).then(function() {
      console.info("symlink successfully");
  }).catch(function(err){
      console.info("symlink failed with error:"+ err);
  });
  ```


## fileio.symlink<sup>7+</sup>

symlink(target: string, srcPath: string, callback: AsyncCallback&lt;void&gt;): void

Asynchronously creates a symbolic link based on a path. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | target | string | Yes| Absolute path of the symbolic link.|
  | srcPath | string | Yes| Absolute path of the referenced file or directory contained in the symbolic link.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the symbolic link is created asynchronously.|

- Example
  ```js
  fileio.symlink(target, srcPath, function (err) {
      // Do something.
  });
  ```


## fileio.symlinkSync<sup>7+</sup>

symlinkSync(target: string, srcPath: string): void

Synchronously creates a symbolic link based on a specified path.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | target | string | Yes| Absolute path of the symbolic link.|
  | srcPath | string | Yes| Absolute path of the referenced file or directory contained in the symbolic link.|

- Example
  ```js
  fileio.symlinkSync(target, srcPath);
  ```


## fileio.chown<sup>7+</sup>

chown(path: string, uid: number, gid: number): Promise&lt;void&gt;

Asynchronously changes the file owner based on its path. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | uid | number | Yes| New user ID (UID).|
  | gid | number | Yes| New group ID (GID).|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result asynchronously. An empty value is returned.|

- Example
  ```js
  let stat = fileio.statSync(path);
  fileio.chown(path, stat.uid, stat.gid)).then(function(){
      console.info("chown successfully");
  }).catch(function(err){
      console.info("chown failed with error:"+ err);
  });
  ```


## fileio.chown<sup>7+</sup>

chown(path: string, uid: number, gid: number, callback: AsyncCallback&lt;void&gt;): void

Asynchronously changes the file owner based on its path. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file owner is changed asynchronously.|

- Example
  ```js
  let stat = fileio.statSync(fpath)
  fileio.chown(path, stat.uid, stat.gid, function (err){
      // Do something.
  });
  ```


## fileio.chownSync<sup>7+</sup>

chownSync(path: string, uid: number, gid: number): void

Synchronously changes the file owner based on its path.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|

- Example
  ```js
  let stat = fileio.statSync(fpath)
  fileio.chownSync(path, stat.uid, stat.gid);
  ```


## fileio.mkdtemp<sup>7+</sup>

mkdtemp(prefix: string): Promise&lt;string&gt;

Asynchronously creates a temporary directory. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | prefix | string | Yes| A randomly generated string used to replace "XXXXXX" in a directory.|

- Return value
  | Name| Description|
  | -------- | -------- |
  | Promise&lt;string&gt; | Promise used to return the unique path generated.|

- Example
  ```js
  fileio.mkdtemp(path + "XXXX").then(function(path){
      console.info("mkdtemp successfully:"+ path);
  }).catch(function(err){
      console.info("mkdtemp failed with error:"+ err);
  });
  ```


## fileio.mkdtemp<sup>7+</sup>

mkdtemp(prefix: string, callback: AsyncCallback&lt;string&gt;): void

Asynchronously creates a temporary directory. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | prefix | string | Yes| A randomly generated string used to replace "XXXXXX" in a directory.|
  | callback | AsyncCallback&lt;string&gt; | Yes| Callback invoked when a temporary directory is created asynchronously.|

- Example
  ```js
  fileio.mkdtemp(path + "XXXX", function (err, res) {
      // Do something.
  });
  ```


## fileio.mkdtempSync<sup>7+</sup>

mkdtempSync(prefix: string): string

Synchronously creates a temporary directory.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | prefix | string | Yes| A randomly generated string used to replace "XXXXXX" in a directory.|

- Return value
  | Name| Description|
  | -------- | -------- |
  | string | Unique path generated.|

- Example
  ```js
  let res = fileio.mkdtempSync(path + "XXXX");
  ```


## fileio.fchmod<sup>7+</sup>

fchmod(fd: number, mode: number): Promise&lt;void&gt;

Asynchronously changes the file permissions based on the file descriptor. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | mode | number | Yes| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|

- Return value
  | Name| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result asynchronously. An empty value is returned.|

- Example
  ```js
  fileio.fchmod(fd, mode).then(function() {
      console.info("chmod successfully");
  }).catch(function(err){
      console.info("chmod failed with error:"+ err);
  });
  ```


## fileio.fchmod<sup>7+</sup>

fchmod(fd: number, mode: number, callback: AsyncCallback&lt;void&gt;): void

Asynchronously changes the file permissions based on the file descriptor. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | mode | number | Yes| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|
  | callback | AsyncCallback&nbsp;&lt;void&gt; | Yes| Callback invoked when the file permissions are changed asynchronously.|

- Example
  ```js
  fileio.fchmod(fd, mode, function (err) {
      // Do something.
  });
  ```


## fileio.fchmodSync<sup>7+</sup>

fchmodSync(existingPath: string, newPath: string): void

Synchronously changes the file permissions based on the file descriptor.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | mode | number | Yes| Permissions on the file. You can specify multiple permissions, separated using a bitwise OR operator (&#124;). <br/>-&nbsp;**0o700**: The owner has the read, write, and execute permissions. <br/>-&nbsp;**0o400**: The owner has the read permission. <br/>-&nbsp;**0o200**: The owner has the write permission. <br/>-&nbsp;**0o100**: The owner has the execute permission. <br/>-&nbsp;**0o070**: The user group has the read, write, and execute permissions. <br/>-&nbsp;**0o040**: The user group has the read permission. <br/>-&nbsp;**0o020**: The user group has the write permission. <br/>-&nbsp;**0o010**: The user group has the execute permission. <br/>-&nbsp;**0o007**: Other users have the read, write, and execute permissions. <br/>-&nbsp;**0o004**: Other users have the read permission. <br/>-&nbsp;**0o002**: Other users have the write permission. <br/>-&nbsp;**0o001**: Other users have the execute permission.|

- Example
  ```js
   fileio.fchmodSync(fd, mode);
  ```


## fileio.createStream<sup>7+</sup>

createStream(path: string, mode: string): Promise&lt;Stream&gt;

Asynchronously opens a stream based on the file path. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | string | Yes| -&nbsp;**r**: Open a file for reading. The file must exist. <br/>-&nbsp;**r+**: Open a file for both reading and writing. The file must exist. <br/>-&nbsp;**w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). <br/>-&nbsp;**a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Stream](#stream7)&gt; | Promise used to return the result.|

- Example
  ```js
  fileio.createStream(path, "r+").then(function(stream){
      console.info("createStream successfully");
  }).catch(function(err){
      console.info("createStream failed with error:"+ err);
  });
  ```


## fileio.createStream<sup>7+</sup>

createStream(path: string, mode: string, callback: AsyncCallback&lt;Stream&gt;): void

Asynchronously opens a stream based on the file path. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | string | Yes| -&nbsp;**r**: Open a file for reading. The file must exist. <br/>-&nbsp;**r+**: Open a file for both reading and writing. The file must exist. <br/>-&nbsp;**w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). <br/>-&nbsp;**a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).|
  | callback | AsyncCallback&lt;[Stream](#stream7)&gt; | Yes| Callback invoked when the stream is open asynchronously.|

- Example
  ```js
  fileio.createStream(path, mode, function(err, stream){
      // Do something.
  });
  ```


## fileio.createStreamSync<sup>7+</sup>

createStreamSync(path: string, mode: string): Stream

Synchronously opens a stream based on the file path.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | mode | string | Yes| -&nbsp;**r**: Open a file for reading. The file must exist. <br/>-&nbsp;**r+**: Open a file for both reading and writing. The file must exist. <br/>-&nbsp;**w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). <br/>-&nbsp;**a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).|

- Return value
  | Name| Description|
  | -------- | -------- |
  | [Stream](#stream7) | Stream obtained.|

- Example
  ```js
  let ss = fileio.createStreamSync(path, "r+");
  ```


## fileio.fdopenStream<sup>7+</sup>

fdopenStream(fd: number, mode: string): Promise&lt;Stream&gt;

Asynchronously opens a stream based on the file descriptor. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | mode | string | Yes| -&nbsp;**r**: Open a file for reading. The file must exist. <br/>-&nbsp;**r+**: Open a file for both reading and writing. The file must exist. <br/>-&nbsp;**w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). <br/>-&nbsp;**a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).|

- Return value
  | Name| Description|
  | -------- | -------- |
  | Promise&lt;[Stream](#stream7)&gt; | Promise used to return the result.|

- Example
  ```js
  fileio.fdopenStream(fd, mode).then(function(stream){
      console.info("openStream successfully"+);
  }).catch(function(err){
      console.info("openStream failed with error:"+ err);
  });
  ```


## fileio.fdopenStream<sup>7+</sup>

fdopenStream(fd: number, mode: string, callback: AsyncCallback&lt;Stream&gt;): void

Asynchronously opens a stream based on the file descriptor. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | mode | string | Yes| -&nbsp;**r**: Open a file for reading. The file must exist. <br/>-&nbsp;**r+**: Open a file for both reading and writing. The file must exist. <br/>-&nbsp;**w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). <br/>-&nbsp;**a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).|
  | callback | AsyncCallback&nbsp;&lt;[Stream](#stream7)&gt; | Yes| Callback invoked when the stream is open asynchronously.|

- Example
  ```js
  fileio.fdopenStream(fd, mode, function (err, stream) {
      // Do something.
  });
  ```


## fileio.fdopenStreamSync<sup>7+</sup>

fdopenStreamSync(fd: number, mode: string): Stream

Synchronously opens a stream based on the file descriptor.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | mode | string | Yes| -&nbsp;**r**: Open a file for reading. The file must exist. <br/>-&nbsp;**r+**: Open a file for both reading and writing. The file must exist. <br/>-&nbsp;**w**: Open a file for writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**w+**: Open a file for both reading and writing. If the file exists, clear its content. If the file does not exist, create a file. <br/>-&nbsp;**a**: Open a file in append mode for writing at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved). <br/>-&nbsp;**a+**: Open a file in append mode for reading or updating at the end of the file. If the file does not exist, create a file. If the file exists, write data to the end of the file (the original content of the file is reserved).|

- Return value
  | Name| Description|
  | -------- | -------- |
  | [Stream](#stream7) | Stream operation result.|

- Example
  ```js
  let ss = fileio.fdopenStreamSync(fd, "r+");
  ```


## fileio.fchown<sup>7+</sup>

fchown(fd: number, uid: number, gid: number): Promise&lt;void&gt;

Asynchronously changes the file owner based on the file descriptor. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  let stat = fileio.statSync(path);
  fileio.fchown(fd, stat.uid, stat.gid).then(function() {
      console.info("chown successfully");
  }).catch(function(err){
      console.info("chown failed with error:"+ err);
  });
  ```


## fileio.fchown<sup>7+</sup>

fchown(fd: number, uid: number, gid: number, callback: AsyncCallback&lt;void&gt;): void

Asynchronously changes the file owner based on the file descriptor. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file owner is changed asynchronously.|

- Example
  ```js
  let stat = fileio.statSync(fpath);
  fileio.fchown(fd, stat.uid, stat.gid, function (err){
      // Do something.
  });
  ```


## fileio.fchownSync<sup>7+</sup>

fchownSync(fd: number, uid: number, gid: number): void

Synchronously changes the file owner based on the file descriptor.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | fd | number | Yes| File descriptor of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|

- Example
  ```js
  let stat = fileio.statSync(fpath);
  fileio.fchownSync(fd, stat.uid, stat.gid);
  ```


## fileio.lchown<sup>7+</sup>

lchown(path: string, uid: number, gid: number): Promise&lt;void&gt;

Asynchronously changes the file owner based on the file path, changes the owner of the symbolic link (not the referenced file), and returns the result in a promise.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the result. An empty value is returned.|

- Example
  ```js
  let stat = fileio.statSync(path);
  fileio.lchown(path, stat.uid, stat.gid).then(function() {
      console.info("chown successfully");
  }).catch(function(err){
      console.info("chown failed with error:"+ err);
  });
  ```


## fileio.lchown<sup>7+</sup>

lchown(path: string, uid: number, gid: number, callback: AsyncCallback&lt;void&gt;): void

Asynchronously changes the file owner based on the file path, changes the owner of the symbolic link (not the referenced file), and returns the result in a callback.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the file owner is changed asynchronously.|

- Example
  ```js
  let stat = fileio.statSync(path);
  fileio.lchown(path, stat.uid, stat.gid, function (err){
      // Do something.
  });
  ```


## fileio.lchownSync<sup>7+</sup>

lchownSync(path: string, uid: number, gid: number): void

Synchronously changes the file owner based on the file path and changes the owner of the symbolic link (not the referenced file).

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | path | string | Yes| Absolute path of the target file.|
  | uid | number | Yes| New UID.|
  | gid | number | Yes| New GID.|

- Example
  ```js
  let stat = fileio.statSync(path);
  fileio.lchownSync(path, stat.uid, stat.gid);
  ```


## fileio.createWatcher<sup>7+</sup>

createWatcher(filename: string, events: number, callback: AsyncCallback&lt;number&gt;): Watcher

Asynchronously listens for the changes of a file or directory. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | filename | string | Yes| Absolute path of the target file.|
  | events | Number | Yes| -&nbsp;**1**:&nbsp;: The file or directory is renamed. <br/>-&nbsp;**2**: The file or directory is modified. <br/>-&nbsp;**3**: The file or directory is modified and renamed.|
  | callback | AsyncCallback&lt;number&nbsp;&gt; | Yes| Called each time a change is detected.|

- Return value
  | Name| Description|
  | -------- | -------- |
  | [Watcher](#watcher7) | Instance for listening for a file change event.|

- Example
  ```js
  fileio.createWatcher(filename, events, function(watcher){
      // Do something.
  });
  ```


## Readout

Obtains the file read result. This class applies only to the **read()** method.

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| bytesRead | number | Yes| Yes| Length of the data read.|
| offset | number | Yes| Yes| Position of the buffer to which the data will be read in reference to the start address of the buffer.|
| buffer | ArrayBufer | Yes| Yes| Buffer for storing the data read.|


## Stat

Provides detailed file information. Before calling a method of the **Stat** class, use the [stat()](#fileiostat) method synchronously or asynchronously to create a **Stat** instance.


### Attributes

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| dev | number | Yes| No| Major device number.|
| ino | number | Yes| No| File ID. Different files on the same device have different **ino**s.|
| mode | number | Yes| No| File type and permissions. The first four bits indicate the file type, and the last 12 bits indicate the permissions. The bit fields are described as follows: <br/>-&nbsp;**0o170000**: mask used to obtain the file type. <br/>-&nbsp;**0o140000**: The file is a socket. <br/>-&nbsp;**0o120000**: The file is a symbolic link. <br/> -&nbsp;**0o100000**: The file is a regular file. <br/>-&nbsp;**0o060000**: The file is a block device. <br/>-&nbsp;**0o040000**: The file is a directory. <br/>-&nbsp;**0o020000**: The file is a character device. <br/>-&nbsp;**0o010000**: The file is a named pipe (FIFO). <br/>-&nbsp;**0o0700**: mask used to obtain the owner permissions. <br/>-&nbsp;**0o0400**: The owner has the permission to read a regular file or a directory entry. <br/>-&nbsp;**0o0200**: The owner has the permission to write a regular file or create and delete a directory entry. <br/>-&nbsp;**0o0100**: The owner has the permission to execute a regular file or search for the specified path in a directory. <br/>-&nbsp;**0o0070**: mask used to obtain the user group permissions. <br/>-&nbsp;**0o0040**: The user group has the permission to read a regular file or a directory entry. <br/>-&nbsp;**0o0020**: The user group has the permission to write a regular file or create and delete a directory entry. <br/>-&nbsp;**0o0010**: The user group has the permission to execute a regular file or search for the specified path in a directory. <br/>-&nbsp;**0o0007**: mask used to obtain the permissions of other users. <br/>-&nbsp;**0o0004**: Other users have the permission to read a regular file or a directory entry. <br/>-&nbsp;**0o0002**: Other users have the permission to write a regular file or create and delete a directory entry. <br/>-&nbsp;**0o0001**: Other users have the permission to execute a regular file or search for the specified path in a directory.|
| nlink | number | Yes| No| Number of hard links in the file.|
| uid | number | Yes| No| User ID, that is ID of the file owner.|
| gid | number | Yes| No| Group ID, that is, ID of the user group of the file.|
| rdev | number | Yes| No| Minor device number.|
| size | number | Yes| No| File size, in bytes. This parameter is valid only for regular files.|
| blocks | number | Yes| No| Number of blocks occupied by a file. Each block is 512 bytes.|
| atime | number | Yes| No| Time of the last access to the file. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.|
| mtime | number | Yes| No| Time of the last modification to the file. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.|
| ctime | number | Yes| No| Time of the last status change of the file. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.|


### isBlockDevice

isBlockDevice(): boolean

Checks whether the current directory entry is a block special file. A block special file supports access by block only, and it is cached when accessed.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a block special file.|

- Example
  ```js
  let isBLockDevice = fileio.statSync(path).isBlockDevice();
  ```


### isCharacterDevice

isCharacterDevice(): boolean

Checks whether the current directory entry is a character special file. A character special file supports random access, and it is not cached when accessed.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a character special file.|

- Example
  ```js
  let isCharacterDevice = fileio.statSync(path).isCharacterDevice();
  ```


### isDirectory

isDirectory(): boolean

Checks whether a directory entry is a directory.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a directory.|

- Example
  ```js
  let isDirectory = fileio.statSync(path).isDirectory(); 
  ```


### isFIFO

isFIFO(): boolean

Checks whether the current directory entry is a named pipe (or FIFO). Named pipes are used for inter-process communication.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a FIFO.|

- Example
  ```js
  let isFIFO = fileio.statSync(path).isFIFO(); 
  ```


### isFile

isFile(): boolean

Checks whether a directory entry is a regular file.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a regular file.|

- Example
  ```js
  let isFile = fileio.statSync(fpath).isFile();
  ```


### isSocket

isSocket(): boolean

Checks whether a directory entry is a socket.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a socket.|

- Example
  ```js
  let isSocket = fileio.statSync(path).isSocket(); 
  ```


### isSymbolicLink

isSymbolicLink(): boolean

Checks whether a directory entry is a symbolic link.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a symbolic link.|

- Example
  ```js
  let isSymbolicLink = fileio.statSync(path).isSymbolicLink(); 
  ```


## Watcher<sup>7+</sup>

Listens for the changes of a file. You can call the **Watcher.stop()** method synchronously or asynchronously to stop the listening.


### stop<sup>7+</sup>

stop(): void

Asynchronously stops **watcher**. This method uses a promise to return the result.

- Example
  ```js
  fileio.stop();
  ```


### stop<sup>7+</sup>

stop(callback: AsyncCallback): void

Asynchronously stops **watcher**. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when **watcher** is stopped asynchronously.|

- Example
  ```js
  fileio.stop(function(err){
      // Do something.
  });
  ```
## Stream<sup>7+</sup>

File stream. Before calling a method of the **Stream** class, use the **createStream()** method synchronously or asynchronously to create a **Stream** instance.


### close<sup>7+</sup>

close(): Promise&lt;void&gt;

Asynchronously closes the stream. This method uses a promise to return the result.

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the stream close result.|

- Example
  ```js
  let ss= fileio.createStreamSync(path);
  ss.close().then(function(){
      console.info("close fileStream successfully");
  }).catch(function(err){
      console.info("close fileStream  failed with error:"+ err);
  });
  ```


### close<sup>7+</sup>

close(callback: AsyncCallback&lt;void&gt;): void

Asynchronously closes the stream. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the stream is closed asynchronously.|

- Example
  ```js
  let ss= fileio.createStreamSync(path);
  ss.close(function (err) {
      // do something
  });
  ```


### closeSync<sup>7+</sup>

closeSync(): void

Synchronously closes the stream.

- Example
  ```js
  let ss= fileio.createStreamSync(path);
  ss.closeSync();
  ```


### flush<sup>7+</sup>

flush(): Promise&lt;void&gt;

Asynchronously flushes the stream. This method uses a promise to return the result.

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise used to return the stream flushing result.|

- Example
  ```js
  let ss= fileio.createStreamSync(path);
  ss.flush().then(function (){
      console.info("flush successfully");
  }).catch(function(err){
      console.info("flush failed with error:"+ err);
  });
  ```


### flush<sup>7+</sup>

flush(callback: AsyncCallback&lt;void&gt;): void

Asynchronously flushes the stream. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | Yes| Callback invoked when the stream is asynchronously flushed.|

- Example
  ```js
  let ss= fileio.createStreamSync(path);
  ss.flush(function (err) {
      // do something
  });
  ```


### flushSync<sup>7+</sup>

flushSync(): void

Synchronously flushes the stream.

- Example
  ```js
  let ss= fileio.createStreamSync(path);
  ss.flushSync();
  ```


### write<sup>7+</sup>

write(buffer: ArrayBuffer | string, options?: Object): Promise&lt;number&gt;

Asynchronously writes data into the stream. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer&nbsp;\|&nbsp;string | Yes| Data to write. It can be a string or data from a buffer.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position of the data to write in reference to the start address of the data. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to write. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): start position to write the data in the file. By default, data is written from the current position. <br/>-&nbsp;**encoding** (string): format of the string to be encoded. The default value is **utf-8**, which is the only value supported.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;number&gt; | Promise used to return the length of the data written in the file.|

- Example
  ```js
  let ss= fileio.createStreamSync(fpath, "r+");
  ss.write("hello, world",{offset: 1,length: 5,position: 5,encoding :'utf-8'}).then(function (number){
      console.info("write successfully:"+ number);
  }).catch(function(err){
      console.info("write failed with error:"+ err);
  });
  ```


### write<sup>7+</sup>

write(buffer:ArrayBuffer | string,options?:Object, callback:AsyncCallback&lt;number&gt;): void

Asynchronously writes data into the stream. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer&nbsp;\|&nbsp;string | Yes| Data to write. It can be a string or data from a buffer.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position of the data to write in reference to the start address of the data. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to write. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): start position to write the data in the file. By default, data is written from the current position. <br/>-&nbsp;**encoding** (string): format of the string to be encoded. The default value is **utf-8**, which is the only value supported.|
  | callback | AsyncCallback&lt;number&gt; | Yes| Callback invoked when the data is written asynchronously.|

- Example
  ```js
  let ss= fileio.createStreamSync(fpath, "r+");
  ss.write("hello, world", {offset: 1, length: 5, position: 5, encoding :'utf-8'}, function (err, bytesWritten) {
      if (!err) {
         // do something
         console.log(bytesWritten);
      }
  });
  ```


### writeSync<sup>7+</sup>

writeSync(buffer: ArrayBuffer | string, options?:Object): number

Synchronously writes data into the stream.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer&nbsp;\|&nbsp;string | Yes| Data to write. It can be a string or data from a buffer.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position of the data to write in reference to the start address of the data. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to write. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): start position to write the data in the file. By default, data is written from the current position. <br/>-&nbsp;**encoding** (string): format of the string to be encoded. The default value is **utf-8**, which is the only value supported.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | number | Length of the data written in the file.|

- Example
  ```js
  let ss= fileio.createStreamSync(fpath,"r+");
  let num = ss.writeSync("hello, world", {offset: 1, length: 5, position: 5, encoding :'utf-8'});
  ```


### read<sup>7+</sup>

read(buffer: ArrayBuffer, options?: Object): Promise&lt;Readout&gt;

Asynchronously reads data from the stream. This method uses a promise to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer | Yes| Buffer used to store the file read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to read. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): position of the data to be read in the file. By default, data is read from the current position.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Readout](#readout)&gt; | Promise used to return the data read.|

- Example
  ```js
  let ss = fileio.createStreamSync(fpath, "r+");
  ss.read(new ArrayBuffer(4096), {offset: 1, length: 5, position: 5}).then(function (readout){
      console.info("read data successfully");
  }).catch(function(err){
      console.info("read data failed with error:"+ err);
  });
  ```


### read<sup>7+</sup>

read(buffer: ArrayBuffer, options?: Object, callback: AsyncCallback&lt;Readout&gt;): void

Asynchronously reads data from the stream. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer | Yes| Buffer used to store the file read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to read. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): position of the data to be read in the file. By default, data is read from the current position.|
  | callback | AsyncCallback&lt;[Readout](#readout)&gt; | Yes| Callback invoked when data is read asynchronously from the stream.|

- Example
  ```js
  let ss = fileio.createStreamSync(fpath, "r+");
  ss.read(new ArrayBuffer(4096),{offset: 1, length: 5, position: 5},function (err, readOut) {
      if (!err) {
          // do something
      }
  });
  ```


### readSync<sup>7+</sup>

readSync(buffer: ArrayBuffer, options?: Object): number

Synchronously reads data from the stream.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | buffer | ArrayBuffer | Yes| Buffer used to store the file read.|
  | options | Object | No| The options are as follows: <br/>-&nbsp;**offset** (number): position to store the data read in the buffer in reference to the start address of the buffer. The default value is **0**. <br/>-&nbsp;**length** (number): length of the data to read. The default value is the buffer length minus the offset. <br/>-&nbsp;**position** (number): position of the data to be read in the file. By default, data is read from the current position.|

- Return value
  | Type| Description|
  | -------- | -------- |
  | number | Length of the data read.|

- Example
  ```js
  let ss = fileio.createStreamSync(fpath, "r+");
  let num = ss.readSync(new ArrayBuffer(4096), {offset: 1, length: 5, position: 5});
  ```


## Dir

Manages directories. Before calling a method of the **Dir** class, use the [opendir()](#fileioopendir) method synchronously or asynchronously to create a **Dir** instance.


### read

read(): Promise&lt;Dirent&gt;

Asynchronously reads the next directory entry. This method uses a promise to return the result.

- Return value
  | Type| Description|
  | -------- | -------- |
  | Promise&lt;[Dirent](#dirent)&gt; | Directory entry that is read asynchronously.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  dir.read().then(function (dirent){
      console.info("read successfully:"+ dirent.name);
  }).catch(function(err){
      console.info("read failed with error:"+ err);
  });
  ```


### read

read(callback: AsyncCallback&lt;Dirent&gt;): void

Asynchronously reads the next directory entry. This method uses a callback to return the result.

- Parameters
  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;[Dirent](#dirent)&gt; | Yes| Callback invoked when the next directory entry is asynchronously read.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  dir.read(function (err, dirent) {
      if (!err) {
          // do something
          console.log(dirent.name)
      }
  });
  ```


### readSync

readSync(): Dirent

Synchronously reads the next directory entry.

- Return value
  | Type| Description|
  | -------- | -------- |
  | [Dirent](#dirent) | Directory entry read.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let dirent = dir.readSync();
  ```


### closeSync

closeSync(): void

Closes a directory. After a directory is closed, the file descriptor in Dir will be released and no directory entry can be read from Dir.

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  dir.closeSync();
  ```


## Dirent

Provides information about files and directories. Before calling a method of the **Dirent** class, use the [dir.read()](#read) method synchronously or asynchronously to create a **Dirent** instance.


### Attributes

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| name | string | Yes| No| Directory entry name.|


### isBlockDevice

isBlockDevice(): boolean

Checks whether the current directory entry is a block special file. A block special file supports access by block only, and it is cached when accessed.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a block special file.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let isBLockDevice = dir.readSync().isBlockDevice();
  ```


### isCharacterDevice

isCharacterDevice(): boolean

Checks whether a directory entry is a character special file. A character special file supports random access, and it is not cached when accessed.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a character special file.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let isCharacterDevice = dir.readSync().isCharacterDevice(); 
  ```


### isDirectory

isDirectory(): boolean

Checks whether a directory entry is a directory.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a directory.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let isDirectory = dir.readSync().isDirectory(); 
  ```


### isFIFO

isFIFO(): boolean

Checks whether the current directory entry is a named pipe (or FIFO). Named pipes are used for inter-process communication.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a FIFO.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let isFIFO = dir.readSync().isFIFO(); 
  ```


### isFile

isFile(): boolean

Checks whether a directory entry is a regular file.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a regular file.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let isFile = dir.readSync().isFile(); 
  ```


### isSocket

isSocket(): boolean

Checks whether a directory entry is a socket.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a socket.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let isSocket = dir.readSync().isSocket(); 
  ```


### isSymbolicLink

isSymbolicLink(): boolean

Checks whether a directory entry is a symbolic link.

- Return value
  | Type| Description|
  | -------- | -------- |
  | boolean | Whether the directory entry is a symbolic link.|

- Example
  ```js
  let dir = fileio.opendirSync(dpath);
  let isSymbolicLink = dir.readSync().isSymbolicLink();
  ```