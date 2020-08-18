##### https://www.liaoxuefeng.com/wiki/896043488029600/1163625339727712（廖雪峰Git）



##### git bash 获取公钥

```
ssh-keygen -t rsa -C "994431678@qq.com"
```



##### 上传公钥

#### （台式）jatal-sshkey-win：

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCqL9wy/c/qQbXwLGWDS6vrqg139nqRo+cuaSunDm5/Zrca0O3rvh6JCpEwzf/0OZTVmWRpEeMtkEMAAH+t1Tbe62oEz8QXdSbfcPTFjXXMCY8OV25LShgnwgVAJB4H9e/IdDxsxSA80+/V6O7HV9xmHjgdtz9Gg++43AmPs6m+wDQAFQEesfX1tvVMrpu6+V5L8ZCrLMRM/dTxvIGlBFe71rvX9CE9gYbpQYqxbwTLULiDMicjZmBAa/6pIrEN6UceeB9U2F26sOuGESeAbwsJCneH8vBEVcu3m+yXgFDFsfw64b6kn3bbsYN1XZ/wfeyOpLphQgpSF/L64ad/njCZZU6pvBis7bEwoT/+8r9D5nVESA58aPkzJNHvfT8BAOhniBBdVVc4lxcVHLNSgnbs5/aLY95ZzoJ6Qo1RUEQvVbVuX7ctgIxF4RTPug4z3KOlRsUnLMKJ13oT0Emt3KH2UtykDQ5roJ8s38VmvQPLTJSQQSGSB2WkXN8gyldDXmk= Administrator@yz-4f-xxk-01

#### （笔记本）jatal-sshkey-laptop:

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDHI49W0O1xjPALXJ85PFB840lLJt8W+LsQbjzCHjhAiQ6pWW9R7lSCKh56erxzpBLuaA0kuZ4pyFeRq66/gFpvMiqI2SGwnIUEUAohNKroOEK2ACClO0oezCdxuT6NRRCgwIRDZqhP2KYnk7skW8UP//zKJHCVfnYGxsSCSHxl86Kh32cE7C90DEnrN65SDiDrrMW0f0c+0hXNn6rQcK5S5tZcZxL9G+Q9g9o/FTNwMiwSM97EmSZQI0i8YsfPCXVRKyZAS3vZ/B19wU5cFj3H9w+9RGUTJ5IdeNsY217oHeG1xIE3sU1Xeei0sDEVpOtM26RIosM6I1oGJ+3bKHAD 994431678@qq.com

#### 托管平台（`github`或`gitee`）上新建仓库

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200414173256218.png" alt="image-20200414173256218" style="zoom:67%;" />

#### 初始化一个新的本地仓库：

##### git init

##### 查看本地项目是否关联远程库：

##### git remote -v

##### 已关联 -> 删除：(git给远程库起的默认名称是`origin`)

##### git remote rm origin

##### 重新关联：

##### git remote add origin  + ssh地址

##### 例：git remote add origin git@gitee.com:jatal/frontend.git

##### 再次查看：

```cmd
D:\Devlop_Project\sysgy-vue> git remote -v
origin  git@gitee.com:jatal/sjsgy-vue.git (fetch)
origin  git@gitee.com:jatal/sjsgy-vue.git (push)
# 如上，表示关联成功
```



#### 提交远程库：

##### 主分支：

##### git checkout master;

##### git push -u origin master;

##### 开发分支：

##### git checkout develop;

##### git push -u origin develop;



#### 其他常用：

##### git status;

##### git add . ;

##### git commit -m "fix";

##### git pull;

##### git push;



##### 

```nginx
# 查看当前本地分支
git branch
# 查看本地所有分支 
git branch -a
# 查看远程分支
git branch -r
# 创建本地分支（git branch + 分支名）
git branch develop
# 把本地分支推送到远程分支（git push origin + 分支名）
git push origin develop

# 切换本地分支（查看当前分支 -> 切换）
git branch
git checkout develop

# 删除本地分支（例如：删除 develop 分支）
git branch -d develop
# 删除远程分支（例如：删除 develop 分支）
git push origin --delete develop

```





