# 分支管理

* 查看分支：
``` base
$ git branch
```

* 创建分支：
``` base
$ git branch <name>
```

* 切换分支：
``` base
$ git checkout <name>
```  dasddas

* 创建+切换分支：
``` base
$ git checkout -b <name>
```

* 合并某分支到当前分支：
``` base
$ git merge <name>
```

* 删除分支：
``` base
$ git branch -d <name>
$ git branch -D <name>              # 强制删除分支
$ git push origin --delete <name>   # 删除远程分支
```

## 解决冲突

* `git merge <branch>`发现冲突时，`git status`查看冲突文件。
* 解决冲突后，再`git add <file>`,最后删除分支`git checkout -d <branch>`

### 分支管理策略
* 合并分支时，主动为`commit`打上信息。
``` base
$ git merge --no-ff -m "message" <branch>
```
合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并就看不出来曾经做过合并。

### Bug分支
* 当你正在开发分支`dev`时，但当前工作流为完成，而需要修复主分支BUG。
``` base
$ git stash         # 保留当前工作进度
$ git stash list    # 查看工作所有保存的进度
$ git stash pop     # 切换至最近的保存状态并删除
$ git stash apply stash@{0}     # 切换指定状态
$ git stash drop  stash@{0}     # 删除指定状态
```
修复bug时，我们会通过创建新的bug分支进行修复，然后合并，最后删除；
当手头工作没有完成时，先把工作现场git stash一下，然后去修复bug，修复后，再git stash pop，回到工作现场。
