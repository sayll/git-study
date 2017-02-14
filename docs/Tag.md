# 标签Tag

## 创建

* 查看所有tag
``` base
$ git tag
```

* 创建一个tag
``` base
$ git tag <name>
```

* 回补前几个版本的tag
``` base
$ git log       # 找回conmit_id
$ git tag v1.0.0 <conmit_id>        # 基础tag
$ git tag -a <tagname> -m "version 1.0.0" <conmit_id>  # -a指定标签名，-m指定说明文字
```

## 操作

* 删除tag
``` base
$ git tag -d <tagname>
```

* 推送远程tag
``` base
$ git push origin <tagname>
$ git push origin --tags        # 推送全部的tag
```

* 删除远程tag
``` base
$ git tag -d <tagname>                      # 先删除本地tag
$ git push origin :refs/tags/<tagname>      # 推送删除远程tag
```



