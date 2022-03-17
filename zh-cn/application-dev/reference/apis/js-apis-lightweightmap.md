# 非线性容器LightWeightMap  

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```
import LightWeightMap from '@ohos.util.LightWeightMap'  
```

## 系统能力

SystemCapability.Utils.Lang

## LightWeightMap


### 属性

| 名称 | 参数类型 | 可读 | 可写 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| length | number | 是 | 否 | LightWeightMap的元素个数。 |


### constructor

constructor()

LightWeightMap的构造函数。

**示例：**

```
let lightWeightMap = new LightWeightMap();
```


### isEmpty

isEmpty(): boolean

判断该LightWeightMap是否为空。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 为空返回true，不为空返回false。 |

**示例：**

```
const lightWeightMap = new LightWeightMap();
let result = lightWeightMap.isEmpty();
```


### hasAll

hasAll(map: LightWeightMap<K, V>): boolean

判断此LightWeightMap中是否含有该指定map中的所有元素。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| map | LightWeightMap<K, V> | 是 | 比较对象。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含所有元素返回true，否则返回false。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let map = new LightWeightMap();
map.set("sdfs", 356);
let result = lightWeightMap.hasAll(map);
```


### hasKey

hasKey(key: K): boolean;

判断此LightWeightMap中是否含有该指定key。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含指定key返回true，否则返回false。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
let result = lightWeightMap.hasKey;
lightWeightMap.hasKey("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
let result1 = lightWeightMap.hasKey("Ahfbrgrbgnutfodgorrogorgrogofdfdf");
```


### hasValue

hasValue(value: V): boolean

判断此LightWeightMap中是否含有该指定value。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | V | 是 | 指定元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 包含指定元素返回true，否则返回false。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
let result = lightWeightMap.hasValue(123);
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
let result1 = lightWeightMap.hasValue(123);
```


### increaseCapacityTo

increaseCapacityTo(minimumCapacity: number): void

将当前LightWeightMap扩容至可以容纳指定数量元素。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| minimumCapacity | number | 是 | 需要容纳的数量。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.increaseCapacityTo(10);
```


### get

get(key: K): V

获取指定key所对应的value。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V | 返回key映射的value值。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let result = lightWeightMap.get("sdfs");
```


### getIndexOfKey

getIndexOfKey(key: K): number

查找指定元素第一次出现的下标值，如果没有找到该元素返回-1。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 被查找的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回指定元素第一次出现时的下标值，查找失败返回-1。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let result = lightWeightMap.getIndexOfKey("sdfs");
```


### getIndexOfValue

getIndexOfValue(value: V): number

查找指定元素第一次出现的下标值，如果没有找到该元素返回-1。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | V | 是 | 被查找的元素。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| number | 返回指定元素第一次出现时的下标值，查找失败返回-1。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let result = lightWeightMap.getIndexOfValue(123);
```


### getKeyAt

getKeyAt(index: number): K

查找指定下标的元素键值对中key值，否则返回undefined。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | number | 是 | 所查找的下标。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| K | 返回该下标对应的元素键值对中key值。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let result = lightWeightMap.getKeyAt(1);
```


### setAll

setAll(map: LightWeightMap<K, V>): void

将一个LightWeightMap中的所有元素组添加到另一个lightWeightMap中。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| map | LightWeightMap<K, V> | 是 | 被添加元素的lightWeightMap。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let map = new LightWeightMap();
lightWeightMap.setAll(map);
```


### set
set(key: K, value: V): Object

向LightWeightMap中添加一组数据。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 添加成员数据的键名。 |
| value | V | 是 | 添加成员数据的值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Object | 返回添加数据后的lightWeightMap。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
let result = lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
```


### remove

remove(key: K): V

