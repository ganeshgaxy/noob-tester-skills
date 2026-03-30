# noob-tester-skills

Claude Code plugins for [noob-tester](https://www.npmjs.com/package/@ganeshgaxy/noob-tester) — an AI-powered QA testing system that turns Claude Code into a fully autonomous test engineer.

Give it a ticket and a target URL — it reads the requirements, analyzes the codebase, writes test cases, executes them via browser automation and direct API testing, finds bugs, and delivers a comprehensive report with root cause analysis.

## Prerequisites

- [noob-tester CLI](https://www.npmjs.com/package/@ganeshgaxy/noob-tester) — `npm install -g @ganeshgaxy/noob-tester`
- [Claude Code](https://claude.com/claude-code)
- [agent-browser](https://github.com/vercel-labs/agent-browser) — for UI test execution
- [Atlassian MCP](https://github.com/anthropics/claude-code/blob/main/docs/mcp.md) — for ticket reading and updates
- git, curl, jq

## Install

```bash
# Add the marketplace
claude plugin marketplace add ganeshgaxy/noob-tester-skills

# List available plugins
claude plugin marketplace list noob-tester-skills

# Install all testing plugins
claude plugin install noob-tester@noob-tester-skills
claude plugin install noob-analyze@noob-tester-skills
claude plugin install noob-plan@noob-tester-skills
claude plugin install noob-testcase@noob-tester-skills
claude plugin install noob-explore@noob-tester-skills
claude plugin install noob-api-explore@noob-tester-skills
claude plugin install noob-rca@noob-tester-skills
claude plugin install noob-report@noob-tester-skills

# Install utility plugins
claude plugin install bb@noob-tester-skills
claude plugin install subagent-metrics@noob-tester-skills
```

## Plugins

### Testing Pipeline

| Plugin | Skill | What it does |
|--------|-------|-------------|
| **noob-tester** | `/noob-tester` | Main orchestrator — routes to the right skill based on what you ask. Use for full QA pipelines |
| **noob-analyze** | `/noob-analyze` | Deep analysis: gap, requirements, feasibility, and impact analysis against the codebase. Runs before dev starts |
| **noob-plan** | `/noob-plan` | Test planning for dev-complete tickets — reads MRs, code diffs, produces plan with steps, blockers, coverage gaps |
| **noob-testcase** | `/noob-testcase` | Generate BDD and traditional test cases from tickets with deep codebase analysis |
| **noob-explore** | `/noob-explore` | Browser automation — execute UI test cases via run packs, UI map learning, axe-core a11y audit. One test case per invocation |
| **noob-api-explore** | `/noob-api-explore` | API testing — execute ALL api-layer test cases in one run via curl/jq, per-role auth, per-test cleanup |
| **noob-rca** | `/noob-rca` | Root cause analysis — classify failures (env/flaky/bug/data/network), suggest actions. Run after test execution |
| **noob-report** | `/noob-report` | Generate comprehensive report with verdict, RCA, a11y results. Notify Slack, update ticket |

### Utilities

| Plugin | What it does |
|--------|-------------|
| **bb** | Bitbucket CLI expertise for managing pull requests, pipelines, and repositories |
| **subagent-metrics** | Captures Claude Code subagent metrics (tokens, tools, duration) and logs them to noob-tester sessions |

## Usage

In Claude Code:

```
> Use noob-tester to test PROJ-123 at https://staging.app.com
> /noob-analyze PROJ-123
> /noob-testcase PROJ-123
> /noob-plan PROJ-123
> /noob-explore test the login page at https://staging.app.com
> /noob-api-explore run the API tests for PROJ-123
> /noob-rca analyze the failures
> /noob-report generate a report for PROJ-123
```

### Pipeline Flow

```
/noob-analyze  →  /noob-testcase  →  /noob-plan  →  /noob-explore + /noob-api-explore  →  /noob-rca  →  /noob-report
  (analyze)        (test cases)       (plan)          (execute)                             (classify)     (report)
```

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
