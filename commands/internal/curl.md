> 一个功能强大的网络传输工具。它提供发送和接受数据，支持多种网络传输协议。

# 1 options

1. `-o -O` 保存到文件中
2. `-k` 不安全的ssl数据传输
3. `-v -s` 详细 静默模式
4. `-d` 向服务发送POST请求, 并附带的数据

```bash
Usage: curl [options...] <url>
 -d, --data <data>           HTTP POST data
 -f, --fail                  Fail fast with no output on HTTP errors
 -h, --help <category>       Get help for commands
 -i, --include               Include response headers in output
 -o, --output <file>         Write to file instead of stdout
 -O, --remote-name           Write output to file named as remote file
 -s, --silent                Silent mode
 -T, --upload-file <file>    Transfer local FILE to destination
 -u, --user <user:password>  Server user and password
 -A, --user-agent <name>     Send User-Agent <name> to server
 -v, --verbose               Make the operation more talkative
 -V, --version               Show version number and quit

This is not the full help, this menu is stripped into categories.
Use "--help category" to get an overview of all categories.
For all options use the manual or "--help all".

```
