# Obtaining Process Information

> ![icon-note.gif](public_sys-resources/icon-note.gif) **NOTE**
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```
import process from '@ohos.process';
```

## System Capabilities

SystemCapability.Utils.Lang

## Attributes

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| egid | number | Yes| No| Effective group identifier (EGID) of a process.|
| euid | number | Yes| No| Effective user identifier (EUID) of a process.|
| gid | number | Yes| No| Group identifier (GID) of a process.|
| uid | number | Yes| No| User identifier (UID) of a process.|
| groups | number[] | Yes| No| Array with supplementary group IDs.|
| pid | number | Yes| No| Process ID (PID) of a process.|
| ppid | number | Yes| No| Parent process ID (PPID) of a process.|
| tid<sup>8+</sup> | number | Yes| No| Thread ID (TID) of a process.|


## ChildProcess

Allows a process to obtain the standard input and output of its child processes, send signals, and close its child processes.


### Attributes

| Name| Type| Readable| Writable| Description|
| -------- | -------- | -------- | -------- | -------- |
| pid | number | Yes| No| PID of the child process.|
| ppid | number | Yes| No| PPID of the child process.|
| exitCode | number | Yes| No| Exit code of the child process.|
| killed | boolean | Yes| No| Whether the parent process successfully sends a signal to the child process to terminate it.|


### wait

wait(): Promise&lt;number&gt;

Waits until the child process ends. This method uses a promise to return the exit code of the child process.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;number&gt; | Promise used to return the exit code of the child process.|

**Example**

```
var child = process.runCmd('ls');
var result = child.wait();
result.then(val=>{
    console.log("result = " + val);
})
```


### getOutput

getOutput(): Promise&lt;Uint8Array&gt;

Obtains the standard output of the child process.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Uint8Array&gt; | Promise used to return the standard output in a Uint8Array.|

**Example**

```
var child = process.runCmd('ls');
var result = child.wait();
child.getOutput.then(val=>{
    console.log("child.getOutput = " + val);
})
```


### getErrorOutput

getErrorOutput(): Promise&lt;Uint8Array&gt;

Obtains the standard error output of the child process.

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;Uint8Array&gt; | Promise used to return the standard error output in a Uint8Array.|

**Example**

```
var child = process.runCmd('madir test.text');
var result = child.wait();
child.getErrorOutput.then(val=>{
    console.log("child.getErrorOutput= " + val);
})
```


### close

close():  void

Closes the child process in running.

**Example**

```
var child = process.runCmd('sleep 5; ls');
child.close();
```


### kill

kill(signal: number | string): void

Sends a signal to the specified child process to terminate it.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| signal | number&nbsp;\|&nbsp;string | Yes| Number or string to send.|

**Example**

```
var child = process.runCmd('sleep 5; ls');
child.kill(9);
```


## process.isIsolatedProcess<sup>8+</sup>

isIsolatedProcess(): boolean

Checks whether this process is isolated.

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the process is isolated; returns **false** otherwise.|

**Example**

```
var result = process.isIsolatedProcess();
```


## process.isAppUid<sup>8+</sup>

isAppUid(v:number): boolean

Checks whether a UID belongs to this app.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| v | number | Yes| UID.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the UID is the app's UID; returns **false** otherwise.|

**Example**

```
var result = process.isAppUid(688);
```


## process.is64Bit<sup>8+</sup>

is64Bit(): boolean

Checks whether this process is running in a 64-bit environment.

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the process is running in a 64-bit environment; returns **false** otherwise.|

**Example**

```
var ressult = process.is64Bit();
```


## process.getUidForName<sup>8+</sup>

getUidForName(v:string): number

Obtains the process UID based on the process name.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| v | string | Yes| Name of a process.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Process UID.|

**Example**

```
var pres = process.getUidForName("tool")
```


## process.getThreadPriority<sup>8+</sup>

getThreadPriority(v:number): number

Obtains the thread priority based on the specified TID.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| v | number | Yes| TID.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | Priority of the thread.|

**Example**

```
var tid = process.getTid();
var pres = process.getThreadPriority(tid);
```


## process.getStartRealtime<sup>8+</sup>

getStartRealtime() :number

Obtains the duration, in milliseconds, from the time the system starts to the time the process starts.

**Return value**

