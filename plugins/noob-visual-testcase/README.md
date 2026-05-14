# noob-visual-testcase

Generate visual test cases (BDD/traditional + visual steps config) from tickets. Maps test steps to visual capture config (screenshot vs snapshot, full-page vs scoped, per-step thresholds).

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-visual-testcase
```

## Usage

```
/noob-visual-testcase
```

Generates visual test cases with BDD or traditional format plus visual steps configuration that specifies which steps capture screenshots and how, including diff type, scope, and per-step thresholds.
