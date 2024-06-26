> 将标准输入读取到一系列文件中，并写入到标准输出

# 1 options

1. `-a` 追加输出到文件中

```bash

用法：tee [选项]... [文件]...
将标准输入复制到每个 <文件>，并同时输出到标准输出。

  -a, --append              追加到 <文件>，而不是覆盖
  -i, --ignore-interrupts   忽略中断信号
  -p                        使用一个更适合用于管道的 <模式>。
      --output-error[=模式]   设置写入出错时的行为。见下面 <模式> 部分
      --help        显示此帮助信息并退出
      --version     显示版本信息并退出

<模式> 决定了写入到输出对象时出错后的行为：
  warn           写入到任一输出对象时出错，则输出诊断信息
  warn-nopipe    写入到任一非管道的输出对象时出错，则输出诊断信息
  exit           写入到任一输出对象时出错，则退出
  exit-nopipe    写入到任一非管道的输出对象时出错，则退出
-p 选项的默认 <模式> 是 "warn-nopipe"。
使用 "nopipe" 的 <模式> 时，如果所有输出都变成断开的管道，则立刻退出。
未指定 --output-error 选项时，默认的操作是写入到管道出错时立刻退出，
写入到非管道对象出错时输出诊断信息。

```
