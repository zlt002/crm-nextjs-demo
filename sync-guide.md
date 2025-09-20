# GitHub Sync 快速指南

## 前置条件
1. 您已经将此项目复制到本地
2. 您有一个GitHub仓库
3. 您有仓库的推送权限

## 步骤

### 1. 安装GitHub CLI
根据您的操作系统安装gh CLI

### 2. 认证GitHub
```bash
gh auth login
```
选择:
- What account do you want to log into? → GitHub.com
- What is your preferred protocol? → HTTPS
- Authenticate Git with your GitHub credentials? → Yes
- How would you like to authenticate? → Login with a web browser

### 3. 设置远程仓库
```bash
# 检查当前远程
git remote -v

# 如果需要更改远程仓库
git remote set-url origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
```

### 4. 安装gh-sub-issue扩展
```bash
gh extension install yahsan2/gh-sub-issue
```

### 5. 运行同步命令
在Claude Code中运行：
```bash
/pm:epic-sync crm-nextjs-js-json
```

## 预期结果
- 创建Epic issue
- 创建9个任务sub-issues
- 任务文件重命名为issue编号
- 创建开发worktree

## 如果遇到问题
- 确保您有仓库的写入权限
- 检查GitHub CLI是否正确认证
- 确保远程仓库URL正确