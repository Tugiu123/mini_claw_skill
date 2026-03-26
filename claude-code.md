---
name: claude-code
description: 使用 Claude Code CLI 执行编码任务、代码审查、Bug 修复、测试生成等。通过 exec 工具调用 claude 命令的 print 模式 (-p) 进行非交互式调用。
metadata:
  {
    "openclaw":
      {
        "requires": { "bins": ["claude"] },
        "install":
          [
            {
              "id": "node",
              "kind": "node",
              "package": "clawhub",
              "bins": [],
              "label": "Install Claude Code (see docs)",
            },
          ],
      },
  }
---

# Claude Code Skill

通过 OpenClaw 调用 Claude Code CLI 执行各种编码任务。

## 使用方式

使用 `exec` 工具执行 Claude Code 命令。

### 基本用法

```bash
# 单次查询 (print mode)
claude -p "你的任务描述"

# 指定工作目录
claude -p --add-dir C:\path\to\project "任务"

# 指定模型 (sonnet, opus, haiku)
claude -p --model opus "任务"

# 限制执行轮次
claude -p --max-turns 5 "任务"

# JSON 输出 (适合程序解析)
claude -p --output-format json "任务"
```

### 会话管理

```bash
# 继续最近会话
claude -c -p "继续任务"

# 恢复指定会话
claude -r session-name "任务"
```

### 常用场景

| 场景 | 命令 |
|------|------|
| 代码审查 | `claude -p "review 代码文件路径"` |
| 修复 Bug | `claude -p "fix bug: 错误描述"` |
| 写测试 | `claude -p "write tests for 文件"` |
| 解释代码 | `claude -p "explain 文件路径"` |
| 重构 | `claude -p "refactor 文件"` |
| 探索项目 | `claude -p "explore 项目结构"` |
| 生成文档 | `claude -p "生成 API 文档"` |

## OpenClaw 调用示例

### 执行代码审查

```
exec: claude -p --add-dir C:\Users\Aaron\project "review src/auth/login.ts 的安全问题"
```

### 修复 Bug

```
exec: claude -p --add-dir C:\Users\Aaron\myapp "fix: 修复登录页面的 CSRF 漏洞"
```

### 写测试

```
exec: claude -p --add-dir C:\Users\Aaron\myapp "为 utils/helpers.ts 编写单元测试"
```

## 注意事项

1. **认证**: 确保已运行 `claude auth login` 登录
2. **权限**: 可用 `--permission-mode plan` 预览操作而不执行
3. **工作目录**: 使用 `--add-dir` 指定项目路径
4. **输出格式**: 建议用 `--output-format json` 便于解析结果

## OpenClaw 集成经验

### 创建独立 Agent 实例

在 OpenClaw 中创建独立的代码工作 agent，实现与主实例并行处理：

```bash
# 创建新 agent 并绑定到特定频道
openclaw agents add <agent-name> --workspace <workspace-path> --bind discord:<channel-id> --non-interactive
```

**示例**：为代码任务创建独立实例

```bash
openclaw agents add mini-code-bot \
  --workspace "C:\Users\Aaron\.openclaw\workspace\telegram-group-1003892420880" \
  --bind discord:1486568227218919625 \
  --non-interactive
```

### Agent 管理命令

```bash
# 查看所有 agent
openclaw agents list

# 查看绑定关系
openclaw agents bindings

# 删除 agent
openclaw agents delete <agent-name>
```

### 使用场景

- **并行处理**: 创建多个 agent 绑定不同频道，实现真正并行
- **专事专用**: 代码任务用独立 workspace，避免阻塞主对话
- **环境隔离**: 不同项目使用不同 workspace，互不干扰
