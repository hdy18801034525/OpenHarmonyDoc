# du

- [命令功能](#命令功能)
- [命令格式](#命令格式)
- [参数说明](#参数说明)
- [使用指南](#使用指南)
- [使用实例](#使用实例)
- [输出说明](#输出说明)

## 命令功能

du显示指定的文件所占用的磁盘空间。


## 命令格式

du [_-kKmh_] [_file..._]


## 参数说明

**表1** 参数说明

| 参数 | 参数说明 | 取值范围 | 
| -------- | -------- | -------- |
| --help | 查看du命令支持的参数列表。 | N/A | 
| -k | 显示占用的块，每块1024bytes（默认）。 | N/A | 
| -K | 显示占用的块，每块512bytes（posix标准）。 | N/A | 
| -m | 兆字节为单位。 | N/A | 
| -h | 以K，M，G为单位，提高信息的可读性（例如，1K&nbsp;243M&nbsp;2G）。 | N/A | 
| file | 指定的需要统计的文件。 | N/A | 


## 使用指南

- 不支持统计目录的大小，只支持统计文件的大小。

- file的内容既为文件名，不能包含其所在的目录。


## 使用实例

举例：du -h testfile


## 输出说明

**示例:**显示结果如下

```
OHOS:/$ du-h testfile
1.8K    testfile
```