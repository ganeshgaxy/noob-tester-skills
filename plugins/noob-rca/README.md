# noob-rca

Root cause analysis — classify failures (env/flaky/bug/data/network), update patterns, suggest actions. Run after test execution.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-rca
```

## Usage

```
/noob-rca
```

Classifies failures from a completed run pack into categories (env_issue, flaky_selector, actual_bug, test_data_issue, network, auth_issue, timeout, unknown) with confidence scores and suggested actions.
