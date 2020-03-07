# git-learn

本地库和远程库的交互方式
- 团队内协作
- 团队外协作：使用PR功能

用户签名
- 项目级别
    - git config user.name xxxx
    - git config user.email yyy@github.com
    - 信息存放位置： ./.git/config文件
- 系统级别（全局）
    - git config user.name xxxx
        - git config user.email yyy@github.com
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
