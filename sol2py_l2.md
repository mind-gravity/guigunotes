# Python程序员的Solidity迁移学习

## 第二课知识点

### 一、数组

| 内容 | Solidity | Python |
| :-- | :-- | :-- |
| 申明创建 | 元素类型[*数组长度*] 数组变量名|列表变量名 = [] |
| 数组长度 | 数组名.length |len(列表名) |
| 追加元素 | 数组.push(元素) |列表.append(元素) |
| 元素索引 | 数组[位置] |列表[位置] |
| 起始索引 | 0 | 0 |
| 动态数组用索引赋值 | 不可 |不可 |


### 二、结构

| 内容 | Solidity | Python |
| :-- | :-- | :-- |
| 申明创建 | struct 首字大写结构名 {<br>&nbsp;&nbsp;&nbsp;&nbsp;属性1;<br>&nbsp;&nbsp;&nbsp;&nbsp;属性2;<br>&nbsp;&nbsp;&nbsp;&nbsp;...;<br>}|class 首字大写类名():<br>&nbsp;&nbsp;&nbsp;&nbsp;def \_\_init\_\_(self, 属性参数1, 属性参数2, ...):<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.属性1 = 属性参数1<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;self.属性2 = 属性参数2<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...|
| 创建实例 | 首字大写结构名(属性参数1, 属性参数2, ...) | 首字大写类名(属性参数1, 属性参数2, ...) |


### 三、循环


| 内容 | Solidity | Python |
| :-- | :-- | :-- |
| 语法 |  | |
