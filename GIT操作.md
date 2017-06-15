# 1.安装
- mac下安装xcode ,即成了git
# 2.创建项目

```
$ mkdir /work/java
$ cd /work/java
$ git init #初始化
$ touch README
$ git add . #更新当前目录
$ git commit -m "java技术栈"
$ git remote add origin  https://github.com/jinweida/worker.git
$ git push -u origin master #将本地项目更新到github仓库
$ git commit --amend -m "更改最后一次注释" #更改最后一次注释，历史的无法修改了
# 代码库文件完全覆盖本地工作版本
$ git reset --hard
$ git pull #github仓库更新到本地
```
