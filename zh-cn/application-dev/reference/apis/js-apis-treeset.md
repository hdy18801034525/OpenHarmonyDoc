# 非线性容器TreeSet  

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```
import {TreeSet} from '@ohos.util.TreeSet'  
```


## 权限

无

## TreeSet


### 属性

| 名称 | 参数类型 | 可读 | 可写 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | number | 是 | 否 | TreeSet的元素个数 |


### constructor

constructor(comparator?:(firstValue: T, secondValue: T) => boolean);

TreeSet的构造函数。

- 参数：
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | comparator | function | 否 | 用户自定义的比较函数 |

- 示例：
  ```
  let treeSet = new TreeSet();
  ```


### isEmpty

isEmpty(): boolean;

判断该容器是否为空。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | 为空返回true, 不为空返回false |

- 示例:
  ```
  const treeSet = new TreeSet();
  treeSet.isEmpty();
  ```


### has

has(value: T): boolean;

判断此容器中是否含有该指定value。

- 参数：
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | value | T | 是 | 指定元素 |

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | 是否包含指定元素 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.has(123);
  treeSet.add(123);
  treeSet.has(123);
  ```


### getFirstValue

getFirstValue(): T;

获取容器中排序第一的数据。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | T | 返回排序第一的数据 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  let result = treeSet.getFirstValue();
  ```


### getLastValue

getLastValue(): T;

获取容器中排序最后的数据。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | T | 返回排序最后的数据 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  let result = treeSet.getLastValue();
  ```


### add
add(value: T): boolean;

向TreeSet中添加一组数据。

- 参数：
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | value | T | 是 | 添加的成员数据 |

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | 是否成功添加新数据至容器 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  ```


### remove

remove(key: T): boolean;

删除指定的元素。

- 参数：
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | key | T | 是 | 指定的元素 |

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | boolean | 判断是否成功删除元素 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  treeSet.remove("sdfs");
  ```


### getLowerValue

getLowerValue(key: T): T;

获取容器中比传入元素排序靠前一位的元素。

- 参数：
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | key | T | 是 | 对比的元素值 |

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | T | 返回排序中对比元素前一位的数据 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  treeSet.add("zdfgsd");
  let result = treeSet.getLowerValue("sdfs");
  ```


### getHigherValue

getHigherValue(key: T): T;

获取容器中比传入元素排序靠后一位的元素。

- 参数：
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | key | T | 是 | 对比的元素 |

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | T | 返回排序中传入元素后一位的数据 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  treeSet.add("zdfgsd");
  let result = treeSet.getHigherValue("sdfs");
  ```


### popFirst

popFirst(): T;

删除容器中排序最前的数据。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | T | 返回删除的数据 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  let result = treeSet.popFirst();
  ```


### popLast

popLast(): T;

删除容器中排序最后的数据。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | T | 返回删除的数据 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  let result = treeSet.popLast();
  ```


### clear

clear(): void;

清除容器中的所有元素,并把length置为0。

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  treeSet.clear();
  ```


### values

values(): IterableIterator&lt;T&gt;;

返回包含此映射中包含的键的新迭代器对象。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | IterableIterator&lt;T&gt; | 返回一个迭代器 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  let iter = treeSet.values();
  let temp = iter.next().value;
  while(temp != undefined) {
    console.log(temp);
    temp = iter.next().value;
  } 
  ```


### forEach

forEach(callbackfn: (value: T, key?: T, treeSet?: TreeSet&lt;T&gt;) => void, thisArg?: Object): void;

通过回调函数来遍历实例对象上的元素以及元素对应的下标。

- 参数：
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | callbackfn | function | 是 | 回调函数 |
  | thisArg | Object | 否 | callbackfn被调用时用作this值 |

- callbackfn的参数说明
  | 参数名 | 类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | value | T | 是 | 当前遍历到的元素 |
  | key | T | 否 | 当前遍历到的元素（和value相同）. |
  | treeSet | TreeSet&lt;T&gt; | 否 | 当前调用forEach方法的实例对象 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("sdfs");
  treeSet.add("dfsghsf");
  treeSet.forEach((value, key) => {
    console.log(value, key)
  });
  ```


### entries

entries(): IterableIterator<[T, T]>;

返回包含此映射中包含的键的新迭代器对象。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | IterableIterator<[T, T]> | 返回一个迭代器 |

- 示例:
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
  let iter = treeSet.entries();
  let temp = iter.next().value;
  while(temp != undefined) {
    console.log(temp[0]);
    console.log(temp[1]);
    temp = iter.next().value;
  }
  ```


### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;T&gt;;


返回一个迭代器，迭代器的每一项都是一个 JavaScript 对象,并返回该对象。

- 返回值：
  | 类型 | 说明 |
  | -------- | -------- |
  | IterableIterator&lt;T&gt; | 返回一个迭代器 |

- 示例：
  ```
  let treeSet = new TreeSet();
  treeSet.add("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
  treeSet.add("sdfs");
    
  // 使用方法一：
  for (let item of treeSet) { 
    console.log("value: " + item);
  }

  // 使用方法二：
  let iter = treeSet[Symbol.iterator]();
  let temp = iter.next().value;
  while(temp != undefined) {
    console.log(temp);
    temp = iter.next().value;
  }
  ```