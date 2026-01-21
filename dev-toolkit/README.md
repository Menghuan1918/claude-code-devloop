# Dev Toolkit Plugin

开发工具包插件，目标是可维护性地开发大型软件项目。包含斜杠命令：
- 智能开发任务调度器(Claude+Codex/Claude版本)
- 代码园丁：处理代码腐化
- Git 工具
- 文档维护

## 包含的命令

所有命令使用 `/dev:` 命名空间前缀。

### 开发调度器

- **`/dev:dev`** - 智能开发任务调度器（使用Claude Code内置代理）
  - 协调多个 AI 代理并发执行开发任务
  - 自动根据任务类型选择合适的代理
  - 支持调研类和编写类任务的自动分类和执行

- **`/dev:dev-c`** - 智能开发任务调度器（使用 codex）
  - 使用 codex MCP 服务器来执行任务
  - 支持复杂的多轮对话任务
  - 提供更强的任务执行能力

### 代码质量工具

- **`/dev:gardener`** - 代码园丁（防止代码腐化）
  - 识别和清理重复代码
  - 删除死代码和未使用的导入
  - 统一不一致的实现
  - 更新过时的模式
  - 保证幂等性：连续运行产生零或最小 diff

### Git 工具

- **`/dev:git-commit`** - Git 智能提交
  - 智能分析代码变更
  - 自动生成符合规范的提交信息
  - 支持交互式确认

- **`/dev:git-check`** - Git 代码审查
  - 自动审查代码变更
  - 检查代码质量和最佳实践
  - 提供改进建议

### 文档维护

- **`/dev:update-agents`** - 更新 AGENTS.md 文件
  - 自动更新项目的 AI 代理文档
  - 保持文档与代码同步

## 安装

### 使用 `--plugin-dir` 标志（开发/测试）

```bash
claude --plugin-dir /path/to/dev-toolkit
```

### 从 Git 仓库安装（推荐用于团队共享）

如果你将此插件推送到 Git 仓库，团队成员可以这样安装：

```bash
/plugin install Menghuan1918/claude-code-devloop
```

## 使用示例

### 执行开发任务

```bash
# 使用内置代理
/dev:dev
# 然后输入你的开发任务描述

# 使用 codex
/dev:dev-c
# 然后输入你的开发任务描述
```

### 代码清理

```bash
/dev:gardener
# 自动扫描并清理代码库中的技术债务
```

### Git 提交

```bash
/dev:git-commit
# 自动生成提交信息并提交
```

## 目录结构

```
dev-toolkit/
├── .claude-plugin/
│   └── plugin.json          # 插件清单
├── commands/                 # 斜杠命令目录
│   ├── dev.md               # 开发调度器（内置代理）
│   ├── dev-c.md             # 开发调度器（codex）
│   ├── gardener.md          # 代码园丁
│   ├── git-check.md         # Git 审查
│   ├── git-commit.md        # Git 提交
│   └── update-agents.md     # 更新 AGENTS.md
└── README.md                # 本文件
```