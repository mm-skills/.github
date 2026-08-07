# 🧠 Matt McNeill's Skill Library

A curated collection of **AI agent skills** for [Google Antigravity (AGY)](https://github.com/google/antigravity) and [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — each skill lives in its own repo, ready to be added to any project.

> Skills are portable instruction sets that extend what your AI coding assistant can do — from debugging workflows, to architecture planning, to session summarisation and beyond.

---

## ⚡ Quick Start

### Prerequisites

- [Git](https://git-scm.com/) — for submodule-based skill management
- [GitHub CLI (`gh`)](https://cli.github.com/) — authenticated with `gh auth login`
- [jq](https://jqlang.github.io/jq/) — for JSON processing

### 1. Install the Skill Manager

The [`skill-manager`](https://github.com/mm-skills/skill-manager) is the only skill you install globally — it handles everything else:

```bash
# Clone into your global skills directory
git clone https://github.com/mm-skills/skill-manager.git ~/.gemini/config/skills/skill-manager
```

### 2. Browse Available Skills

Ask your AI agent:

> `/skill-manager catalog`

Under the hood, this runs:

```bash
~/.gemini/config/skills/skill-manager/scripts/catalog.sh '{}'
```

This queries the `mm-skills` org and returns all available skills with descriptions.

### 3. Add Skills to Your Project

From within any git project, ask your agent:

> `/skill-manager add distillery`

Under the hood, this runs:

```bash
.agents/skills/skill-manager/scripts/add.sh '{"name": "distillery"}'
git commit -m "Add distillery skill"
```

Skills are added as **git submodules** at `.agents/skills/<name>/`, making them fully portable — anyone cloning your project gets the skills too with `git submodule update --init`.

---

## 🔀 Cross-Harness Support

This library works with both **Gemini / AGY** (`.agents/skills/`) and **Claude Code** (`.claude/skills/`). The skill manager keeps them in sync automatically via a symlink:

| Scenario | What happens |
|---|---|
| Only `.agents/` exists | Creates `.claude → .agents` symlink |
| Only `.claude/` exists | Creates `.agents → .claude` symlink |
| Both exist independently | You'll be prompted to choose which to keep |

Either way, both tools discover skills from the same location — no duplication needed.

---

## 🔧 Key Commands

| Command | What it does |
|---|---|
| `catalog.sh` | Browse all available skills in the org |
| `add.sh` | Add a skill to your project as a submodule |
| `update.sh` | Pull the latest version of a skill (or all skills) |
| `status.sh` | Check which skills are installed and their state |
| `push.sh` | Push local edits to a skill back upstream |
| `remove.sh` | Cleanly remove a skill from your project |
| `fork.sh` | Import a third-party skill into the org |

> **Tip**: You don't need to run these scripts manually — just ask your AI agent! The skill manager is designed to be invoked by your coding assistant.

---

## 🤝 Contributing

Contributions are welcome! Since each skill is its own repository:

- **🐛 Bug reports** — Open an issue on the specific skill's repo
- **✨ Feature requests** — Open an issue on the relevant skill's repo
- **📬 Pull requests** — Submit PRs directly to the skill repo you'd like to improve

For general questions, feedback, or ideas that don't fit a specific skill, open an issue on this [`.github`](https://github.com/mm-skills/.github) repo.

See **[CONTRIBUTING.md](https://github.com/mm-skills/.github/blob/main/CONTRIBUTING.md)** for full guidelines on skill structure, testing, and submitting changes.

---

## 📖 Skill Anatomy

Every skill repo follows a standard structure:

```
skill-name/
├── SKILL.md          # Main instruction file (required)
├── scripts/          # Helper scripts and utilities
├── examples/         # Reference implementations
├── references/       # Additional documentation
└── resources/        # Templates, assets, etc.
```

The `SKILL.md` file is the entry point — it contains YAML frontmatter with the skill's `name` and `description`, followed by detailed instructions your AI agent reads and follows.

---

## 📄 Licence

Unless otherwise noted, skills in this org are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0). Individual skills may have their own licences — check each repo for details.

---

<p align="center">
  <sub>Maintained by <a href="https://github.com/mcneillm">Matt McNeill</a> · Built for the AI-native dev workflow</sub>
</p>
