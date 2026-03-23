---
name: codex
description: 使用 OpenAI Codex CLI 执行编码任务、代码审查、Bug 修复等。通过 exec 工具调用 codex 命令进行非交互式调用。
metadata:
  {
    "openclaw": {
      "requires": { "bins": ["codex"] },
      "install": [
        {
          "id": "npm",
          "kind": "node",
          "package": "@openai/codex",
          "label": "Install Codex CLI (npm)"
        }
      ]
    }
  }
---

# Codex CLI Skill

通过 OpenClaw 调用 OpenAI Codex CLI 执行各种编码任务。

## 安装

```bash
npm install -g @openai/codex
```

或

```bash
brew install --cask codex
```

## 使用方式

使用 `exec` 工具执行 Codex 命令。

### 基本用法

```bash
# 单次查询 (print mode)
codex "你的任务描述"

# 指定工作目录
codex --dir C:\path\to\project "任务"

# 指定模型
codex --model opus "任务"

# 限制执行轮次
codex --max-turns 5 "任务"

# JSON 输出 (适合程序解析)
codex --output-format json "任务"
```

### 会话管理

```bash
# 继续最近会话
codex --continue "继续任务"

# 恢复指定会话
codex --resume session-name "任务"
```

### 常用场景

| 场景 | 命令 |
|------|------|
| 代码审查 | `codex "review 代码文件路径"` |
| 修复 Bug | `codex "fix bug: 错误描述"` |
| 写测试 | `codex "write tests for 文件"` |
| 解释代码 | `codex "explain 文件路径"` |
| 重构 | `codex "refactor 文件"` |
| 探索项目 | `codex "explore 项目结构"` |
| 生成文档 | `codex "生成 API 文档"` |

## OpenClaw 调用示例

### 执行代码审查

```
exec: codex --dir C:\Users\Aaron\project "review src/auth/login.ts 的安全问题"
```

### 修复 Bug

```
exec: codex --dir C:\Users\Aaron\myapp "fix: 修复登录页面的 CSRF 漏洞"
```

### 写测试

```
exec: codex --dir C:\Users\Aaron\myapp "为 utils/helpers.ts 编写单元测试"
```

## 认证

首次使用需运行 `codex` 登录 ChatGPT 账号。

或使用 API key（需要额外配置）。

## 注意事项

1. **认证**: 确保已登录 ChatGPT 账号
2. **权限**: 可用 `--permission-mode plan` 预览操作而不执行
3. **工作目录**: 使用 `--dir` 指定项目路径
4. **输出格式**: 建议用 `--output-format json` 便于解析结果
