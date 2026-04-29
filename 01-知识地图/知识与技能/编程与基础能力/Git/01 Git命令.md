---
title: "Git命令"
source: "https://www.yuque.com/yuqueyonghu4szrfu/ipzbhw/wh9ggug8dahrmgvo"
slug: "wh9ggug8dahrmgvo"
doc_id: "180563393"
updated: "2024-08-07T14:31:32.000Z"
tags:
  - yuque
---

# Git命令

### 1. 配置 Git 用户名和邮箱

在使用 Git 进行任何操作之前，首先需要配置你的用户名和邮箱。这些信息将用于标识你的提交记录。

```plain
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

 你可以使用 `--global` 标志来设置全局配置，这样所有的 Git 仓库都会使用这些信息。你也可以在一个特定的仓库中使用这些配置，只需在仓库的根目录下运行相同的命令，但不加 `--global` 标志。

### 2. 登录账户

确保你已经登录到你的 Git 账户。如果你使用 GitHub，可以使用 `gh` CLI 工具进行登录：

```plain
gh auth login
```

按照提示完成登录。如果使用其他 Git 托管服务，如 GitLab 或 Bitbucket，请参考相应的文档进行登录。

### 3. 克隆远程仓库

使用 `git clone` 命令将远程仓库克隆到本地：

```plain
#克隆repo
git clone https://github.com/username/repo.git

#进入repo
cd repo
```

### 4. 创建和切换到新分支

在开始新的开发任务之前，创建一个新的分支：

```plain
git checkout -b new-feature-branch
```

### 5. 开发和提交更改

在新分支上进行开发，并在适当的时候进行提交：

```plain
git add .
git commit -m "Add new feature"
```

### 6. 保持分支同步

在开发过程中，定期将远程仓库的主分支（如 `main` 或 `master`）的最新更改合并到你的分支，以减少冲突的可能性：

```plain
# 切换到主分支
git checkout main

# 拉取最新的更改
git pull origin main

# 切换回你的分支
git checkout new-feature-branch

# 合并主分支的更改
git merge main
```

### 7. 解决冲突

如果在合并过程中出现冲突，手动解决冲突后进行提交：

```plain
# 解决冲突后
git add conflicted_file
git commit -m "Resolve merge conflict"
```

### 8. 提交分支到远程仓库

将你的分支推送到远程仓库：

```plain
git push origin new-feature-branch
```

### 9. 创建 Pull Request (PR)

在远程仓库（例如 GitHub、GitLab 或 Bitbucket）上创建一个 Pull Request，要求将你的更改合并到主分支。

### 10. 代码审查和合并

等待其他开发人员审查你的代码，并根据反馈进行必要的更改。审查通过后，将 PR 合并到主分支。

### 11. 更新本地仓库

合并后，更新本地仓库的主分支：

```plain
# 切换到主分支
git checkout main

# 拉取最新的更改
git pull origin main
```

### 总结

完整的流程从配置 Git 用户名和邮箱开始，确保你能顺利与远程仓库交互。然后通过以下步骤进行协作开发：

- 配置 Git 用户名和邮箱

- 登录账户

- 克隆远程仓库

- 创建和切换到新分支

- 开发和提交更改

- 保持分支同步

- 解决冲突

- 提交分支到远程仓库

- 创建 Pull Request

- 代码审查和合并

- 更新本地仓库

这种流程有助于团队成员之间高效协作，减少代码冲突，确保代码库的稳定性和质量。
