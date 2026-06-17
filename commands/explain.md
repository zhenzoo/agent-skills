---
description: "用「看实物」的方式解释一个技术词/文件格式/概念 — CS入门级讲解 + 结构化链接(官方/可视化HTML/真实图片) + 打开文件夹与代表性文件 + 逐窗引导，建立直觉(intuitive understanding)"
argument-hint: "<要解释的词/文件/概念，如 .pt、weights、dataset、ONNX、embedding>"
---

# /explain · 看实物式解释（建立直觉）

用户用 `/explain $ARGUMENTS` 让你解释一个技术概念 / 文件格式 / 词。

**核心 taste（最重要）**：目标是让用户建立**直觉（intuitive understanding）= 亲眼看到实物**，
而**不是**贴一堆文字和数字、画抽象架构图。能打开就打开、能可视化就可视化、能给真实图就给，然后**像导游一样逐窗引导他看**。
（一句话点题：「1607 个文件，我要亲眼见到这些文件铺开的样子才叫 intuitive。」）

下面 4 块每次都要做到：

## 1. CS 入门级讲解（大白话 + 类比）
- 像给计算机入门的人讲：它**是什么、干嘛用的**，用生活类比。结论先行，简短，不堆术语。
- 例：「.pt 本质是个 zip 压缩包，里面装着一层层的数字（权重），就是模型的『脑内容』。」

## 2. 结构化链接（每次必带，分三类）
- **官方文档 / 概念来源**：权威出处 URL。
- **可视化 / 交互 HTML**：能在浏览器里直接「看」的——如模型可视化 **https://netron.app**、格式规范交互页、在线 demo、playground。
- **真实图片搜索**：给 Google 图片链接，**关键词指向真实物件 / GUI 截图 / 实物照片**
  （如 `Netron model viewer screenshot`、`hex editor binary file screenshot`、`COCO annotation json example`），
  **绝不**用 "neural network architecture diagram" 这种抽象示意图（实证：这种没用）。
  - 形如 `https://www.google.com/search?q=<关键词>&tbm=isch`。

## 3. 打开实物给用户看（这个 command 的灵魂）
- **打开相关文件夹**：用系统默认方式打开，让用户看到文件在文件夹里**铺开**长什么样。
  - Windows(PowerShell)：`Invoke-Item "<path>"` · macOS：`open "<path>"` · Linux：`xdg-open "<path>"`。
- **用合适程序打开几个代表性文件**，让用户看到「打开后是什么样」：
  - 可读文本（.md/.txt/.json/.yaml/.csv/.py）→ 默认程序，或你环境里的编辑器（VSCode：`code "<path>"`）。
  - 二进制（.pt/.pth/.onnx/.safetensors）→ 它打开是乱码；**改为**：① `.pt`/`.pth` 本质是 zip，解压出来打开文件夹看内部结构；② 或引导用户拖进 Netron 看。
  - 图片（.jpg/.png/.webp）→ 默认看图器。
  - 数据集 → 打开 images 文件夹看几张真图 + 打开一个 label（.txt/.json）看标注长什么样。
- **跑命令 / 调 API，把真实输出当实物**：`<cmd> --help`、真实跑一次工具 / API 调用，把终端返回或截图直接展示——**输出本身就是「实物」**。
- **启动本地交互工具给 URL 实测**：能起 inspector / playground / dashboard 的，**起在后台 + 把 `http://localhost:<port>` 给用户点开**。⚠ **起了长驻进程要记一笔 + 收尾主动 offer kill**，别留孤儿进程占端口。
- **只开代表性的几个，别全开**：某文件夹有上千个文件，**只打开文件夹本身 + 挑 1–2 个典型文件**打开，别一次弹一堆窗口塞满屏幕。
- 临时解压 / 产物放可丢弃的 `_<名>_peek` 文件夹，并提醒用户「看完可删」。

## 4. 逐窗引导（既解释也带看）
- 每打开一个窗口，**明确说**：打开的是**哪个**窗口、里面是**什么内容**、**重点看什么**、怎么把它和上面的文字解释对应起来。
- 像导游：把「概念」↔「亲眼所见的实物」一一挂钩，帮他建立直觉。回复要短，重心在「打开 + 引导看」，不在堆字。

## 5. 进阶招式（实证有效）
- **对照法**：概念有关键区分（本地 vs 远程 / A vs B / 旧 vs 新）时，**同时开两个对照实物**并排看 + 配一张对照表（一眼看出差在哪）。
- **优先用用户自己项目里的实物**：同一概念若用户项目里就有现成例子（他的 config / 脚本 / 在跑的服务），**用他的**，别用通用 demo——在自己代码里看到，直觉最强。
- **概念↔实物对照表 OK**：表格只要**每一格都对应一个看得见的真东西**（某文件 / 某命令 / 某窗口）就鼓励用；被禁的只是「方框 + 箭头」那种抽象架构图。
- **点破同构**：发现几样东西其实是「同一个思路的变体」时说出来（如 CLI 的 `add_argument` ≈ MCP 的 `@tool` ≈ schema 的 `interface`，都是「声明我接受什么输入」）——一通百通。

## 工具备忘（OS / agent 通用 · 换环境按需调）
- 打开文件夹/文件（默认程序）：Windows `Invoke-Item "<path>"` · macOS `open "<path>"` · Linux `xdg-open "<path>"`。
- 文本类优先用你环境里的编辑器（VSCode：`code "<path>"`）。
- `.pt`/`.pth` 解压看内部：`python -c "import zipfile; zipfile.ZipFile(r'<pt>').extractall(r'<dst>')"`。
- 在线可视化首选 **Netron**（netron.app，拖入 .pt/.onnx/.safetensors 即可视化每一层）。
- 别污染项目目录：解压/截图等临时产物放 `_*_peek` 之类可删文件夹。

> 一句话：用户要「亲眼见到」。`/explain` = CS入门讲解 + 三类链接 + 打开代表性实物文件夹/文件 + 逐窗引导看，目标建立 intuitive understanding。
