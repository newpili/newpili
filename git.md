1 创建ssh key

```shell
ssh-keygen -t rsa -C "xxxxxx@163.com" //123 是你自己注册GitHub的邮箱
```

2 登录

```shell
ssh -T git@github.com
```

3 设置全局

```
git config --global user.name  "xxxxxx"//你的GitHub登陆名
git config --global user.email "xxxxxx@163.com"//你的GitHub注册邮箱
```

4 测试

```
git init
git add first.txt
git commit -m "test"
git remote add origin git@github.com:newpili/newpili.git 
git push -u origin master

```

5上传

```shell
以后上传和更新仓库，特别方便：
只需要三句命令:
git add .//git add . 
#是更新仓库的语句，如果只是要添加某文件到仓库，就用 git add 文件名.后缀
git commit -m "备注"
git push

git remote set-url origin git@github.com:newpili/newpili.git

git remote rm origin
git remote add origin url
```

6.补充

```shell
一：切换远程仓库
1：删除原服务端
git remote remove origin
2：添加新目标服务端地址
git remote add origin git@github.com:newpili/newpili.git #仓库地址(ssh或http都可以)

最近遇到一个问题，git每次pull或者push的时候都需要输入密码，但是从网上找了很多办法都没有解决，最后只好切换成http仓库

二：删除分支
1：删除本地分支
（1）：git checkout 指定分支（切换到其它分支）
（2）：git branch -d 分支名 （删除本地分支）
        或 git branch -D 分支名（强制删除本地分支）
2：删除远程分支
（1）：git checkout 指定分支（切换到其它分支）
（2）：git push origin --delete 分支名

三：版本切换（回退）

1：reset （强制退回）
通過reset方法將head指針指向之前的某次提交，reset之後，後續版本找不到
（1）：找到要回退的版本號
（2）：git指令：git reset --hard 版本號
（3）：git push -f -u origin 分支名
適合單人開發
缺點：代碼被還原，但是多人使用時本地代碼版本號高於當前版本號，需要先刪除本地分支，再重新拉取
更改前：版本1 ---版本2 --- 版本3
更改後：版本1（後續版本被刪除）


2：revert（生成新版本）
（1）：要恢復的版本號
（2）：git revert -n 版本號
（3）：git commit -m '***'
（4）：git push 分支名
更改前：版本1 --- 版本2 --- 版本3
更改後：版本1 --- 版本2 --- 版本3 --- 版本4(revert生成的新版本)
```

