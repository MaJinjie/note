# url

https://github.com/wfxr/forgit

# 1 概述

1. 定义了一些git命令别名以及对应的与fzf的集成
2. 允许通过环境变量， 自定义每一个命令的git选项 fzf选项

# 2 使用

## 1 aliases

ga -> git add
glo -> git log
gd -> git diff
gi -> .gitignore 生成器 gi -> .gitignore
grh -> git reset HEAD [file]
gcf -> git checkout [file]
gbd -> git branch -D [branch]
gct -> git checkout [tag]
gco -> git checkout [commit]
gcb -> git checkout [branch]
gro -> git revert [commit]
gss -> git stash
gsp -> git stash push
gclean -> git clean
gcp -> git cherry-pick
grb -> git rebase -i
gbl -> git blame
gfu -> git commit --fixup && git rebase -i --autosquash

## 2 keybindings

Enter Confirm
Tab Toggle mark and move down
Shift - Tab Toggle mark and move up
? Toggle preview window
Alt - W Toggle preview wrap
Ctrl - S Toggle sort
Ctrl - R Toggle selection
Ctrl - Y Copy commit hash/stash ID\*
Ctrl - K / P Selection move up
Ctrl - J / N Selection move down
Alt - K / P Preview move up
Alt - J / N Preview move down
Alt - E Open file in default editor (when possible)

# 3 具体阐述

## 1 git log

> 查看文件的版本历史（在每一个版本中做了那些更改）

```bash
git log $FORGIT_LOG_GIT_OPTS $* -- $files

```

1. 提交预览：当前提交的更改
2. 文件预览：除了第一次提交是前面所有提交更改汇总(\*)，其他提交都是本次提交的更改

## 2 git diff

> 查看文件在版本、工作区、暂存区之间的差异

```bash
# 暂存区和工作区之间
git diff $FORGIT_DIFF_GIT_OPTS $files|$directories
# 版本库和工作区之间
git diff $FORGIT_DIFF_GIT_OPTS [commit] $files|$directories
# 不同提交之间
git diff $FORGIT_DIFF_GIT_OPTS [commit] [commit] $files|$directories
# 版本库和暂存区
git diff $FORGIT_DIFF_GIT_OPTS(--cached) [commit] [commit] $files|$directories

```

## 3 add(@)

```bash
git add $FORGIT_ADD_GIT_OPTS

git add $FORGIT_ADD_GIT_OPTS $@

```

## 4 fixup

> 向指定的提交中补充修改内容。

```bash
1. 检查暂存区是否有内容，如果没有直接返回。
2. 使用fzf选择指定要更改的提交
3. git commit --fixup=<commit>
4. GIT_SEQUENCE_EDITOR=: git rebase --autostash -i --autosquash "$prev_commit"
```

## 5 rebase

> 变基到指定的提交上

1. 使用fzf选择指定要更改的提交
   `cmd="git log $graph --color=always --format='$\_forgit_log_format' $\* $\_forgit_emojify`
2. `git rebase -i $FORGIT_REBASE_GIT_OPTS <commit>^`

## 6 reset head(@)

> 将选中的文件由staged -> unstaged

```bash
1. fzf 选择在暂存区中的文件, 预览是HEAD和暂存区之间的差异 -> files
2. git reset -q $FORGIT_RESET_HEAD_GIT_OPTS HEAD $files


git reset -q $FORGIT_RESET_HEAD_GIT_OPTS HEAD $@

```

## 7 stash show(@)

> 查看stash内容

```bash
git_stash_show="git stash show --color=always --ext-diff"
[[ $# -ne 0 ]] && { $git_stash_show "$@"; return $?; }

1. git stash list | fzf
2. git_stash_show ..

```

## 8 stash push(@-)

```bash
-m 选项+信息

git_stash_push="git stash push $FORGIT_STASH_PUSH_GIT_OPTS"
1. git ls-files --exclude-standard --modified --others | fzf => $files
2. git_stash_push -m <..> $files


preview="
    if $_forgit_is_file_tracked; then
        git diff --color=always {} | $_forgit_diff_pager
    else
        git diff --color=always /dev/null {} | $_forgit_diff_pager
    fi
"
```

## 9 clean

1. `git clean -xdffn "$@" | fzf`
   移除ignored files & untracked directory & untracked files & untracked nested repositores
2. `git clean -xdff $files`

## 10 branch delete(@)

> 删除普通分支

1. `git branch | fzf` 选择要删除的分支
2. `git branch -D $branches`

## 11 revert commits

1. `git log | fzf` => $commits
2. `git revert $FORGIT_REVERT_COMMIT_GIT_OPTS $commits`

## 12 checkout file(@)

1. `git ls-files --modified | fzf`
2. `git checkout $FORGIT_CHECKOUT_FILE_GIT_OPTS`
