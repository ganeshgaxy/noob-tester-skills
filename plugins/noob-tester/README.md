# noob-tester

Automated QA tester for web applications. Can run full test cycles or individual phases — analysis, test case generation, planning, browser exploration, reporting.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-tester
```

## Usage

```
/noob-tester
```

The orchestrator skill — routes to the appropriate phase (analyze, plan, testcase, explore, api-explore, rca, report) based on user intent. Use for full QA pipelines or when unsure which specific skill to invoke.
