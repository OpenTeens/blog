---
title: JSON 基础知识
tags: 
  - cxzlw
  - JSON
  - 开源知识库
category: "开源知识库"
description: 你是否曾经疑惑过，当我们提到 JSON 的时候，我们在说什么？JSON 以 JS 开头，那么其与 JS 的联系到底是什么？在这篇文章中，我们将尽可能通俗地了解 JSON 的起源、基本格式和意义，并解答一些常见的疑惑。
published: 2024-07-11
image: "./cover.jpg"
---

> 转自 [JSON 基础知识 - 创新者老王的博客](https://blog.cxzlw.top/2024/07/11/json-format/)

你是否曾经疑惑过，当我们提到 `JSON` 的时候，我们在说什么？`JSON` 以 `JS` 开头，那么其与 `JavaScript` 的联系到底是什么？在这篇文章中，我们将尽可能通俗地了解 `JSON` 的起源、格式和意义，并解答一些常见的疑惑。

:::important
标准 `JSON` 格式中不可以使用任何形式的注释。

本文仅为了解释方便，使用了注释。在实际使用中请删除所有注释。
:::

## 一、JSON 是什么

`JSON` (JavaScript Object Notation，读作 `Jason`) 是一种轻量级的数据交换格式，是基于 `JavaScript` 的一个子集。易于人阅读和编写，同时也易于机器解析和生成。这些特性使其成为理想的数据交换语言 [^1]。

Crockford 率先设计并普及了 `JSON`。源自当年对不依赖 `Flash` & `Java Applet` 的实时 `Server-to-Browser` 通信协议的需求 [^2]。

## 二、JSON 的格式

### 1. 基本结构

`JSON` 由三种元素组成 [^1]，包括：
 - Object: 记录无序的映射关系，在 `Python` 中称为字典（`dict`），在一些语言中被称为映射（`map`）
 - Array: 记录有序的数据集合，在 `Python` 中称呼为列表（`list`）
 - Value：如其名，记录各种类型的数据，具体类型稍后解释

这些结构都是 `language-independent` 的，被大部分现代计算机语言以各种形式支持。这使跨编程语言，进行数据交换成为一种可能 [^1]。

接下来将分别解释上面的概念。

### 2. JSON 语法

`JSON Text` 是数据经过序列化后的 `JSON` 字符串。可以是 `Object`, `Array` 和 `Value` [^3]。

但是因为 `Value` 囊括了 `Object` & `Array`。所以一个非常简洁明了的等式是：

```plaintext
JSON Text = Value
```

### 3. Value

其中 `Value` 是一个比较特别的元素，包括了不同的类型 [^1]，包括：
 - Object & Array：嵌套的 `Object` 和 `Array`
 - String：被引号 `""` 包住的字符串
 - Number：数字，包括 `fixed` 和 `float`
 - Boolean：布尔值, `true` 或 `false`
 - Null：空值，在 `Python` 中对应 `None`

`Value` 是一个基本概念，任何作为 `Object`, `Array`, `String`, `Number`, `Boolean`, `Null` 的数据都算作是 `Value`。

可以理解为只要是 `Value` 的地方实际上可以是上述任一类型的数据。（包括 `JSON Text` 的根元素）[^1] [^3]

如果你略懂一点 `Python` 的 `type hints`，那么我想用 `Union` 来解释 `Value` 会更加直观：

```python
from typing import Union

Value = Union[Object, Array, str, int, float, bool, None]
```

### 4. Object

`Object` 是 `JSON` 非常重要的一个组成部分甚至不少人认为 `JSON` 必须以 `{}` 作为最外层元素（尽管这并不正确 [^3]）。

`Object` 内含有数对 `key-value` 的映射关系，其形态如下：
    
```json
{
    "key1": <value1>,
    "key2": <value2>,
    "key3": <value3> // 最后一个元素不可以有逗号
}
```

在这里 `key` 必须是一个 `String`，`value` 的类型则为 `Value`。

`key` 和 `value` 之间用 `:` 分隔，`key-value` 之间用 `,` 分隔。外面则用 `{}` 包裹 [^1]。

前面提到过，`Object` 也是 `Value` 的一种 [^1]，所以 `Object` 也可以作为 `Value` 的一部分。看下面这个例子：

```json
{
    "key1": { // 这里 key1 对应的 value 是一个 Object
        "key2": "value" // 这里 key2 对应的 value 是一个 String
    }, 
    "key3": [1, 2, 3] // 这里 key3 对应的 value 是一个 Array
}
```

### 5. Array

`Array` 是 `JSON` 中的另一个重要元素，其形态如下：

```json
[
    <value1>,
    <value2>,
    <value3> // 最后一个元素不可以有逗号
]
```

和上面一样，这里的 `value` 也是 `Value` 类型的数据。`value` 之间用 `,` 分隔，外面则用 `[]` 包裹。[^1]

同样，这里我们展示一下 `Object` 和 `Array` 作为 `Value` 的一个例子：

```json
[
    [1, 2, 3], // 这里是一个 Array
    {
        "key1": "value1",
    }
]
```

### 6. String

`String` 是 `JSON` 中的一个基本数据类型，其形态如下：

```json
"Hello, World!"
```

`String` 是由 `"` 包裹的字符序列。`String` 也是 `Value` 的一种。[^1]

### 7. Number

`Number` 也是 `JSON` 中的一个基本数据类型，其形态如下：

```json
123456
123.456
123456e-3
```

这里的 `Number` 包括了整数和浮点数。`Number` 也是 `Value` 的一种。[^1]

### 8. Boolean

`Boolean`，布尔值，作为基本类型的它只存在两个不同的数据：

```json
true
false
```

`Boolean` 也是 `Value` 的一种。[^1]

### 9. Null

`Null`，空值，比 `Boolean` 还过分，只有一个数据：

```json
null
```

`Null` 也是 `Value` 的一种。[^1]

## 三、示例
```json
{
    "name": "cxzlw", // string
    "age": 16, // number
    "gender": "mtf", // also string（夹杂私货）
    "balance": 123.45, // also number
    "is_student": true, // boolean
    "hobbies": [ // array of strings
        "coding",
        "reading",
        "writing"
    ],
    "friends": [ // array of objects
        { // 这里演示的是一个 Object 嵌套在 Array 中，再嵌套在另一个 Object 中
            "name": "Alice",
            "age": 18,
            "is_student": true, 
            "balance": 123.45
        },
        {
            "name": "Bob",
            "age": 19,
            "is_student": false, 
            "balance": 123.45
        } // 末尾不能有逗号
    ] // 注意每个 [ 都要有与之配对的 ]
} // 同样 { 要有配对的 }
```

## 四、JSON 的意义

`JSON` 作为一种数据交换格式，其最大的意义在于其跨语言的特性。`JSON` 可以被大部分现代编程语言解析，这使得 `JSON` 成为了一种非常之理想的数据交换格式 [^1]。

同时，随着前后端分离概念的出现，越来越多网站使用 `JSON` 格式在前后端之间交换数据。无论是进行 Web 开发，还是反过来进行数据抓取（爬虫），`JSON` 都是值得掌握的一种数据格式。

在不久后的 [TeensCamp3](https://mp.weixin.qq.com/s/yGyvLGjcdLOM2JqgufhvwQ) 中，我们将会涉及到使用 `JSON` 来存储数据的项目。因此提前了解 `JSON` 的基本知识是非常有必要的。

---

[^1]: [介绍 JSON](https://www.json.org/json-zh.html)
[^2]: [JSON - Wikipedia](https://en.wikipedia.org/wiki/JSON)
[^3]: [JSON Grammar - RFC 8259](https://datatracker.ietf.org/doc/html/rfc8259#section-2)
