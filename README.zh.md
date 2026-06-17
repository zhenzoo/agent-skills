<div align="right"><a href="README.md">English</a> · <a href="README.zh.md"><b>中文</b></a></div>

# skillzoo

> 给 **AI 编程智能体**（Claude Code、Codex、Kimi、GLM……）即插即用的 **skills 和斜杠命令**。
> 你不用手动安装——把一段 prompt 丢给你的智能体，它自己全配好。

一个持续增长的小集合，收录我自己觉得真好用的 agent 能力，打包成任何人 ~30 秒就能装上的形式。

---

## ⚡ 30 秒安装（你的智能体替你做）

你**不需要懂 git**。只要两件事：**①** 已登录 GitHub，**②** 把一段 prompt 粘给你的智能体。

1. **复制本仓库地址** —— 本页顶部绿色 **`<> Code`** 按钮 → `HTTPS` → 复制 `git clone https://github.com/zhenzoo/skillzoo.git` 那一行。（或直接复制浏览器地址栏的 URL。）
2. **把下面这整段 prompt 粘给你的智能体**（Claude Code / Codex / Kimi / GLM / Claude……）：

```text
克隆 https://github.com/zhenzoo/skillzoo.git
（我已用 gh CLI 登录 GitHub——如果没登录，先带我走一遍 `gh auth login`。）

从这个仓库里，把 `explain` command 安装到我智能体的【用户级 / user level】——
这是我到处都想用的通用基础设施，不是某个项目专属：
- Claude Code：把 commands/explain.md 拷进 ~/.claude/commands/（或我的 CLAUDE_CONFIG_DIR/commands/）。
- 其它智能体（Codex / Kimi / GLM……）：放进它对应的【用户级】commands/prompts 目录；
  如果该 agent 需要不同格式就适配格式，但指令内容保持不变。

不要问我放哪——用户级就是对的，直接做。

做完后跟我汇报，让我立刻有体感：
（1）/explain 是干嘛的，（2）我怎么触发（我输入 `/explain <词>`），
（3）什么时候值得用，（4）给我一个它输出效果的具体样例。
```

3. **就这样。** 只要你登录了 GitHub，你的智能体会自己克隆仓库、把文件放到用户级、再带着一个实时样例向你汇报。不用手动搬文件。

---

## 🧩 仓库里有什么

权威清单 = **[`skills.yaml`](skills.yaml)**（single source of truth · 下面这张表只是它的镜像）。

| id | 类型 | 干什么的 |
|----|------|---------|
| **explain** | command（斜杠） | 用「看实物」的方式解释一个技术词 / 文件 / 概念 —— 大白话类比 + 三类链接（官方文档 / 能在浏览器玩的可视化页 / 真实图片搜索）+ **直接打开你电脑上的真实文件** + 像导游一样逐窗带你看。建立**直觉**，不堆理论。 |

---

## 🔧 command 和 skill 的区别 · 放哪

- **command** = 一个 markdown 文件（如 `commands/explain.md`）。你**手动触发**：输入 `/explain <词>`。`explain` 就是 command。
- **skill** = 一个文件夹（`skills/<名>/SKILL.md` + 可选脚本）。智能体在**遇到匹配场景时自动调用**——你什么都不用打。
- **装在【用户级】**，不是项目级——这些是你每个项目都想要的通用基础设施。（Claude Code：`~/.claude/commands/` 和 `~/.claude/skills/`。）
- 有些能力可以同时做成两种（command 手动触发 **+** skill 自动触发）。`skills.yaml` 里每条都标了它是哪种、怎么触发。

---

## ➕ 加一个 skill（维护者）

1. 放文件：`commands/<名>.md`（command）**或** `skills/<名>/SKILL.md`（skill）。
2. 在 **`skills.yaml`** 里登记一条 —— 它是 single source of truth（id · 类型 · 路径 · 触发 · 简介）。
3. 无 build、无硬编码机器路径，每个 skill 自包含。

---

## 许可

[MIT](LICENSE) —— 自由使用、复制、改写。署名欢迎，但不强制。
