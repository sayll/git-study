# 学习自用

## 查看版本库状态
* 本地暂存区文件状态：
``` bash
$ git status
```
* 本地历史版本库
``` base
$ git log           # 查看当前历史
$ git reflog        # 查看所有（未来）历史
```


## 版本库操作
* 文件新添/修改：
``` bash
$ git add `fileName`  # 添加指定文件到版本库
$ git add *           # 添加所有文件到版本库
```
* 撤销文件新添/修改
``` base
$ git checkout -- `fileName`
```
* 撤销add文件新添/修改
``` base
$ git reset HEAD `fileName`
```
* 撤销commit文件新添/修改
``` base
$ git reset --hard commit_id    # 回退到指定版本
$ git reset --hard HEAD^^       # 回退到上一版本
```
* 更新本地版本库
``` base
$ git commit -m "message"
```
* 提交至线上版本库
``` base
$ git push
```