删除并返回指定key映射的元素。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| key | K | 是 | 指定key。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V | 返回删除元素的值。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
lightWeightMap.remove("sdfs");
```


### removeAt

removeAt(index: number): boolean

删除指定下标对应的元素。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | number | 是 | 指定下标。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功删除元素返回true，否则返回false。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let result = lightWeightMap.removeAt(1);
```


### setValueAt

setValueAt(index: number, newValue: V): boolean

替换指定下标对应键值对中的元素。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | number | 是 | 指定下标。 |
| newValue | V | 是 | 替换键值对中的值。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 成功替换指定位置数据返回true，否则返回false。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
lightWeightMap.setValueAt(1, 3546);
```


### getValueAt

getValueAt(index: number): V

获取指定下标对应键值对中的元素。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| index | number | 是 | 指定下标。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| V | 返回指定下标对应键值对中的元素。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let result = lightWeightMap.getValueAt(1);
```


### clear

clear(): void

清除LightWeightMap中的所有元素,并把length置为0。

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
lightWeightMap.clear();
```


### keys

keys(): IterableIterator&lt;K&gt;

返回包含此映射中包含的键的新迭代器对象。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;K&gt; | 返回一个迭代器。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let iter = lightWeightMap.keys();
let temp = iter.next().value;
while(temp != undefined) {
  console.log(temp);
  temp = iter.next().value;
}
```


### values

values(): IterableIterator&lt;V&gt;

返回包含此映射中包含的键值的新迭代器对象。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator&lt;V&gt; | 返回一个迭代器。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let iter = lightWeightMap.values();
let temp = iter.next().value;
while(temp != undefined) {
  console.log(temp);
  temp = iter.next().value;
} 
```


### forEach

forEach(callbackfn: (value: V, key?: K, map?: LightWeightMap<K, V>) => void, thisArg?: Object): void

通过回调函数来遍历实例对象上的元素以及元素对应的下标。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| callbackfn | function | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackfn被调用时用作this值。 |

callbackfn的参数说明：
| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | V | 是 | 当前遍历到的元素键值对的值。 |
| key | K | 是 | 当前遍历到的元素键值对的键。 |
| map | LightWeightMap<K, V> | 否 | 当前调用forEach方法的实例对象。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("sdfs", 123);
lightWeightMap.set("dfsghsf", 357);
lightWeightMap.forEach((value, key) => {
  console.log(value, key);
});
```


### entries

entries(): IterableIterator<[K, V]>

返回包含此映射中包含的键值对的新迭代器对象。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator<[K, V]> | 返回一个迭代器。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);
let iter = lightWeightMap.entries();
let temp = iter.next().value;
while(temp != undefined) {
  console.log(temp[0]);
  console.log(temp[1]);
  temp = iter.next().value;
}
```

### toString

toString(): string

将此映射中包含的键值对拼接成字符串，并返回字符串类型。

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | string | 返回一个字符串。 |

**示例：**

  ```
  let lightWeightMap = new LightWeightMap();
  lightWeightMap.set("A", 123);
  lightWeightMap.set("sdfs", 356);
  let iter = lightWeightMap.toString();
  ```

### [Symbol.iterator]

[Symbol.iterator]\(): IterableIterator&lt;[K, V]&gt;

返回一个迭代器，迭代器的每一项都是一个 JavaScript 对象,并返回该对象。

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| IterableIterator<[K, V]> | 返回一个迭代器。 |

**示例：**

```
let lightWeightMap = new LightWeightMap();
lightWeightMap.set("Ahfbrgrbgnutfodgorrogorgrogofdfdf", 123);
lightWeightMap.set("sdfs", 356);

// 使用方法一：
for (let item of lightWeightMap) { 
  console.log("key: " + item[0]);
  console.log("value: " + item[1]);
}

// 使用方法二：
let iter = lightWeightMap[Symbol.iterator]();
let temp = iter.next().value;
while(temp != undefined) {
  console.log(temp[0]);
  console.log(temp[1]);
  temp = iter.next().value;
}
```