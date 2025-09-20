# GitHub 仓库设置指南

## 当前状态
- ✅ GitHub CLI 已安装 (v2.79.0)
- ✅ 已认证到GitHub账户 zlt002
- ✅ 本地git仓库已初始化
- ❌ 未设置远程仓库
- ❌ 未提交初始代码

## 设置步骤

### 1. 创建GitHub仓库

#### 选项A：使用GitHub CLI创建
```bash
# 在项目根目录运行
gh repo create crm-nextjs-demo --public --source=. --remote=origin --push
```

#### 选项B：手动创建
1. 访问 https://github.com
2. 点击 "New repository"
3. 仓库名：crm-nextjs-demo
4. 选择 Public/Private
5. 不要初始化README（我们已经有了）
6. 点击 "Create repository"

### 2. 设置远程仓库（如果手动创建）
```bash
# 替换YOUR_USERNAME为您的GitHub用户名
git remote add origin https://github.com/YOUR_USERNAME/crm-nextjs-demo.git
```

### 3. 提交初始代码
```bash
# 添加所有文件
git add .

# 创建初始提交
git commit -m "Initial commit: Claude Code PM - Next.js CRM project

- Product Requirements Document (PRD) for CRM system
- Technical implementation epic with 9 tasks
- Project management setup with CCPM workflow
- Next.js + shadcn/ui + local JSON storage"

# 推送到GitHub
git push -u origin main
```

### 4. 安装gh-sub-issue扩展
```bash
gh extension install yahsan2/gh-sub-issue
```

### 5. 运行同步命令
```bash
/pm:epic-sync crm-nextjs-js-json
```

## 验证设置
运行以下命令验证一切正常：
```bash
# 检查远程
git remote -v

# 检查GitHub连接
gh repo view

# 检查扩展
gh extension list | grep gh-sub-issue
```

## 预期结果
设置完成后，同步命令将：
- 创建Epic issue
- 创建9个任务sub-issues
- 重命名任务文件为issue编号
- 创建开发worktree