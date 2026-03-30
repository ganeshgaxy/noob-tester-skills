# noob-testcase

Generate BDD and traditional test cases from tickets with deep codebase analysis. Produces direct functional, impact regression, and general regression test cases.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-testcase
```

## Usage

```
/noob-testcase
```

Reads wide for context (parent + siblings + ticket), writes narrow from MR diff — generates direct functional, impact regression, and general regression test cases with full BDD format.
