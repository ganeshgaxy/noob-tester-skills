# noob-tester-skills

A collection of Claude Code testing skills and plugins.

## Quick Start

```bash
# Add the marketplace
claude plugin marketplace add ganeshgaxy/noob-tester-skills

# List available plugins
claude plugin marketplace list noob-tester-skills

# Install a plugin
claude plugin install <plugin-name>@noob-tester-skills
```

## Plugins

<!-- Add plugins here as you create them -->

## Adding a Plugin

Each plugin lives under `plugins/<plugin-name>/` with this structure:

```
plugins/<plugin-name>/
├── .claude-plugin/
│   └── plugin.json        # Plugin manifest
├── README.md              # Plugin docs
└── skills/
    └── <skill-name>/
        └── SKILL.md       # Skill instructions + frontmatter
```

After creating a plugin, add an entry to [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) in the `plugins` array.

## License

MIT
