# mm-skills

Reusable AI skills managed as git submodules. Each repo in this org is a standalone skill that can be added to any project.

## Quick Start

```bash
# Add a skill to your project
git submodule add https://github.com/mm-skills/<skill-name> .agents/skills/<skill-name>

# Or use skill-manager (the only globally-installed skill)
.agents/skills/skill-manager/scripts/add.sh '{"name": "<skill-name>"}'

# Clone a project with all its skills
git clone --recurse-submodules https://github.com/you/your-project.git
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to report issues, propose changes, and submit pull requests.

## License

Unless otherwise noted, skills in this org are licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
