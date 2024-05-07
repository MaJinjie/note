> 获取文件或文件系统的信息

# option

1. `--format` 指定格式输出
2. `-L -f`

# style

```bash
  文件：1.sh
  大小：43              块：8          IO 块大小：4096   普通文件
设备：259,6     Inode: 2380879     硬链接：1
权限：(0644/-rw-r--r--)  Uid: ( 1000/     mjj)   Gid: ( 1000/     mjj)
访问时间：2024-04-28 17:02:05.191509114 +0800
修改时间：2024-04-28 17:01:41.978088978 +0800
变更时间：2024-04-28 17:11:59.713134388 +0800
创建时间：2024-04-28 16:59:45.886974557 +0800

```

1. `access time` 最后一次访问文件的时间,不会影响到其他时间。比如，打开文件，
   比如对这个文件运用 grep、sed、more、cat 、less、tail、head等命令，
   ls、stat命令都不会修改文件的访问时间。
2. `modify time` 最后一次修改的时间，其他两者可能都会影响。
3. `change time` 最后一次对文件属性改变的时间, 不会影响其他两者，包括权限，大小，属性等等。
   如使用chmod，chown，mv，ln，就会改变文件的Change time。

# common examples

```bash
stat -c "..."
stat 1.sh

```

# help

```bash

用法：stat [选项]... 文件...
显示文件或文件系统的状态。

长选项的必选参数对于短选项也是必选的。
  -L, --dereference     跟随链接
  -f, --file-system     显示文件系统状态而非文件状态
      --cached=模式     指定如何使用已缓存的属性；
                          对于远程文件系统很有用。参见下面的 <模式>
  -c  --format=格式     使用指定的 <格式>，而非默认格式；
                          每使用一次 <格式>，就输出一个换行符
      --printf=格式     类似 --format，但是会解释反斜杠转义序列，并且不会
                          强制在末尾输出换行符。如果您仍希望进行换行，
                          可以在 <格式> 中加入 "\n"
  -t, --terse           使用简洁格式输出
      --help        显示此帮助信息并退出
      --version     显示版本信息并退出

--cached 选项的 <模式> 可以是：always、never 或 default。
"always" 会在可用时使用已缓存的属性，
"never" 会尝试和最新的属性进行同步，
"default" 会由底层的文件系统作出决定。

用于文件的有效的格式序列有（不使用 --file-system）：

  %a   八进制权限（参见 printf 的 "#" 和 "0" 标志）
  %A   用可读性较好的格式输出权限和文件类型
  %b   已分配的块数（参见 %B）
  %B   以字节为单位输出 %b 所报告的每个块的大小
  %C   SELinux 安全上下文字符串
  %d   十进制设备号 (st_dev)
  %D   十六进制设备号 (st_dev)
  %Hd  十进制主设备号
  %Ld  十进制次设备号
  %f   十六进制原始模式
  %F   文件类型
  %g   所属组 ID
  %G   所属组名称
  %h   硬链接数量
  %i   inode 编号
  %m   挂载点
  %n   文件名
  %N   如果文件是一个符号链接，显示解引用后的文件名，并加上引号
  %o   提示最佳的 I/O 传输大小
  %s   总大小，以字节为单位
  %r   十进制设备类型 (st_rdev)
  %R   十六进制设备类型 (st_rdev)
  %Hr  十进制主设备类型，用于字符或块设备特殊文件
  %Lr  十进制次设备类型，用于字符或块设备特殊文件
  %t   十六进制主设备类型，用于字符或块设备特殊文件
  %T   十六进制次设备类型，用于字符或块设备特殊文件
  %u   所有者的用户 ID
  %U   所有者的用户名
  %w   文件创建时间（可读性较好的格式），若未知则为 -
  %W   文件创建时间（自 Epoch 以来的秒数），若未知则为 0
  %x   上次访问时间（可读性较好的格式）
  %X   上次访问时间（自 Epoch 以来的秒数）
  %y   上次数据修改的时间（可读性较好的格式）
  %Y   上次数据修改的时间（自 Epoch 以来的秒数）
  %z   上次文件状态变更的时间（可读性较好的格式）
  %Z   上次文件状态变更的时间（自 Epoch 以来的秒数）

用于文件系统的有效的格式序列有：

  %a   非超级用户可用的空闲块数
  %b   文件系统的数据块总数
  %c   文件系统的文件节点总数
  %d   文件系统的空闲文件节点数
  %f   文件系统的空闲块数
  %i   十六进制文件系统 ID
  %I   允许的文件名最大长度
  %n   文件名
  %s   块大小（用于优化传输速度）
  %S   基本块大小（用于块计数）
  %t   十六进制文件系统类型
  %T   可读性较好的文件系统类型

--terse 和以下 <格式> 等价：
    %n %s %b %f %u %g %D %i %h %t %T %X %Y %Z %W %o
--terse --file-system 和以下 <格式> 等价：
    %n %i %l %t %s %S %b %f %a %c %d

```