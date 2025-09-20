---
name: crm-nextjs-js-json
status: backlog
created: 2025-09-20T10:55:33Z
progress: 0%
prd: .claude/prds/crm-nextjs-js-json.md
github: https://github.com/zlt002/crm-nextjs-demo/issues/1
---

# Epic: crm-nextjs-js-json

## Overview

构建一个基于Next.js 14+和shadcn/ui的简洁CRM演示系统。采用全栈JavaScript架构，使用本地JSON文件作为数据存储，重点展示现代前端开发最佳实践。系统将包含客户管理、商机跟踪、销售漏斗、任务管理和基础数据可视化功能，适合作为学习示例和技术演示。

## Architecture Decisions

### 核心技术栈选择
- **Next.js 14+ App Router**: 利用最新的服务端组件和路由功能
- **shadcn/ui**: 提供现代化、可定制的UI组件系统
- **Tailwind CSS**: 实现快速样式开发和响应式设计
- **TypeScript**: 提供类型安全和更好的开发体验
- **本地JSON存储**: 简化演示，无需数据库配置

### 数据层架构
- **JSON文件存储**: 在`data/`目录下存储所有数据
- **内存缓存**: 使用React Query缓存数据，提升性能
- **localStorage备份**: 防止刷新数据丢失
- **模拟API**: 创建与真实API一致的接口层

### 状态管理策略
- **React Query**: 服务端状态管理和缓存
- **Zustand**: 客户端全局状态（轻量级）
- **URL状态**: 使用路由参数管理过滤和分页状态
- **Form状态**: React Hook Form处理表单状态

## Technical Approach

### Frontend Components

#### 页面结构（App Router）
```
app/
├── (auth)/
│   ├── login/           # 登录页
│   └── layout.tsx      # 认证布局
├── dashboard/          # 仪表盘
├── customers/          # 客户管理
├── opportunities/      # 商机管理
├── tasks/             # 任务管理
├── reports/           # 报表分析
└── layout.tsx         # 主布局
```

#### 核心UI组件
- **Layout组件**: 侧边栏导航、顶部栏
- **DataTable组件**: 可排序、可筛选的数据表格
- **Kanban组件**: 拖拽式销售漏斗
- **Chart组件**: Recharts封装的图表组件
- **Form组件**: 基于shadcn/ui的表单组件
- **Modal组件**: 弹窗组件

#### 交互设计
- **实时搜索**: 防抖处理的搜索功能
- **拖拽排序**: HTML5 Drag and Drop API
- **无限滚动**: 虚拟滚动优化大数据列表
- **快捷键**: 常用操作的键盘快捷键
- **主题切换**: 深色/浅色模式

### Backend Services

#### API路由设计
```
app/api/
├── auth/
│   ├── login/route.ts    # 登录
│   └── logout/route.ts   # 登出
├── customers/
│   ├── route.ts         # CRUD操作
│   └── [id]/route.ts    # 单个客户操作
├── opportunities/
│   ├── route.ts         # CRUD操作
│   └── [id]/route.ts
├── tasks/
│   ├── route.ts
│   └── [id]/route.ts
└── export/
    └── route.ts         # 数据导出
```

#### 数据模型
```typescript
// 用户
interface User {
  id: string;
  name: string;
  email: string;
  role: 'admin' | 'user';
}

// 客户
interface Customer {
  id: string;
  name: string;
  email: string;
  phone?: string;
  company?: string;
  status: 'active' | 'inactive';
  createdAt: string;
  updatedAt: string;
}

// 商机
interface Opportunity {
  id: string;
  title: string;
  customerId: string;
  value: number;
  stage: 'lead' | 'qualified' | 'proposal' | 'negotiation' | 'closed';
  expectedCloseDate: string;
  createdAt: string;
}

// 任务
interface Task {
  id: string;
  title: string;
  description?: string;
  assigneeId?: string;
  dueDate?: string;
  status: 'todo' | 'in_progress' | 'completed';
  priority: 'low' | 'medium' | 'high';
}
```

#### 中间件设计
- **认证中间件**: 保护需要登录的路由
- **CORS中间件**: 处理跨域请求
- **错误处理**: 统一错误响应格式
- **日志中间件**: 记录API调用

### Infrastructure

#### 项目结构
```
src/
├── app/                 # Next.js App Router
├── components/          # UI组件
│   ├── ui/             # shadcn/ui组件
│   ├── charts/         # 图表组件
│   ├── forms/          # 表单组件
│   └── layout/         # 布局组件
├── lib/                # 工具函数
│   ├── api.ts          # API客户端
│   ├── utils.ts        # 通用工具
│   └── validations.ts  # 数据验证
├── types/              # TypeScript类型定义
├── hooks/              # 自定义Hooks
├── data/               # JSON数据文件
└── constants.ts        # 常量定义
```

