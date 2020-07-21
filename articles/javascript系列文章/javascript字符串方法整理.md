# 字符串常用方法

> 这里我们定义一个变量 `let str = "hello world";`，下方使用字符串方法是，也将会用到 `str` 变量。`[, xxx]`此格式表示可选参数。

- `String.prototype.charAt()`  
  `str.charAt(1); // e` **返回给定索引处的字符，如果没有提供索引，`charAt()`将使用0。**

- `String.prototype.charCodeAt()`  
  `str.charCodeAt(1) // 101` **返回给定索引处字符的UTF-16代码单元值的数字，如果超出范围(0-65536)，则返回NaN**

- `String.prototype.concat()`  
  此方法将一个或多个字符串与原字符串连接合并，形成一个新的字符串并返回。**返回拼接好的字符串，不改变原字符串。根据性能测试，强烈建议使用（+，+=）代替concat方法**

- `String.prototype.slice()`  
  此方法提取某个字符串的一部分，并返回一个新的字符串，并**不会改变原字符串**

- `String.prototype.substring(indexStart[, indexEnd])`  
  此方法返回一个字符串在开始索引到索引介绍之间的一个子集，或从开始索引直到字符串的末尾的一个子集。**不改变原字符串**。参数规则：
  - 如果 `indexStart` 等于 `indexEnd`，方法返回一个空字符串。
  - 如果省略 `indexEnd`，方法提取字符一直到字符串末尾。
  - 如果任一参数小于 0 或为NaN，则被当做0。
  - 如果任一参数大于 `stringName.length`，则被当作 `stringName.length`。
  - 如果 `indexStart` 大于 `indexEnd`，则方法的执行效果就像两个参数调换了一样。

- `String.prototype.substr(start[, length])`  
  **此方法作为是遗留的函数并且可以的话应该避免使用，它并非JavaScript核心语言的一部分，未来将可能会被移除掉。如果可以的话，使用 `substring()` 替代它**。参数说明：
  - `start`开始提取字符的位置。如果为负值，则被看作 `strLength + start`，其中 `strLength` 为字符串的长度（例如，如果 `start` 为 -3，则被看作 `strLength + (-3)`）。
  - `length` 可选。提取的字符数。

- `String.prototype.toLowerCase()`  
  将字符串转换成小写并返回。**不改变原字符串**

- `String.prototype.toUpperCase()`  
  将字符串转换成大写并返回。**不改变原字符串**

- `String.prototype.trim()`  
  此方法会从一个字符串的两端删除空白字符(中间的空白字符不会删除)。**不改变原字符串**

- `String.prototype.indexOf(searchVal [, fromIndex])`  
  此方法返回调用它的String对象中第一次出现的指定值的索引，从`fromIndex`处进行搜索。**如果找不到该值，则返回-1。**

- `String.prototype.match(regexp)`  
  此方法检索返回一个字符串匹配正则表达式的结果。
  - `regexp`，如果传入一个非正则表达式对象，则会隐式地使用 `new RegExp(obj)`将其转换为一个`RegExp`。如果没传任何参数将会得到一个包含空字符串的Array：[""]

- `String.prototype.replace(regexp|substr, newSubStr|function)`  
  此方法返回一个由替换值（replaceMent）替换一些或所有匹配的模式后的新字符串。模式可以是一个字符串或者一个正则表达式，替换值可以是一个字符串或者一个每次匹配都要调用的回调函数。**不改变原字符串**
