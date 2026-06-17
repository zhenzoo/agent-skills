<div align="right"><a href="README.md"><b>English</b></a> · <a href="README.zh.md">中文</a></div>

# agent-skills

> Drop-in **skills & slash-commands for AI coding agents** (Claude Code, Codex, Kimi, GLM, …).
> You don't install them by hand — you hand one prompt to your agent and it sets everything up.

A small, growing collection of agent capabilities I find genuinely useful, packaged so anyone can add them in ~30 seconds.

---

## ⚡ Install in ~30 seconds (your agent does the work)

You do **not** need to know git. You need two things: **(1)** be signed in to GitHub, **(2)** paste one prompt to your agent.

1. **Copy this repo's URL** — the green **`<> Code`** button at the top of this page → `HTTPS` → copy the `git clone https://github.com/zhenzoo/agent-skills.git` line. (Or just copy the URL from your browser's address bar.)
2. **Paste this whole prompt to your agent** (Claude Code / Codex / Kimi / GLM / Claude / …):

```text
Clone https://github.com/zhenzoo/agent-skills.git
(I'm signed in to GitHub via the `gh` CLI — if I'm not, walk me through `gh auth login` first.)

From that repo, install the `explain` command at the USER level of my agent — this is
general infrastructure I want everywhere, NOT project-specific:
- Claude Code: copy commands/explain.md into ~/.claude/commands/  (or my CLAUDE_CONFIG_DIR/commands/).
- Other agents (Codex / Kimi / GLM / …): put it in the equivalent USER-level commands/prompts
  folder; adapt the file's format if that agent needs it, but keep the instructions intact.

Do NOT ask me where to put it — user level is correct, just do it.

When you're done, report back so I feel it immediately:
(1) what /explain does, (2) how I trigger it (I type `/explain <term>`),
(3) when it's worth using, and (4) ONE concrete example of its output.
```

3. **That's it.** If you're signed in to GitHub, your agent clones the repo, drops the file at user level, and reports back with a live example. No manual file juggling.

---

## 🧩 What's inside

Canonical list = **[`skills.yaml`](skills.yaml)** (single source of truth — the table below just mirrors it).

| id | type | what it does |
|----|------|--------------|
| **explain** | command (slash) | Explain a tech term / file / concept by **showing you the real thing** — a plain-language analogy + 3 kinds of links (official docs / an interactive page you can play with / a real-image search) + it **opens the actual files** on your machine + guides you window by window. Builds **intuition**, not theory. |

---

## 🔧 command vs skill — and where it goes

- **command** = one markdown file (e.g. `commands/explain.md`). You **trigger it manually** by typing `/explain <term>`. `explain` is a command.
- **skill** = a folder (`skills/<name>/SKILL.md` + optional scripts). The agent **auto-invokes** it when it detects the matching situation — you don't type anything.
- **Install at USER level**, not project level — these are general infrastructure you want in every project. (Claude Code: `~/.claude/commands/` and `~/.claude/skills/`.)
- Some capabilities can ship as both (a command for manual trigger **and** a skill for auto-trigger). Each entry in `skills.yaml` says which it is and how it triggers.

---

## ➕ Adding a skill (maintainers)

1. Drop the file(s): `commands/<name>.md` (command) **or** `skills/<name>/SKILL.md` (skill).
2. Register it in **`skills.yaml`** — the single source of truth (id · type · path · trigger · summary).
3. No build step. No hardcoded machine paths. Keep each skill self-contained.

---

## License

[MIT](LICENSE) — free to use, copy, adapt. Attribution welcome, not required.