#### 开发工具配置
- **ESLint**: 代码质量检查
- **Prettier**: 代码格式化
- **Husky**: Git hooks
- **TypeScript**: 类型检查
- **Path aliases**: 简化导入路径

#### 性能优化
- **图片优化**: Next.js Image组件
- **代码分割**: 动态导入组件
- **缓存策略**: React Query缓存
- **Bundle分析**: 分析包大小

## Implementation Strategy

### 开发阶段划分

#### 第一阶段：基础架构（3天）
- 项目初始化和依赖安装
- 配置开发环境和工具链
- 设置shadcn/ui和主题系统
- 创建基础布局和导航
- 实现路由结构

#### 第二阶段：核心功能（5天）
- 实现用户认证系统
- 客户管理CRUD功能
- 数据表格组件开发
- 搜索和筛选功能
- 响应式设计优化

#### 第三阶段：业务功能（4天）
- 商机管理系统
- 销售漏斗可视化
- 任务管理功能
- 数据持久化方案
- 错误处理完善

#### 第四阶段：完善优化（3天）
- 数据可视化报表
- 性能优化
- 单元测试编写
- 文档完善
- 部署配置

### 风险缓解措施

#### 技术风险
- **JSON性能问题**: 实现数据分页和懒加载
- **数据丢失**: localStorage自动备份机制
- **并发问题**: 使用简单的事务机制

#### 项目风险
- **范围蔓延**: 严格MVP原则，优先核心功能
- **时间不足**: 每个功能模块设定时间上限
- **技术债务**: 保持代码简洁，避免过度设计

### 测试策略
- **单元测试**: 核心业务逻辑
- **集成测试**: API接口测试
- **E2E测试**: 关键用户流程
- **性能测试**: 大数据量场景

## Task Breakdown Preview

- [ ] **项目初始化**: 设置Next.js项目、配置工具链、安装依赖
- [ ] **UI系统搭建**: 集成shadcn/ui、主题系统、基础组件
- [ ] **数据层实现**: JSON数据结构、API接口、数据访问层
- [ ] **认证系统**: 登录/登出、权限控制、用户状态管理
- [ ] **客户管理**: 客户CRUD、搜索筛选、数据表格
- [ ] **商机管理**: 商机跟踪、阶段管理、价值计算
- [ ] **任务系统**: 任务CRUD、分配、状态更新
- [ ] **数据可视化**: 销售漏斗、图表展示、仪表盘
- [ ] **优化测试**: 性能优化、测试覆盖、文档编写

## Dependencies

### 外部依赖
- Next.js 14+
- React 18+
- shadcn/ui组件库
- Tailwind CSS
- Recharts（图表）
- React Hook Form（表单）
- React Query（状态管理）
- Zod（数据验证）

### 开发依赖
- TypeScript
- ESLint + Prettier
- Husky + lint-staged
- @types/node

### 前置条件
- Node.js 18+ 环境
- 包管理器（npm/yarn/pnpm）
- Git仓库
- 基础的前端开发知识

## Success Criteria (Technical)

### 性能指标
- 首屏加载时间 < 2秒
- API响应时间 < 200ms
- 搜索响应时间 < 300ms
- Lighthouse评分 > 90

### 质量指标
- TypeScript覆盖率100%
- ESLint零警告
- 组件单元测试覆盖率 > 80%
- 无严重的安全漏洞

### 功能指标
- 所有CRUD操作正常
- 数据持久化有效
- 响应式设计完好
- 主题切换正常
- 快捷键功能可用

## Estimated Effort

### 时间估算
- **总开发时间**: 约15天
- **每周投入**: 20小时
- **预计完成**: 3-4周

### 资源需求
- **开发人员**: 1名前端全栈开发者
- **设计资源**: 使用shadcn/ui默认设计
- **测试资源**: 开发者自测
- **部署**: Vercel或类似平台

### 关键路径
1. 项目初始化 → UI系统 → 数据层
2. 认证系统 → 客户管理 → 商机管理
3. 任务系统 → 数据可视化 → 测试优化

### 风险缓冲
- 预留20%的缓冲时间应对意外问题
- 每个模块预留1天的优化时间
- 准备回滚方案防止功能延期

## Tasks Created
- [ ] #10 -  (parallel: false)
- [ ] #2 -  (parallel: true)
- [ ] #3 -  (parallel: true)
- [ ] #4 -  (parallel: false)
- [ ] #5 -  (parallel: false)
- [ ] #6 -  (parallel: false)
- [ ] #7 -  (parallel: false)
- [ ] #8 -  (parallel: true)
- [ ] #9 -  (parallel: false)

Total tasks: 9
Parallel tasks: 3
Sequential tasks: 6
