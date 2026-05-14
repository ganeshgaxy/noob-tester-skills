# noob-visual-rca

Visual root cause analysis — classify visual diff failures (visual_regression, intentional_change, env_issue, flaky_render, threshold_issue), file issues for real regressions. Run after a visual verification run completes.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-visual-rca
```

## Usage

```
/noob-visual-rca
```

Classifies visual diff failures from a completed verification run into categories with confidence scores and suggested actions. Files issues automatically for confirmed visual regressions.
