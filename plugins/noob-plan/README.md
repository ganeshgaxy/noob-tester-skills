# noob-plan

Create a test plan for a dev-complete ticket. Reads MRs, analyzes code diffs, checks deployed target, produces plan with steps, blockers, coverage gaps.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-plan
```

## Usage

```
/noob-plan
```

Creates a comprehensive test plan after development is complete — reads wide for context, writes narrow from MR diff and ticket requirements.
