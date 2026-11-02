# 知识回传 ima 闭环 · IMA Knowledge Loop

> 每当会话产出有长期复用价值的正式内容，自动生成「ima 保存建议」，确认后回传知识库，形成沉淀→调用→产出→再沉淀的闭环

![License](https://img.shields.io/badge/license-MIT-5a6b4f)
![Type](https://img.shields.io/badge/type-Agent%20Skill-4a6b7c)
![Platform](https://img.shields.io/badge/platform-WorkBuddy%20%7C%20Claude%20Code-b8935a)

## 它解决什么问题

大多数「沉淀」失败在最后一步：内容产出在对话里，关掉窗口就没了。

这个 skill 把「回传」变成产出流程的一部分——只要这次生成的东西还有复用价值，就会主动给出一份保存建议，你点一下头就入库。

## 触发时机

- 产出了报告、方案、文档、Skill、代码、表格、分析结论
- 用户说「回传 ima」「存进知识库」「沉淀这份成果」「给个保存建议」

## 复用价值判断

| 值得回传 | 不值得 |
|---|---|
| 有明确结论的分析 | 一次性的查询结果 |
| 可复用的模板 / 代码 / 流程 | 过程性的中间稿 |
| 决策依据与取舍理由 | 单纯的格式转换产物 |
| 踩坑记录与解法 | 已被新版本取代的内容 |

## 保存建议格式

```markdown
【建议保存】
标题：<可直接当文件名的标题>
建议知识库：<库名> / <分类>
复用场景：<未来什么情况下会再打开它>
需要人工核对：是 / 否 —— <原因>
```

## 知识库路由规则

| 内容类型 | 目标库 |
|---|---|
| 方法论 / 框架 | 方法库 |
| 具体项目产出 | 项目库 / <项目名> |
| 技术踩坑 | 技术库 |
| 周期复盘 | 周刊库 |

## 入库流程

1. 生成保存建议 → 2. 用户确认 → 3. 转成知识卡片（标题 / 核心内容 / 可复用场景 / 关联）→ 4. 写入 ima → 5. 回报「存到哪、叫什么、下次怎么找」

## 硬性规则

- **未经确认不入库**，避免知识库被半成品污染
- 标题必须自解释，不出现「文档 1」「分析报告（终版）」这类名字
- 必须写「复用场景」，否则三个月后你自己都不知道为什么存它

## 配套技能

- [`wechat-deposit`](https://github.com/px-pangu/wechat-deposit) — 聊天内容的卡片化入口
- [`ima-skills`](https://github.com/px-pangu/ima-skills) — ima 知识库的底层读写能力

## 目录结构

```
ima-knowledge-loop/
└─ SKILL.md     角色 · 触发时机 · 价值判断 · 路由规则 · 入库流程 · 硬性规则
```

## 许可

MIT © 2026 px-pangu


## 安装

把本仓库整个目录放进 Agent 的 skills 目录即可，目录名保持仓库名：

```bash
# WorkBuddy
git clone https://github.com/px-pangu/ima-knowledge-loop.git ~/.workbuddy/skills/ima-knowledge-loop

# Claude Code
git clone https://github.com/px-pangu/ima-knowledge-loop.git ~/.claude/skills/ima-knowledge-loop
```

装好后在对话里说一句相关的话就会自动触发，也可以用 `@ima-knowledge-loop` 显式点名。

