> 整数之间的运算

1. `expr 13 '/' 2 6`

```bash

用法：expr 表达式
　或：expr 选项

      --help        显示此帮助信息并退出
      --version     显示版本信息并退出

将 <表达式> 的值打印到标准输出。以下运算符按优先级从低到高排列，不同
优先级之间以空行隔开。<表达式> 可以是：

  参数1 | 参数2     若 <参数1> 的值不为 0 或 null，则返回 <参数1>，
                      否则返回 <参数2>

  参数1 & 参数2     若两边的值都不为 0 或 null，则返回 <参数1>，否则返回 0

  参数1 < 参数2     <参数1> 小于 <参数2>
  参数1 <= 参数2    <参数1> 小于或等于 <参数2>
  参数1 = 参数2     <参数1> 等于 <参数2>
  参数1 != 参数2    <参数1> 不等于 <参数2>
  参数1 >= 参数2    <参数1> 大于或等于 <参数2>
  参数1 > 参数2     <参数1> 大于 <参数2>

  参数1 + 参数2     计算 <参数1> 加 <参数2> 的和
  参数1 - 参数2     计算 <参数1> 减 <参数2> 的差

  参数1 * 参数2     计算 <参数1> 乘以 <参数2> 的积
  参数1 / 参数2     计算 <参数1> 除以 <参数2> 的商
  参数1 % 参数2     计算 <参数1> 除以 <参数2> 的余数

  字符串 : 正则     在 <字符串> 起始处进行 <正则> 的模式匹配

  match 字符串 正则          等于 "字符串 : 正则"
  substr 字符串 位置 长度    求 <字符串> 的子串，<位置> 从 1 开始数
  index 字符串 字符          在 <字符串> 中搜索 <字符> 中任何一个，返回其索引，
                               如未找到则返回 0
  length 字符串              <字符串> 的长度
  + 记号                     将 <记号> 解释为字符串，即使它是一个关键字，
                               例如 "match"，或者运算符，例如 "/"

  ( 表达式 )                 <表达式> 的值

请注意，由于 shell 这一层的存在，可能有许多运算符需要转义或者加引号。
如果两个 <参数> 都是数字，比较运算符就是算术比较，否则就是字典序比较。
模式匹配会返回 \( 和 \) 之间的字符串匹配的字符串，若没有匹配则返回 null；
如果未使用 \( 和 \)，则会返回匹配的字符的个数，若没有匹配则返回 0。

若 <表达式> 的值既不是 null 也不是 0，则退出状态为 0；若 <表达式> 的值为 null
或者 0，则退出状态为 1；如果 <表达式> 的句法无效，则退出状态为 2；如果有错误
发生，则退出状态为 3。
```