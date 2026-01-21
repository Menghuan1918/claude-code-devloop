# DevLoop Toolkit - Claude Code 插件市场

这是一个 Claude Code 插件市场，提供高效的开发工具包，目标是**可维护性地**开发大型软件项目

## 📦 快速安装

从 GitHub 安装此插件市场及其插件：

```bash
# 1. 添加市场
/plugin marketplace add Menghuan1918/claude-code-devloop

# 2. 安装 dev-toolkit 插件
/plugin install dev-toolkit@devloop-toolkit
```

## 🔧 包含的插件

### dev-toolkit

开发工具包插件，提供智能开发任务调度器、代码质量工具和 Git 辅助工具。

**包含命令：**

| 命令 | 描述 |
|------|------|
| `/dev:dev` | 智能开发任务调度器（Claude 内置代理版本） |
| `/dev:dev-c` | 智能开发任务调度器（Codex 版本） |
| `/dev:gardener` | 代码园丁 - 防止代码腐化，清理技术债务 |
| `/dev:git-commit` | Git 智能提交 - 自动生成规范的提交信息 |
| `/dev:git-check` | Git 代码审查 - 自动审查代码变更 |
| `/dev:update-agents` | 更新 AGENTS.md 文件 |

## 📖 使用示例

### 智能开发调度

```bash
/dev:dev
# 输入开发任务，AI 会自动协调多个代理并发执行
```

### 代码质量维护

```bash
/dev:gardener
# 自动扫描并清理：
# - 重复代码
# - 死代码和未使用的导入
# - 不一致的实现
# - 过时的模式
```

### Git 智能提交

```bash
/dev:git-commit
# 自动分析变更并生成规范的提交信息
```

## 🔄 更新市场

保持市场和插件为最新版本：

```bash
# 更新市场列表
/plugin marketplace update

# 更新已安装的插件
/plugin update dev-toolkit@devloop-toolkit
```

## 📂 项目结构

```
claude-code-devloop/
├── .claude-plugin/
│   └── marketplace.json      # 市场清单
├── dev-toolkit/              # 开发工具包插件
│   ├── .claude-plugin/
│   │   └── plugin.json       # 插件清单
│   ├── commands/             # 斜杠命令
│   │   ├── dev.md
│   │   ├── dev-c.md
│   │   ├── gardener.md
│   │   ├── git-check.md
│   │   ├── git-commit.md
│   │   └── update-agents.md
│   └── README.md             # 插件文档
├── AGENTS.md                 # AI 代理开发指南
└── README.md                 # 本文件
```

## 🚀 系统要求

- **Claude Code**: >= 1.0.33
- **可选依赖**: codex MCP 服务器（用于 `/dev:dev-c` 命令）

## 📝 许可证

MIT License

## 🤝 贡献

欢迎提交 Issues 和 Pull Requests！

---

如有问题或建议，请在 [GitHub Issues](https://github.com/Menghuan1918/claude-code-devloop/issues) 中反馈。
