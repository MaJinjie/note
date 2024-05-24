# 1 options

1. `-s[afp]`
2. `-d`
3. `-[sl]u [glob]`
4. `-i`

# help

```bash
USAGE:
    rip [FLAGS] [OPTIONS] [TARGET]...

ARGS:
    <TARGET>...    File or directory to remove

FLAGS:
    -a, --all          Prints all files in graveyard
    -d, --decompose    Permanently deletes (unlink) the entire graveyard
    -f, --fullpath     Prints full path of files under current directory (with -s)
    -h, --help         Prints help information
    -i, --inspect      Prints some info about TARGET before prompting for action
    -l, --local        Undo files in current directory (local to current directory)
    -N, --no-color     Do not use colored output (in progress)
    -p, --plain        Prints only file-path (to be used with scripts)
    -s, --seance       Prints files that were sent under the current directory
    -v, --verbose      Print what is going on
    -V, --version      Prints version information

OPTIONS:
    -G, --graveyard <graveyard>    Directory where deleted files go to rest
    -m, --max-depth <max-depth>    Set max depth for glob to search (default: 10)
    -u, --unbury <target>          Undo the last removal, or specify some file(s) in the graveyard.
                                   Can be glob, or combined with -s (see --help)

```
