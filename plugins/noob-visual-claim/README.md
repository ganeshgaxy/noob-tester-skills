# noob-visual-claim

Claim the next visual test case from a visual run. Supports creating a new run (first invocation) or resuming an existing one. Returns $CLAIM for noob-visual to execute.

## Installation

```bash
claude plugin add /path/to/noob-tester-skills/plugins/noob-visual-claim
```

## Usage

```
/noob-visual-claim
```

Claims one visual test case entry from a visual run. Returns `$CLAIM` JSON with the claimed entry and its full test case data. Pass `$CLAIM` to `noob-visual` for execution.
