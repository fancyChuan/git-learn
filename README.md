# git-learn

本地库和远程库的交互方式
- 团队内协作
- 团队外协作：使用PR功能

用户签名
- 项目级别
    - git config user.name xxxx
    - git config user.email yyy@github.com
    - 信息存放位置： 项目主目录/.git/config文件
- 系统级别（全局）
    - git config --global user.name xxxx
    - git config --global user.email yyy@github.com
    - 信息存放位置： ~/.gitconfig文件
> 用户签名的邮箱是可以不存在的，只是用来区分是识别不同用户

git日志
```
git log 显示详细的日志信息。简洁的如下：

$ git log --pretty=oneline
71c66af624308648c3522b8fe81d128c036148a9 (HEAD -> master) 修改gitignore
9295545977ae5b9c0c06f536bd8a36dff7169a83 (origin/master, origin/HEAD) Initial commit

$ git log --oneline
71c66af (HEAD -> master) 修改gitignore
9295545 (origin/master, origin/HEAD) Initial commit
```




##### revert 的几种模式
Hard：这个最好理解【至少要掌握这种】，就是将当前版本的数据100%与回退的版本一致（特例：当前所有未add的代码才会保留），但是之前在回退版本之后提交的数据都会丢失；

Mixed:这种回滚后本地代码乍一看什么都没变化，但查看version Control–>local changes下发现数据出现了尚未commit的。实质上它是保持了100%现有代码不变的基础上，将本地仓库最近一次commit版本改为到待回滚的版本了，【特例：现有代码中相对回滚版本新增的代码全部变为未add状态】：相当于其实已经回退到指定版本了，只是在指定版本上修改代码成"现有代码",这样我们就可以方便我们选择保留下“现有代码”上的哪些操作，如果完全放弃现有代码，全部进行简单revert即可；

keep：功能基本和Hard一样，特例：当前所有未commit的代码（含未add的）会保留，且keep后都变为尚未add的文件------------------------------测试时要点击下左上方的同步圈圈进行刷新才看的出来

soft：功能和Mixed基本一样，【特例：现有代码中原本已add的文件仍然保持已add状态】，测试也要点击左上方的圈圈刷新下

> 以上4种方式都会将仓库的真实版本更改为待回滚的版本（用一中的revert可证明）；且除了soft外保留下来的数据中新增的文件都会处于未被版本控制状态（即未add）；
  hard：当前版本中只有未add的数据会保留下来，当前的其他数据全部丢失
  【即未被git管理的文件会保留】
  keep：当前版本中只有已经commit的数据会丢失，其他数据都保留着
  【即，没有提交的数据都会保留】
  mixed和soft都会将当前所有数据保留下来，但如果是soft，已经add的数据保留下来后仍然处于add状态而不是非add
  【即所有数据保留】