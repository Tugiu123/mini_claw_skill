---
name: gstack
description: Y Combinator 的 AI 开发工作流工具集，把 Claude Code 变成虚拟工程团队。28 个 Skills 覆盖完整开发周期。
metadata:
  {
    "openclaw": {
      "requires": { "bins": ["git", "bun"] },
      "install": [
        {
          "id": "git-clone",
          "kind": "shell",
          "command": "git clone https://github.com/garrytan/gstack.git .agents/skills/gstack",
          "label": "Clone gstack to .agents/skills/gstack"
        }
      ]
    }
  }
---

# gstack - AI Engineering Workflow

gstack 是 Y Combinator 总裁 Garry Tan 的 AI 开发工具集，将 Claude Code 转变为虚拟工程团队。

## 核心数据

| 指标 | 数据 |
|------|------|
| 近期产出 | 60天 60万+ 行生产代码 (35% 测试) |
| 日均产出 | 10,000-20,000 行 |
| 效率提升 | 2013年 772 次提交 → 2026年 1,237+ 次提交 |

## 安装

```bash
# 克隆到项目
git clone https://github.com/garrytan/gstack.git .agents/skills/gstack

# 或克隆到用户目录
git clone https://github.com/garrytan/gstack.git ~/gstack
```

## 工作流

gstack is a process, not a collection of tools.

**Think → Plan → Build → Review → Test → Ship → Reflect**

每个 skill 自动衔接：office-hours 输出的设计文档 → plan-ceo-review 自动读取 → plan-eng-review 生成测试计划 → qa 拾取执行

## Skills 列表

### 思考阶段

| Skill | 角色 | 功能 |
|-------|------|------|
| `/office-hours` | YC Office Hours | 重构产品问题，6 个强制问题重新定义产品 |
| `/plan-ceo-review` | CEO | 重新审视产品方向，寻找 10 星产品 |
| `/plan-design-review` | 高级设计师 | AI 设计质量检测，0-10 评分 |

### 规划阶段

| Skill | 角色 | 功能 |
|-------|------|------|
| `/plan-eng-review` | 工程经理 | 锁定架构，数据流，边缘案例，测试计划 |
| `/design-consultation` | 设计伙伴 | 从零构建完整设计系统 |

### 构建阶段

使用 `/browse` skill 进行浏览器交互

### 审查阶段

| Skill | 角色 | 功能 |
|-------|------|------|
| `/review` | Staff Engineer | 找 passing CI 但 prod 爆炸的 bug |
| `/codex` | OpenAI Codex | 独立代码审查，跨模型分析 |
| `/cso` | 首席安全官 | OWASP Top 10 + STRIDE 安全审计 |

### 测试阶段

| Skill | 角色 | 功能 |
|-------|------|------|
| `/qa` | QA Lead | 真实浏览器测试，找 bug 并修复 |
| `/qa-only` | QA Reporter | 仅报告 bug，不修改代码 |
| `/investigate` | Debugger | 系统性根因调试 |

### 发布阶段

| Skill | 角色 | 功能 |
|-------|------|------|
| `/ship` | 发布工程师 | 同步 main，跑测试，推送，开 PR |
| `/land-and-deploy` | 发布工程师 | 合并 PR，等待 CI 部署，验证生产 |
| `/canary` | SRE | 部署后监控，监控控制台错误 |

### 复盘阶段

| Skill | 角色 | 功能 |
|-------|------|------|
| `/retro` | 工程经理 | 周报回顾，团队统计，交付 streaks |
| `/document-release` | 技术作家 | 更新项目文档匹配发布内容 |

### 安全技能

| Skill | 功能 |
|-------|------|
| `/careful` | 破坏性命令警告 (rm -rf, DROP TABLE) |
| `/freeze` | 限制文件编辑到指定目录 |
| `/guard` | /careful + /freeze 组合 |
| `/unfreeze` | 解除目录限制 |

### 其他技能

| Skill | 功能 |
|-------|------|
| `/autoplan` | 自动运行 CEO → design → eng review |
| `/benchmark` | 性能基准测试，Core Web Vitals |
| `/gstack-upgrade` | 自更新到最新版本 |

## 使用示例

```
你: 我想做一个日历每日简报应用
你: /office-hours
AI: [询问具体痛点]

你: 多个 Google 日历，事件信息陈旧，地点错误...
AI: 重新定义，你在构建的是"个人首席助理 AI"
   [提取 5 个你未描述的能力]
   [挑战 4 个前提]
   [生成 3 种实现方案及工作量估算]
   建议：先交付最窄版本，明天开始

你: /plan-ceo-review
你: /plan-eng-review
你: 批准计划
AI: [编写 2,400 行代码，11 个文件，~8 分钟]

你: /review
AI: [自动修复 2 个问题]

你: /qa https://staging.myapp.com
AI: [打开真实浏览器，点击流程，找 bug 并修复]

你: /ship
AI: 测试: 42 → 51 (+9 新), PR 已打开
```

## 与 OpenClaw 集成

gstack 可以直接作为 OpenClaw 的 skill 使用：

1. 克隆到 `.agents/skills/gstack`
2. 通过 `/skill-name` 调用各技能
3. gstack 依赖 Bun 和 Node.js

## 核心理念

1. **Completeness is cheap** - 完整实现是"湖"不是"海"
2. **Search before building** - 三层知识：经典、新潮、第一性原理
3. **AI effort compression** - AI 压缩开发时间 10-100x

## 参考

- [gstack 官网](https://github.com/garrytan/gstack)
- [Skill Deep Dives](https://github.com/garrytan/gstack/blob/main/docs/skills.md)
- [Builder Ethos](https://github.com/garrytan/gstack/blob/main/ETHOS.md)