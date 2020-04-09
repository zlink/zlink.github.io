---
title: "常用alias记录"
date: 2020-04-09T10:02:48+08:00
draft: false
---

常用的 git aslias 记录

```shell
alias g="git"
alias gst="git status"
alias gcmsg="git commit -m"
alias gco="git checkout"
alias gcb="git checkout -b"
alias gb="git branch"
alias gp="git push"
alias gd="git diff"
alias gaa="git add ."
alias gm="git merge"
alias gcm="git checkout master"
# 合并当前分支到master
alias gmc="git branch --show-current | xargs -I {} sh -c 'git checkout master; git merge {}'"
```
