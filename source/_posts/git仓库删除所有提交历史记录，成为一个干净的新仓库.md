---
title: git仓库删除所有提交历史记录，成为一个干净的新仓库
date: 2018-07-11 11:45:01
tags: git
---

把旧项目提交到 git 上，但是会有一些历史记录，这些历史记录中可能会有项目密码等敏感信息。如何删除这些历史记录，形成一个全新的仓库，并且保持代码不变呢？

```bash
# 创建一个空分支 (如果不提交，该分支不会实际创建)
   git checkout --orphan new

# Add all the files
   git add -A

# Commit the changes
   git commit -am "commit message"

# Delete the branch
   git branch -D master

# Rename the current branch to master
   git branch -m master

# Finally, force update your repository
   git push -f origin master
```
