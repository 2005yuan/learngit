# Git命令学习
## 初始化相关操作
pwd  **查询当前路径**

git init   **初始化仓库**

## 本地文件上传相关操作
git add 文件名    **准备上传（没有反应是一切正常）**

git add .      **上传所有改动**

git commit -m "文本说明"    **正式提交**

git status     **检查状态，检查有无文件有修改**

git diff    **查看有修改文件的差异**

git diff HEAD -- 文件名    **比较当前工作区内容和最后一次上传内容的差别**

git rm 文件名     **在暂存区提交删除该文件的申请**

git reset HEAD 文件名   **把暂存区的提交撤回**

## 版本更换相关操作
reset指令
    --mixed   该参数为默认参数，可以不写，用于重置暂存区的文件上次一致，工作区不变
git reset HEAD 文件名    **把暂存区的提交还原成上一次的**

    --soft    该参数可以将当前的版本还原至之前的某个版本，但保留当前暂存区和工作区未提交的修改
git reset --soft HEAD^   **回溯之前的版本(几个^代表上几个版本) (也可以写成HEAD~3表示回退三个版本)**

git reset --soft 版本号   **回溯到之前的某个版本（版本号不用写全，四位就够了）**

    --hard    该参数可以撤销所有工作区未提交的修改，将暂存区和工作区都还原到某一版本 (谨慎使用)
git reset --hard HEAD^   **回溯之前的版本(几个^代表上几个版本) (也可以写成HEAD~3表示回退三个版本)**

git reset --hard 版本号   **回溯到之前的某个版本（版本号不用写全，四位就够了）**

git checkout -- 文件名   **将工作区某一文件还原到最后一次上传的状态**

## 历史查询相关操作
git reflog  **查看之前的命令**

git log    **查看之前上传的版本**

git log --graph --pretty=oneline --abbrev-commit  **查看之前上传的版本(以图形的形式)**

git rebase     **重置本地提交记录，使分支合并更美观**

## 远程库相关操作
git remote add origin git@github.com:用户名/库名.git   **添加远程库**

git push origin master     **将本地改动上传到远程库**

git remote -v     **查看远程库的信息**

git remote rm origin   **删除本地库与远程库的链接**

git clone git@github.com:用户名/库名.git   **克隆远程库的文件**

git checkout -b 分支名 origin/远程库分支名   **将远程库分支建立本地分支**

git pull         **将远程库的最新提交抓下来**

git branch --set-upstream-to=本地分支名 origin/远程库分支名   **当git pull提示no tracking information时用于建立本地分支与远程库分支的联系**

## 分支相关操作
git switch -c 分支名       **新建并切换至该分支**

git switch 分支名          **切换至该分支**

git checkout -b 分支名     **新建并切换至该分支(等于下面两条指令合起来)**

git branch 分支名         **新建一个分支**

git checkout 分支名        **切换至该分支**

git branch                **查看分支**

git merge 分支名          **把该分支合并到当前分支上**

git merge --mo-ff 分支名  **(禁用快速合并模式)普通合并，相当于一次提交（可加-m提交备注）**

git branch -d 分支名      **删除该分支(已合并的)(未合并的要用-D)**

## stash相关操作
git stash                **将当前工作区变动存起来**

git stash list           **查看存储的stash**

git stash pop            **还原最后一次储存的工作区，并删除最后一次的存储记录**

git stash apply          **还原最后一次储存的工作区**

git stash apply stash编号(例如stash@{0})    **还原特定某次储存的工作区**

git stash drop           **删除最后一次储存的stash**

git cherry-pick  版本号   **仅将某次提交的内容合并进来**

## 标签相关操作
git tag 标签名                **为当前分支打上标签(默认标签是打在最新提交的commit上)**

git tag 标签名 版本号        **为该提交打上标签**

git tag                     **查看当前有的标签**

git show 标签名             **查看该标签的具体信息**

git tag -a 标签名 -m "注释" 版本号

git tag -d 标签名           **删除该标签**

git push origin --tags     **将本地标签推送到远程库**

git push origin :refs/tags/标签名   **将远程库的标签删除**

## 文件相关操作
cd 文件名                 **进入文件夹(cd是change dictory)**

cd ..                    **回到上一级文件夹**

cat 文件名               **显示文件内容**

ls                       **列出当前目录中的所有文件(ls 是list)**

rm 文件名                **删除文件**

rm .git/index.lock  	**删除index.lock**

rm -r 文件夹名           **删除一个文件夹**

touch 文件名            **新建一个文件**

mkdir 文件夹名         **新建一个文件夹**

mv 文件名 目标文件夹名   **移动文件到目标文件夹(文件与文件夹应在同一目录下)**

reset                   **将当前git.bush清屏**

## 简写相关操作
git config --global alias.改写名 原指令    **为原指令提供缩写**

git config --global alias.改写名 '多指令'  	**同上**

### 本地缩写：

st          status

ci          commit

co          checkout

br          branch

unstage     reset HEAD

lg          log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit