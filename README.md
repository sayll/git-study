# 学习自用

## 时光机穿梭

### 查看状态

* 本地暂存区文件状态：
``` bash
$ git status
```

* 本地历史版本库
``` base
$ git log           # 查看当前历史
$ git reflog        # 查看所有（未来）历史
```


### 版本库操作
* 文件新修改：
``` bash
$ git add <fileName>  # 添加指定文件到版本库
$ git add *           # 添加所有文件到版本库
```

* 删除add的文件
``` base
$ git rm <fileName>
```

* 回退文件修改(新添/删除/修改)
``` base
$ git checkout -- <fileName>
```
场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。

* 回退add文件新添/修改
``` base
$ git reset HEAD <fileName>
```
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作

* 回退commit文件新添/修改
``` base
$ git reset --hard commit_id    # 回退到指定版本
$ git reset --hard HEAD^^       # 回退到上一版本
```
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交

* 更新本地版本库
``` base
$ git commit -m "message"
```

* 提交至线上版本库
``` base
$ git push origin <master|name>
```

## 分支管理

### 创建与合并分支

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
```

### 解决冲突

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