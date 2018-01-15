[廖dalao的教程](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

#### Git用户名邮箱的全局配置和单仓库配置
[链接](http://blog.csdn.net/u011535508/article/details/53056976)

- 全局：
    - $git config --global user.name "xxxx"
    - $git config --global user.email "xxxx@xx.com"
    - $git config --list

- 单仓库：
    - $git config user.name "gitlab's Name"
    - $git config user.email "gitbal@xx.com"
    - $git config --list

*git config --list 查看当前配置，在当前项目下查看的配置是全局配置+当前项目的配置，使用的时候会优先使用当前项目的配置*

---

#### Git提交

- git add :把文件修改添加到暂存区；
- git commit -m "message" 把暂存区的修改提交到分支；
- git pull；
- git push;

ps: git log -p -2 # 查看最近两次详细修改内容的diff


#### git分支
1. 查看分支：`git branch`
2. 创建分支：`git branch <name>`
3. 切换分支：`git checkout dev`
4. 创建+切换分支：`git checkout -b <name>`
5. 合并某分支到当前分支：`git merge <name>`
6. 删除分支：`git branch -d <name>`

*ps：*本地新建一个分支后，必须要做远程分支关联：`git push --set-upstream origin <name>`

#### git本地合分支，要求输信息时
1. 按`esc`退出编译模式；
2. 输入`:`；进入命令模式；
3. 输入`wq`完成
--set-upstream-to=origin/<branch> login