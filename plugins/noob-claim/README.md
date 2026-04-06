# noob-claim

Claim test cases from run packs. Supports claiming next unclaimed test, claiming by name (with validation), and retrying specific tests.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-claim
```

## Usage

```
/noob-claim
```

Claims a test case from a run pack for execution. Handles three modes: claim next unclaimed test, claim by name with validation, and retry specific tests. Returns a test entry object to pass to noob-explore for execution.
