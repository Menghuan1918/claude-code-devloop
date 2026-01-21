# AGENTS.md - Claude Code Dev Toolkit Plugin 项目

> 这是一个给 AI 代理使用的自述文件，包含项目上下文和开发指令。

## 项目概览

这是一个 Claude Code 插件项目，将本地 `~/.claude/commands` 中的斜杠命令打包成可重用的插件。

### 项目目标

- 将个人的本地斜杠命令迁移到插件格式
- 使命令可以跨项目重用
- 为团队共享做准备

## 项目结构

```
claude-code-devloop/
├── AGENTS.md                 # 本文件 - AI 代理指南
└── dev-toolkit/              # 插件目录
    ├── .claude-plugin/       # 插件元数据
    │   └── plugin.json       # 插件清单
    ├── commands/             # 斜杠命令
    │   ├── dev.md           # 开发调度器（内置代理）
    │   ├── dev-c.md         # 开发调度器（codex）
    │   ├── gardener.md      # 代码园丁
    │   ├── git-check.md     # Git 审查
    │   ├── git-commit.md    # Git 提交
    │   ├── svg.md           # SVG 处理
    │   └── update-agents.md # 更新 AGENTS.md
    └── README.md            # 插件文档
```

## 开发准则

### 插件开发规范

1. **目录结构规则**
   - `.claude-plugin/` 目录只包含 `plugin.json` 清单文件
   - 所有功能目录（`commands/`、`agents/`、`skills/`、`hooks/`）必须放在插件根目录
   - **禁止**将功能目录放在 `.claude-plugin/` 内

2. **命名空间**
   - 所有命令使用 `/dev:` 前缀（插件名为 "dev"）
   - 例如：`/dev:gardener`、`/dev:git-commit`

3. **版本管理**
   - 使用语义化版本：`MAJOR.MINOR.PATCH`
   - 在 `plugin.json` 中更新版本号
   - 重大变更需要更新 README.md

### 代码质量要求

1. **命令文件**
   - 必须包含前置元数据（description）
   - 使用 Markdown 格式
   - 提供清晰的使用说明

2. **文档**
   - README.md 必须保持最新
   - 包含所有命令的使用示例
   - 提供清晰的安装说明

### 测试流程

在修改插件后，必须执行以下测试：

```bash
# 1. 使用 --plugin-dir 加载插件
claude --plugin-dir ./dev-toolkit

# 2. 在 Claude Code 中测试命令
/help                    # 验证命令是否列出
/dev:gardener           # 测试具体命令
```

## 常见任务

### 添加新命令

1. 在 `dev-toolkit/commands/` 创建新的 `.md` 文件
2. 添加前置元数据和命令说明
3. 更新 `README.md` 添加新命令的文档
4. 使用 `--plugin-dir` 测试

### 更新插件版本

1. 修改 `dev-toolkit/.claude-plugin/plugin.json` 中的 `version` 字段
2. 在 `README.md` 的版本历史中记录变更
3. 如果推送到 Git，创建对应的 tag

### 分享插件

**方式 1：本地共享**
```bash
claude --plugin-dir /path/to/dev-toolkit
```

**方式 2：Git 仓库**
1. 将 `dev-toolkit/` 推送到 Git 仓库
2. 团队成员使用 `/plugin install <repo-url>` 安装

## 依赖关系

### 外部依赖
- **codex MCP 服务器**：`/dev:dev-c` 命令需要
- 其他命令使用 Claude Code 内置代理

### 系统要求
- Claude Code 版本 >= 1.0.33

## 注意事项

1. **命名空间变更**
   - 原来的 `/dev` 现在是 `/dev:dev`
   - 原来的 `/gardener` 现在是 `/dev:gardener`
   - 用户需要适应新的命令名称

2. **迁移后的文件**
   - 原始文件仍在 `~/.claude/commands/`
   - 可以考虑删除以避免重复，但建议先测试插件版本是否正常工作

3. **插件更新**
   - 修改命令文件后需要重启 Claude Code
   - 使用 `--plugin-dir` 测试时会立即加载最新版本

## 相关资源

- [Claude Code 插件文档](https://code.claude.com/docs/create-plugins)
- [斜杠命令指南](https://code.claude.com/docs/slash-commands)
- [插件市场](https://code.claude.com/docs/plugin-marketplaces)