| Type| Description|
| -------- | -------- |
| number | Duration obtained.|

**Example**

```
var realtime = process.getStartRealtime();
```

## process.getPastCputime<sup>8+</sup>

getPastCputime() :number

Obtains the CPU time (in milliseconds) from the time the process starts to the current time.

**Return value**

| Type| Description|
| -------- | -------- |
| number | CPU time obtained.|

**Example**

```
var result = process.getPastCputime() ;
```


## process.getSystemConfig<sup>8+</sup>

getSystemConfig(name:number): number

Obtains the system configuration.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | number | Yes| System configuration parameter name.|

**Return value**

| Type| Description|
| -------- | -------- |
| number | System configuration obtained.|

**Example**

```
var _SC_ARG_MAX = 0
var pres = process.getSystemConfig(_SC_ARG_MAX)
```


## process.getEnvironmentVar<sup>8+</sup>

getEnvironmentVar(name:string): string

Obtains the value of an environment variable.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Environment variable name.|

**Return value**

| Type| Description|
| -------- | -------- |
| string | Value of the environment variable.|

**Example**

```
var pres = process.getEnvironmentVar("PATH")
```


## process.runCmd

runCmd(command: string, options?: { timeout : number, killSignal : number | string, maxBuffer : number }) : ChildProcess

Forks a new process to run a shell command and returns the **ChildProcess** object.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| command | string | Yes| Shell command to run.|
| options | Object | No| Related parameters.|

**Table 1** options

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| timeout | number | No| Maximum running time (in ms) of the child process. When the running time of the child process exceeds the value of this parameter, the parent process sends a **killSignal** to the child process to terminate it. The default value is **0**.|
| killSignal | number&nbsp;&nbsp;\|&nbsp;string | No| Signal sent to the child process when the running time of a child process exceeds the timeout period. The default value is **SIGTERM**.|
| maxBuffer | number | No| Maximum buffer size for the standard input and output of the child process. When the size is exceeded, the child process will be terminated. The default value is **1024 \* 1024**.|

**Return value**

| Type| Description|
| -------- | -------- |
| [ChildProcess](#childprocess) | **ChildProcess** object.|

**Example**

```
var child = process.runCmd('ls', { maxBuffer : 2 });
var result = child.wait();
child.getOutput.then(val=>{
    console.log("child.getOutput = " + val);
})
```


## process.abort

abort(): void

Aborts a process and generates a core file. This method will cause a process to exit immediately. Exercise caution when using this method.

**Example**

```
process.abort();
```


## process.on

on(type: string, listener: EventListener): void

Stores the events triggered by the user.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the events to store. |
| listener | EventListener | Yes| Callback invoked to return the event.|

**Table 2** EventListener

| Name| Description|
| -------- | -------- |
| EventListener&nbsp;=&nbsp;(evt:&nbsp;Object)&nbsp;=&gt;&nbsp;void | Event to store.|

**Example**

```
process.on("data", (e)=>{
    console.log("data callback");
})
```


## process.off

off(type: string): boolean

Deletes the event stored by the user.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| type | string | Yes| Type of the event to delete.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the event is deleted; returns **false** otherwise.|

**Example**

```
process.on("data", (e)=>{
    console.log("data callback");
})
var result = process.off("data");
```


## process.exit

exit(code: number): void

Terminates this process.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| code | number | Yes| Exit code of the process.|

**Example**

```
process.exit(0);
```


## process.cwd

cwd(): string

Obtains the working directory of this process.

**Example**

```
var path = process.cwd();
```


## process.chdir

chdir(dir: string): void

Changes the working directory of this process.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| dir | string | Yes| Path|

**Example**

```
process.chdir('/system');
```


## process.uptime

uptime(): number

Obtains the running time of this process.

**Return value**

| Type| Description|
| -------- | -------- |
| number | Running time of the process, in seconds.|

**Example**

```
var time = process.uptime();
```


## process.kill

kill(pid: number, signal: number): boolean

Sends a signal to the specified process to terminate it.

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| pid | number | Yes| PID of the process, to which the signal will be sent.|
| signal | number | Yes| Signal to send.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Returns **true** if the signal is sent successfully; returns **false** otherwise.|

**Example**
```
var pres = process.pid
var result = that.kill(pres, 28)
```