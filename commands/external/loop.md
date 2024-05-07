# 1 options

1. `-o -b` 计数器初始值 步长
2. `-e` 时间间隔
3. `-n -d -t` 和命令执行无关的限制 次数 时长 时间点
4. `-c -m -r` 和命令输出有关的限制 固定字符串匹配 正则表达式匹配 退出代码(可以提前终止命令)
5. `-C -S -s -f` 不同 相同 成功 失败(提前终止命令)
6. `-i` 从标准输入列表项
7. `-l` 最后一个输出
8. `-D` 满足`duration` 后才退出，退出代码为`timeout`命令相同的124

# 2 envs

1. `COUNT` 名义上的计时器，受`--count-by`影响
2. `ACTUALCOUNT`
3. `ITEM` `--for` 指定的循环项，超过指定次数始终为最后一个值

# 3 注意

1. 超时时，不会强制杀死进程。
2. 可以通过管道传入列表项，而不指定`--stdin` 。

```bash
loop 0.6.1
Rich Jones <miserlou@gmail.com>
UNIX's missing `loop` command

USAGE:
    loop [FLAGS] [OPTIONS] [input]...

FLAGS:
    -D, --error-duration    Exit with timeout error code on duration
    -h, --help              Prints help information
    -l, --only-last         Only print the output of the last execution of the command
    -i, --stdin             Read from standard input
        --summary           Provide a summary
    -C, --until-changes     Keep going until the output changes
    -f, --until-fail        Keep going until the command exit status is non-zero
    -S, --until-same        Keep going until the output changes
    -s, --until-success     Keep going until the command exit status is zero
    -V, --version           Prints version information

OPTIONS:
    --for[A comma-separated list of values, placed into 4ITEM. ex., red,green,blue]
    -b, --count-by <count_by>                Amount to increment the counter by [default: 1]
    -e, --every <every>                      How often to iterate. ex., 5s, 1h1m1s1ms1us [default: 1us]
        --for <ffor>                         A comma-separated list of values, placed into 4ITEM. ex., red,green,blue
    -d, --for-duration <for_duration>        Keep going until the duration has elapsed (example 1m30s)
    -n, --num <num>                          Number of iterations to execute
    -o, --offset <offset>                    Amount to offset the initial counter by [default: 0]
    -c, --until-contains <until_contains>    Keep going until the output contains this string
    -r, --until-error <until_error>          Keep going until the command exit status is the value given
    -m, --until-match <until_match>          Keep going until the output matches this regular expression
    -t, --until-time <until_time>            Keep going until a future time, ex. "2018-04-20 04:20:00" (Times in UTC.)

ARGS:
    <input>...    The command to be looped

```

# 其他相似

grosser/parallel
