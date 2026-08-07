# Contributing to mm-skills

Thank you for your interest in contributing to our AI skills! This guide covers how to report issues, propose changes, and submit contributions.

## How Skills Work

Each skill in the `mm-skills` org is a standalone Git repo containing:

```
skill-name/
├── SKILL.md          # Instructions (required — YAML frontmatter + markdown body)
├── scripts/          # Executable automation (optional)
├── references/       # Additional docs loaded on demand (optional)
└── .upstream.json    # Provenance tracking for forked skills (if applicable)
```

Skills are consumed as **git submodules** in projects at `.agents/skills/<name>/`.

## Reporting Issues

1. Navigate to the skill's repo at `https://github.com/mm-skills/<skill-name>`
2. Open a new issue and include:
   - What you expected the skill to do
   - What actually happened
   - The prompt or context that triggered the issue
   - Your AI harness (Gemini/AGY, Claude Code, etc.)

## Proposing Changes

### For your own use

If you want to modify a skill for your own project, you don't need to contribute upstream. Just edit the submodule locally — your changes live in your project's `.agents/skills/<name>/` directory.

### To improve the shared skill

1. **Fork** the skill repo on GitHub
2. **Clone** your fork and create a feature branch
3. **Make your changes** — follow the skill structure conventions below
4. **Test** your changes by adding your fork as a submodule in a test project:
   ```bash
   git submodule add https://github.com/YOUR-USER/skill-name .agents/skills/skill-name
   ```
5. **Submit a Pull Request** against `main` with a clear description of what changed and why

### Skill structure conventions

- **SKILL.md frontmatter** must include `name` and `description` fields
- **Description** should be "pushy" — list scenarios where the skill should trigger, not just what it does
- **Instructions** use imperative form ("Do X" not "You should do X")
- **Scripts** accept a single JSON argument and return JSON responses
- **Keep SKILL.md under 500 lines** — use `references/` for longer docs

## Forked Skills

Some skills in this org were forked from third-party repos (e.g., Anthropic, Google). These have a `.upstream.json` file tracking their origin.

If your fix applies to the original upstream repo too, please also consider contributing there. The `.upstream.json` file in the skill directory tells you where it came from.

## Code of Conduct

Be respectful, constructive, and helpful. We're building tools that help people work with AI more effectively — contributions that serve that goal are welcome.

## License

Unless otherwise noted, skills in this org are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
