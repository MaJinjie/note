> 查看磁盘的使用情况

# option

1. `-h` 同df
2. `-s` 仅报告每一个参数的总和
3. `-m -b -k` 以`M/k/b`为单位显示

# style

```bash
:du
8       ./others
16      ./fzf/test/majinjie
4       ./fzf/test/1
8       ./fzf/test/2
56      ./fzf/test
24      ./fzf/.bkt/bkt-0.8-cache/keys
136     ./fzf/.bkt/bkt-0.8-cache/data/60
140     ./fzf/.bkt/bkt-0.8-cache/data
168     ./fzf/.bkt/bkt-0.8-cache
172     ./fzf/.bkt
272     ./fzf
40      ./bash
12      ./tools
8       ./test
16      ./.bkt/bkt-0.8-cache/keys
16      ./.bkt/bkt-0.8-cache/data/60
20      ./.bkt/bkt-0.8-cache/data
40      ./.bkt/bkt-0.8-cache
44      ./.bkt
12      ./tmp
8       ./tmux/.bkt/bkt-0.8-cache/keys
36      ./tmux/.bkt/bkt-0.8-cache/data/60
40      ./tmux/.bkt/bkt-0.8-cache/data
52      ./tmux/.bkt/bkt-0.8-cache
56      ./tmux/.bkt
112     ./tmux
564     .

```

# common examples

```bash
du -h # 递归地查看每一个目录的磁盘使用情况
du -sh # 查看当前目录的磁盘使用情况

```
