# 1. basic

`手动通过Git命令将本地更新的文件提交到远程仓库的基本步骤：`

```shell
# 1. 进入项目目录
cd path/project
# 拉取远程分支
git pull origin main
# 2. 查看当前工作区的状态
# 显示所有未跟踪的文件、已修改的文件和暂存（staged）的更改
git status
# 3. 添加要修改的文件 单个 or all
git add .  # git add path/file
# （可选）预览即将提交的更改
git diff --cached
# 4. 提交时需要提供一个简短而有意义的提交消息
git commit -m "Your commit message here"
# 5. 检查远程分支并拉取最新更改
git fetch origin
# 6. 合并远程分支到本地（如果需要）
git merge origin/main
# 7. 推送到远程分枝
git push origin main
```

